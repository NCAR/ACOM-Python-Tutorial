# ACOM Python Tutorial

Python Tutorial requested by individuals in NCAR's ACOM laboratory.

or...

> "How to use Python to read and plot CESM output, satellite output, 
> aircraft observations (netcdf files)."

## Preparation

### Get Miniconda and install

We will use _Miniconda_ to install and manage our Python environment. 

For this tutorial, we will do everything on Cheyenne, but the _same
steps_ work on your laptop, too.  (Or, when there are differences, we will
indicate them so you can reproduce this on your laptop.)

First, download the Miniconda installer for your system
[here](https://docs.conda.io/en/latest/miniconda.html), and follow the
instructions to install it on your system.  On Cheyenne, you need to
install the _Linux_ version of the bash install script and install
that way.


```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh
bash miniconda.sh    # Follow the prompts on the installer screens.
```

If you are unsure about any setting, accept the defaults. We recommend adding the miniconda path to your PATH variable manually. For a bash user, this would entail adding something like the following to your .bashrc file:

```bash
export PATH=/path/to/installation/miniconda3/bin:${PATH}
```

To make the changes take effect, logout and log back in.


To verify that conda is available on your system, you can try

```bash
conda --version 
```

After install, update conda:

```bash 
 conda update -n base conda
```

And configure the shell, replacing {SHELL} in the command below with your shell (i.e., bash, tcsh,...):

```bash
conda init {SHELL}
```


### Create environments

After Miniconda is installed, you will want to set up Conda so that it
installs packages from a trusted _channel_.  Within the Python community,
the `conda-forge` channel is considered the most trusted source of packages
that will work together.  So, we enable the use of the `conda-forge` channel
for all packages with the following:

```bash
conda config --add channels conda-forge
```

will probably want to download this
tutorial to a space on your laptop or workspace on Cheyenne, like so:

```bash
git clone https://github.com/NCAR/ACOM-Python-Tutorial.git
```

and then change directory into the tutorial repository:

```bash
cd ACOM-Python-Tutorial
```

First update the conda base environment.

```bash
conda env update -f environments/base.yaml
```

Next create the Conda _environment_ for this tutorial (this can take ~ 5 min).

```bash
conda env update -f environments/environment.yaml
```

To use one of these environments, we need to activate it using the command conda activate ENV_NAME, and to deactivate an environment, we use conda deactivate.


Once you've created the above environments, you will need to run the `post_build` script in order to build JupyterLab extensions.

```bash 
conda activate base
./environments/post_build
```

**Note:** To manage environments, the `conda env`, `conda info`, and `conda list` commands are helpful tools. The `conda info` command can be used to list available environments (same as `conda env list`).

Now, let's activate our `tutorial` environment with:

```bash
conda activate tutorial
```

Once the environment is activated, you will need to download additional plotting assets such as coastlines, etc by executing the following script:

```bash 
python scripts/download_cartopy_assets.py --output ~/.local/share/cartopy cultural-extra cultural gshhs physical
```


## Running JupyterLab

### Cheyenne

 When you are ready to start your Jupyter Lab session,simply point your browser to:

```
https://jupyterhub.ucar.edu
```

### Running Locally

To run the tutorial from your laptop.  You can launch Jupyter 
Lab to start going through the tutorial:

```bash
jupyter lab
```

and this will take you to a browser window/tab where your Jupyter Lab session 
will run.
