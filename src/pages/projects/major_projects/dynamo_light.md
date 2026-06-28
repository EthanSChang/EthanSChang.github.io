---
layout: /src/layouts/MarkdownWorksLayout.astro
title: 'Dynamo Light'
---
<p style="text-align: center;">I wanted to design another pcb, so I decided to build a dynamo light to go with the gravel bike I just built. The light is designed to output ~500 lumens in normal operation and ~150 lumens in standlight mode (where the light stays on when the dynamo is not providing power). The standlight is powered by a large supercapacitor, and is sized to last for around 90 seconds.</p>


<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/dynamo_light/led_schematic.webp">
<img class="markdown_image" src="/major_projects/dynamo_light/led_layout.webp">
</div>

<p style="text-align: center;">The first board I designed is the LED and LED driver board. Its a pretty simple constant current buck driver and a Cree XM-L2 led. The LED has thermal vias under the central pad to conduct heat to the ground plane on the back of the board. There is also exposed copper in the area of the LED on the back of the board to provide a spot for thermal paste to conduct heat to an aluminum plate. The third pin to the board is an analog dimming signal, used to dim the brightness once the light switches into standlight mode.</p>

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/dynamo_light/psu_schematic.webp">
<img class="markdown_image" src="/major_projects/dynamo_light/psu_layout.webp">
</div>

<p style="text-align: center;">The second board in the light is the power supply for the LED driver. First, the dynamo output is passed through a bridge rectifier. A zener diode clamps the DC voltage to 30v to prevent damage to downstream components when the dynamo voltage rises due to low load. The DC output of the rectifier is then regulated down to 5v with a buck converter. On the 5v rail is the MAX38889, which handles the supercapacitor backup function. When the MAX38889 goes into backup mode, the BKB pin is pulled low, which pulls current through a voltage divider, sending the dim signal to the LED board. I also included two potentiometers, one to adjust the supercapacitor charging current between 0.6A and 1.5A, and the second to adjust the dimming signal to vary the brightness in standlight mode.</p>

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/dynamo_light/led_board.webp">
<img class="markdown_image" src="/major_projects/dynamo_light/led_test.webp">
</div>

<p style="text-align: center;">I built the LED board first. It was pretty simple, but it was my first time using solder paste and a stencil. It took a few tries to get the paste applied evenly, but everything ended up working well. I was pleasantly suprised at how little heat the board generates even without a heatsink.</p>

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/dynamo_light/psu_paste.webp">
</div>

<p style="text-align: center;">The power supply board went together pretty easily as well. The fine pitch of the QFN package of the MAX38889 required a bit of rework to remove some solder bridges, but otherwise wasn't too difficult.</p>

<div class="markdown_img_container">
<img class="markdown_image" src="/major_projects/dynamo_light/assembled1.webp">
<img class="markdown_image" src="/major_projects/dynamo_light/assembled2.webp">
</div>

<p style="text-align: center;">Both boards worked perfectly first try! Everything seems as expected, and I can vary the standlight brightness such that the standlight lasts up to ~4 minutes. So far I've only tested with a bench power supply, not the actual dynamo. Next up is to design the housing and test with the actual dynamo. I also have plans to build a rear light with a similar architecture.</p>
