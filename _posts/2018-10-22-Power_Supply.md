---
layout: media
title: "Benchtop Power Supply"
category: DIY
image:
  teaser: powersupply_v1.jpg
  feature: powersupply_v1_main.jpg
---


<h2 id="intro">Introduction</h2>
&nbsp;&nbsp;&nbsp;&nbsp;Goal of the project is to make a benchtop power supply from an ATX PC power supply.  I started this project a few months ago and made a working protoyped (pictured).
The intent was to have a 3.3V, 5V and a 12V rail with voltage and current sense, as well as a buck converted to drop the 12V to a user selectable voltage.  

&nbsp;&nbsp;&nbsp;&nbsp; After using it for a short amount of time, I learned that this power supply has quite a bit of voltage drop even when pulling a small amount of current (<100mA).  
The resistance from the output of the ATX supply to the front face of the supply is very small (<0.3 Ohm),so I don't think the drop is from that.  I grabbed this power supply 
from an old PC, so I am thinking it is just poor load regulation or the low side current sense is created an undesired ground potential.  Whatever the reason, it's perfect opportunity to upgrade.  



<h2 id="Upgrades">Upgrades</h2>
&nbsp;&nbsp;&nbsp;&nbsp; One area that I plan on changing is the current sense.  Right now this ebay module is setup for a low side sense and it will meaure the summation of all three power rails.  I designed a high side current sense (and voltage)
for each of the three rails using hall effect sensors.  This gives me a current sense range of 0-5A.  I also added a shunt resistor with a programmable gain amplifier to measure currents in the uA with reasonable accuracy.  

&nbsp;&nbsp;&nbsp;&nbsp; The next major upgrade will be the display.  I'm adding a 3.5" TFT LCD touchscreen, purchased from ebay for about $8 (Note: I do not recommend this display, as you get shipped an LCD with an unknown LCD driver.  It was very 
difficult to get the Arduino to display anything on here.  It took hours and hours of hunting down the correct [library](https://www.arduinolibraries.info/libraries/mcufriend_kbv).  Definitely worth the extra $20 for a known
and reliable display)).  Planned upgrades is for the display to autoscale the currents to uA, mA or A.    
 
<iframe width="1280" height="720" src="https://www.youtube.com/embed/xq3ul1rn_Qg" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
  
 
&nbsp;&nbsp;&nbsp;&nbsp; I'm also adding MOSFETs to enable or disable each rail and a PolySwitch for a soft over-current limiter.  

![Schematic Rev -](/images/ps_schem.PNG)