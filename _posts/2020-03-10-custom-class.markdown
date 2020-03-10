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
<pre><code>
/**
 * Displays text to the user.
 */
public class TextView extends View {
 
    // String value
    private String mText;
 
    // Text color of the text
    private int mTextColor;
    
    // Context of the app
    private Context mContext;
 
    /**
     * Constructs a new TextView with initial values for text and text color.
     */
    public TextView(Context context) {
      mText = "";
      mTextColor = 0;
      mContext = context;
    }
 
    /**
     * Sets the string value in the TextView.
     *
     * @param text is the updated string to be displayed.
     */
    public void setText(String text) {
        mText = text;
    }
 
    /**
     * Sets the text color of the TextView.
     *
     * @param color of text to be displayed.
     */
    public void setTextColor(int color) {
        mTextColor = color;
    }
 
    /**
     * Gets the string value in the TextView.
     *
     * @return current text in the TextView.
     */
    public String getText() {
        return mText;
    }
 
    /**
     * Gets the text color of the TextView.
     *
     * @return current text color.
     */
    public int getTextColor() {
        return mTextColor;
    }
}
//source - udacity
</code></pre>
