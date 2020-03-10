---
layout: post
title:  "[Miwok] Custom ArrayAdapter"
date:   2020-03-10 16:30
categories: ["android"]
author: "J-Shine"
---

# Make custom ArrayAdapter using custom Word class and custom ArrayAdapter.

-**Create a custom ArrayAdapter**   

By default, the ArrayAdapter class expects that it'll be populating a single TextView.   
So we need to create a custom ArrayAdapter and override 'getView method'.

WordAdapter.java
```java
package com.example.android.miwok;

import android.app.Activity;
import android.support.annotation.NonNull;
import android.support.annotation.Nullable;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ArrayAdapter;
import android.widget.TextView;

import java.util.ArrayList;

public class WordAdapter extends ArrayAdapter<Word> {

    /**
     * Make constructor of 'WordAdapter' class.
     * @param context The context.(Where we are)
     */
    public WordAdapter(Activity context, ArrayList<Word> words){
        // Initialize WordAdapter using ArrayAdapter's constructor.
        // Because second parameter is used to populate single TextView, we don't use it here. We customize.
        // So, put the value 0.
        super(context, 0, words);
    }

    @NonNull
    @Override
    public View getView(int position, @Nullable View convertView, @NonNull ViewGroup parent) {

        // Check if the existing view is being reused, otherwise inflate the view
        View listItemView = convertView;
        if(listItemView == null) {
            listItemView = LayoutInflater.from(getContext()).inflate(
                    R.layout.list_item, parent, false);
        }

        // Get 'Word' object located at this position in the list.
        Word currentWord = getItem(position);

        // Find the TextView in the list_item.xml layout with the ID miwok_text_view
        TextView miwokTextView = (TextView) listItemView.findViewById(R.id.miwok_text_view);
        // Get the miwok word from the current Word object and
        // set this text on the miwok TextView
        miwokTextView.setText(currentWord.getMiwokTranslation());

        // Find the TextView in the list_item.xml layout with the ID default_text_view
        TextView defaultTextView = (TextView) listItemView.findViewById(R.id.default_text_view);
        // Get the default word from the current Word object and
        // set this text on the default TextView
        defaultTextView.setText(currentWord.getDefaultTranslation());

        // Return the whole list item layout (containing 2 TextViews)
        // so that it can be shown in the ListView
        return listItemView;
    }
}
```

Also change list_item.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<!--
    xmlns is short for xml namespace.
    in tools namespace, we can set texts.
    Go 'tools.android.com/tech-docs/tools-attributes' and find attributes in tools namespace.
    Or 'https://developer.android.com/studio/write/tool-attributes'
    'tools:text' is one of 'Design time attributes'  which are used when the layout is rendered in the tool,
    but have no impact on the runtime.
    -->

<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:padding="16dp">

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
```

Also need to change ArrayAdpater to -> WordAdpater

```java
package com.example.android.miwok;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.GridView;
import android.widget.LinearLayout;
import android.widget.ListView;
import android.widget.TextView;

import java.util.ArrayList;

public class NumbersActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_numbers);

        //Create ArrayList of numbers by using Word object.
        ArrayList<Word> words = new ArrayList<Word>();

        // Add words by using 'add' function.

        words.add(new Word("one", "lutti"));
        words.add(new Word("two", "otiiko"));
        words.add(new Word("three", "tolookosu"));
        words.add(new Word("four", "oyyisa"));
        words.add(new Word("five", "massokka"));
        words.add(new Word("six", "temmokka"));
        words.add(new Word("seven", "kenekaku"));
        words.add(new Word("eight", "kawinta"));
        words.add(new Word("nine", "wo'e"));
        words.add(new Word("ten", "na'aacha"));

        // Create a WordAdapter (custom adapter), using constructor.
        WordAdapter itemsAdapter =
                new WordAdapter(this, words);

        // Find the ListView object in the view hierarchy of the Activity.
        // There should be a ListView with the view ID called list, which is declared in the
        // activity_numbers.xml layout file.
        ListView listView = findViewById(R.id.list);

        // Make the ListView use the ArrayAdapter we created above, so that the
        // ListView will display list items for each word in the list of words.
        // Do this by calling the setAdapter method on the ListView object and pass in
        // 1 argument, which is the ArrayAdapter with the variable name itemsAdapter.
        listView.setAdapter(itemsAdapter);
        // setAdapter needs ListAdapter as an input parameter.
        // ListAdapter is an Interface, BaseAdapter is an Abstract class and lastly ArrayAdapter is a Concrete class.
        // ListAdapter -> BaseAdapter -> ArrayAdapter.
        // ArrayAdapter is also used with GridList and Spinner
    }
}
```
