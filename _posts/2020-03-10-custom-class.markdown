---
layout: post
title:  "Custom class android"
date:   2020-03-10
categories: ["android"]
author: "J-Shine"
---

# Make custom class to pass in to the ArrayAdapter constructor as a parameter.

-**public class vs private class**   
public class - we can access from anywhere. 
<pre><code>


  textView.setText("Hello")
</code></pre>
private class - we can only access when we are in that class. 
<pre><code>
public class TextView {
  public setText(){
    ~~~~
    }
  setText("Hello")
  }
</code></pre>
