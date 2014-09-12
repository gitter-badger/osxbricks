---
layout: post
title:  "Documentation in Xcode"
date:   2014-06-12 22:59:35
categories: development

---

All developpers on Xcode know the `⎇+clic` shortcut which show quiclky informations about a method or a class provided by Apple's Frameworks. If you don't know it, try it now !

<a href="http://farm8.staticflickr.com/7313/12364419514_d32c9cfd3d.jpg" rel="lightbox">
![Alt+clic sur runModal d'un NSSavePanel](http://farm8.staticflickr.com/7313/12364419514_d32c9cfd3d.jpg)
</a>

Since Xcode 5, Apple permits to use this feature to document your own code. That's can be useful to show quickly a difficult method that's your co-worker did.

## Use the good syntax of documentation

each language or IDE have it own documentation rules. They all look alike, but they all have there particularity. The Apple tool is not an exception to the rule. [Doxygen](www.doxygen.org) centralize the question, because it works for all platforms. But some developers, like me, prefer to use the built in method for the IDE or languages they use.

#### Exemple

- your documentation

<a href="http://farm3.staticflickr.com/2853/12443847493_fac0325c51.jpg" rel="lightbox">
![Exemple de docuement](http://farm3.staticflickr.com/2853/12443847493_fac0325c51.jpg)
</a>

- the result

<a href="http://farm3.staticflickr.com/2819/12443709685_17d7e55a35.jpg" rel="lightbox">
![resultat de la documenation précédente](http://farm3.staticflickr.com/2819/12443709685_17d7e55a35.jpg)
</a>    

Rather to explain all the standards, i maid a [little project](https://github.com/leolelego/OSX-Bricks-Codes/tree/master/XcodeDocumentation) with somes exemples (which will evolve). But be aware that there is a plugin for Xcode for chewing your labour. 

## The plugin or Xcode for chewing your labour

I search if somebody did something to improve my user exeprience and i found  **VVDocument**. This plugin for Xcode generate a template documentation in  function of your *Method (parameters)* or *Class*. You just type `///` and it found the good format for your code using `<#variable#>`. Next, just type `tab` to fill it. I use it since 1 year and i can't live without !

<a href="https://raw.github.com/onevcat/VVDocumenter-Xcode/master/ScreenShot.gif" rel="lightbox">
![GIF montrant le fonctionnement de VVDocumenter](https://raw.github.com/onevcat/VVDocumenter-Xcode/master/ScreenShot.gif)
</a>    


To use this splendid plugin [download it](https://github.com/onevcat/VVDocumenter-Xcode/archive/master.zip) and i recommend to visit the developer [github page](https://github.com/onevcat/VVDocumenter-Xcode).

> Reminder : that's not an obligation to run Xcode, just enter this line in terminal : `xcodebuild -project path/to/VVDocumenter-Xcode.xcodeproj --alltarguets`
