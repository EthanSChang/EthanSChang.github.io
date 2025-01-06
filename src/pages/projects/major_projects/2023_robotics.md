---
layout: /src/layouts/MarkdownWorksLayout.astro
title: '2023 FRC'
---
2023 was my senior year of high school, and my last year of FRC. Coming off of a quite [successful year](/projects/major_projects/2022_robotics) in 2022, we were cautiously hopeful of our chances for the year. <a class="accent" href="https://www.youtube.com/watch?v=0zpflsYc4PA">This year's game</a> was focused on picking up and placing miniature traffic cones and inflatable cubes. The game posed two major hurdles: 1. manipulating oddly shaped game pieces, and 2. placing those game pieces far away from the robot, requiring almost 4 ft of extension outside of the robot. 

Like last year, I was again the design lead for the team. However, this year, we had more people interested in design, so I only designed one subsystem (the drivebase) and focused on managing the designers and integrating subsystems together. With more people collaborating on the design, I decided to try a different approach at cad organization:

The main robot assembly and master geometry sketches would be a single document. Each of the mechanisms would have it's own document, where the master geometry sketches would be derived from the main document. Each of the mechanisms could be imported into the main assembly from the mechanism documents. The main advantages of this approach was that it separates versioning and changes between mechanisms, and it reduces regeneration time. When all the cad was in the same document, every small change to a mechanism would have to be propagated through to the whole robot cad. Now, changes only propagate when the document is versioned and updated.

Here you can see the master geometry sketches for the robot. I started with field geometry and worked down to key mechanism geometry.
<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/mastersketch.webp">
</div>

From there, we started working on the major mechanisms. Deciding on the extension mechanism was likely the most important decision we made the whole season. Since it was so large and complicated, we wouldn't have another shot to get it right, and it's size means it drives the other mechanisms' packaging requirements. We evaluated a few options, ending up with a single stage elevator with a virtual 4-bar rotation arm on the end. This was mostly due to simplicity, since we were already familiar with single stage elevators from 2022. 

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/extension.webp">
</div>

The extension mechanism is one of my favorite mechanisms we've designed. The gearbox that drives the rotation arm is packaged nicely in between the moving stage of the linear elevator. We even managed to fit an absolute encoder in the space. However, we couldn't simply attach the absolute encoder to the gearbox, since there is a second chain reduction between the gearbox output shaft and the arm pivot. Instead, I simply recreated that gear ratio with a belt and pulley, syncing the encoder to the arm's rotation.

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/extension_gearbox.webp">
</div>

Another neat aspect about the extension is the 4-bar linkage that keeps the intake/grabber at a constant angle relative to the ground. Instead of having separate links, a loop of chain creates the "virtual 4 bar". One sprocket is fixed to the linear elevator, while the other is fixed to the intake. This allows for much more angular rotation and is more compact. 

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/v4bar.webp">
</div>

Perhaps the most interesting part of the extension is the encoder setup. We wanted to know the absolute position of the arm at all times. However, an absolute encoder only reads 1 revolution, and the main drive shaft undergoes many revolutions during the full extension/retraction. Suppose we place 1 absolute encoder directly on the drive shaft. This gives the angle of the shaft, but not the number of rotations. Lets say the encoder read 0 degrees. Then, based on just this encoder, we know that the motor could be at 0, 360+0, 2x360+0, nx360+0 ... degrees. In addition, a second encoder is geared to the first encoder with a ratio close to 1:1, lets say a 15:16 reduction. Now, lets say the first encoder reads 0 degrees again, but the second encoder reads 337.5 degrees. Well, 337.5 degrees is 360 degrees x 15/16. Therefore, the first encoder rotated 1 full revolution, 360 degrees. The second encoder gives us the n, the number of rotations. Combined, we know the absolute angle of the system. Unfortunately, this setup wasn't quite necessary for us, with relative encoders being sufficient. However, it was still a super interesting way to get absolute position for 10+ rotations.

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/encoders.webp">
</div>

The extension was by far the most difficult part to design of this robot. However, we still needed an intake. This was a fairly simple mechanism. 2 sets of wheels allow us to grab both cones and cubes in the same mechanism. However, it did take 2 revisions to nail down the back set of wheels so that it could reliably hold cones. 

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/handoff.webp">
</div>

Last was the ground intake. We knew from the start that this would be challenging. We ended up wasting a few weeks on a mechanism that was supposed to pick up both both game elements and hand them off to the arm intake. We should have abandoned this idea way earlier, but oh well. The solution we ended up with used a pair of horizontal rollers to grab the flange of the cones, and eject them in the lower level (left). We also modified the arm to allow it to reach to the ground and pick up cubes from the ground (right). Ultimately, ground pick up wasn't super useful to us since the ground game pieces were often handled by other robots pretty quickly. 

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/cone_intake.webp">
<img class="markdown_image" src="/major_projects/2023_robotics/cube_intake.webp">
</div>

Build season quickly flew by, and then it was time for competition. Our first competition in week 1 went better than we could ever have hoped for, with us finishing 3rd and winning the excellence in engineering award. Earlier in the season we decided to focus on setting up automatic game piece placing, rather than focusing on the autonomous mode. This meant we outscored the majority of teams who had the drivers align the robot, even if we were slightly behind in auto. Our second competition, Sundome, was more of a mixed bag. We consistently ran into electrical gremlins and performed inconsistenly. However, for a few days, we held the <a class="accent" href="https://www.youtube.com/watch?v=KYA3zd6EpGI">world record</a>! Then it was onto our third competition, which we used as practice for new members since it didn't count towards our rankings. 

Before we knew it, it was time for district championships. Over spring break a few members rewired the whole robot in hopes of fixing the electrical issues we kept running into. This turned out to save our competition. We were incredibly consistent at DCMP, seeding 5th and placing 3rd after eliminations, meaning we had qualified for the world championship for the first time since 2017!. Worlds was a mixed bag, with a sheared arm pivot putting us out of commission for a few matches and ultimately ending our elimination bid. This season was an amazing way to end my FRC experience, with a robot that placed 10th in the PNW and qualified for worlds!

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/2023_robotics/full_bot.webp">
<img class="markdown_image" src="/major_projects/2023_robotics/in_pit.webp">
<img class="markdown_image" src="/major_projects/2023_robotics/closeup1.webp">
<img class="markdown_image" src="/major_projects/2023_robotics/closeup2.webp">
<img class="markdown_image" src="/major_projects/2023_robotics/closeup3.webp">

</div>
<!-- ![The San Juan Mountains are beautiful!](/src/images/2023_robotics/cover_img.jpg) -->