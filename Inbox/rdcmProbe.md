	

09-12-2024 10:05

Status: #in_progress

Tags:

# Probe

[[rdcmProbe#Run pcap with GTP|setup for gtp]]
[[rdcmProbe#run pcap with pure gi|setup for pure gi]]
[[rdcmProbe#Models|models]]



## Update 

 ``` bash
 cd /hpadir/
```
 
## Run pcap with GTP

choose the connection

![[Probe.png]]

filter by that connection

![[Probe-1.png|1000]]

find the *client hello* and use the *destination IP*
### *config/ggsnlist.xml*
![[Probe-2.png]]
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
### for zoom
``` xml
  <video_ml debug_log_enabled="yes" enabled="yes" ignore_rejected_frames_enabled="no" record_video_frames="no" zoom_offload_by_ports="yes" zoom_offload_min_bpp="0" zoom_offload_min_packets="1" zoom_offload_min_pps="0" zoom_offload_timeout_msec="0" zoom_ports="8801,8802,8803,8804,8805,8806,8807,8809,8810"/>
```
config/capture.xml:
``` xml
<auto_detector name="radius" enable="no" number_of_frames_to_detect="100000"/>
```

resets xmls
``` bash
sh hostinstallhelper.sh swoffline
```

### */arch/video_ml/files/config/constants_mobile_line.ini*
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
set to *yes*
### *config/elements.xml*
![[rdcmProbe-1.png]] 
insert ip under *<element_class type="ipv4_pure_gi">*
## Offlinegenerator
**use original timestamp**
### *hpaofflinegen.xml*
``` xml
use_original_timestamps="file_time_stamp"
```

## Models
which models are being used:
``` bash
arch/video_ml/files/xgmodels
```
Note: the models are copied to archive . if you want to change model go to [[rdcmProbe#update model|update model]]

### update model
``` bash
# update model
```

## My Questions


## References

