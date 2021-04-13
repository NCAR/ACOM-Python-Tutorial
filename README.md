# ACOM Python Tutorial

Python Tutorial requested by individuals in NCAR's ACOM laboratory.

or...

> "How to use Python to read and plot CESM output, satellite output, 
> aircraft observations (netcdf files)."

I'm not sure we'll get to everything in the time allotted, but we'll try to make 
the most of our time.

## Preparation & Setup

**Note:** These instructions are for `bash` shell users, only.  There appear to be
problems when installing conda/miniconda with `csh` or `tcsh`.  (I'm not even sure
it works at all with `csh`.)  There is a fix for this coming, but the easiest way
to set up conda on Cheyenne, if you are a `tcsh` shell user, then just do everythin
below inside a `bash` instance.  In other words, just start by typing:

```bash
bash
```

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

If you are unsure about any setting, accept the defaults. We recommend adding the miniconda
path to your PATH variable manually. For a bash user, this would entail adding something
like the following to your `.bashrc` file:

```bash
export PATH=/path/to/installation/miniconda3/bin:${PATH}
```

To make the changes take effect, logout and log back in.  (You will need
to initialize another `bash` instance, if you are a `tcsh` user.)

To verify that conda is available on your system, you can try

```bash
conda --version 
```

After install, update conda:

```bash 
 conda update -n base conda
```

And configure the shell, replacing `{SHELL}` in the command below with your shell
(e.g., bash, tcsh, ...):

```bash
conda init {SHELL}
```

**Note:** This last step will probably not work for you if you use `csh` or `tcsh`
as your default shell on Cheyenne (or your laptop).  That does not mean you cannot
use conda, though.  And there is a fix coming for `tcsh` users, apparently.

### Create environments

After Miniconda is installed, you will want to set up Conda so that it
installs packages from a trusted _channel_.  Within the Python community,
the `conda-forge` channel is considered the most trusted source of packages
that will work together.  So, we enable the use of the `conda-forge` channel
for all packages with the following:

```bash
conda config --add channels conda-forge
```

You will probably want to download this tutorial to a space on your laptop or
workspace (e.g., `$HOME`) on Cheyenne, like so:

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
conda env update -f environments/tutorial.yaml
```

To use one of these environments, we need to activate it using the command
`conda activate {ENV_NAME}`, and to deactivate an environment, we use 
`conda deactivate`.


**Note:** To manage environments, the `conda env`, `conda info`, and
`conda list` commands are helpful tools. The `conda info --envs` command
can be used to list available environments (same as `conda env list`).

Finally, you will need to download additional plotting assets (for `cartopy`)
such as coastlines, etc., by executing the following script:

```bash
python scripts/download_cartopy_assets.py --output ~/.local/share/cartopy cultural-extra cultural gshhs physical
```

This last step is only necessary for certain special aspects of `cartopy`
to work, namely the plotting of coastlines at different resolutions, etc.

## Running JupyterLab

### Cheyenne

 When you are ready to start your Jupyter Lab session, simply point your
 browser to NCAR's JupyterHub deployment. This JupyterHub is accessible at:

```
https://jupyterhub.ucar.edu
```

Online documentation for NCAR JupyterHub is available [here](https://www2.cisl.ucar.edu/resources/jupyterhub-ncar). 


**Note:** You may find the Conda environment we created above useful after this tutorial, but you 
may want to give it a name that is more informative than `acom-tutorial`, such as `mypython` or
something.  There is no simple "rename" operation in Conda, but you can make a copy of the environment 
(with a new name) and delete the original environment by do the following:

```bash
conda create --name {NEW_NAME} --clone acom-tutorial
conda remove --name acom-tutorial --all
```

### Running Locally

To run the tutorial from your laptop.  You can launch Jupyter 
Lab from your laptop's command line to start going through the tutorial:

```bash
jupyter lab
```

and this will take you to a browser window/tab where your Jupyter Lab session 
will run.
