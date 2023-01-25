---
layout: page
title: Data Processing
parent: Introduction to Synthetic Aperture Radar (SAR)
nav_order: 3
---

# Data Processing
One of the challenges associated with remote sensing data is the processing steps a user must go through in order to make the data analysis-ready. Radar data, specifically the side-looking characteristic of its data collection mechanism, presents its own specific set of processing challenges. Let’s explore those challenges and required corrective steps here.

## Data Distortion
The data values collected by SAR systems can be distorted in two primary ways: geometric and radiometric. 

### Geometric
**Slant range.** This type of distortion is caused by the fact that the distance between the radar antenna and the target, known as the slant range, is not constant along the image. This happens because the radar antenna is not perpendicular to the ground, but rather it is pointed at an angle (side-looking). Thus, within a radar image, objects that are closer to the radar system appear compressed while objects farther away are more stretched out. The image does not represent the true horizontal, ground range distance on the surface of the Earth. In order to measure distances between objects, this distortion must be corrected.

[IMAGE slant vs ground range]

**Layover.** This type of distortion occurs more often in mountainous areas. This error will cause features to appear at the wrong location or in the wrong direction because of the timing in which the radar beam hits the object. For example, a radar beam may hit the top of a tall mountain before it hits the base of the mountain. Since it reached the top of the mountain first, it will receive the signal from the top of the mountain earlier than the signal from the base of the mountain, and will thus appear shifted towards the radar system and look as though the top of the mountain is *laid over* the base.

[IMAGE layover before and after]

**Foreshortening.** This type of distortion occurs when an object is tilted towards the radar system, as in mountainous areas. The angle between the base and the top of the object will appear compressed due to the timing in which the radar beam hits the object and the fact that radars have slant range distortions. Foreshortening severity can vary, and is most severe when the radar beam is directly perpendicular to the object’s slope. For example, if a radar beam hits the base of a mountain before it hits the top of the mountain, the distance between the base and the top of the mountain will appear much shorter than the actual physical distance because of slant range distortions. 

[IMAGE foreshortening before and after]

### Radiometric
**Antennae pattern and signal strength.** Radar beams emit more power in the middle of the swath rather than the near or far portions of the swath. This results in an image that has stronger results in the center rather than the near or far edges. This distortion is called the *antennae pattern*, and it varies significantly depending on the range of the image. Across an image swath, the strength of the return signal diminishes in the farther ranges of the swath. Part of the antennae correction may include a step to produce a uniform average brightness to correct for this effect. 

**Topographic effects.** Topography, especially complex topography, may skew the backscatter values received by the radar system. Steep slopes can, for instance, cause a brightening effect. These effects must be removed in order to capture data related to the characteristics of the Earth you are interested in studying, such as vegetation or soil moisture. 

[IMAGE radiometric before and after]

### Additional Challenges
**Shadow.** This type of error is conceptually similar to that of clouds in optical imagery. When the radar beam illuminates a large or steep vertical object, such as a mountain or tall building, it may be unable to illuminate the ground on the farther side of the object, resulting in shadow effects on the image. The effect is particularly pronounced at the top of the vertical object, where the incidence angle is larger. Although you can apply some shadow corrections and attempt to fill in the data gaps using interpolation methods, many researchers choose to treat the shadows as missing data – just like the masked out portions of cloudy images.

[IMAGE shadow]

**Speckle.** This error is the result of random noise and interference from the radar waves that occurs within the pixel cell. It results in a grainy, almost salt-and-pepper image appearance. There are lots of different gray tones that may appear within a single, uniform surface as the result of speckling.  These variations must be filtered in order to improve the visual quality of the data and make it easier to identify features. Unfortunately, the correction method often used to reduce speckling reduces the resolution, so you must balance the visual quality of the image with the resolution of data.

[IMAGE speckle]
