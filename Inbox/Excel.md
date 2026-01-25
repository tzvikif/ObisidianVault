

22-01-2026 17:40

Status: #in_progress

Tags:

# Excel

### SUM over J only where C is numeric
``` excel
=SUM(FILTER(J2:J100000, ISNUMBER(C2:C100000)))
# or
=SUMPRODUCT(--ISNUMBER(C2:C100000), J2:J100000)
# SUMPRODUCT is like dot product
```

### datetime to epoch
``` excel
# seconds
=(H2 - DATE(1970,1,1)) * 86400
```

### filter rows
``` excel
# in K2
=FILTER(I2:I100000, ISNUMBER(C2:C100000))
```
k2 will be a dense column of the filtered values

## My Questions


## References

