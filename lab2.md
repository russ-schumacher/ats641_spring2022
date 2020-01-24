# Lab assignment 2

For lab assignment 2, we'll be using [MetPy](https://unidata.github.io/MetPy/latest/index.html), developed by Unidata, to produce maps and other graphics. The first step, if you haven't done this before, will be to install python, and then ultimately install MetPy.

## Installing python via miniconda
First, let's install the miniconda version of python.  (If you already have miniconda or anaconda installed on the computer you want to use, you can skip this step.)  Following the instructions used in the [Unidata python workshop](https://unidata.github.io/python-training/):


### Windows

- Download the [Miniconda installer](http://conda.pydata.org/miniconda.html) for Python 3.X. Windows 32-bit machines are NOT supported by most packages and cannot be used.

- After downloading the installer, open it and click through the graphical install utility. Accept all of the default installation settings.

- You should now have a program called “Anaconda Prompt” installed. Open it (this will be your Python command prompt).

### Mac/Linux

- Download the [Miniconda bash installer](http://conda.pydata.org/miniconda.html).

- After downloading the bash installer, open a command prompt (terminal program on the Mac).

- Change the directory at the terminal to wherever the installer was downloaded. On most systems, this will default to the downloads directory in your user account. If that’s the case, `cd ~/Downloads` will get you there, or replace the path with wherever you saved the file.

- Run the installer script by typing `bash Miniconda3-latest-MacOSX-x86_64.sh`. Note: Your file name may be different depending upon your operating system! replace `Miniconda3-latest-MacOSX-x86_64.sh` with whatever the name of the file you downloaded was.

- Accept the defaults.

- After the installer has completed completely close and restart your terminal program (this sources the newly modified path).

- If bash isn't your default shell, switch to it by running the command bash.

- Verify that your install is working by running `conda --version`. You should see a response like `conda 4.8.0` or similar (though yours may be a slightly different version number).

## Setting up your environment

Now we will set up an environment with the packages we need to have installed. Here is a link to an environment file that we'll use for the class (again, borrowed from Unidata's workshop materials): [environment.yml file](environment_ats641_2020.yml)

To set up this environment, follow these steps:

- Open a terminal window (Anaconda Prompt if you're on Windows).

- Download the .yml file that tells your system what should be in the environment (see link above).

- In the terminal, navigate to wherever this file saved, probably cd ~/Downloads will get you there.

- Run the command `conda env create -f environment_ats641_2020.yml` and wait for the installation to finish (it may take a while, especially if you're on a slow internet connection).

- Run the command `conda activate ats641` to activate the unidata environment and verify that everything is ready.  (It may ask you to do something like `conda init bash`, if so then do that first.)

## Opening and running a jupyter notebook

There are different ways you can run and interact with python, but a great way to get started is with Jupyter notebooks.  They allow for you to write and test your code in a really user-friendly way. (People tried to sell them on me and I resisted for a long time, but once I started using them, now it's my favorite way to test out new code.)

- At the terminal, `cd` into whatever directory you want to work out of (this might be a directory you've set up just for the class, or you can make a new one, etc.)

- if you haven't, run `conda activate ats641` to activate the environment.

- We're going to start with an example notebook, obtained from the Unidata website.  Right-click and download [this file](https://unidata.github.io/python-gallery/_downloads/45a886d6aaa2fa40c8e7d9239a6af334/500hPa_HGHT_Winds.ipynb).   (This notebook originates from [this page](https://unidata.github.io/python-gallery/examples/500hPa_HGHT_Winds.html).)

- Now, open Jupyter Lab, by simply running `jupyter lab`. This will open a new browser tab with Jupyter Lab in it.

- Click on 'Python3' to launch the python kernel.

- Open up the `500hPa_HGHT_Winds.ipynb` notebook (double-click it from the menu on the left) -- this will give you a feel for what a notebook looks like and how it works.

- Walk through the steps in this notebook (Hint: you can run the code in cells using `shift-R`, or using the "play button" at the top) and hopefully you will reproduce the same 500-hPa map that is shown on the webpage linked above!  If so, congratulations, you're well on your way!  

- As you go, you might want to save your notebook by clicking the 'save' button in the upper left.

- The first time you run things, there may be some map files that need to be downloaded, which takes a little longer and gives  a warning. This is normal and won't happen after those files have been downloaded.

- Now spend a little time experimenting with the code in this notebook, to get a sense for some of the options (for example, try changing the contour intervals, or the map boundaries, or the vertical level shown, etc.)

- You may want to learn more about notebooks and how they work: a good resource is the Unidata training at [https://unidata.github.io/python-training/workshop/Jupyter_Notebooks/jupyter-notebooks-introduction/](https://unidata.github.io/python-training/workshop/Jupyter_Notebooks/jupyter-notebooks-introduction/)

- When you're done with JupyterLab, simply go under the File menu and select "Shut down".  Once this happens, you can close that browser window.

## Lab 2 assignment

- Now we're going to move on to what we actually want to do in the lab, etc...









