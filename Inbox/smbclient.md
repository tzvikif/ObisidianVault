

23-04-2026 15:21

Status: #in_progress

Tags:

# smbclient

A command-line SMB client (similar to FTP client behavior) that allows:

- browsing network shares
- listing files
- uploading/downloading files
- testing authentication and connectivity

It communicates using the SMB protocol (Windows file sharing).

## example
``` bash
smbclient //172.16.1.143/Traces -U RAD_NTDOM01/tzviki.fisher
```
### SBM resource path
``` bash
//172.16.1.143/Traces
```
format: //SERVER/SHARE
**invalid**: //SERVER/SHARE/subfolder

### -U RAD_NTDOM01/tzviki.fisher
Specifies authentication identity.
format:
``` bash
-DOMAIN/username
```
Meaning:
- `RAD_NTDOM01` = Windows authentication domain
- `tzviki.fisher` = user account
Equivalent login formats:
``` bash
RAD_NTDOM01\tzviki.fisher
```
or
``` bash
tzviki.fisher@RAD_NTDOM01
```
depending on tool

## Excecution
What happens when the command runs
Sequence:
1. Connects to SMB server `172.16.1.143`
2. Requests access to share `Traces`
3. Prompts for password
4. Opens interactive session:
Inside the session you can run commands like:
``` bash
ls -l
```
download file
``` bash
get filename
```
upload file
``` bash
put filename
```
exit session
``` bash
exit
```



## My Questions


## References

