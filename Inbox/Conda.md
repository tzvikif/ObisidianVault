

14-04-2025 15:34

Status: #in_progress

Tags:

# Conda

[[Conda#create environment|create environment]]
[[Conda#remove environment|remove environment]]
[[Conda#list all conda environments|list environments]]
[[Conda#list packages in environment|list packages in environment]]
[[Conda#install package from conda-forge|install package from conda-forge|]]


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
## create environment
``` shell
conda create --name <environment_name>
# with packages
conda create --name <environment_name> python=3.9 scipy=0.17.3
# clone
conda create --name <new_environment_name> --clone <existing_environment_name>
```


## remove environment
``` shell
conda env remove --name <environment_name>
# example
conda deactivate
conda env remove --name my_project_env
```

## clean
``` shell
conda clean --all -y

```

## My Questions


## References

