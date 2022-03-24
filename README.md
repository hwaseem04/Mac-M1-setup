# Mac-M1-setup


## Setting up conda package manager
- Installing miniforge3 -> A conda based package manager for M1
  M1 variant Mac, it's "[Miniforge3-MacOSX-arm64](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh)" <- click     for direct download.
- After downloading miniforge, execute the below commands
```bash
chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
```
```bash
source ~/miniforge3/bin/activate
```


## Needed Conda commands

- Create and activate environment
```bash
conda create --name <env-name> -y
conda activate <env-name>
```
- Delete environment
```bash
conda env remove --name <env-name>
```
- Important things to do when you encounter error while changing interpreter in Spyder IDE
```bash
conda install -c apple tensorflow-deps
```
- To see the list of environments
```bash
conda env list
```

## Setup for Spyder 

- Important things to do when you encounter error while changing interpreter in Spyder IDE
```bash
conda install spyder-kernels -y

```
- Add **/bin/python** at end of the **environment path** for interpreter in spyder IDE
- Install this essential dependency in terminal once you change interpreter path from default path in spyder IDE. This ensures spyder to run smoothly.
  (As of now version >= 0.9.7 is enough , but it may change in future)
  ```bash
  conda install -c conda-forge rtree=0.9.7
  ```
  

