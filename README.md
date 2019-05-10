# ACOM Python Tutorial

Python Tutorial requested by individuals in NCAR's ACOM laboratory.

or...

> "How to use Python to read and plot CESM output, satellite output, 
> aircraft observations (netcdf files)."

## Preparation

We will use _Miniconda_ to install and manage our Python environment. 

For this tutorial, we will do everything on our laptops, but the _same
steps_ work on Cheyenne, too.  (Or, when there are differences, we will
indicate them so you can reproduce this on Cheyenne.)

First, download the Miniconda installer for your system
[here](https://docs.conda.io/en/latest/miniconda.html), and follow the
instructions to install it on your system.  (On Cheyenne, you need to
install the _Linux_ version of the bash install script and install
that way.)

After Miniconda is installed, you will want to set up Conda so that it
installs packages from a trusted _channel_.  Within the Python community,
the `conda-forge` channel is considered the most trusted source of packages
that will work together.  So, we enable the use of the `conda-forge` channel
for all packages with the following:

```bash
conda config --add channels conda-forge
```

will probably want to download this
tutorial to a space on your laptop, like so:

```bash
git clone https://github.com/NCAR/ACOM-Python-Tutorial.git
```

and then change directory into the tutorial repository:

```bash
cd ACOM-Python-Tutorial
```

Now, you want to create the base Conda _environment_ for this tutorial.

```bash
conda create --name tutorial python=3.7 jupyterlab
```

In this case, we just created an environment called `tutorial`, and we
can activate this environment with:

```bash
conda activate tutorial
```

Next, you will probably want to download the tutorial data to your laptop:

```bash
cd data
./get_cesm_data # Follow prompt for password/token response
cd ..
```

Now you are ready to run the tutorial from your laptop.  You can launch Jupyter 
Lab to start going through the tutorial:

```bash
jupyter lab
```

and this will take you to a browser window/tab where your Jupyter Lab session 
will run.

### On Cheyenne...

If you are doing this tutorial on Cheyenne, you can install Miniconda in your 
home or work space on GLADE, and you can create your conda environment and
activate it exactly the same way.  When you are ready to start your Jupyter Lab
session, however, simply point your browser to:

```
https://jupyterhub.ucar.edu
```
