---
layout: default
title: EJS
nav_order: 7
---
# EJS 
TABLE OF CONTENTS

* [What is EJS?](#what-is-ejs)
* [Display Notes](#display-notes)
* [Error Handling](#404-error-page)
* [Single Note](#single-note)
* [Create Note](#create-note)
* [Final Steps](#final-step)

- - - -
## What is EJS?
EJS stands for embedded Javascript. Generally, HTML and CSS is sufficient for building websites that are static. But, when it comes to dynamic websites, EJS is super useful to use. 

The syntax used to embed javascript into our html is done with these tags: 
```
<%= Date() %>
````
:bulb: *This line of code displays the current date*

- - - -

## Display Notes

By using the functions we created in our database, we'll be making a page that displays a preview of all our notes. 

1. Create a new file named notes.ejs in the views folder
2. Add the following content to your notes.ejs file:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="/style.css">
    <title>All Notes</title>
</head>
<body>
   
    <h1>Notes</h1>

    <form action="/notes" method="GET">
        <label for="searchInput">Search:</label>
        <input type="text" name="searchTerm" id="searchInput">
        <button>Search</button>
    </form>
    
    <ul>
    <% notes.forEach(note => { %>
        <li>
            <h2><%= note.title %></h2>
            <p><%= note.contents.substring(0, 200) %>...</p>
            <p><%= new Date(note.timestamp) %></p>
            <a href="/notes/<%= note.id %>">View More</a>
        </li>
    <% }) %>
    </ul>
    <a href="/createNote">Create New Note</a>

</body>
</html>
```

- - - -

## 404 Error Page

We want to be able to handle our errors, so let's create a page that displays a 404 error. 

1. Create a new file named note404.ejs in the views folder
2. Add the following content to your note404.ejs file:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="/style.css">
    <title>Note Not Found</title>
</head>
<body>

    <h1>Note not found</h1>
    
</body>
</html>
```

:bulb: *This is a good practice in web development.*

- - - -

## Single Note

Let's create a page that displays all the content of a single note when we click on the note. 

1. Create a new file named singleNote.ejs in the views folder
2. Add the following content to your singleNote.ejs file:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="/style.css">
    <title>Notes</title>
</head>
<body>
   
    <h1><%= note.title %></h1>
    
    <p><%= note.contents %>...</p>
    <p><%= new Date(note.timestamp) %></p>

    <a href="/notes">Back</a>

    <form action="/notes/<%= note.id %>/delete" method="post">
        <button type="submit">Delete Note</button>
    </form>
    
    
</body>
</html>
```

- - - -

## Create Note

Our final step will be to make our create note form. This step is entirely done with just html.  

1. Create a new file named createNote.ejs in the views folder
2. Add the following content to your createNote.ejs file:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="/style.css">
    <title>Create Note</title>
</head>
<body>
   
    <h1>Hello World!</h1>
    
    <form action="/notes" method="POST">
        <label for="titleInput">Title</label>
        <input type="text" id="titleInput" name="title">

        <label for="contentsInput">Contents</label>
        <textarea name="contents" id="contentsInput" cols="30" rows="10"></textarea>

        <button type="submit">Create Note</button>
    </form>
    

</body>
</html>
```

- - - -


## CSS

To make things look presentable, we'll add some basic css to our web page. 

1. Create a new folder named public in the root folder
2. Create a new file named style.css inside the public folder
3. Add the following content to your style.css file: 
```
body {
    font-family: Arial, Helvetica, sans-serif;
    max-width: 800px;
    margin: auto;
}

img {
    width: 100%;
}

ul {
    list-style: none;
    padding: 0;
}

form {
    display:flex;
    flex-direction: column;
}
```

The final folder structure should look like this: 
 ![image of web browser displaying index.ejs](https://github.com/iantelli/Yasmina-Ian/blob/gh-pages/assets/images/ejsDirectory.png?raw=true)