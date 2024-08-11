---
layout: /src/layouts/MarkdownWorksLayout.astro
title: 'Bike Linkage Simulation'
---

## **Background Info:**

 Rear suspension designs for mountain bikes are characterized by a few parameters, primarily: leverage ratio, axle path, anti-rise, and anti-squat (more info [here](https://www.pinkbike.com/news/introducing-behind-the-numbers-a-new-suspension-analysis-series.html)). For framebuilders, the standard analysis tool is [Linkage X3](https://bikechecker.com/), but I wanted to develop my own tool. Coincidentally, I also wanted to learn Python as Cal Poly doesn't teach ME students python in classes. Inspired by [Colin Reay's linkage analysis](https://forum.customframeforum.com/t/colins-trials-and-tribulations-with-bikes/549/32), I developed my own version.

<a href="https://github.com/EthanSChang/BikeKinematicSolver"><h3 style="text-align: center;">Github Link</h3></a>

## **Approach:**

-  I divided suspension linkages into 2 categories: 4-bar linkages, and single pivots. In both of these cases, the fundamental "unit" is the "link", a vector with a few other properties. 4-bar linkages are constructed out of 3 links (the 4th bar is a fixed vector), while single pivot suspensions are constructed out of a single link. 
 - **The link:** 
	 - A link is initialized with it's starting and ending points, and I store an array containing the x-component and y-component of the link vector. A link can also be initialized with "auxiliary points" that represent either the rear axle mounting point and/or the shock mounting point. Then I calculate the "auxiliary vector" from the link's start point to the auxiliary point. Finally, I store the transformation matrix that transform the link vector into the auxiliary vector. This is calculated by combining the length scaling factor (the ratio of the 2 vector lengths) with the rotation matrix for the angle between the two vectors.
     
- **4-bar linkages:**
	- A 4-bar linkage is constructed out of 3 links along with starting and ending positions. The starting/ending positions replace the 4th, fixed link. Given one of the link's angle, the other 2 links form a system of non-linear equations for the other 2 angles. I use numpy's fsolve to calculate these other 2 angles, and then update the 2 unknown links with the new x and y components using trig. 
	- For single pivots, this step is skipped, as the wheel and shock positions can be calculated directly given the link angle.
- **Wheel and shock positions:**
	- Given each link vector, I can solve for each joint position by summing each of the vectors. Using the transformation matrix calculated earlier results in the wheel or shock position in space.
- **Iterating over the suspension travel:**
	- To calculate wheel and shock positions over the whole travel, one of the links is rotated by a small angle (0.05 degrees). The new wheel and shock positions are recalculated, and stored in an array. This is repeated until the shock has reached it's maximum travel.
- **Calculating suspension characteristics:**
	- Given wheel and shock point arrays throughout the bike's travel, I can then calculate the leverage ratio, axle path, anti-rise, and anti-squat. Leverage ratio is simple; it's just the ratio of wheel travel to shock travel for each iteration. Similarly, axle path just involves plotting the axle points normalized to start at 0,0. Anti-rise and anti-squat are more complicated, involving calculating the instant center, chainline, etc. I followed these 2 methods for calculating these parameters: [anti-rise](https://bikerumor.com/suspension-tech-what-is-anti-rise/), [anti-squat](https://www.pinkbike.com/news/definitions-what-is-anti-squat.html).
- **Plotting:**
	- Once I have arrays storing the parameters over the whole suspension travel, the parameters are plotted with matplotlib. 

## **Results:**
The calculated results agree quite closely with published figures, which I'm quite happy about. They aren't perfect, but I suspect this is mostly due to the input data on the suspension geometry. I simply took an image of the bikes into Onshape and pulled pivot points off the image, but this likely isn't quite accurate. A few results are shown below.

<div class="markdown_img_container">
<img class="markdown_image" src="/linkage_simulation/cover_img.webp">
<img class="markdown_image" src="/linkage_simulation/raaw_madonna_pinkbike.webp">
</div>

<h3 style="text-align: center;">Raaw madonna v3 (horst link) - My results (left) and Pinkbike published results (right)</h3>

<div class="markdown_img_container">
<img class="markdown_image" src="/linkage_simulation/starling_megamurmur.webp">
<img class="markdown_image" src="/linkage_simulation/starling_megamurmur_pinkbike.webp">
</div>

<h3 style="text-align: center;">Starling MegaMurmur (single pivot) - My results (left) and Pinkbike published results (right)</h3>