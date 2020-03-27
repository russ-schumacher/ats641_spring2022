# ATS 641
## Lab exercise 4

March 30, 2020

Due April 13, 2020

## Numerical simulation of convective storms

In this lab, we will use the Weather Research and Forecasting (WRF) model to simulate and analyze convection in a few different situations. We will do this in the AWS cloud using the instructions and tools that were provided by the WRF team in their tutorial when they visited class.  (However, if you are already experienced with WRF and have a computer of your own or in your group where you can easily set up and run it without needing assistance, you're certainly free to use that. 
Instructions for accessing what you need on the AWS cloud are found in the document distributed separately.  Although this removes a lot of the barriers to setting up and running WRF, there will still be some hurdles to cross (plus the fact that we can't help each other in person) so I you will want to get started on it sooner rather than later.

### Background information
First, read [Klemp and Wilhelmson (1978)](https://doi.org/10.1175/1520-0469(1978)035<1070:TSOTDC>2.0.CO;2) (a paper documenting the truly pioneering work in numerical cloud modeling; 1882 citations according to Google Scholar!) — it’s understandable if you aren’t able to completely grasp the sections dealing with the numerical methods, etc., but the main equations should look familiar, and this is a rare example of a paper that describes a cutting-edge method (for its time) and cutting-edge scientific insights. We'll first use WRF to reproduce the results shown in their Fig. 2.

### Set up and run WRF for a simple idealized case.
Once you've logged into AWS (or are ready to use WRF on your own system), the first step will be to set up an idealized simulation. Use the version of WRF in the `wrfv4.1.3_serial_no_nest`. `cd` into this directory, and then we will want to compile the model for the idealized supercell "quarter_ss" configuration - a 3D simulation with convection initiated by a single warm bubble.  Simply run `./compile em_quarter_ss`, and after a minute or two this should finish.  If you look in the `run` directory you should now have an `ideal.exe` executable in addition to `wrf.exe`.

Now, let's set up the namelist. Start with the default namelist (it's always a good idea to make a copy of it in case you need a fresh version later).  Some information about the many WRF namelist settings can be found at [https://www2.mmm.ucar.edu/wrf/users/docs/user_guide_v4/v4.0/users_guide_chap5.html#Namelist](https://www2.mmm.ucar.edu/wrf/users/docs/user_guide_v4/v4.0/users_guide_chap5.html#Namelist).  Run the model at 1-km horizontal grid spacing, on an 80 km × 80 km grid. Use a model time step of 6 seconds.  Run the simulation for 60 minutes, and set it so the "history" files are written every 5 minutes.  Set the cloud microphysics scheme to be the Kessler scheme, the same one that Klemp and Wilhelmson used.  Leave the rest of the namelist settings at their default value. For reference, the initial sounding is attached.

The homogeneous initial conditions are defined by a file called `input_sounding`.  You'll find a few of these files in `/home/ec2-user/ats641_wrf_ideal`.  For the first simulation, we will use an initial condition with no wind (just like Klemp and Wilhelmson).  This is the file called `input_sound.nowind` - copy this file so that it's named `input_sounding` (which is what the model will read in).  

Running the model is a two-step process: first run `ideal.exe`, then assuming it has "SUCCESS", you can run `wrf.exe`.

### Analyze the output
Plot the fields that Klemp and Wilhelmson showed in their Fig. 2.  A couple of examples for using WRF-python to do this are in the `wrf-python-ideal-examples.ipynb` notebook in `/home/ec2-user/ats641_wrf_ideal`.  (First do `conda activate wrf-python` to load an environment with the needed modules.)  Feel free to use color or add other fields (for example, wind vectors) in your plots to make them look nice if you like, and you're also free to use a different plotting software if you prefer.  

Use the output from t=25 minutes to make your plots, and include them when you turn the assignment in. Also, make an animation of the output every five minutes, so you can watch the convective cell initiate, mature, and decay. (No need to turn this in, but it will help put things in context, and hopefully make more clear what the model is doing.) Describe whether your results look the same as those in the paper, and discuss any substantial differences. Also, describe physically in a few sentences what is happening at t=25 minutes. By the end of your simulation (t=60 minutes), what is the status of the modeled storm?

## A more interesting simulation...
