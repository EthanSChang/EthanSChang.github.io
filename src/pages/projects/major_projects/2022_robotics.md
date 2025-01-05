---
layout: /src/layouts/MarkdownWorksLayout.astro
title: '2022 FRC'
---

My first full season of FRC robotics was 2022. <a class="accent" href="https://www.youtube.com/watch?v=LgniEjI9cCM">The game</a> involved shooting large balls into a goal and lifting the robot off the ground onto a set of horizontal bars at the end of the game. I led the whole design team, and designed the climber and ball intake. This was also our team's first year using Onshape. We ended up chosing to switch to Onshape from Solidworks because it lends it self to top down design and rapid collaboration rather well. It's also quite accessible for people new to cad.

I started by roughing out subsystem space claims and key dimensions, "crayon" cad style. 
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/block_cad.webp">
</div>

Once the subsystems had major design decisions locked down, we proceeded to the full cad model. I implemented a top-down design process, unlike in the past with solidworks. Onshape was great for this, with features such as in context modeling, derived sketches, and part studios. All the subsystems start with an overarching geometry sketch, and parts are built off that. For 2023, we took this a step further, which you can read about [here](/projects/major_projects/2023_robotics). 

The first subsystem I designed was the intake, which collects the balls from the field. The intake takes the majority of abuse, since it extends outside the robot's bumpers. It has to sustain impacts between 150lb robots going 15 ft/s. 

The first part of designing the intake was to determine the geometry of the rollers that collect the balls. Three rollers made of squishy rubber wheels bring the balls over the robot's bumpers and into the hopper. The rollers are represented by the solid circles in the geometry sketch.
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/intake_geo.webp">
</div>

After the basic roller positions in the deployed state, I designed the linkage that retracts/extends the intake. I quickly determined that a 4 bar mechanism would be necessary to allow the intake to retract into the available space. I determined this geometry by sketching the rollers in the extended and retracted states, and connecting the two with lines that represent the individual links in the 4-bar mechanism. Here is a case where Onshape's top down design features came in handy. The in context modeling feature allows sketches and parts to be created on top of the main assembly. While sketching the linkage geometry, I could easily see how well my design fits in the available space. 
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/4bar_geo.webp">
</div>

From here, I designed the main plate (grey) and the two linkage arms (blue). Both were designed to be made out of 1/4" polycarbonate, something durable enough to withstand impacts. A simple sketch confirmed that the plates would have clearance in both the retracted and extended states.
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/main_plates.webp">
<img class="markdown_image" src="/major_projects/2022_robotics/plates_clearance.webp">
</div>

Next was mounting the pneumatic cylinders that would deploy the intake. Here I made an interesting decision. Most intakes extend the piston to deploy the intake. However, the pistons are susceptible to bending when the fragile rods are extended. To minimize this risk, I designed the intake to retract the pistons to deploy the intake. When the piston rods are fully retracted, the piston is much stronger. The tradeoff for this is that packaging the pistons neatly into the intake was challenging.
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/retracted.webp">
<img class="markdown_image" src="/major_projects/2022_robotics/extended.webp">
</div>

The intake ended up working incredibly well. The polycarbonate plates were compliant enough to absorb impacts, lasting the whole season without needing replacements. The pneumatic cylinders ended up acting as gas springs, so when the intake was hit from the front the intake would just fold back into the robot. We didn't have to replace a single piston! You can see the intake's compliance in action in the video below (center-right blue robot).
<div class="markdown_img_container">
<video class="markdown_image" controls> <source src="/major_projects/2022_robotics/intake_video.mp4">
</div>

The second subsystem I designed was the climber, which was a fairly straightforward single stage chain driven elevator. I took the same design approach as the intake, starting with defining major geometry and working down to individual parts.
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/climber_assem.webp">
</div>

My favorite part of the climber is the pneumatic latch. At the end of the match, power is cut to the motors, which would cause the robot to fall. However, since climb points aren't socred until 5s after the match ends, we needed a way to keep the robot in the air. The solution I came up with uses a small pancake pneumatic cylinder and a gearbox ratchet. I removed the pawl from the ratchet, and located the piston such that the piston shaft (yellow) would block the ratchet gear (black) from rotating, locking the gearbox and the climber. By placing the ratchet lock at the input side of the gearbox, the bending force on the piston was kept small, <10lbs. 
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/climber_lock.webp">
</div>

With both of my mechanisms designed, I focused on helping other designers and integrating all of the mechanisms together. I also helped fabricate parts with our new CNC router. The rest of the build season went fairly smoothly, and then it was onto competition! We did great, coming off of COVID and a few bad years. We won excellence in engineering at our first competition, qualified for the district championship, and missed qualifying for the world championship by 1 place. 

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2022_robotics/cover_img.webp">
<img class="markdown_image" src="/major_projects/2022_robotics/driving.webp">
<img class="markdown_image" src="/major_projects/2022_robotics/climb.webp">
<img class="markdown_image" src="/major_projects/2022_robotics/closeup1.webp">
<img class="markdown_image" src="/major_projects/2022_robotics/closeup2.webp">
</div>

<!-- dcmp 2022 qual 94 1:51 for intake compliance -->