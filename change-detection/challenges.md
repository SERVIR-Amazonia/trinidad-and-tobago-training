---
layout: page
title: Challenges - Customize Your Change Detection
parent: Two Date Change Detection
nav_order: 3
---

# Overview

These challenges are an addendum to the Water Change Detection module. After your script is complete and functional, complete one or several of the challenges below.

**Challenge 1.** Try using a different index, such as MNDWI (Modified Normalized Difference Water Index) or a Tasseled Cap Transformation (refer to EEFA book chapter [F3.1 - Section 2 Manipulating Images with Matrix Algebra](https://www.eefabook.org/table-of-contents.html)), to run the change detection steps, and compare the results with those obtained from using NDWI.

**Challenge 2.** Experiment with adjusting the `thresholdLoss` and `thresholdGain` values.

**Challenge 3.** Use what you have learned in the Mangrove Mapping and Flood Mapping workshops to run a supervised classification on the difference layer (or layers, if you have created additional ones). Hint: To complete a supervised classification, you would need reference examples of both the stable and change classes of interest to train the classifier.

**Challenge 4.** Think about how things like clouds and cloud shadows could affect the results of change detection. What do you think the two-date differencing method would pick up for images in the same year in different seasons?
