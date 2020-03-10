---
layout: post
title:  "Custom class android"
date:   2020-03-10
categories: ["android"]
author: "J-Shine"
---

# Make custom class to pass in to the ArrayAdapter constructor as a parameter.

-**public vs private**   
public - we can access from anywhere. 
<pre><code>
public class MainActivity {
  ~~~
  textView.setText("Hello")
  }
</code></pre>
private - we can only access when we are in that class. 
<pre><code>
public class TextView {
  private setText(){
    ~~~~
    }
  setText("Hello")
  }
</code></pre>

We need to set variables private and make get and set functions to control those variables.    
Set variable private in order to protect from unexpected value and behavior.
<pre><code>
package com.example.android.miwok;

// It contains a Miwok translation and a default translation for that word.
public class Word {

    // Default translation for the word.
    private String mDefaultTranslation;
    // 'm' is short for 'private member of class'

    // Miwok translation for the word.
    private String mMiwokTranslation;

    // Word class constructor.
    public Word(String defaultTranslation, String miwokTranslation) {
        mDefaultTranslation = defaultTranslation;
        mMiwokTranslation = miwokTranslation;
    }

    // A method that gets default translation of the word
    public String getDefaultTranslation() {
        return mDefaultTranslation;
    }

    // A method that gets miwok translation of the word
    public String getMiwokTranslation() {
        return mMiwokTranslation;
    }
}

//source - udacity
</code></pre>
