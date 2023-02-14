---
layout: page
title: Practice: Making Your Own Classification
parent: Mangrove Mapping Using Multiple Sensors
nav_order: 4
---

# Overview

You've successfully written a remote sensing workflow to train a Random Forest classification model to map Mangrove presence with the Landsat archive. Now make it your own! There are several ways to tweak the original workflow right away to change the objective and make improvments. Here are a few ideas. 

*Tip*: The Docs tab is your friend. If you see a function is being used in the script, find that function in the Docs to see what the required arguments are. It'll help you understand how to change the pre-existing functionality. 

<img align="center" src="../images/mangrove-mapping/Docs.png" hspace="15" vspace="10" width="600">


## Area of Interest (AOI)

We defined our AOI at the beginning of the script using FAO GAUL data. As discussed previously you can define an AOI in GEE in many other ways. Review Step-Through Part 1 section to get some ideas. 

## Date Range

After merging together our full Landsat `ImageCollection`, we filtered it on a date range (i.e. 2000-2005). Come up with another date range that you'd like to map mangroves for. Remember that we can also specify a Day of Year range in our filters on the `ImageCollection`. This is useful for areas where there is heavy cloud cover during a certain time of year, or the phenomena you want to map exhibits a specific seasonal pattern that we can sense from satellite data.

## Model Improvements

There are several ways we could make our RF model more robust... 

The first is in the number of 'trees' in the Random Forest. You can change that in the `ee.Classifier.smileRandomForest()` function and observe whether any of the accuracy metrics have improved. 

Beyond the model itself, we can also provide more and/or better reference data. The first improvement would be to increase the amount of total samples. Try a number between 200 and 500 per class. 

To provide better quality reference data, we can look for another source of Mangrove presence/absence data, or make our own. Making your own will take time and expertise. However, take a look under the `projects/caribbean-training/_data/` asset folder for another source of presence/absence data. How could you replace the Giri et al 2011 data in the workflow with this other data source?