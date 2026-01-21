

2024-08-14 15:00

Status:

Tags:

## Wireshark

## sni
``` shell
tls.handshake.extensions_server_name contains "google"
# with client hello
tls.handshake.type == 1 &&
tls.handshake.extensions_server_name contains "google"
```
### regex
``` shell
tls.handshake.extensions_server_name matches "google|youtube"
# starts with
tls.handshake.extensions_server_name matches "^api\\."
# case-insensitive
tls.handshake.extensions_server_name matches "(?i)google"
# ends with
tls.handshake.extensions_server_name matches "\\.google\\.com$"
# wildcard like behavior
tls.handshake.extensions_server_name matches ".*cdn.*"
```
### quic / http-3
``` shell
quic.tls.handshake.extensions_server_name contains "google"
```


## References

