

04-05-2026 18:06

Status: #in_progress

Tags:

# rg

| Goal                             | Command                            | Example                                             |
| -------------------------------- | ---------------------------------- | --------------------------------------------------- |
| Search text recursively          | `rg "pattern"`                     | `rg "ProcessPacket"`                                |
| Search literal text              | `rg -F "text"`                     | `rg -F "CrDpiWrapper::GetInstance().ProcessPacket"` |
| Show only matching filenames     | `rg -l "pattern"`                  | `rg -l "ProcessPacket"`                             |
| Show files without matches       | `rg -L "pattern"`                  | `rg -L "ProcessPacket"`                             |
| Show line numbers                | `rg -n "pattern"`                  | `rg -n "ProcessPacket"`                             |
| Ignore case                      | `rg -i "pattern"`                  | `rg -i "processpacket"`                             |
| Smart case                       | `rg -S "pattern"`                  | `rg -S "processPacket"`                             |
| Search exact word                | `rg -w "word"`                     | `rg -w "Packet"`                                    |
| Search in specific file type     | `rg -t <type> "pattern"`           | `rg -t cpp "ProcessPacket"`                         |
| Search only `.cpp` files         | `rg -g "*.cpp" "pattern"`          | `rg -g "*.cpp" "ProcessPacket"`                     |
| Search `.cpp` and `.h` files     | `rg -g "*.cpp" -g "*.h" "pattern"` | `rg -g "*.cpp" -g "*.h" "ProcessPacket"`            |
| Exclude files                    | `rg -g "!pattern" "text"`          | `rg -g "!*.log" "ProcessPacket"`                    |
| Exclude directory                | `rg -g "!dir/**" "text"`           | `rg -g "!build/**" "ProcessPacket"`                 |
| Search hidden files              | `rg --hidden "pattern"`            | `rg --hidden "ProcessPacket"`                       |
| Search ignored files too         | `rg -u "pattern"`                  | `rg -u "ProcessPacket"`                             |
| Search hidden + ignored + binary | `rg -uuu "pattern"`                | `rg -uuu "ProcessPacket"`                           |
| Count matching lines per file    | `rg -c "pattern"`                  | `rg -c "ProcessPacket"`                             |
| Count total matches              | `rg -o "pattern" \| wc -l`         | `rg -o "ProcessPacket" \| wc -l`                    |
| Show only matched text           | `rg -o "pattern"`                  | `rg -o "ProcessPacket"`                             |
| Show context before/after        | `rg -C <N> "pattern"`              | `rg -C 3 "ProcessPacket"`                           |
| Show lines before match          | `rg -B <N> "pattern"`              | `rg -B 2 "ProcessPacket"`                           |
| Show lines after match           | `rg -A <N> "pattern"`              | `rg -A 2 "ProcessPacket"`                           |
| Search in one directory          | `rg "pattern" path/`               | `rg "ProcessPacket" src/`                           |
| Search in one file               | `rg "pattern" file`                | `rg "ProcessPacket" main.cpp`                       |
| List searchable file types       | `rg --type-list`                   | `rg --type-list \| grep cpp`                        |
| Use regex alternation            | `rg "foo\|bar"`                    | `rg "ProcessPacket\|GetInstance"`                   |
| Use PCRE2 regex                  | `rg -P "regex"`                    | `rg -P "Process\\w+"`                               |
| Replace text in output only      | `rg "old" -r "new"`                | `rg "ProcessPacket" -r "HandlePacket"`              |
| Show matches with column numbers | `rg --column "pattern"`            | `rg --column "ProcessPacket"`                       |
| No color output                  | `rg --color never "pattern"`       | `rg --color never "ProcessPacket"`                  |
| Follow symlinks                  | `rg -L "pattern"`                  | `rg -L "ProcessPacket"`                             |


## My Questions


## References

