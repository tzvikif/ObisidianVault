	

09-12-2024 10:05

Status: #in_progress

Tags:

# Probe

[[rdcmProbe#Run pcap with GTP|setup for gtp]]
[[rdcmProbe#run pcap with pure gi|setup for pure gi]]
[[rdcmProbe#Models|models]]
[[rdcmProbe#Record CDRs|Record CDRs]]

## Web Monitor
	http://172.16.10.140:8080/monserver/AjaxClient/JSP/Login/Login.jsp


### solving problems
``` bash
[root@swprobe-rand ~]# systemctl stop wildfly_27  
ראיתי שגם אחרי שהסרוויס נעצר עדיין הוובמון מראה שגיאה  
[root@swprobe-rand ~]# pkill -9 java

אחרי זה שעשיתי רענון לא הייתה תגובה  
[root@swprobe-rand ~]# systemctl start wildfly_27
```

## Set Environment
``` shell
ln -sfn /home/nfsroot/cloned_maveriqprobe/maveriqprobe /hpadir
```
also
``` shell
mkhpadir cloned_maveriqprobe/maveriqprobe
```
## Update 

 ``` bash
 cd /hpadir/
 ```
 
## DNS
sometimes the ip is *ipv6*  and the dns request is in *ipv4* 
in that case you must add both. 

to elements.xml / ggsnlist.xml
![[rdcmProbe_dns.png]]

## Run pcap with GTP

choose the connection

![[Probe.png]]

filter by that connection

![[Probe-1.png|1000]]

find the *client hello* and use the *destination IP*
### *config/ggsnlist.xml*
![[Probe-2.png]]

### enable DNS
### *config/hpagidecoder* 
``` xml
<dns_gi_correlation enabled="yes" dns_record_timeout_seconds="86400"/>
```

### *config/hpagidecoder* 
``` xml
data_debug_enabled="yes"

  <video_ml enabled="yes" debug_log_enabled="yes" ignore_rejected_frames_enabled="no" record_video_frames="no"/>  

  <dns_gi_correlation enabled="yes" dns_record_timeout_seconds="86400"/>  
<dpi_flow_detection enabled="yes">

        <!-- Zoom 88928 -->  
<flow_detection dpi_id="88928" />  
</dpi_flow_detection>
```
set *pure_gi_enabled* to *no*

### for zoom
``` xml
  <video_ml debug_log_enabled="yes" enabled="yes" ignore_rejected_frames_enabled="no" record_video_frames="no" zoom_offload_by_ports="yes" zoom_offload_min_bpp="0" zoom_offload_min_packets="1" zoom_offload_min_pps="0" zoom_offload_timeout_msec="0" zoom_ports="8801,8802,8803,8804,8805,8806,8807,8809,8810"/>
```
config/capture.xml:
``` xml
<auto_detector name="radius" enable="no" number_of_frames_to_detect="100000"/>
```

config/packetrouter.xml
``` bash
# remove RADIUS ???
```


### *arch/video_ml/files/config/constants_mobile_line.ini*
``` 
EGIN_SECTION mobile:zoom  
average_trhoughput_threshold=100  
traffic_consistency_trheshold=0.1  
consistent_traffic_min_duration=2  
max_gap_allowed=4  
prebuffering_ahead_time=0  
tuple_min_bpp=1  
high_traffic_window_size=5  
silence_min_duration=57  
threshold=100  
END_SECTION
```
## run pcap with pure gi
### *config/hpagidecoder* 
![[rdcmProbe.png]]
set *pure_gi_enabled* to *yes*
### *config/elements.xml*
![[rdcmProbe-1.png]] 
insert ip under *<element_class type="ipv4_pure_gi">*
``` xml
<element name="ipv4elem3" address="192.168.0.103" />
```
**Note**: *name* attribute must me different for every entry.

## Offlinegenerator

#### proc_config.xml
search for  offlinegen.xml switch enabled="yes"

``` xml
<process>
      <proc_attr accumulated_packets_size="50" async_proxy="no" config_file_path="/hpadir/config/hpaofflinegen.xml" enabled="yes" hmop_port_lower_bound="9060" hmop_port_upper_bound="9069" instance_id="1" ip_address="127.0.0.1" machine_name="1234" proc_name="hpaofflinegen" uds_lower_bound="9050" uds_source_lower_bound="8960" uds_source_upper_bound="9049" uds_upper_bound="9059" wait_for_signal="0"/>
    </process>
    <process>
```
### *hpaofflinegen.xml*
``` xml
use_original_timestamps="file_time_stamp"
```

## Resets xmls
``` bash
sh hostinstallhelper.sh swoffline
```


## Models
**on build (make) time the models are copied** from
*hpadir/source/extlibs/video_ml* to *arch/video_ml/files/xgmodels*

which models are being used:
``` bash
arch/video_ml/files/xgmodels
```
Note: the models are copied to archive . if you want to change model go to [[rdcmProbe#update model|update model]]
### update model
in the file *arch/video_ml/files/config/ml_api_xgboost.ini*
update the name of the model if needed. copy the new model to *arch/video_ml/files/xgmodels*
## Build
``` bash
cd /hpadir
# dry run
# git clean -n -d
git clean -f -d
git checkout .
make BLD=rebuild

# after build is done run this to reset config to fit current version scheme:
sh /hpadir/hostinstallhelper.sh swoffline
```

check */hpadir/log* for compilation issues

## SNI filter
*/hpadir/source/processes/hpagidecoder/hpagidecoderimpl/CrVideoKpiMngr.h*

## Record CDRs

``` bash
sh /hpadir/RecordAllCDRS.sh start
# when done:
sh /hpadir/RecordAllCDRS.sh stop
# cdrs in /hpadir/cdrs.txt
```

## My Questions


## References

