# Lab assignment 4
## Due Friday, April 15

Part 1 of the lab was distributed separately and involves analyzing an observed severe weather event (see the PDF for instructions.) 

In this lab, we will use [Cloud Model 1 (CM1)](https://www2.mmm.ucar.edu/people/bryan/cm1/) to simulate and analyze convection in a few different situations. I expect that it will be a bit challenging for some of you to get CM1 up and running, so you have about 3 weeks to do this lab, but you will want to get started on it sooner rather than later.

## Installing the CM1 model
The first step is to download and install CM1. Some instructions for doing that are [here](lab4/cm1_instructions.md).

## Analyzing and plotting CM1 output
If you want to use python to analyze and plot the model output, I've put together an example notebook [here](lab4/cm1_plots_examples.ipynb). Likewise, if you're more comfortable with using a different programming language, you're more than welcome to use that. The 'original' language used by CM1 is [GrADS](http://cola.gmu.edu/grads/), and this is another good choice.

## Assignment

### Reading
Read [Klemp and Wilhelmson (1978)](https://journals.ametsoc.org/view/journals/atsc/35/6/1520-0469_1978_035_1070_tsotdc_2_0_co_2.xml?tab_body=abstract-display) (a paper documenting the truly pioneering work in numerical cloud modeling; over 2000 citations according to Google Scholar!) --- it's understandable if you aren't able to completely grasp the sections dealing with the numerical methods, etc., but the main equations should look familiar, and this is a rare example of a paper that describes a cutting-edge method (for its time) **and** cutting-edge scientific insights.  Use CM1 to reproduce the results shown in their Figure 2.

### Your first simulation
For your simulation, start with the default namelist, but make the following changes.  Run the model at 1-km horizontal grid spacing, on an 60 km x 60 km grid.  Use a model time step of 5 seconds.  Change the initial wind profile to have no winds (hint: look through README.namelist to see how to do this if you haven't already), and set *imove* to 0.  Run a 60-minute simulation, and set it so the 3-D output is written every five minutes.  Change the namelist so that the variables "thpert", "prspert", "upert", and "vpert" are output.  Set the cloud microphysics ("explicit moisture") scheme to be the Kessler scheme, the same one that Klemp and Wilhelmson used.  Leave the rest of the namelist settings at their default value.  For reference, the initial sounding is shown below.  (It should take a few minutes for this to run on most machines, with some variations depending on the computer you're using.)

Plot the fields that Klemp and Wilhelmson showed in their Fig. 2, though feel free to use color or add other fields (for example, wind vectors) in your plots to make them look nice if you like.  Use the output from *t*=25 minutes to make your plots, and attach them.  Also, make an animation of the output every five minutes, so you can watch the convective cell initiate, mature, and decay.  (No need to turn this in, but it will help put things in context, and hopefully make more clear what the model is doing.)
Describe whether your results look the same as those in the paper, and discuss any substantial differences.  Also, describe physically in a few sentences what is happening at *t*=25 minutes.  By the end of your simulation (*t*=60 minutes), what is the status of the modeled storm?

### An experiment

Now, change the initial wind profile to be the "RKW-type" wind profile.  (This is essentially the same wind profile used in the paper, with 10 m/s of wind shear over the lowest 2.5 km of the model atmosphere.)  Set *imove* to 1, and set *umove* to 5.0 and *vmove* to 0.  (What this does is keep the storm near the center of the model domain, now that winds have been added.)


Create the same plots for this run as you did for the first run.  Also, reproduce what is shown in Figs. 5 and 6 of Klemp and Wilhelmson, using *t*=35 minutes. (Their 
<img src="https://render.githubusercontent.com/render/math?math=\theta-\overline{\theta}"> field is the *thpert* field in CM1.)  What are the main differences in the structure of the storm between the no-shear run and this run with vertical shear?  Are there differences between your simulation and what's shown in the paper?  If so, discuss them.  What is the status of this storm at *t*=60 minutes?

### Your experiment
Now choose something to change in the model to run one experiment of your own.  Discuss the change(s) you made in the model and why you made them, present the results, and discuss and what the results mean.  A few possibilities (though feel free to come up with your own): increase the model's horizontal or vertical resolution; change the microphysics to use a scheme that includes ice; turn on Coriolis; change the initial thermodynamic or wind profile.  There are some other example soundings on the CM1 webpage if you would like to try any of them.

<img src="https://user-images.githubusercontent.com/18426375/160020822-428ced7c-44d6-4ecb-80e1-2bc4c3474673.png" width=500>

## Squall line simulation

Now we'll move on to use CM1 to simulate the development of a squall line from individual convective cells.  Make the following changes to the namelist that you used for the simulations above:

- Change the horizontal grid spacing to 4 km.  (Note, this is a fairly coarse grid for a squall-line simulation, but this allows it to run quickly on most any computer and still reveals the basic structure.)
- Make the domain 320 km x 320 km.
- Change the model time step to 16 s.
- Integrate the model for 3 hr (10800 s).
- Initiate convection with a line of warm bubbles (instead of a single bubble).

### Horizontal slices

Starting at *t*=30 minutes, plot the following three fields every 30 minutes of the simulation: vertical motion at 1.25 km above ground, pressure perturbation at the surface, and <img src="https://render.githubusercontent.com/render/math?math=\theta"> perturbation at the surface.  Feel free to combine any of these fields together onto the same plot at each time if you can make them look nice.  How are these fields evolving with time?  What processes are taking place in the model?  What are the primary features that are simulated?  Do the features that the model simulated resemble observations of squall lines?

### Vertical sections

At *t*=90, 105, 120, and 135 minutes, plot cross-sections through *y*=25 km.  (This should cut through the squall line.)  Plot the vertical motion and <img src="https://render.githubusercontent.com/render/math?math=\theta">-perturbation fields.  Also, plot airflow vectors at these times.  (Since *y* is constant, you will want your vectors to show *u, w*.)  Again, combine fields on plots as appropriate.  What is the structure of the simulated updrafts and downdrafts?  Are they tilted or upright?  At what levels are the updrafts and downdrafts maximized?  Where has the air been warmed or cooled, and how does this relate to the processes taking place?  What are the primary features of the airflow within the squall line?

### (EXTRA CREDIT---you don't need to do this part but it's an opportunity to gain a few extra points)

 Like you did up above, choose something to change in the model to run a squall-line experiment of your own.  Discuss the change(s) you made in the model and why you made them, present the results, and discuss and what the results mean.  A few possibilities (though feel free to come up with your own): increase the model's horizontal or vertical resolution; change the microphysics to use a scheme that includes ice; turn on Coriolis; change the initial thermodynamic or wind profile; add or subtract bubbles or change the characteristics of the bubbles (you'd need to alter the source code for this).  There are some other example soundings on the CM1 webpage if you would like to try any of them.



