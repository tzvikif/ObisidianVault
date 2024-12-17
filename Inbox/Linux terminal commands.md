

22-10-2024 14:42

Status: #in_progress

Tags:

# Linux terminal commands


mount drive *D* to folder */mnt/d*
``` bash
sudo mount -t drvfs D: /mnt/d
```

## Directory Size

``` shell
du -sh <directory name>

ncdu <directory>
```

## Disks Size

``` bash
df -h
```

## awk

>ajay manager account 45000  
sunil clerk account 25000  
varun manager sales 50000  
amit manager account 47000  
tarun peon sales 15000  
deepak clerk sales 23000  
sunil peon sales 13000  
satvik director purchase 80000

``` bash
awk '/manager/ {print}' employee.txt
```

>ajay manager account 45000  
varun manager sales 50000  
amit manager account 47000

``` bash
awk '{print $1,$4}' employee.txt
```

> ajay 45000  
sunil 25000  
varun 50000  
amit 47000  
tarun 15000  
deepak 23000  
sunil 13000  
satvik 80000

build in variables

- ****NR**** number of records
- ****NF**** number of fields

``` bash
awk '{print NR,$0}' employee.txt
```

>1 ajay manager account 45000  
2 sunil clerk account 25000  
3 varun manager sales 50000  
4 amit manager account 47000  
5 tarun peon sales 15000  
6 deepak clerk sales 23000  
7 sunil peon sales 13000  
8 satvik director purchase 80000

``` bash
awk '{print $1,$NF}' employee.txt
```

$NF represents last field (salary)

>ajay 45000  
sunil 25000  
varun 50000  
amit 47000  
tarun 15000  
deepak 23000  
sunil 13000  
satvik 80000

## References

