

22-10-2024 14:42

Status: #in_progress

Tags:

# Linux terminal commands

[[Linux terminal commands#Directory Size|Directory size]]
[[Linux terminal commands#Disks Size|Disk size]]
[[Linux terminal commands#awk|awk]]
[[Linux terminal commands#find|find]]
[[Linux terminal commands#keep running after logout|keep running after logout]]
[[Linux terminal commands#vi|vi cheat sheet]]
[[Linux terminal commands#kill|kill]]
[[Linux terminal commands#copy|move and copy]]
[[Linux terminal commands#add string to file name|change file names to all files in a folder]]
[[Linux terminal commands#grep|grep]]
[[Linux terminal commands#symlink|symlink]]






mount drive *D* to folder */mnt/d*
``` bash
sudo mount -t drvfs D: /mnt/d
```

## Directory Size

``` shell
du <options> <directory name>
```
options:
- -a: all
- -h: human-readable
- -d: max-depth
- -s: summarize
- -time: show time of last modification of any file or directory
- –exclude: Excludes specific directories or files from disk usage calculation based on patterns or names.
``` bash
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

## find
### file names

find by file name
``` bash
# Find files with .txt extension 
find . -name "*.txt"
# Case insensitive search
find . -iname "*.txt"
# Using regex 
# all the files zoom_test10_27thDec.txt - zoom_test99_27thDec.txt
find . -regextype posix-extended -regex ".*/zoom_test[0-9]{2}_27thDec\.txt"
```
**Notes**
".\*/" matches any directory path (including none)

find by type
``` bash
# Find only files 
find . -type f
# Find only directories 
find . -type d
# Find symbolic links 
find . -type l
```

find by size
``` bash
# Files larger than 100MB 
find . -size +100M 
# Files smaller than 100KB 
find . -size -100k
```
Find with multiple conditions
``` bash
# Find .txt files OR .pdf files 
find . \( -name "*.txt" -o -name "*.pdf" \) 
# Find files AND directories 
find . -name "*.txt" -type f -and -size +1M
```
Find and execute commands
``` bash
# Delete all .tmp files 
find . -name "*.tmp" -exec rm {} \; 
# Move all .pdf files to /documents 
find . -name "*.pdf" -exec mv {} /documents \; 
# Change permissions 
find . -type f -exec chmod 644 {} \;
```
Count specific file types (e.g., .txt files)
``` bash
find . -type f -name "*.txt" | wc -l
# Count files in current directory only (no subdirectories)
find . -maxdepth 1 -type f | wc -l
```
Find and exclude directories
``` bash
# Exclude 'node_modules' directory 
find . -not -path "./node_modules/*" 
# Multiple exclusions 
find . -not \( -path "./node_modules/*" -o -path "./dist/*" \)
```
Find empty files or directories
``` bash
# Empty files 
find . -type f -empty 
# Empty directories 
find . -type d -empty
```
find with depth constraints
``` bash
# Only current directory 
find . -maxdepth 1 
# Up to 2 levels deep 
find . -maxdepth 2 -name "*.txt"
```
### finding test in files
``` bash
grep "search_term" filename
grep -r "search_term" /path/to/directory
# Combine `find` and `grep` for more control 
find /path/to/search -type f -name "*.txt" -exec grep "search_term" {} \;
ack "search_term" /path/to/directory
ag "search_term" /path/to/directory
```
grep options
- `-i`: Case-insensitive search
- `-l`: Show only filenames with matches
- `-n`: Show line numbers
- `-v`: Show lines that don't match
- `-w`: Match whole words only
## keep running after logout

``` bash
nohup ./script.sh &
# Custom output file
nohup ./script.sh > output.log 2>&1 &
# Check if process is still running
ps aux | grep script.sh
```
**Notes**
`> output.log`: Redirects standard output (stdout) to output.log
`2>&1`:
- `2` refers to stderr (standard error)
- `>&1` means "redirect to where 1 (stdout) is pointing"
- So stderr is redirected to the same place as stdout (output.log)
`&` at the end: Runs the process in the background

## vi
display line numbers
``` bash
:set number
```

## kill
``` bash
# Find Firefox PID
ps aux | grep firefox 
# Kill it gracefully 
kill PID 
# If it doesn't respond, force kill: 
kill -9 PID
#kill by name
pkill process_name 
# or forcefully: 
pkill -9 process_name
```


## copy

``` bash
# copy with differenct name
cp <source_path> <dest_path>
# copy with same name
cp <source_path> <dest_folder>
# example:
cp report.pdf backup/report_2024.pdf
# options:
# -i to prompt before overwriting
# -v for verbose output showing what's being copied
# -p to preserve file permissions and timestamps
```

## move
``` bash
mv source_file.txt destination/new_filename.txt

# options
# -i to prompt before overwriting
# -v to show what's being moved
# -n to not overwrite existing files
# -f to force overwrite without prompting
```

## grep

``` bash
grep -E 'a{2,4}' file.txt # "aa", "aaa", or "aaaa"
# Search recursively for a pattern in all text files
grep -r "TODO" --include="*.txt" /path/to/search
```

## add string to file name
``` bash
for file in *.pcapng; do mv "$file" "ml_kpi_debug_decoder_$file"; done
# caustios way. dry run first
for file in *.pcap; do echo "Would rename $file to ml_kpi_debug_decoder_$file"; done
```

## symlink
``` bash
# make symlic your_new_name to /path/to/your/python/executable
ln -s /path/to/your/python/executable your_new_name
# -f force if the symlink exists you overwrite it
```
find the path for which the link points to
``` bash
readlink -f <symlink name>
# example
readlink -f python
```



## References

[Panes in Windows Terminal](https://learn.microsoft.com/en-us/windows/terminal/panes?WT.mc_id=-blog-scottha#creating-a-new-pane)

