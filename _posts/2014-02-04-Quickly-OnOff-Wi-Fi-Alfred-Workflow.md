---
layout: post
title:  "Quickly OnOff Wi-Fi Alfred Workflow"
date:   2014-02-04 22:22:22
categories: Alfred Workflow
download: https://raw.github.com/leoderbois/Wi-Fi-Enabler-Alfred-Workflow/blob/master/Wi-Fi%20Enabler.alfredworkflow
source: https://github.com/leoderbois/Wi-Fi-Enabler-Alfred-Workflow
---

**[Wi-Fi Enabler](http://inft.ly/QEv3ieV)** is a little bash script which permits.to enable/disable Wi-Fi quickly on Mac OS X. This can be useful when your have an Ethernet connection and you want to favorite it.

<pre>
#!/bin/bash
#Léo Derbois (@osxbricks): www.osxbricks.com

interface="en1" #your airport interface
ret=`networksetup -getair
portpower $interface`
if [[ "$ret" == *On* ]]
then
    networksetup -setairportpower $interface off
    echo "Wi-Fi is Off"
else
    networksetup -setairportpower $interface on
    echo "Wi-Fi is On"
fi
</pre>


To use the [Alfred](http://www.alfredapp.com) workflow just type `wifi` and it detects if it needs to enable or disable connection.