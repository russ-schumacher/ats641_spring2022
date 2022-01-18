# Lab assignment 1

For lab assignment 1, we'll be using [MetPy](https://unidata.github.io/MetPy/latest/index.html), developed by Unidata, to produce maps and other graphics. The first step, if you haven't done this before, will be to install python, and then ultimately install MetPy.

## Installing python via miniconda
First, let's install the miniconda version of python.  (If you already have miniconda or anaconda installed on the computer you want to use, you can skip this step.)  Following the instructions used in the [Unidata python workshop](https://unidata.github.io/python-training/):


### Windows

- Download the [Miniconda installer](http://conda.pydata.org/miniconda.html) for Python 3.X. (I suggest getting 3.8, though others should work fine too.) 

- After downloading the installer, open it and click through the graphical install utility. Accept all of the default installation settings.

- You should now have a program called “Anaconda Prompt” installed. Open it (this will be your Python command prompt).

### Mac/Linux

- Download the [Miniconda bash installer](http://conda.pydata.org/miniconda.html).

- After downloading the bash installer, open a command prompt (terminal app on the Mac).

- Change the directory at the terminal to wherever the installer was downloaded. On most systems, this will default to the downloads directory in your user account. If that’s the case, `cd ~/Downloads` will get you there, or replace the path with wherever you saved the file.

- Run the installer script by typing `bash Miniconda3-latest-MacOSX-x86_64.sh`. Note: Your file name may be different depending upon your operating system! replace `Miniconda3-latest-MacOSX-x86_64.sh` with whatever the name of the file you downloaded was.

- Accept the defaults.

- After the installer has completed completely close and restart your terminal program (this sources the newly modified path).

- If bash isn't your default shell, switch to it by running the command bash.

- Verify that your install is working by running `conda --version`. You should see a response like `conda 4.11.0` or similar (though yours may be a slightly different version number).

## Setting up your environment

Now we will set up an environment with the packages we need to have installed. Here is a link to an environment file that we'll use for the class (adapted from Unidata's workshop materials): [environment.yml file](environment_ats641_2022.yml)

To set up this environment, follow these steps:

- Open a terminal window (Anaconda Prompt if you're on Windows).

- Download the .yml file that tells your system what should be in the environment (see link above).

- In the terminal, navigate to wherever this file saved, probably cd ~/Downloads will get you there.

- Run the command `conda env create -f environment_ats641_2022.yml` and wait for the installation to finish (it may take a while, especially if you're on a slow internet connection).

- Run the command `conda activate ats641_2022` to activate the unidata environment and verify that everything is ready.  (It may ask you to do something like `conda init bash`, if so then do that first.)

## Opening and running a jupyter notebook

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




apply some of these techniques to make some maps from a recent event, and to diagnose some fields traditionally associated with QG forcing for ascent.  Namely, we'll plot the 500-hPa absolute vorticity advection, and the 850-hPa temperature advection.  For this exercise, we'll use the gridded NAM analysis from 0000 UTC 7 February 2020 (last Friday).

- To start, we can use this template from Unidata [https://unidata.github.io/python-training/gallery/500hpa_vorticity_advection/](https://unidata.github.io/python-training/gallery/500hpa_vorticity_advection/).  Start a new notebook, and you can copy the code from this page in to cells as you go.  (One hint regarding notebooks is that if you run into trouble, you can break up the code into even more cells to isolate the problem. But - remember that if you define a variable in one cell and change it farther down, if you need to set it back to the original value you'll need to go back up and re-run the earlier cell(s).)

- In this example, they get the archived data from NCEI, but their server doesn't have near-real-time data.  So we'll use the Unidata THREDDS server instead. So you can use a line of code like this: 
`ncss = NCSS('https://thredds.ucar.edu/thredds/ncss/grib/NCEP/NAM/CONUS_12km/NAM_CONUS_12km_20200207_0000.grib2')`.  Also change the dates and times accordingly in the code.

- Because we will use the temperature field later, add `Temperature_isobaric` to the list of variables that are pulled in with `hgt.variables`

- You'll also likely run into an issue when getting the data on the 500-hPa isobaric level, because the data file actually has the pressure in Pa rather than hPa, whereas the code example uses hPa.  Make this adjustment in your code.

- The rest of this code should then produce a map of 500-hPa vorticity advection. One thing you may want to experiment with is the level of smoothing, to optimize the "look" of your map.

- While you're going, one good thing to check to make sure all is well is to check the units of a variable or two.  This can be done just by calling something like `hght_500.units`  (In a notebook, if you make a new cell with this call it'll just print that value to the screen.)

- Now we'll move on to calculating and plotting the 850-hPa temperature advection. You won't need to re-run a lot of the earlier code, because you've already read in much of what you need. Instead, you'll just need to repeat where you get the height and winds at 500-hPa but this time for 850 hPa, and make sure to also read the temperature at 850 hPa in Kelvin.

- You can use your earlier code as a template for calculating the 850-hPa temperature advection.

- And now, plot the 850-hPa heights, winds, temperature, and temperature advection.  For plotting details, you might find this example helpful: [https://unidata.github.io/python-training/gallery/850hpa_temperature_advection/](https://unidata.github.io/python-training/gallery/850hpa_temperature_advection/).  (Note that not all details of that example will work because it uses a different dataset.)

- OK, you should now have maps of 500-hPa vorticity advection and 850-hPa temperature advection. Include these maps with your assignment when you turn it in. Discuss what the maps show in terms of where QG forcing for ascent and descent exist at this time.  Are there areas where the two maps give conflicting information in relation to QG forcing?

- Now we'll also use this same gridded analysis to calculate 850-hPa Q-vectors (and their divergence).  There are a couple tricky aspects to plotting Q-vectors with MetPy, so I've provided a sample notebook here, which should work once you've done all the steps up to this point: [https://github.com/russ-schumacher/ats641_spring2020/blob/master/lab2_qvectors_only.ipynb](https://github.com/russ-schumacher/ats641_spring2020/blob/master/lab2_qvectors_only.ipynb).  You'll probably just want to copy these cells into your own notebook that you've been using.  Plot the 850-hPa heights, Q-vectors, and Q-vector divergence.  Where does this diagnostic indicate QG forcing for ascent?  How does it compare with what you found earlier for the "traditional" QG omega equation?

- Are there any locations where you see a direct connection between the Q-vectors you calculated in question 1 of the lab?  If so, discuss.

- Locate a radar image at the approximate time that we've been analyzing. If you want to make your own, the Iowa State RadMap API: [https://mesonet.agron.iastate.edu/GIS/radmap_api.phtml](https://mesonet.agron.iastate.edu/GIS/radmap_api.phtml) is a great resource, or else feel free to find one that already exists, like in the NCAR MMM image archive [https://www2.mmm.ucar.edu/imagearchive/](https://www2.mmm.ucar.edu/imagearchive/).  Do the regions of precipitation shown on the radar image generally correspond to the regions of forcing for ascent that you've identified?  Briefly discuss any notable consistencies or inconsistencies.

- Finally, think back to the diagnostics we used to represent the "traditional" QG omega equation, and in particular the 500-hPa vorticity advection.  In using this diagnostic, there's one potentially important simplification that has been made with respect to the equation. State what this simplification is and whether you think it's reasonable in this case.





