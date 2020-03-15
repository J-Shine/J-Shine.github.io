---
layout: post
title:  "[Miwok] How to get integer color from resource ID?"
date:   2020-03-15 16:00
categories: ["android"]
author: "J-Shine"
---

#Set different background colors for each activity in Miwok.   

In order to get integer color from resource id,    
we need to use getColor method which is in the ContextCompat class.   
```java
int textcolor = ContextCompat.getColor(context, R.color.textcolor);
```

ArrayAdapter.java

```java
public class WordAdapter extends ArrayAdapter<Word> {

    /**
     * Create background color variable.
     */
    private int mBackgroundColor;
    // Create getter.
    public int getBackgroundColor(){
        return mBackgroundColor;
    }
    /**
     * Make constructor of 'WordAdapter' class.
     * @param context The context.(Where we are)
     */
    public WordAdapter(Activity context, ArrayList<Word> words, int backgroundColor){
        // Initialize WordAdapter using ArrayAdapter's constructor.
        // Because second parameter is used to populate single TextView, we don't use it here. We customize.
        // So, put the value 0.
        super(context, 0, words);
        mBackgroundColor = backgroundColor;
    }
    /*
     * @param convertView is an existing view we can reuse.(recycle)
     */
    @NonNull
    @Override
    public View getView(int position, @Nullable View convertView, @NonNull ViewGroup parent) {
        
        View listItemView = convertView;
        ...
        View textContainer = listItemView.findViewById(R.id.text_container);
        int color = ContextCompat.getColor(getContext(), getBackgroundColor());
        textContainer.setBackgroundColor(color);

        return listItemView;
    }
}

```

