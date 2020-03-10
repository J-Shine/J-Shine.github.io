---
layout: post
title:  "Custom class android"
date:   2020-03-10
categories: ["android"]
author: "J-Shine"
---

# Make custom class to pass in to the ArrayAdapter constructor as a parameter.

-**public vs class**   
public class - we can access from anywhere. 
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
