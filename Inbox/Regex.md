

23-10-2025 09:58

Status: 

Tags:

# Regex


|           | explanation                                        | example                                                  | output |
| --------- | -------------------------------------------------- | -------------------------------------------------------- | ------ |
| .*        | greedy - grabs the longest possible text           | (merges multiple sections                                |        |
| .*?       | .lazy - grabs the shortest that still fits         | captures only one section                                |        |
| (?= ... ) | positive lookahead. Match X, **only if** Y follows | text: apple pie. r'apple(?=\spie)'. matches only *apple* |        |
| (?: ... ) | none capturing group                               |                                                          |        |



``` shell
Frame #77
38.211.116.18:8598 --> 10.144.206.203:8567
Adding CONNECTION 0xa909e20
CrSwUdpConnection::ProcessFrame
CrDpiWrapperQosmos::ProcessPacket_qosmos
App Layer Offset = 102...App layer size = 57...Tranport Protocol = UDP...IP Version = 4
First bytes of app layer = 12 01 00 39 77 07
TIMESTAMP = 1761032753.636951
Transport protocol = udp
Creating flow...Client = 38.211.116.18:8598...Server = 10.144.206.203:8567
Frame direction = 1
DPI QOSMOS...App ID = 216...AppName = base.ip.udp
In OffloadByVideoMngrIfNeeded:
In RecordFrame:
In ProcessLearningFrame:
```

``` python
sec_re = re.compile(
    r'^Frame\s*#(?P<frame>\d+)(?P<body>.*?)(?=^Frame\s*#\d+|\Z)',
    flags=re.M | re.S

# ^Frame\s*#(?P<frame>\d+) finds the frame name and assign it  the name *frame*
# (?P<body>.*?) find the body until the next frame and name it *body*
# .*? lazy. take as little as possible(until next Frame is reached)
# ?= lookahead assertion. it says to the engine don't actually  include it in the current  match.
# \Z - end of text
# re.M = re.MULTILINE. changes how the special anchors `^` and `$` behave.
# match at the start and end of each line, not just the entire string
# re.S = re.DOTALL cause dot to match also newline (\n)
# re.search(r'a.*b', "a\nb", flags=re.S)
```

## My Questions


## References

