---
layout: media
title: "GPS Logger"
category: DIY
image:
  teaser: GPS_logger_assembly.png
  feature: GPS_logger_assembly.png
---



Goal of the project is to make a lightweight GPS logger that has a few different functionalities.  I couldn't find a GPS tracker that had the features I was looking for, had the battery life or was reasonably affordable.  
I started this project a couple years back, but I have been constantly been changing the design, form factor and features.  Currently the design uses  a few breakout boards for convenience.  The end goal is to remove those
and reduce the overall form factor.  The next biggest upgrade will be switching to a Nordic based uC to further reduce the form factor and for built in Bluetooth.


<ul>
  <li>SD Card writing/reading</li>
  <li>BLE to transfer data to a smart phone</li>
  <li>Temperature, humidity, and pressure measurement</li>
  <li>60+ hour battery life</li>
  <li>E-Ink display</li>
</ul>

One of my favorite additions to this project is the inclusion of pogo pins for the Li-ion battery.  This allows for easy swapping of depleted batteries for the longer trips.  

![Bogo pins](/images/battery_pogo.png)

I also managed to mess around with the E-Ink display as well and created a fun little GUI for this device.  Next challenge is to port over the code the nRF52.  With each iteration of this design, I have been shrinking the design.  The main limitation of my designs used to have been the size of the parts I have been using.  But since I have been getting more familar with smaller components, I am able to hand assemble down to 0402 resisitors and with my new hot air rework station, I will do QFN type packages too.  In addition to those and getting a microscope, my designs have been shrinking and becoming more of an embedded solution.  I'm excited to see the next revision of this project and what it will soon look like.  Now I just need a way to find more time to work on it....
![Eink demo](/images/gpsLogger/eink.png){: .center-image }
