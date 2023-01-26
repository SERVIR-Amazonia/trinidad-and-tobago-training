---
layout: page
title: SAR in QGIS
parent: Introduction to Synthetic Aperture Radar (SAR)
nav_order: 5
---

# SAR in QGIS
While most data processing happens in SNAP, you can use those processed images to do some analysis and visualization of SAR data in QGIS as well. The ASF [website](https://asf.alaska.edu/how-to/data-basics/data-recipe-tutorials-2/) has a number of good “recipes” for using SAR data in various platforms, including QGIS. Let’s go through a similar classification exercise to look at our processed images in the QGIS platform.

#### Exercise 4.1 Open and view SAR imagery in QGIS.
Open QGIS. 
Create a new project by selecting the `New Empty Project` template. 
Save your project as `intro-radar`. 
Click on `Layer > Add Layer > Add Raster Layer…`. 
Select the `...` next to the `Raster dataset(s)` field. 
Navigate to the `intro-radar-data > subset_0_of_S1A_IW_GRDH_1SDV_20230120T090602_20230120T090627_046865_059EA0_7322_Cal_ML_TC.data` folder. We know this is the folder for the fully corrected image, since the file ends in `Cal_ML_TC`. 
Select the `Sigma0_VH` and the `Sigma0_VV` bands.
Click `Add` and then close the window. 
**Convert the bands into decibels.** The bands we converted into dB in our SNAP analysis did not save in the file, so we have to do that in QGIS to properly view the image. 
Go to `Raster > Raster Calculator…`
In the `Raster Calculator Expression` field, enter the following: `10*log10(VV)`.
Now highlight the portion of the equation where it says VV and input the actual band by double-clicking on the `Sigma0_VV` band in the `Raster Bands` field. Your equation should now read: `10*log10(“Sigma0_VV”)`.
Click on the `...` next to the `Output layer` field. Save the file in the `intro-radar-data` folder and name it `Sigma0_VV_db`. 
Click `OK`.
Repeat steps a-e for the `Sigma0_VH` band.

You should see two new bands added to the map canvas. These look brighter and more similar to the `db` bands we viewed in the `SNAP` software. Now let’s manipulate the bands to create another water classification and an RGB image.

#### Exercise 4.2 Create an RGB image in QGIS. 
It is important to note that there are no standardized rules on how to represent microwave data visually, nor specific rules on how to compose a 3-channel color image from only two input channels. The `HH, HV, HH/HV` and `VV, VH, VV/VH` combinations for `R, G, B` are both commonly used in remote sensing for generating an RGB image from Sentinel-1 C-band SAR imagery.

Since we are using a DV type image, we will be using the `VV` band for `R`, `VH` for `G`, and a ratio band `VV/VH` for `B`. First, create the ratio band.
Select `Raster > Raster Calculator…`.
In the `Raster Calculator Expression` field, enter the following: `"Sigma0_VV_db@1"/"Sigma0_VH_db@1"`
Click on the `...` next to the `Output layer` field. Save the file in the `intro-radar-data` folder and name it `Sigma0_db_ratio`. 
Click `OK`.
Merge the bands into a single image to generate an RGB image.
Select `Raster > Miscellaneous > Merge…`
Select `...` next to the `Input Layers` field and check the boxes next to `Sigma0_VV_db`, `Sigma0_VH_db`, and `Sigma0_db_ratio`. Drag the bands to ensure they are listed in that exact order.
Click `OK`.
Check the box `Place each input file into a separate band`.
Select `... > Save to File…` next to the `Merged` field. Save the file in the `intro-radar-data` and name it `sentinel-1-rgb`. Click `Save`.
Click `Run`. 
Click `Close` to close the window.

Great! Now we have an RGB image generated in QGIS. It should look fairly similar to the one we generated in SNAP. Next, let’s replicate the water binary classification methodology that we did in SNAP.

#### Exercise 4.3 Classify water/non-water in QGIS.

**Confirm the threshold for our classification scheme.**
Right-click on the `Sigma0_VH_db@1` layer name and select `Properties`.
Click on the `Histogram` tab.
Click `Compute Histogram`. 
A histogram with two peaks should appear. Confirm the value that separates the water values (minimum peak) from the non-water values (maximum peak).
It appears that the value is about the same, so we can use the same threshold that we did in the SNAP software. 
**Create a binary image.**
Select `Raster > Raster Calculator…`.
In the `Raster Calculator Expression` field, enter the following: `255*(Sigma0_VH_db@1<-18.38)`
Click on the `...` next to the `Output layer` field. Save the file in the `intro-radar-data` folder and name it `water_nowater`. 
**Color the image.** QGIS gives you a lot more flexibility with the color options, so get creative and make the image look nice!
Right-click on the `water_nowater` image name in the `Layers` panel and click `Properties`. 
Select the `Symbology` tab.
Next to the `Render type` field, choose `Singleband psuedocolor` from the dropdown menu.
Next, select a color ramp or make your own. Make sure to follow the golden rules of data visualization. 

Terrific! Now you have a beautiful image that illustrates the water bodies in the region in QGIS. 

**Congratulations!** You completed the Introduction to Synthetic Aperture Radar (SAR) workshop. Don’t forget to complete the feedback form, and get ready to build on this material to do even more complex analyses in future workshops. Way to go!
