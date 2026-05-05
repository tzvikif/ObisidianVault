

29-03-2026 18:13

Status: #in_progress

Tags:

# rdcmIcebergDB

## set AWS

install **AWS CLI** (Windows) from https://awscli.amazonaws.com/AWSCLIV2.msi
verify
``` PowerShell
aws --version
```

install **Session Manager** plugin (required for SSM tunnel)
``` PowerShell
https://s3.amazonaws.com/session-manager-downloads/plugin/latest/windows/SessionManagerPluginSetup.exe
```
verify
``` PowerShell
session-manager-plugin
```

get AWS credentials from here: https://d-936763cb2d.awsapps.com/start/#/?tab=accounts
![[rdcmIcebergDB-1.png]]

![[rdcmIcebergDB-2.png]]
past in PowerShell terminal. ^0b9794

params.json
``` json
{
  "host": ["ECAA1F6657EF4222DD5606967EA416A3.gr7.us-east-1.eks.amazonaws.com"],
  "portNumber": ["443"],
  "localPortNumber": ["8448"]
}
```

**PowerShell terminal 1**
``` PowerShell
aws ssm start-session `
   --region us-east-1 `
   --target i-0b8966c9e8f640b5f `
   --document-name AWS-StartPortForwardingSessionToRemoteHost `
   --parameters file://"C:\Users\tzviki.fisher\OneDrive - RADCOM Ltd\Documents\AWS_tools\params.json"
```
output:
``` PowerShell
Starting session with SessionId: tzviki.fisher@radcom.com-ayxky5a2naa2szgb5juveeu3hu
Port 8448 opened for sessionId tzviki.fisher@radcom.com-ayxky5a2naa2szgb5juveeu3hu.
Waiting for connections...
```
## Kubectl

``` PowerShell
aws eks update-kubeconfig --name veon-rea-eks --region us-east-1
Added new context arn:aws:eks:us-east-1:577162834617:cluster/veon-rea-eks to C:\Users\tzviki.fisher\.kube\config
```
and then
``` PowerShell
kubectl config set-cluster arn:aws:eks:us-east-1:577162834617:cluster/veon-rea-eks --server=https://127.0.0.1:8448 --insecure-skip-tls-verify=true
Cluster "arn:aws:eks:us-east-1:577162834617:cluster/veon-rea-eks" set.
```
check
``` PowerShell
kubectl get svc -n db
```
output
``` shell
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
postgresql      ClusterIP   172.20.140.10   <none>        5432/TCP   114d
postgresql-hl   ClusterIP   None            <none>        5432/TCP   114d
trino           ClusterIP   172.20.205.1    <none>        8080/TCP   63d
trino-worker    ClusterIP   None            <none>        8080/TCP   63d
```


check kubectl installation
``` PowerShell
kubectl version --client
```

aws configuration (you don't need that if you already [[rdcmIcebergDB#^0b9794| set environment variables]])
``` PowerShell
aws configure
AWS Access Key ID [None]: AKIAYMYMV6K4X2GQNB47
AWS Secret Access Key [None]: ***
Default region name [us-east-1]:
Default output format [json]:
```

**PowerShell terminal 2**
``` PowerShell
kubectl -n db port-forward svc/trino 8080:8080
```
output
``` shell
Forwarding from 127.0.0.1:8080 -> 8080
Forwarding from [::1]:8080 -> 8080
Handling connection for 8080
Handling connection for 8080
Handling connection for 8080
```

## DBeaver

download from https://dbeaver.io/download/
### connection to database
![[rdcmIcebergDB-3.png]]
settings
``` yaml
Host: localhost
Port: 8080
Database: iceberg
Schema: default
Username: trino
Password: (leave empty)
```

![[rdcmIcebergDB-4.png]]
## My Questions


## References

