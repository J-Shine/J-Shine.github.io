---
layout: post
title:  "[Miwok] Put images into Miwok app."
date:   2020-03-14 19:00
categories: ["android"]
author: "J-Shine"
---

# How to put images for the word list in the Miwok app.

-**Put different resolution versions of same images into AndroidStudio.**    


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

![image01](https://user-images.githubusercontent.com/61873510/76682337-ad511880-663e-11ea-9a1c-207aea438a3a.png)     


-**Modify list_item.xml layout**     

Wrap the LinearLayout with another horizontal LinearLayout.       
And put ImageView in there.    


list_item.xml
```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:padding="16dp">

    <ImageView
        android:id="@+id/image"
        android:src="@mipmap/ic_launcher"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:paddingLeft="16dp">

        <TextView
            android:id="@+id/miwok_text_view"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            tools:text="lutti"/>

        <TextView
            android:id="@+id/default_text_view"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            tools:text="one"/>

    </LinearLayout>
    
</LinearLayout>
```

-**Modify Word.java**   

Create a variable for an image.    
Set as 'int' because it will contain image resource id.    
And create constrcutor and getter.    

```java
public class Word {

    ...   

    // Image resouce id for the word.
    private int mImageResourceId;

    // 2-input Word class constructor.
    public Word(String defaultTranslation, String miwokTranslation) {
        mDefaultTranslation = defaultTranslation;
        mMiwokTranslation = miwokTranslation;
    }
    
    // 3-input Word class constructor.
    public Word(int imageResourceId, String defaultTranslation, String miwokTranslation) {
        mImageResourceId = imageResourceId;
        mDefaultTranslation = defaultTranslation;
        mMiwokTranslation = miwokTranslation;
    }

    // A method that gets resource image id of the word
    public int getmImageResourceId() {
        return mImageResourceId;
    }
    
    ...   
    
}