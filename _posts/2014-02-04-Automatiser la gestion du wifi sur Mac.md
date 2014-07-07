---
layout: post
title:  "Automatiser la gestion du wifi sur Mac"
date:   2014-02-04 22:22:22
categories: OSXBricks
---

En soi ce script n'est pas des plus utile, mais si vous utilisez un lanceur comme [Alfred](http://www.alfredapp.com) et que vous souhaitez favoriser l'Ethernet quand vous êtes chez vous, ce petit script peut vous être pratique. Il va vous aidez pour activer ou désactiver rapidement le Wifi sur Mac.

   
    #!/bin/bash
    #Léo Derbois (@osxbricks): www.osxbricks.com
    #This code permit to swith On/Off Wifi on OSX

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
Et en bonus le petit workflow pour Alfred que je me suis fais [ici](http://inft.ly/QEv3ieV)