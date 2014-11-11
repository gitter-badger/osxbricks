---

layout: post
title:  Create simple daemon on OS X 
date:   2014-11-11 22:22:22
categories: server

---

> If you make a service on your OS X Server, like a python script, you probably need to start it at every reboot. OS X integrate, like every UNIX system, a simple daemons system named **LaunchDaemons**.

## Create a daemon file

For each daemons, informations and options are located in one [*Property List file*](http://en.wikipedia.org/wiki/Property_list) per daemon which can be created and edited simply with [Xcode](https://developer.apple.com/xcode/).  

![Plist Exemple](/assets/posts/create-daemon-plist.png)

#### There are 3 different items in standard daemon Plist : 

- a `String` for the **bundle identifier / label**
- an `Array` for the command line  launching the `script or the program`, alias **ProgramArguments** and command line options
- some `Strings` for daemons system options.

A lot of different options can be used with LaunchDamons, but I will give you some of the most interesting : 

Name | type | value | description
-|-|-
**KeepAlive** | Boolean | true/false | re-run the daemon if the program shut down / crash 
**StartInterval** | String | time in seconds | run the service every X seconds 
**RunAtLoad** | Boolean |  true/false |run when computer boot (but not keep alive if crash) - if you don't use keep alive, use this, else daemon never run
**StandardOutPath**  | String | a path | print logs into a specific file
**Debug** | Boolean|  true/false |print debug logs in logs
**Disabled** | Boolean |  true/false |tell if service is enable or not

## Daemon action

All custom LaunchDaemons are located in `/Library/LaunchDaemons/` (not system's daemon), to enable your daemon move your **Property List** in this folder.

Next you need to tell to [`launchd`](http://en.wikipedia.org/wiki/Launchd) (the daemon manager) to add a new task to run . First make it as root file : 

`sudo chown root /Library/LaunchDaemons/com.me.myservice.plist `

And tell to launchd to load it : 

`sudo launchctl load -w /Library/LaunchDaemons/com.me.myservice.plist` (`launchctl` is the launchd interface and  -w permit to remove the `Disable` in Plist )

> note : it exists a *per-user* version of  LaunchDaemons named LaunchAgents which is in `/Library/LaunchAgents/` for all user and `~/Library/LaunchAgents/` per user. This can be useful to only run script for some user.

*Go further* : 

- [Apple Documentation](https://developer.apple.com/library/mac/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/CreatingLaunchdJobs.html#//apple_ref/doc/uid/10000172i-SW7-BCIEDDBJ)
- [Wikipedia](http://en.wikipedia.org/wiki/Launchd) - launchd
- [different use of LaunchDaemon](http://paul.annesley.cc/2012/09/mac-os-x-launchd-is-cool/)

 


