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

- Run the command `conda env create -f environment_ats641_2020.yml` and wait for the installation to finish.

- Run the command `conda activate ats641` to activate the unidata environment and verify that everything is ready.
