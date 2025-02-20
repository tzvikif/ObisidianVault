

09-12-2024 10:05

Status: #in_progress

Tags:

# Probe

## Update 

 ``` bash
 cd /hpadir/
```
 
## run pcap with GTP

choose the connection

![[Probe.png]]

filter by that connection

![[Probe-1.png|1000]]

find the *client hello* and use the *destination IP*
update *config/ggsnlist.xml*

![[Probe-2.png]]

in *config/hpagidecoder* 
``` xml
data_debug_enabled="yes"

  <video_ml enabled="yes" debug_log_enabled="yes" ignore_rejected_frames_enabled="no" record_video_frames="no"/>  

  <dns_gi_correlation enabled="yes" dns_record_timeout_seconds="86400"/>  
<dpi_flow_detection enabled="yes">

        <!-- Zoom 88928 -->  
<flow_detection dpi_id="88928" />  
</dpi_flow_detection>
```

for zoom
``` xml
  <video_ml enabled="yes" debug_log_enabled="yes" ignore_rejected_frames_enabled="no" record_video_frames="no" zoom_offload_by_ports="yes" zoom_ports="8801,8802" zoom_offload_min_pps="0" zoom_offload_timeout_msec="3000" zoom_offload_min_packets="300" zoom_offload_min_bpp="250"/>
```


resets xmls
``` bash
sh hostinstallhelper.sh swoffline
```

*/hpadir/arch/video_ml/files/config/constants_mobile_line.ini*
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

**use original timestamp**
*hpaofflinegen.xml*
``` xml
use_original_timestamps="yes"
```


capture -> protocols 
decoder distribution לבדוק שהכל מגיע לאותו decoder

kpi 






## My Questions


## References

