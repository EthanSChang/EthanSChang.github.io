---
layout: /src/layouts/MarkdownWorksLayout.astro
title: 'PCB Design'
---

I've been wanting to learn how to design a PCB for a while, and I finally found the time to do so over winter break. I roped a friend into the project, and we decided to make a simple PCB with a raspberry pi pico, OLED display, Gyro/IMU, neopixels, buttons, and a temperature sensor. We split the work designing the schematic, I did most of the layout, and my friend did the software. I'm really happy with the PCB we designed. It is super simple, but I felt like it gave me a good foundation for more complex projects. My next PCB project is going to be a lot more complicated; I'm making a bike dynamo light. 

<div class="markdown_img_container">
<img class="markdown_image" src="/small_projects/PCB/schematic.webp">
</div>
<h4 style="text-align: center;">The schematic is fairly straightforward. The 8 neopixels are powered off the 5v USB rail, which did mean I have to add a level shifter chip from the 3.3v pi pico logic. However, according to various sources, normal I2C level shifter ICs are too slow for the neopixel communication. Instead, I selected a non inverting buffer chip that I found recommended for neopixels. The temperature sensor is the MPC9808, a simple I2C sensor. All the ICs have decoupling capacitors and the I2C line has pullup resistors. </h4>

<div class="markdown_img_container">
<img class="markdown_image" src="/small_projects/PCB/layout.webp">
</div>
<h4 style="text-align: center;">Layout was also pretty simple. The board is a 2 layer board, with a 3.3V power plane on the top layer and a ground plane on the bottom. I did my best to follow best principles, such as by placing the decoupling capacitors nearby the power pins. All the passive components were 0805 size for ease of soldering. We chose to use a breakout board for the gyro and pi pico since I don't have the capability to solder QFN packages at home.</h4>

<div class="markdown_img_container">
<img class="markdown_image" src="/small_projects/PCB/assembled.webp">
<img class="markdown_image" src="/small_projects/PCB/pong.webp">
</div>

<h4 style="text-align: center;">We had the board fabbed with JLCPCB and ordered components from digikey. Soldering was mostly easy, except for the temperature sensor. The pin pitch was super small, making solder bridges inevitable. I ended up getting it working, although 2 pins are still shorted. Luckily the shorted pins are 2 of the I2C address select pins, which both had to be grounded anyways. Somehow, everything worked perfectly on the first try! Our quick demo project was to recreate pong.</h4>

