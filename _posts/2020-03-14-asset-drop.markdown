---
layout: post
title:  "[Miwok] Put images into Miwok app."
date:   2020-03-14 19:00
categories: ["android"]
author: "J-Shine"
---

# Put different resolution versions of same images.    


To put images into our app, we need different resolution version of same each image.   
That's because people have different devices and devices have different resolution.   
Dpi is dots for inch.   
mdpi(~160dpi)(1dp=1px) -> medium density device   
hdpi(~240dpi)(1dp=1.5px) -> high density device   
xhdpi(~320dpi)(1dp=2px) -> extra high density device   
xxhdpi(~480dpi)(1dp=3px) -> extra-extra high density device   
xxxhdpi(~640dpi)(1dp=4px) -> extra-extra-extra high density device   

We can find dpi of some popular devices from [here](https://material.io/resources/devices/).     

In AndroidStudio, we should make folders for each dpi.( ex) drawble-hdpi)    
And put same images of different resolution.

![image01](https://user-images.githubusercontent.com/61873510/76682281-0c625d80-663e-11ea-94e0-b96ca3844e4f.png)

