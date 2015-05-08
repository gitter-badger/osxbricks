---
layout: post
title: Add properties in Objective C Category using ARC
date: 2015-08-06T22:22:22.000Z
categories: Development
keywords:
  - Objective C
  - Category
  - property
  - xcode
---

This afternoon I discovered that the `NSView`property doesn't exist in `UIKit/UIView` so I decided to make a  **Category** of `UIView` to bearing this missing. But I discovered that is not easy to add a new _property_. So that's how to do it.

The the first step is to create your property in your header category :

{% highlight objc %}
//UIView+identifier.h
#import <UIKit/UIKit.h>
@interface UIView (identifier)
/**
* A simple property to identify a view.
*/
@property NSString *identifier; //(nonatomic, strong) by defaults
@end

{% endhighlight %}

Easy, isn't it ?  but if you only do this, you will get a message like `message`. So this is how to declare your new property :

{% highlight objc %}
// UIView+identifier.m
#import "UIView+identifier.h"
#include <objc/runtime.h>
@implementation UIView (identifier)
@dynamic associatedObject;
static char kKeyIdentifier; // permits to save and retrieve associated objetc.

// Common setter
- (void)setIdentifier:(NSString *)identifier {
    // tell to the main object (UIView) to save the object `identifier` with the kKeyIdentifier. OBJC_ASSOCIATION_RETAIN_NONATOMIC means (nonatomic, strong)
    objc_setAssociatedObject(self, &kKeyIdentifier, identifier, OBJC_ASSOCIATION_RETAIN_NONATOMIC);
}

// Common getter
- (NSString *)identifier {
    //return the associated object with the kKeyIdentifier, here the `identifier`
    return (id)objc_getAssociatedObject(self, &kKeyIdentifier);
}
@end
{% endhighlight %}


> If you want to use it I made a little Cocoapod for you : `pod "UIView+identifier"`

Go further :

- [Apple Documentation - Customizing Existing Classes](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/CustomizingExistingClasses/CustomizingExistingClasses.html)
- [NSHipster - Associated Objects](http://nshipster.com/associated-objects/)
