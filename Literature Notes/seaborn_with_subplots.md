

2024-08-15 11:24

Status:

Tags: seaborn, matplotlib

## seaborn_with_subplots

```python
import matplotlib.pyplot as plt
import seaborn as sns

fig, axs = plt.subplots(2, 1, figsize=(24,16), sharex=True)
sns.lineplot(ax=axs[0],  data=df, x='interval_start', y='med_TTFXB')
sns.lineplot(ax=axs[1], data=df, x='interval_start', y='max_MEAN_THROUGHPUT_RECEIVED', color='r' )
axs[2].set_ylim(1e5, 1e10)
```


## References

