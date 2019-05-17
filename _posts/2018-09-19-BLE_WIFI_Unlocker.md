---
layout: media
title: "BLE Wifi Door Unlock"
category: DIY
image:
  teaser: doorUnlocker/doorunlock_3D_t.png
  feature: doorUnlocker/doorunlock_3D.png
---





I recently moved into a new home and am forced to carry a key with me to unlock/lock the front door.  In my previous home, I would always go through the garage and use the built in garage door opening in my car to get into the house
so I never had this problem.  Seeing as how the off-the-shelf bluetooth door unlockers are $200+ and do not do what I want, I figured I could make mine for under $10.   already had most of the parts needed and access to a 3D printer, which makes this project a much easier to put together.

<nav class="toc">
<ul id="markdown-toc">
  <li><a href="#intro" id="markdown-toc-intro">Introduction</a></li>
  <li><a href="#hardware-list" id="markdown-toc-hardware-list">Hardware-List</a></li>
  <li><a href="#code" id="markdown-toc-code">Code</a></li>
</ul>

</nav>


<h3 id="keyfeat">Key Features</h3>
<ul>
  <li>Bluetooth, Bluetooth Low Energy (BLE) and WIFI</li>
  <li>Auto-detection of car and phone</li>
  <li>Schedule based Scanning</li>
  <li>Text Alerts</li>
  <li>Logging in Google Drive</li>
  <li>Guest list with texting for unlock code</li>
</ul>




<h2 id="hardware-list">Hardware List</h2>

I went through a few iterations of microcontroller selection for this project.  My main issue was trying to find a device that had BLE and Bluetooth classic and WIFI in one package, as I was trying to limit the cost and number of components in this design.  And since I had an outlet near the door, I remove the contraint of a battery operated device.  The RPIZW was the best solution I found for what I was trying to do.   It supported BT Classic, BLE and WIFI in one package with a bunch of open software libraries for interfacing with the hardware.  All the other hardware for this project, I had laying around from other projects.  

<ul>
  <li>Raspberry Pi Zero W (RPIZW)</li>
  <li>MG946R Metal Gear, Hi Torque Servo</li>
  <li>Momentary push button switch</li>
  <li>5V Relay</li>
  <li>Reed Switch (NO or NC)</li>
  <li>PCB Shield</li>
</ul>


A small shield was also created for the RPIZW for all the external hardware to plug into.  It was all fit on a 1"x 1" PCB with headers that plug right into the RPIZW.

 
![Schematic](/images/BTSU_shield.PNG)


<h2 id="software-list">Software Setup</h2>

Getting started was relatively straightforward with setting up Raspberian (linux distro for the RPIZW) and Python was chosen for this project.  With many libraries availble in Python, it was pretty simple to find what I needed.  Expanding upon the key features of the project, the software features needed can be split up. 

<h6>GMail</h6>
GMail was used to quickly setup a way to communicate to the RPIZW and a cell phone.  A cell phone can text the email account and using STMP/IMAP protocols, the RPIZW can read the message sent from the phone and respond back to it.  The RPIZW is setup so every 10 seconds it searches GMail for particular keywords that match an allowed command.  If it matches a command, it then verifies that the sender is on the allow list before the command is executed.  

<h6>GPIO</h6>
A few GPIO  ports are needed for interfacing to the servo and switches.  Raspberian has a built int library called Rpi.GPIO.  Basic setup for choosing inputs/outputs and setting up PWM to conntrol the servo.  Had quite a few issues with the built in PWM controller using that built in library.  Timing was all over the place causing lots of servo jitter.  In the end, it was decided that it really didn't matter, since it was only on for about one second and the required accuracy was < 20 degrees or so.  

<h6>Google Sheets</h6>
Google provides an API for accessing Google Sheets from remote devices.  The packages used for this were gspread and oauth2client.  The logging happens every time the door is opened and closed.  The device used and time is also recorded in the log.

<h6>Bluetooth</h6>
Raspberian also has built in support for bluetooth with a Python packages readily available.  With a supplied list of BT MAC addresses, the RPIZW will try to acquire the name of the BT device.  If the name received matches the allowed list, the device will be allowed to communicate with the Door Unlocker.


![Installed on my door](/images/doorUnlocker/installed.jpg)


<h2 id="Updated">Update</h2>
Been using this for about 9 months now, with very limited issues.  I did have once SD card crap out on me, but that SD card was about 7 years old and used for many of my other projects.  Only other main issue with this design is the RPIZW power input.  It uses a USB port and sometimes that gets knocked caused the RPIZW to reboot.  Creating a script to run the python code on start up fixed this issue.












