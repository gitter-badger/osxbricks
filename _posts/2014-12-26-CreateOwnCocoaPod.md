---

layout: post
title:  Create your own CocoaPod 
date:   2014-12-26 22:22:22
categories: Development

---

## Create a CocoaPod

- Go to development folder
- Create a Pod folder with this command : `pod lib create [PodName]`

This will create : 

 -  `[PodName].podspec` which the file specified your Pod
 - `Pod` Folder which contains a `Classes` folder for your sources and `Assets` folder for assets. You can use it or remove it to add your own source folder.
 - `Example` Folder to test your Pod source file
 - `LICENSE` file (do not remove)
 - `README.md` 

All information about your Pod need to be filled in the `[PodName].podspec`. This a simple documented example of `podspec` file.

{% highlight sh %}

	Pod::Spec.new do |s|
 	 s.name             = "PodTest" # the pod name
 	 s.version          = "0.0.1" # the pod version
	 s.summary          = "Pod making for testing." 
 
	 s.homepage         = "http://git.url/YOU/PodTest"  # where the pod homepage is located (a git)
	 s.license          = 'Property Of Me' 
  	s.author           = { "ME" => "contact@me.com" } 
  	s.source           = { :git =>"http://git.url/YOU/PodTest.git", :tag => s.version.to_s } # URL of sources (a git) and tag needed for version
 
  	#Plateform 
 	 s.ios.deployment_target = '7.0' #iOS Min requierment - remove for iOS only
 	 s.osx.deployment_target = '10.8' #Mac OS X Min requierment - remove for iOS only
 	s.requires_arc = true # ARC or Not ARC that's the question
 
 	s.source_files = 'PodTest' # Folder of sources file [default -> Pod/Classes]
 
  	# s.public_header_files = 'Pod/Classes/**/*.h' # Header File when builded
	# s.frameworks = 'UIKit', 'MapKit'   #Need Framework for the pod
  	# s.dependency 'AFNetworking', '~> 2.3' # Dependancies with other Pods
	end
{% endhighlight %}

Test your spec with the command : ` pod lib lint`

> You can first test locally your Pod. 

- Import or write your Pod sources (in your `s.source_files`)
- Go to the `Exemple`with the Terminal and run a `pod install` command to update your project
- Open the `[PodName].xcworkspace` in the `Example` folder 
- Use some of your Pod features and build

> When you have finish create a release on your git.

- Push all your change on a Repo (private or not) : `git add -A && git commit -m "Release 0.0.1."`
- For the CocoaPod Specs create a tag :  `git tag '0.0.1'` and  `git push --tags` 

> Your Pod is ready. 

## Add Your Pod to a CocoaPod Specs Git

### Add to the Standard CocoaPod Specs

> If you want to make your open source for every developer you can add it to the standard [CocoaPod Specs Git](https://github.com/CocoaPods/Specs).

To submit your pod, just go to the pod git root and use : `pod trunk push [PodName].podspec` . Make sure to validating it before ! (` pod lib lint`)

### Add to a personnal Specs Git 

> First of all be sure to have a personal Specs Gits (private or public). Follow these insctructions if you don't have one : [instruction](http://guides.cocoapods.org/making/private-cocoapods.html).

- Pod need to memorise the URL where your PodSpecs is : `pod repo add [REPO_NAME] [SOURCE_URL]`. 
- Next push the `podspec` file  or your pod with : `pod repo push  [REPO_NAME] [PodName].podspec`.

Normally your pod is ready on the server !

## Use your Pod (Oh yeah !)

> If you push your Pod on a CocoaPod Specs, use it like other open source Pod.

With a private Pod Specs Git, be sure your SSH key is authorized on the server. And create your `Podfile`as usually. Add the source URL of your private Pod Specs and add pods you want ! That's it !

{% highlight sh %}
	# platform :ios, '7.0' 
	source 'https://github.com/CocoaPods/Specs.git'
	source 'http://git.url/You/PodSpecs.git'

	target 'MyPodTestProject' do
		 pod 'PodTest' #, '~> 0.0.1' # version
	end
{% endhighlight %}

> Actually Cocoapod had some issues with Github Entreprise account, so you can't push your pod privates specs and use your private pods.  To fix it you can downgrade to CocoaPods version 0.33 (uninstall cocoapod and re install with option `-v "0.33.0"`)

---

> Sources CocoaPod Doc :
>
> - [Making a Pod](http://guides.cocoapods.org/making/making-a-cocoapod.html)
> - [Making a private Pod Specs Git](http://guides.cocoapods.org/making/private-cocoapods.html)
> - [CocoaPod Docs](http://guides.cocoapods.org)
