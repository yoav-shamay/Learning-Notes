Isolates dependencies (pip packages)
## Using python venv
Everything will be saved in the path specified.
After activating, all `python` and `pip` will be from the virtual environment.
Installed packages will be saved in `venv/lib/site-packages`
### Creation
`python -m venv path/to/venv`
### Activation
On windows: `venv/scripts/activate.bat`
On linux: `source myvenv/bin/activate`
### Deactivation
`deactivate`
In vs code it might not deactivate properly, in this case try doing `Ctrl + Shift + P`, select `Python: Select Interpreter` and then select the desired interpreter (not in venv).
## Using conda
After activating, all `python` and `pip` will be from the virtual environment.
The venv will be saved in `~/miniforge3/envs/env-name/`
Installed pip packages are saved in `~/miniforge3/envs/env-name/python3.x/site-packages
### Creation
`conda create -n name [python=3.x] [list of packages to install, seperated by space]`
### Activation
`conda activate name`
### Deactivation
`conda deactivate`
### Installing Packages
`conda` allows you to install packages exclusive to it using `conda install -n name package-name`
You can still use `pip install` inside the environment normally.