

26-04-2026 10:38

Status: #in_progress

Tags:

# vim

[[vim#Settings|permanent settings]]

## mode

| Mode    | Purpose              | Enter              | Exit    |
| ------- | -------------------- | ------------------ | ------- |
| Normal  | navigation, commands | `Esc`              | —       |
| Insert  | typing text          | `i`, `a`, `o`      | `Esc`   |
| Visual  | select text          | `v`, `V`, `Ctrl+v` | `Esc`   |
| Command | execute commands     | `:`                | `Enter` |
## Enter Insert Mode
| Command | Action               |
| ------- | -------------------- |
| `i`     | insert before cursor |
| `a`     | insert after cursor  |
| `I`     | insert at line start |
| `A`     | insert at line end   |
| `o`     | new line below       |
| `O`     | new line above       |
## Save and Exit
| Command | Action              |
| ------- | ------------------- |
| `:w`    | save                |
| `:q`    | quit                |
| `:wq`   | save and quit       |
| `:x`    | save and quit       |
| `:q!`   | quit without saving |
| `ZZ`    | save and quit       |
## Navigation
| Command | Action          |
| ------- | --------------- |
| `h`     | left            |
| `l`     | right           |
| `j`     | down            |
| `k`     | up              |
| `w`     | next word       |
| `b`     | previous word   |
| `0`     | line start      |
| `^`     | first non-space |
| `$`     | line end        |
| `gg`    | file start      |
| `G`     | file end        |
| `:n`    | go to line n    |
## Editing Text
| Command  | Action                |
| -------- | --------------------- |
| `x`      | delete character      |
| `dd`     | delete line           |
| `dw`     | delete word           |
| `d$`     | delete to end of line |
| `yy`     | copy line             |
| `yw`     | copy word             |
| `p`      | paste after cursor    |
| `P`      | paste before cursor   |
| `u`      | undo                  |
| `Ctrl+r` | redo                  |
## Visual Mode Selection
| Command  | Action              |
| -------- | ------------------- |
| `v`      | character selection |
| `V`      | line selection      |
| `Ctrl+v` | block selection     |
| `y`      | copy selection      |
| `d`      | delete selection    |
## Search
| Command | Action          |
| ------- | --------------- |
| `/text` | search forward  |
| `?text` | search backward |
| `n`     | next result     |
| `N`     | previous result |
## Replace
single replacment
``` bash
:s/old/new/
```
whole line
``` bash
:s/old/new/g
```
entire file
``` bash
:%s/old/new/g
```
## Settings
line numbers
``` bash
:set number
```
highlighting
``` bash
:syntax on
```
Save permanently the settings in ~/.vimrc.
example:
``` bash
set number
syntax on
set tabstop=4
set shiftwidth=4
set expandtab
set autoindent
```
effects:

| Setting        | Result                         |
| -------------- | ------------------------------ |
| `set number`   | show line numbers              |
| `syntax on`    | enable syntax highlighting     |
| `tabstop=4`    | tab width = 4 spaces           |
| `shiftwidth=4` | indentation width = 4          |
| `expandtab`    | convert tabs to spaces         |
| `autoindent`   | keep indentation automatically |


## My Questions


## References

