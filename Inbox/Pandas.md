

01-07-2025 11:32

Status: #in_progress

Tags:

# Pandas

[[Pandas#handle Nan|handle Nan]]
[[Pandas#filtering|filtering]]
[[Pandas#Time Series|Time Series]]
- [[Pandas#plot|plot]]
	- [[Pandas#day of week|day of week]]
	- 

## Merge
## Filter rows


## handle NaN
### check existents
``` python
df['app_name'].isna()
# or at least one Nan
df['app_name'].isna().any()
```
### drop rows
``` python
# drop if one of the column is Nan
df = df.dropna(subset=['A', 'B'], axis=0)
# drop if both columns are Nan
df = df.dropna(subset=['A', 'B'], how='all')

```
### default value

## filtering

### group
``` python
df = pd.DataFrame({
    'category': ['A','A','A','B','B','C','C','C','C','C','D','D'],
    'value': [10, 20, 30, 5, 6, 8, 9, 10, 11, 12, 13, 14]
})
```
filter count > 5
``` python
counts = df.groupby('category')['value'].count()
filtered = df[df['category'].isin(counts[counts > 5].index)]

```
df[expression] - expression should be indices of df
``` python
filtered = df.groupby('category').filter(lambda x: len(x) > 5)
```

## Time Series
### datetime conversion
``` python
# for example 2019 Jan
z["Month"] = z["Month"].dt.strftime("%Y %b")
# yearly
.dt.strftime("%Y")
# daily
.dt.strftime("%Y-%m-%d")
# subdaily
.dt.strftime("%Y-%m-%d %H:%M:%S")
# 1987-06
.dt.to_period('M')

```

### date at the index
``` python
df["Date"] = pd.to_datetime(df["Date"], format="%Y-%m-%d")
df.set_index('Date', inplace=True)
# or while reading from csv
df1 = pd.read_csv("bitcoin_price.csv", index_col="Date", parse_dates=True)
```
![[Pandas_ts1.png]]

#### long table -> bright table
It takes the **innermost index level (`Store`)** and moves it to columns.
This is equivalent to a *pivot table*
``` python
df_10.groupby([df_10.index.day_of_week, 'Store'])['Sales'].mean().unstack()

```
- Rows → `day_of_week`
- Columns → `Store`
- Values → mean Sales
the *unstack* is used usually for preparation for plotting.
![[Pandas_ts2.png]]
![[Pandas_ts3-1.png|400]]

### plot
#### day of week
x axis - days of the week.
index - date
``` python
def plot_series(series_df, cols, title=''):
    g = series_df.groupby(series_df.index)[cols].mean()
    fig, ax = plt.subplots(figsize=(10,5))
    for col in cols:
        ax.plot(g.index, g[col], label=col)
    ax.legend()
    weekday_labels = (g.index.dayofweek + 1) % 7 + 1
    ax.set_xticks(g.index)
    ax.set_xticklabels(weekday_labels)
    plt.tight_layout()   # prevents label cutoff
    plt.show()
```

#### two y axis
``` python
# first plot
df["30_day_rolling_vol"] = df["Volume"].rolling(window=30).mean()df[["30_day_rolling_vol"]].plot(legend=True)
# second plot
ax = df["Close"].plot(secondary_y=True, legend=True)
ax.set_ylabel("Closing Price")
plt.show()
```
![[Pandas_2_y_axis.png|500]]
## display
display full column (not scientific notation)
``` python
pd.set_option('display.float_format', '{:.5f}'.format)
```

[[pandas_TimeSeries]]

## My Questions


## References

