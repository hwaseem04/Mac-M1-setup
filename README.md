# Mac-M1-setup
Personal setup stuff, I often forget the commands :). Will do a little bit of organizing the stuff little later

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
  
## Tensorflow for MAC M1

- Execute the following commands in terminal(python=3.8)
```bash
conda install -c apple tensorflow-deps
```
```bash
python -m pip install tensorflow-macos
```
```bash
python -m pip install tensorflow-metal
```

## If there exist some issues with M1 conda packages, so you want to work with x86 arch supported packages use the below commands (there are performance compromises)
```
CONDA_SUBDIR=osx-64 conda create -n myenv_x86 python=3.9  #myenv_x86 in env name
conda activate myenv_x86
conda config --env --set subdir osx-64 # ensures that conda installs x86 versions of Python packages 
```

or create a shell function in either .bashrc (if you use bash shell) or .zshrc (if you use zsh shell) as below
```
create_x86(){
  CONDA_SUBDIR=osx-64 conda create -n $@     # $@ is used to get all command line arguments, i.e env name and other dependencies
  conda activate $1                          # $1 is used to get first command line argument, i.e env name
  conda config --env --set subdir osx-64
}
```
## git related issues

`git config --global url."https://".insteadOf git://` to replace https protocol from ssh, as ssh is blocked in most of private/ public wifi firewall