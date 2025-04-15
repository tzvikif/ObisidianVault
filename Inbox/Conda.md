

14-04-2025 15:34

Status: #in_progress

Tags:

# Conda

## install package from [[conda-forge]]
### Specify the channel during installation
``` bash
conda install -c conda-forge package_name
# example
conda install -c conda-forge numpy
```
### Make conda-forge your priority channel
``` bash
# Add conda-forge to your channels
conda config --add channels conda-forge
# Set conda-forge as the highest priority channel
conda config --set channel_priority strict
```
### Verify channel order
``` bash
conda config --show channels
```
## list all conda environments
``` bash
conda env list
# or
conda info --envs
```
## list packages in environment
``` bash
conda list -n environment_name
# or for the current active environment
conda list
```





## My Questions


## References

