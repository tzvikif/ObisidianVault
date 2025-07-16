

20-03-2025 17:46

Status: 

Tags:

# Python

## Virtual Environment
``` bash
# Creating a virtual environment
python -m venv myenv

# Activating on Windows
myenv\Scripts\activate

# Activating on Unix/MacOS
source myenv/bin/activate
```

Verify which Python is being used by running
``` bash
which python  # On Unix/MacOS
where python  # On Windows
```

``` bash
pip freeze > requirements.txt
pip install -r requirements.txt
```

## jupyter lab
``` bash
pip install jupyter lab
# when running on remote server:
jupyter lab --ip=0.0.0.0 --port=8888 --no-browser
```
## Conda
using [[Conda]]
``` bash
conda create --name myenv python=3.12
conda activate myenv
conda config --set auto_activate_base false # disable automatic conda activation
conda env remove --name fp_env # delete environment
```
### channels
``` bash
conda config --show channels
```
conda automatically adds the name of the channel the base url:
https://conda.anaconda.org/<channel-name>
for example:
for channel *nvidia* : https://conda.anaconda.org/nvidia

## My Questions


## References

