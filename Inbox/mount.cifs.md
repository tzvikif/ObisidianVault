

23-04-2026 15:31

Status: #in_progress

Tags:

# mount.cifs

CIFS = **Common Internet File System**

`mount.cifs` is a Linux command used to **mount a Windows network share (SMB/CIFS share)** into the local filesystem so it behaves like a normal directory.

Conceptually
Before mounting:
You access the share using a network client with [[smbclient]]:
``` bash
smbclient //172.16.1.143/Traces
```
after mounting access it like a normal directory:
``` bash
ls /mnt/traces
```

## Command Structure
``` bash
mount.cifs //SERVER/SHARE /local/mountpoint -o options
```

## Example
``` bash
sudo mount.cifs //172.16.1.143/Traces /mnt/traces \
  -o username=tzviki.fisher,domain=RAD_NTDOM01
```

| Part                  | Explanation           |
| --------------------- | --------------------- |
| mount.cifs            | mount SMB/CIFS share  |
| //172.16.1.143/Traces | remote server share   |
| /mnt/traces           | local mount directory |
| -o                    | options               |
| username=             | login account         |
| domain=               | Windows domain        |


## My Questions


## References

