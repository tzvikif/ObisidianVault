

22-10-2024 19:00

Status: #in_progress

Tags: #radcom

# Zoom

[[rdcmZoom#References|References]]


- Run sanity check on the model. 
- where is the testset??
	- i can split to train/test and retrain and evaluate.


## 24-10-2024
### lab collected data

[[ 588  152   14]
 [  67 1855  127]
 [   6  117 1424]]
trained with *out_receiving_2908_all_temp_merge.csv*
testset *testset_2410.csv*
model *model_24102024_2118.ubj*

	precision    recall  f1-score

   0       0.89      0.78      0.83       754
   1       0.87      0.91      0.89      2049
   2       0.91      0.92      0.92      1547

### Rakuten collected data
	pred
[[311   0   0]
 [ 96   0   0]
 [144   0   0]]


## 27-10-2024

- trained *D:\zoom\nitin_22_10\train\pcaps\zoom_test2_filtered_gtp.pcapng* and tested it on *D:\zoom\nitin_22_10\test\pcaps\zoom_test3_filtered_gtp.pcapng*
[[37  0  3]
 [ 3  0  2]
 [ 2  0 23]]
  - trained both pcaps
  [[52  3  9]
 [10  5  5]
 [ 5  4 24]]

- trained *D:\zoom\nitin_22_10\test\pcaps\zoom_test3_filtered_gtp.pcapng* and tested it on *D:\zoom\nitin_22_10\train\pcaps\zoom_test2_filtered_gtp.pcapng*
[[86 98  2]
 [ 3 13  1]
 [69 73  0]]

## 12-12-2024

i got few pcaps, labels from Rakuten.
a comparison between my code output and probe output.
- how to handle *gtp* pcaps?


## 15-12-2024

- [x]  check ports that weren't detected  at temp\data_debug (Qosmos)
- [x] compare # tuples
- [ ] number of packets
- [x] number of bytes upload / download
- [ ] display graphs, probe and my code. number of packet and bytes in each tuple.


## 17-12-2024

- same raw data input to the *probe* and the *python code*. be able to explain tuple output, against the labels
- build parser to extract features from the probe to *.csv.
- have "same" features in the *probe* and *python code*
- find points which illegibly Qosmos drops packets.
- add timestamp for each feature
- run probe on all pcaps extract features and train model.
- check diversity of labels on Nitin output.

Histogramm from the 12.12 csv files.
i asked Nitin to try to divide the fps more evenly.
![[rdcmZoom.png|400]]

#### Questions

- why not start tuples on start of a second?
- number of tuples in probe as the number in the code.
- figure out when Qosmos omit tuples

## 24-12-2024

the number of tuples and the number of features are not the same at the probe output. *Ran* is checking it.

## 26-12-2024

i trained on:
- Zoom_test1_11thDec_full_probe_ts_output.txt
- Zoom_test2_11thDec_full_probe_ts_output.txt
![[rdcmZoom-1.png]]

### 29-12-2024

ran probe on pcaps. and got the following output <size, name>:
- 129K  Zoom_test1_11thDec.txt
- 57K Zoom_test1_12thDec.txt
- 210K Zoom_test2_11thDec.txt
- 58K Zoom_test2_12thDec.txt
- 0 Zoom_test3_11thDec.txt - video not detected
- 29K Zoom_test3_12thDec.txt
- 170K Zoom_test4_11thDec.txt
- 22K Zoom_test4_12thDec.txt
- 0 Zoom_test5_12thDec.txt - video not detected
- 52K Zoom_test6_12thDec.txt
- 0 Zoom_test7_12thDec.txt - video not detected
- 0 Zoom_test8_12thDec.txt - video not detected


### 30-12-2024
- updated the already opened ticket with more pcaps.
trained model with 11-12.12 

![[rdcmZoom-2.png]]


### 29-01-2025
zoom_test6_27thDec.pcap
![[rdcmZoom-5.png]]
ipv4 + ipv6 using 8801

zoom_test5_27thDec.pcap
![[rdcmZoom-6.png]]
zoom bytes > tunneling ??
same in zoom_test7_27thDec.pcap

### 06-02-2025

#### browsing on cell phone
``` bash
npm install -g local-ssl-proxy

http-serve -p 3000 .
local-ssl-proxy --source 3001 --target 3000

local-ssl-proxy --source 8766 --target 8765
python websocketSrv.py -folder <output_folder_name>
```

**Notes**
use https and port 3001:
``` javascript
https://<CDN_machine_ip>:3001/meeting.html...
```

in meeting.js
use wss:
``` javascript
const webSocketUrl = 'wss://<webSocket_ip>:8766';
```

### 16-02-2025

I have probe output from 12th, 23th, 27th December.
53 files. 41 of them are not empty.
1. train 80/20 train/test. 
2. make the test of separate pcaps. 37 for training and 4 for testing.

#### 80/20
![[rdcmZoom-7.png]]

zoom_test6_27thDec.pcap
27122024104927.csv

zoom_test14_27thDec.pcap
27122024115746.csv



## 13-03-2025
test bad results video_detection:
- ml_kpi_debug_decoder_1_scenario_12_3.txt
- ml_kpi_debug_decoder_1_scenario_13_4.txt


**ml_kpi_debug_decoder_1_scenario_12_1**
std_ul_bytes              0.514883
mean_total_dl_bytes       0.394299
mean_total_ul_bytes       0.021788

**ml_kpi_debug_decoder_1_scenario_12_2**
prev3_upload_std          0.627283
mean_total_ul_bytes       0.233785
mean_total_dl_bytes       0.066917

**ml_kpi_debug_decoder_1_scenario_12_1**
**ml_kpi_debug_decoder_1_scenario_12_2**
mean_total_dl_bytes       0.868490
mean_total_ul_bytes       0.013440
prev3_total_ul_packets    0.011890

**ml_kpi_debug_decoder_1_scenario_12_3**
prev3_upload_std          0.558734
prev2_upload_std          0.369018
prev2_download_std        0.014094

**ml_kpi_debug_decoder_1_scenario_12_1**
**ml_kpi_debug_decoder_1_scenario_12_2**
**ml_kpi_debug_decoder_1_scenario_12_3**
prev3_upload_std          0.451615
mean_total_dl_bytes       0.322295
prev1_mean_download       0.079456

**ml_kpi_debug_decoder_1_scenario_12_4**
prev2_upload_std          0.711926
prev3_upload_std          0.225920
mean_total_dl_bytes       0.040735

**ml_kpi_debug_decoder_1_scenario_12_1**
**ml_kpi_debug_decoder_1_scenario_12_4**
mean_total_dl_bytes       0.733622
prev1_total_dl_packets    0.162258
total_dl_packets          0.032986

**ml_kpi_debug_decoder_1_scenario_12_2**
**ml_kpi_debug_decoder_1_scenario_12_4**
prev2_total_dl_packets    0.264131
mean_total_dl_bytes       0.253767
prev1_total_dl_packets    0.253266

**ml_kpi_debug_decoder_1_scenario_12_3**
**ml_kpi_debug_decoder_1_scenario_12_4**
prev3_total_ul_packets    0.429938
prev3_upload_std          0.272658
prev1_mean_download       0.127759

**ml_kpi_debug_decoder_1_scenario_12_1**
**ml_kpi_debug_decoder_1_scenario_12_2**
**ml_kpi_debug_decoder_1_scenario_12_4**
mean_total_dl_bytes       0.340314
prev3_total_dl_packets    0.317139
prev1_total_dl_packets    0.197154

**ml_kpi_debug_decoder_1_scenario_12_5**
std_ul_bytes              0.492736
prev3_upload_std          0.410360
total_dl_packets          0.083939

**ml_kpi_debug_decoder_1_scenario_12_3**
**ml_kpi_debug_decoder_1_scenario_12_5**
prev3_upload_std          0.537731
prev2_download_std        0.189800
total_ul_packets          0.054397

## 23-03-2025
working on scenario 1, 2, 3
collect 5 pcaps -> test the model.
if poor results add to the model.

## 27-03-2025
B
- sv
- sv
- s
- s
A
- v+
- v-
- v+
- v-
1, 3
3, 1
2, 4
4, 2
### 02-04-2025
problem with video off  in uplink
- build dataset from tirans pcap
	- manual labeling
- drop scenario share screen -> check results 
- add more video off 

### 06-04-2025
![[rdcmZoom-8.png]]

### 20-04-2025
![[rdcmZoom-9.png]]
הדאטה של טירן.
לבדוק מתי צודק טועה בעזרת הקלאסטר. להוסיף לדאטהסט fps pred , fps expected

 a
 ### 07-05-2025
 tiran - the host is recording
## References

https://jira-prod.radcom.co.il:8443/browse/ACE-24253
[Nexus](http://nexus3-prod.radcom.co.il:8081/#browse/browse:automation_files)
[[Tabular Features time series]]
