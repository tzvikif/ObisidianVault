

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

resets xmls
``` bash
sh hostinstallhelper.sh swoffline
```
## My Questions


## References

