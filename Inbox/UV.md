

19-04-2026 15:08

Status: #in_progress

Tags:

# UV

[[UV#initialization|initialization]]
[[UV#Dependency management|Dependency management]]
[[UV#Running scripts and commands|Running scripts and commands]]
[[UV#alternate Python versions|alternate Python versions]]
[[UV#Requirements.txt compatibility|Requirements.txt compatibility]]


## initialization
Create project environment
``` bash
uv init
```
Create environment explicitly
``` bash
uv venv
```
with specific python
``` bash
uv venv --python 3.11
```
un command inside environment (no activation required):
``` bash
uv run python script.py
```
Run interactive Python:
``` bash
uv run python
```
## Dependency management
add dependency
``` bash
uv add pandas
# or
uv add pandas==2.2.2
```
remove
``` bash
uv remove pandas
```
upgrade
``` bash
uv add pandas --upgrade
```
upgrade all
``` bash
uv lock --upgrade
```
## Running scripts and commands
run python file
``` bash
uv run script.py
```
run module
``` bash
uv run python -m module_name
```
## alternate Python versions
``` bash
uv python list
```
install python version
``` bash
uv python install 3.11
```
use interpreter
``` bash
uv venv --python 3.11
```
## Requirements.txt compatibility
install form requirements
``` bash
uv pip install -r requirements.txt
```
export
``` bash
uv pip freeze > requirements.txt
```
list installed packages
``` bash
uv pip list
```
show dependency tree
``` bash
uv pip tree
```
sync *pyproject.toml* with .env
``` bash
uv sync
```




## My Questions


## References

