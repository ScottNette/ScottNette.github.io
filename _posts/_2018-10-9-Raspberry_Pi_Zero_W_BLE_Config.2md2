---
layout: media
title: "Raspberry Pi Zero W BLE Setup"
category: DIY
image:
  teaser: pi_zero_w.jpg
  feature: pi_zero_w_feat.jpg
---


<h2 id="intro">Introduction</h2>

Here are the reference materials I used for this.


[Refernce for hciconfig](https://www.systutorials.com/docs/linux/man/1-hciconfig/)  
[Setup for golan](https://www.thepolyglotdeveloper.com/2018/02/scan-ble-ibeacon-devices-golang-raspberry-pi-zero-w/)  
[Monitorless setup for Pi W Zero](https://www.thepolyglotdeveloper.com/2016/02/use-your-raspberry-pi-as-a-headless-system-without-a-monitor/)  
[Setup for Node.js](https://www.thepolyglotdeveloper.com/2018/03/use-nodejs-raspberry-pi-zero-w-scan-ble-ibeacon-devices/)  


<h2 id="intro">Shutting down BLE services</h2>


*Need hciconfig installed first

{% highlight shell %}
sudo hciconfig hci0 down
sudo service bluetooth stop
{% endhighlight %}

Scan for new devices
{% highlight shell %}
sudo hcitool lescan
{% endhighlight %}



Blue dot
https://bluedot.readthedocs.io/en/latest/gettingstarted.html


