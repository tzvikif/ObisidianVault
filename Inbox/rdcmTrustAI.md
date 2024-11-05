

28-10-2024 13:23

Status: #in_progress

Tags:

# rdcmTrustAI

### 28-10-2024

- [x] send *pred_status* , *embeddings*, binns  for *avg_CELL_AVG_RSRQ* to Yuval.
- [x] send binns (RSRQ) to Udi

### 30-10-2024

- [x] understand [[Temporal Graph Networks for Deep Learning on Dynamic Graphs]]
	- [ ] make notes of the paper
- [ ] go over implementation at [github](https://github.com/twitter-research/tgn/tree/master)
- [ ] train with  Radcom dataset
- [ ] collect new data with overlapping windows
	- [ ] train with new data

### 31-10-2024

trained using **avg_CELL_AVG_RSRQ** as label
used the following features:
['total_bytes_received_by_ms', 'total_bytes_send_by_ms', 'max_MEAN_THROUGHPUT_SENT', 'avg_MEAN_THROUGHPUT_SENT', 'var_MEAN_THROUGHPUT_SENT', 'max_MEAN_THROUGHPUT_RECEIVED', 'avg_MEAN_THROUGHPUT_RECEIVED', 'var_MEAN_THROUGHPUT_RECEIVED', 'max_EFFECTIVE_THROUGHPUT_UL', 'avg_EFFECTIVE_THROUGHPUT_UL', 'var_EFFECTIVE_THROUGHPUT_UL', 'med_EFFECTIVE_THROUGHPUT_UL', 'max_EFFECTIVE_THROUGHPUT_DL', 'avg_EFFECTIVE_THROUGHPUT_DL', 'var_EFFECTIVE_THROUGHPUT_DL', 'med_EFFECTIVE_THROUGHPUT_DL', 'max_RTT', 'avg_RTT', 'med_RTT', 'var_RTT', 'max_INTERNET_LATENCY', 'avg_INTERNET_LATENCY', 'var_INTERNET_LATENCY', 'med_INTERNET_LATENCY', 'max_RAN_LATENCY', 'avg_RAN_LATENCY', 'var_RAN_LATENCY', 'med_RAN_LATENCY', 'max_TTFB', 'avg_TTFB', 'var_TTFB', 'med_TTFB', 'distinct_imsi_count', 'X2_HO_TRANSFER_OG', 'sum_X2_HO_TRANSFER_OG', 'X2_HO_ATTEMPT_OG', 'RRC_TOT_CONN_EST', 'RRC_CONN_RECONF_ATT', 'RRC_CONN_RECONF_SUCC', 'sum_RRC_RE_EST_ATT_HO_FAIL', 'sum_RRC_RE_EST_CAUSE_HO_SUCC', 'sum_RRC_RECONF_HO_INTRA', 'sum_RRC_RECONF_SUCC_HO_INTRA', 'sum_RRC_RECONF_HO_X2', 'sum_RRC_RECONF_SUCC_HO_X2', 'sum_RRC_RECONF_HO_S1', 'sum_CONNECTED_TIME_NR', 'sum_RRC_RECONF_SUCC_HO_S1', 'avg_NR_UE_AVG_RSRP', 'avg_NR_UE_AVG_SINR', 'rrc_connect_success_ratio', 'rrc_ho_intra_success_ratio', 'rrc_ho_x2_success_ratio', 'rrc_reest_success_fail_diff']

resnet: 0.723
gnn: 0.745

### 03-11-2024

**Udi** sent the following:
- radcom_rca_xai_aps.csv
- radcom_rca_xai_aucs.csv
- rca_results.csv
saved them at:
*C:\Users\tzviki.fisher\OneDrive - RADCOM Ltd\research_phase_2\data\processed_01-04-07\obfuscated\Ariel\Round2*


>Hi Tzviki,
Please note that for Radcom's use case, where there are no normal patterns to learn from, we treat the RCA process as a two-stage approach. First, we identify past time events. Then, we focus on suggesting which cell properties might be responsible for the abnormal behavior. Within this round, the anomalies are the only events within the 15-minute window. Therefore, the RCA starts by explaining the cell properties, utilizing XAI.
This time, we are only considering the five features listed below for the RCA process. Since we didn't receive new prediction results from your updated model, we used the previous labels and marked them as anomalies.
We would appreciate your feedback on this, including a quantitative analysis of our result accuracy.

we had a meeting.
the goal is to as before to change the most important feature and observe the model prediction.



## References

