

01-07-2025 11:32

Status: #in_progress

Tags:

# Pandas

[[Pandas#handle Nan|handle Nan]]

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

## display
display full column (not scientific notation)
``` python
pd.set_option('display.float_format', '{:.5f}'.format)
```

[[pandas_TimeSeries]]

## My Questions


## References

