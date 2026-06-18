

01-07-2025 11:32

Status: #in_progress

Tags:

# Pandas

[[Pandas#handle Nan|handle Nan]]
[[Pandas#filtering|Filter rows]]
- [[Pandas#filter row if any column satisfy a condition|filter row if any column satisfy a condition]]

[[Pandas#Group Filtering|Group Filtering]][[Pandas#filtering|]]
[[Pandas#Time Series|Time Series]]
- [[Pandas#plot|plot]]
	- [[Pandas#day of week|day of week]]
	- 

[[Pandas#from long format to wide format|from long format to wide]]
[[Pandas#from wide to long|from wide to long]]
[[Pandas#one-hot encoding|one-hot encoding]]
[[Pandas#display|display]]


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

## Filter rows
### filter row if any column satisfy a condition
``` python
cols = ["col1", "col2", "col3"]
df_filtered = df[(df[cols] < 0).any(axis=1)]

# all columns are < 0
df_filtered = df[(df[cols] < 0).all(axis=1)]
```
## Group Filtering
``` python
df = pd.DataFrame({
    'category': ['A','A','A','B','B','C','C','C','C','C','D','D'],
    'value': [10, 20, 30, 5, 6, 8, 9, 10, 11, 12, 13, 14]
})
```
### filter by number of elements in group
``` python
counts = df.groupby('category')['value'].count()
filtered = df[df['category'].isin(counts[counts > 2].index)]
```
using filter() on group
``` python
df.groupby('category').filter(lambda x: len(x) > 2)
```
Notes:
- x in lambda is a *DataFrame*
- filter() filters *entire group* not individual rows.

df[expression] - expression should be indices of df
``` python
filtered = df.groupby('category').filter(lambda x: len(x) > 5)
```

``` python
df.groupby("Store")["Sales"].agg(["mean", "max", "min"])
df.groupby("Store").agg(
    avg_sales=("Sales", "mean"),
    max_sales=("Sales", "max"),
    total_profit=("Profit", "sum")
)
```
custom
``` python
def my_range(x):
    return x.max() - x.min()

df.groupby("Store")["Sales"].agg(my_range)
```
lambda
``` python
df.groupby("Store")["Sales"].agg(lambda x: x.quantile(0.9))
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
using plot
``` python
# first plot
df["30_day_rolling_vol"] = df["Volume"].rolling(window=30).mean()df[["30_day_rolling_vol"]].plot(legend=True)
# second plot
ax = df["Close"].plot(secondary_y=True, legend=True)
ax.set_ylabel("Closing Price")
plt.show()
```
using ax
``` python
fig, ax = plt.subplots()

ax.plot(df.index, df["sales"])
ax.set_ylabel("Sales")

ax2 = ax.twinx()
ax2.plot(df.index, df["temperature"])
ax2.set_ylabel("Temperature")

plt.show()
```
![[Pandas_2_y_axis.png|500]]
## display
display full column (not scientific notation)
``` python
pd.set_option('display.float_format', '{:.5f}'.format)
```
text
``` python
pd.set_option("display.max_colwidth", None)
```

## from long format to wide format
### pivot
syntax
``` python
 df.pivot(index='row_col', columns='col_to_pivot', values='data_col')
```
**Parameters**:
- **index**: Column(s) to use as the new DataFrame's index.
- **columns**: Column to use to create the new column headers.
- **values**: Column(s) to fill the new table's cells.


### pivot_table
Use `df.pivot_table()` when you need to **aggregate** data or handle duplicate entries for the same index/column pair.

### unstack
It takes the **innermost index level (`Store`)** and moves it to columns.
This is equivalent to a *pivot table*
``` python
df_10.groupby([df_10.index.day_of_week, 'Store'])['Sales'].mean().unstack()

```
- Rows → `day_of_week`
- Columns → `Store`
- Values → mean Sales
the *unstack* is used usually for preparation for plotting.

## from wide to long

![[Pandas-1.png]]
output
![[Pandas-2.png]]

### melt()
- **`id_vars`**: Columns to keep as identifiers (will not be "melted").
- **`value_vars`**: Specific columns to unpivot. If omitted, all columns not in `id_vars` are melted.
- **`var_name`**: Custom name for the new "variable" column.
- **`value_name`**: Custom name for the new "value" column

``` python
pd.melt(df, id_vars=["A"], value_vars=["B", "C"], var_name="myVarname", value_name="myValueName")
```

### stack()
## one-hot encoding

``` python
df = pd.DataFrame({'A': [1, 2, 3]})
df = df.join(pd.get_dummies(df['A'], prefix='A').astype(bool))
```
result:
![[Pandas.png]]
or
``` python
for v in df['A'].unique():
    df[f'A_{v}'] = df['A'].eq(v)
```

[[pandas_TimeSeries]]

## My Questions


## References

