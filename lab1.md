# Lab assignment 1

### Due Wednedsay, February 9

For lab assignment 1, we'll be using [MetPy](https://unidata.github.io/MetPy/latest/index.html), developed by Unidata, to produce maps and other graphics. The first step, if you haven't done this before, will be to install python, and then ultimately install MetPy.

## Installing python via miniconda
First, let's install the miniconda version of python.  (If you already have miniconda or anaconda installed on the computer you want to use, you can skip this step and go to the assignment.)  Following the instructions used in the [Unidata python workshop](https://unidata.github.io/python-training/):


#### Windows

- Download the [Miniconda installer](http://conda.pydata.org/miniconda.html) for Python 3.X. (I suggest getting 3.8, though others should work fine too.) 

- After downloading the installer, open it and click through the graphical install utility. Accept all of the default installation settings.

- You should now have a program called “Anaconda Prompt” installed. Open it (this will be your Python command prompt).

#### Mac/Linux

- Download the [Miniconda bash installer](http://conda.pydata.org/miniconda.html).

- After downloading the bash installer, open a command prompt (terminal app on the Mac).

- Change the directory at the terminal to wherever the installer was downloaded. On most systems, this will default to the downloads directory in your user account. If that’s the case, `cd ~/Downloads` will get you there, or replace the path with wherever you saved the file.

- Run the installer script by typing `bash Miniconda3-latest-MacOSX-x86_64.sh`. Note: Your file name may be different depending upon your operating system! replace `Miniconda3-latest-MacOSX-x86_64.sh` with whatever the name of the file you downloaded was.

- Accept the defaults.

- After the installer has completed completely close and restart your terminal program (this sources the newly modified path).

- If bash isn't your default shell, switch to it by running the command bash.

- Verify that your install is working by running `conda --version`. You should see a response like `conda 4.11.0` or similar (though yours may be a slightly different version number).

### Setting up your environment

Now we will set up an environment with the packages we need to have installed. Here is a link to an environment file that we'll use for the class (adapted from Unidata's workshop materials): [environment.yml file](environment_ats641_2022.yml)

To set up this environment, follow these steps:

- Open a terminal window (Anaconda Prompt if you're on Windows).

- Download the .yml file that tells your system what should be in the environment (see link above).

- In the terminal, navigate to wherever this file saved, probably cd ~/Downloads will get you there.

- Run the command `conda env create -f environment_ats641_2022.yml` and wait for the installation to finish (it may take a while, especially if you're on a slow internet connection).

- Run the command `conda activate ats641_2022` to activate the unidata environment and verify that everything is ready.  (It may ask you to do something like `conda init bash`, if so then do that first.)

### Opening and running a jupyter notebook

There are different ways you can run and interact with python, but a great way to get started is with Jupyter notebooks.  They allow for you to write and test your code in a really user-friendly way. (People tried to sell them on me and I resisted for a long time, but once I started using them, now it's my favorite way to test out new code.)

- At the terminal, `cd` into whatever directory you want to work out of (this might be a directory you've set up just for the class, or you can make a new one, etc.)

- if you haven't, run `conda activate ats641_2022` to activate the environment.

- We're going to start with an example notebook, obtained from the Unidata website.  Right-click and download [this file](https://unidata.github.io/python-training/gallery/500hpa_hght_winds/index.ipynb).   (This notebook originates from [this page](https://unidata.github.io/python-training/gallery/500hpa_hght_winds/).)

- Now, open Jupyter Lab, by simply running `jupyter lab`. This will open a new browser tab with Jupyter Lab in it. Or you can also simply use `jupyter notebook` if you prefer.

- Click on 'Python3' to launch the python kernel.

- Open up the `index.ipynb` notebook (double-click it from the menu on the left) -- this will give you a feel for what a notebook looks like and how it works.

- Walk through the steps in this notebook (Hint: you can run the code in cells using `shift-R`, or using the "play button" at the top) and hopefully you will reproduce the same 500-hPa map that is shown on the webpage linked above.  If so, congratulations, you're well on your way!  

- As you go, you might want to save your notebook by clicking the 'save' button in the upper left.

- The first time you run things, there may be some map files that need to be downloaded, which takes a little longer and gives a warning. This is normal and won't happen again after those files have been downloaded. You might also get some warning messages, but as long as the map plots and looks right, you can ignore them.

- Now spend a little time experimenting with the code in this notebook, to get a sense for some of the options (for example, try changing the contour intervals, or the map boundaries, or the vertical level shown, etc.)

- You may want to learn more about notebooks and how they work: a good resource is the Unidata training at [https://unidata.github.io/python-training/workshop/Jupyter_Notebooks/jupyter-notebooks-introduction/](https://unidata.github.io/python-training/workshop/Jupyter_Notebooks/jupyter-notebooks-introduction/)

- When you're done with JupyterLab, simply go under the File menu and select "Shut down".  Once this happens, you can close that browser window.

## Lab 1 assignment

Now, we're going to use some of these approaches to plot a surface weather map to analyze in multiple ways. For those of you with a lot of meteorological background, some of this may seem simple, but we want to make sure everyone’s on the same page before moving on to more complicated analyses.

### Surface map

We'll start by plotting a surface map from 0300 UTC 11 December 2021 over the eastern part of the US. I've provided an example notebook that you can use for this (adapted from a MetPy example; you can right-click and save from this link): [https://github.com/russ-schumacher/ats641_spring2022/blob/master/lab1/Station_Plot.ipynb](https://github.com/russ-schumacher/ats641_spring2022/blob/master/lab1/Station_Plot.ipynb). You'll also need the file with all of the surface observations (in METAR format, which MetPy nicely decodes), here: [https://github.com/russ-schumacher/ats641_spring2022/blob/master/lab1/metar_20211211_0300.txt](https://github.com/russ-schumacher/ats641_spring2022/blob/master/lab1/metar_20211211_0300.txt). 

Go through the steps in the notebook to get your surface map. Print it out, or if you have a tablet with a pencil you could do the analysis that way too. (If you don't have easy access to a color printer, let Russ or Allie know.)

Analyze the map given the guidelines below. For this analysis, focus on the synoptic-scale features by keeping your contours fairly smooth.
- Draw isobars in solid black lines at 4 hPa intervals.
- Draw isotherms in red (or another color) lines at 5°C intervals.
- Indicate the locations of any high and low pressure centers with an H or L, respectively.
- Analyze any fronts that are present.

In a couple sentences, describe the key features of the weather pattern that were revealed from your surface analysis.

### MetPy automated analysis

Manual analysis is a valuable way to get a real "feel" for the data in a given weather situation, but it also can be time consuming. A wide variety of methods for automating the analysis of weather data have been developed over the years, with varying complexity. MetPy has some of these methods built in. We'll use one of those methods here to analyze the same data that you analyzed by hand above.

Another example notebook, modified from a MetPy example, is at [https://github.com/russ-schumacher/ats641_spring2022/blob/master/lab1/METAR_data_interpolation_dist.ipynb](https://github.com/russ-schumacher/ats641_spring2022/blob/master/lab1/METAR_data_interpolation_dist.ipynb). This will plot the same surface map as before, but will also analyze the pressure and temperature and plot them on the map. Go through this notebook to get the map.

Are there any noticeable/relevant/interesting differences between your hand analysis and this analysis? 

You might not like how this map looks, so spend some time making a nicer-looking version of this analysis. The MetPy notebook that my example was based on (linked near the top) provides some ideas, but feel free to experiment with your own style.

When you turn in your write-up, include your hand-analyzed map, the initial map with the automated analysis, and your "final product" map (hard copy and/or electronic versions are fine). 

### Optional extra credit

There is one clearly erroneous observation in the dataset, though it falls outside of the eastern US domain we've been plotting. Identify this observation (station, location, and why the observation is in error.)




