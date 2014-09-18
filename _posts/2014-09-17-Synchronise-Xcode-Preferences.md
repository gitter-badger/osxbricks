---
layout: post
title:  "Synchronize Xcode preferences"
description : How to synchronize your Xcode preferences beetwen Mac
keywords: synchornization, iCloudDrive, Dropbox
date:   2014-09-17 22:22:22
categories: tricks
---



> This unit starts a suite of articles about  apps synchronisation for developers. How many times did you import an awesome Xcode plug-ins, themes or snippets on a Mac and when you go on another Mac, you don’t remember its name. Or, if you improve a snippet on a Mac, you need to redo the improvement on all other Macs. With this new section I’ll investigate **how to synchronise developer tools between Macs**. And i’m starting today with **Xcode**.

## Synchronise, great, but what ?

i've found these things to synchronize with **Xcode** : 

- **Code snippets** - the most *useful* because I update them regularly - in `~/Library/Developer/Xcode/UserData/CodeSnippets`
- **Plug-ins** - *useful too* - in `~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins`
- **Font and color themes** in `~/Library/Developer/Xcode/UserData/FontAndColorThemes`
- **Key bindings** in `~/Library/Developer/Xcode/UserData/KeyBindings`
- [Uncrustify](https://github.com/benoitsan/BBUncrustifyPlugin-Xcode) file in `~/.uncrustify` (I'll write an article about Uncrustify soon) 

> This list can evoluate (with your help !)


## How to synchronize 

- Firstly, select your favorite synchronisation service (e.g. [Dropbox](http://www.dropbox.com), [Google Drive](http://drive.google.com), iCloud Drive soon in [Yosemite](https://www.apple.com/osx/preview/)) and create a general synchronisation folder for Xcode. 

> *advice : create a synchronisation folder and a sub-folder for all your apps `~/pathToMySyncFolder/SyncApps/Xcode`*.

- Secondly, move folders that you want to synchronize in the app synchronization folder (CodeSnippets, FontAndColorThemes...).
- Thirdly, create symbolic links on the original path which refers to the folder in your app synchronisation folder (`ln -s `)
- to finish, after a complete synchronisation, create symbolic links on other Macs.

## To resume in code

{% highlight sh %}

#!/bin/bash
echo "------ Create Synchronisation Architecture ------"
# General script, you can use it for other app
syncFolder=~/PathToMySyncFolder/AppSync/Xcode #Synchronisation folder
pathToRealFolder=~/Library/Developer/Xcode/UserData #Folder where are datas
fileUser=( "KeyBindings" "CodeSnippets" "FontAndColorThemes" ) #folder to synchronize

# create Sync Folder if necessary
if [ ! -f $syncFolder ]
then
	echo creating sync folder
	mkdir -p $syncFolder
else
	echo sync folder already exist
fi

# move and create symbolic
for folder in "${fileUser[@]}"; do
	echo move $pathToXcodeFolder/$folder to $syncFolder/$folder
	mv $pathToXcodeFolder/$folder $syncFolder/$folder
	echo create symbolic link 
	ln -s $syncFolder/$folder $pathToXcodeFolder/$folder 
done

# For Plug-ins
# mv ~/Library/Application\ Support/Developer/hared/Xcode/Plug-ins $syncFolder/Plug-ins
# ln -s $syncFolder/Plug-ins ~/Library/Application/ Support/Developer/Shared/Xcode/Plug-ins

{% endhighlight %}

	
