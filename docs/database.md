---
layout: default
title: Database
nav_order: 5
---

# Database
- - - -
### Overview
This section is a walkthrough of how to create your own JSON database file and later on use the data in other parts of the web application. This document will store the data as JSON rather than tables and we use it for transmitting data in web applications.

Json or javascript object notation is human - readable format for representing the data. This form is based on key-value data and arrays.
- - - -
### Let's start!
Create a  new file in your main folder, in this instruction we will call it fakeDb. This file will get manipulated with arrays - objects and functions that help us access these objects and get the desired result.

Copy the code underneath and paste it in your db file to create an array of objects consisting of  the notes and their attributes.

```

let notes = [
    {
        id: 1,
        title: "My First Note",
        timestamp: Date.now(),
        contents: 
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam fermentum pharetra dapibus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Ut iaculis erat at euismod porta. Vivamus et nibh tincidunt, egestas arcu a, semper arcu. Quisque ut felis ex. Vivamus nec convallis ligula. Vestibulum sit amet tristique augue."
    },
    {
        id: 2,
        title: "My Second Note",
        timestamp: Date.now(),
        contents:
        "Fusce id nibh convallis, fringilla risus ac, auctor dui. In tristique tellus ligula, sit amet ultricies velit ultrices nec. Suspendisse sit amet sapien quis purus congue vulputate in a velit. Praesent hendrerit ex in mauris rutrum, in semper nibh tincidunt. Aliquam dui ante, pulvinar non venenatis eu, venenatis eu orci. Nam dapibus viverra consectetur. Sed a tincidunt turpis. Aenean nec semper neque. Suspendisse potenti. Fusce convallis finibus justo, ac pharetra mauris porta quis. Phasellus ac blandit turpis, eget lacinia tortor. Donec eleifend tempus condimentum. Interdum et malesuada fames ac ante ipsum primis in faucibus. Pellentesque rutrum et tellus quis egestas. Etiam metus dui, tincidunt ac blandit ut, fermentum quis mauris."
    },
];
```


Perfect ! So now you have 2 notes in your database with unique ids. Now add yhois line to your database  after your array 

```
let currentId = 3; `
```
by adding the code below can store the value of the next note id and update every time you create a new object.
 For the next step we will add a few functions to return our desired result from the notes array of objects 


1. Getting the note if the searched term is either in title or body of the note 
 ```
 function getNotes(searchTerm) {
    if (!searchTerm) {
        return notes;
    }
    return notes.filter(note => note.title.includes(searchTerm) || note.contents.includes(searchTerm))
}
```


2.  Getting the note by passing the id as an argument. 

```
function getNote(id) {
    return notes.find(note => note.id === id)
}
```

3.  Adding a note by only passing the text and auto generate rest of requirements

```
function addNote(note) {
    notes.push({
        ...note,
        id: currentId,
        timestamp: Date.now()
    })
    currentId++
}
```

4.  Delete Note by passing the id number

```
function deleteNote(id) {
    notes = notes.filter(note => note.id !== id);
}
```

That's it ! Now you have a Json database with your notes and its basic functions. Later on you can add more functions to this section to extend your flexibility in accessing  the data  but for now let's move on to server.js


 :warning: **Do not  forget to export your database or only the required  modules so you would have access to them from the router.** 
``` 
export blah blah
```
