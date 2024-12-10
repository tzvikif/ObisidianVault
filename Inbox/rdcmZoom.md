

22-10-2024 19:00

Status: #in_progress

Tags: #radcom

# Zoom

- Run sanity check on the model. 
- where is the testset??
	- i can split to train/test and retrain and evaluate.

*24-10-2024* 
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


*27-10-2024*

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


## References

