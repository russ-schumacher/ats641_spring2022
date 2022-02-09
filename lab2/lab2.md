# Lab assignment 2

For lab assignment 2, we'll build on some of the python/MetPy setup that you did in the first lab assignment. In particular, we'll make some maps from a recent event, and to diagnose some fields traditionally associated with QG forcing for ascent.  Namely, we'll plot the 500-hPa absolute vorticity advection, and the 850-hPa temperature advection.  For this exercise, we'll use the gridded NAM analysis from the major Front Range snowstorm at 1200 UTC 14 March 2021.

- To start, we can use the template this template from Unidata [https://unidata.github.io/python-training/gallery/500hpa_vorticity_advection/](https://unidata.github.io/python-training/gallery/500hpa_vorticity_advection/).  Start a new notebook, and you can copy the code from this page in to cells as you go.  (One hint regarding notebooks is that if you run into trouble, you can break up the code into even more cells to isolate the problem. But - remember that if you define a variable in one cell and change it farther down, if you need to set it back to the original value you'll need to go back up and re-run the earlier cell(s).)

- In this example, we get archived GFS gridded analysis data from NCEI. Change the date and time in the code to match the time given above. 

- Because we will use the temperature field later, add `Temperature_isobaric` to the list of variables that are pulled in when creating the `data_subset`

- The rest of this code should then produce a map of 500-hPa vorticity advection. One thing you may want to experiment with is the level of smoothing, to optimize the "look" of your map.

- While you're going, one good thing to check to make sure all is well is to check the units of a variable or two.  This can be done just by typing the name of a variable (like `hght_500`) into a new cell and running it. What are the units of your calculated vorticity advection, and do they match with what the units should be for this field? 

- Now we'll move on to calculating and plotting the 850-hPa temperature advection. You won't need to re-run a lot of the earlier code, because you've already read in much of what you need. Instead, you'll just need to repeat where you get the height and winds at 500-hPa but this time for 850 hPa, and make sure to also read the temperature at 850 hPa in Kelvin.

- You can use your earlier code as a template for calculating the 850-hPa temperature advection.

- And now, plot the 850-hPa heights, winds, temperature, and temperature advection.  For plotting details, you might find this example helpful: [https://unidata.github.io/python-training/gallery/850hpa_temperature_advection/](https://unidata.github.io/python-training/gallery/850hpa_temperature_advection/).  (Note that not all details of that example will work because it uses a different dataset.)

- OK, you should now have maps of 500-hPa vorticity advection and 850-hPa temperature advection. Include these maps with your assignment when you turn it in. Discuss what the maps show in terms of where QG forcing for ascent and descent exist at this time.  Are there areas where the two maps give conflicting information in relation to QG forcing?

- Now we'll also use this same gridded analysis to calculate 850-hPa Q-vectors (and their divergence).  There are a couple tricky aspects to plotting Q-vectors with MetPy, so I've provided a sample notebook here, which should work once you've done all the steps up to this point: [https://github.com/russ-schumacher/ats641_spring2020/blob/master/lab2_qvectors_only.ipynb](https://github.com/russ-schumacher/ats641_spring2020/blob/master/lab2_qvectors_only.ipynb).  You'll probably just want to copy these cells into your own notebook that you've been using.  Plot the 850-hPa heights, Q-vectors, and Q-vector divergence.  Where does this diagnostic indicate QG forcing for ascent?  How does it compare with what you found earlier for the "traditional" QG omega equation?

- Are there any locations where you see a direct connection between the Q-vectors you calculated in question 1 of the lab?  If so, discuss.

- Locate a radar image at the approximate time that we've been analyzing. If you want to make your own, the Iowa State RadMap API: [https://mesonet.agron.iastate.edu/GIS/radmap_api.phtml](https://mesonet.agron.iastate.edu/GIS/radmap_api.phtml) is a great resource, or else feel free to find one that already exists, like in the NCAR MMM image archive [https://www2.mmm.ucar.edu/imagearchive/](https://www2.mmm.ucar.edu/imagearchive/).  Do the regions of precipitation shown on the radar image generally correspond to the regions of forcing for ascent that you've identified?  Briefly discuss any notable consistencies or inconsistencies.

- Finally, think back to the diagnostics we used to represent the "traditional" QG omega equation, and in particular the 500-hPa vorticity advection.  In using this diagnostic, there's one potentially important simplification that has been made with respect to the equation. State what this simplification is and whether you think it's reasonable in this case.





