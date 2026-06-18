

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
# check environment
echo $VIRTUAL_ENV 
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

## miscellaneous
to verify which interpreter runs
``` bash
uv run python -c "import sys; print(sys.executable)"
```
install [[cuda]]

### check cuda installtion
``` python
python - <<'PY'
import torch

print("torch:", torch.__version__)
print("torch file:", torch.__file__)
print("cuda available:", torch.cuda.is_available())
print("torch cuda version:", torch.version.cuda)

if torch.cuda.is_available():
    print("gpu:", torch.cuda.get_device_name(0))
    x = torch.randn(3, 3, device="cuda")
    print(x)
PY
```
## My Questions


## References

