---
layout: post
title:  "Listen radio with Alfred"
date:   2014-07-02 22:59:35
categories: Alfred Workflow

---

**[Radio](http://inft.ly/4qFB2Sc)** permits to launch your  radios with Alfred on your favorite native app , like [iTunes](https://www.apple.com/itunes/), Quicktime or [VLC](http://www.videolan.org/index.fr.html). This workflow is for [Powerpack](http://www.alfredapp.com/powerpack/) [Alfred](http://www.alfredapp.com)'s users.

<img src="http://cl.ly/image/2E0P210R4204/radioWorkflow.gif" width="834" height="615" alt="Démonstatrion : radio avec alfred" class="aligncenter" />


## What i can do with Radio

- listen 35 radio stations by default. (most of them are french, 'cause i'm french ) 
- add custom radio with a name and m3u/mp3/aac flux with `radioadd {flux} {name}`
- remove a radio you don't like `radiorm {name}`
- reset default stations `radioreset`



> don't hesitate to comment or sent an  <a href="mailto:contact@osxbricks.com">email</a> to propose new radios !

## Technics

This workflow is mostly based on Python (this is my first project in this language !). To exchange easily with Alfred, i used [alp from phyllisstein](https://github.com/phyllisstein/alp), and to improve the speed I remove some useless *pi* files.