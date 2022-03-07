---
layout: default
title: Router
nav_order: 6
---

# Router
- - - -



### Overview 
The server.js file manages the application's endpoints and responds to the client requests through the routes. These routes get executed when the route is matched.

### Setup
Make sure you have all of these  requirements for creating before starting to code in server.js
```js
const express = require("express");
const router = express.Router();
let db = require("../fake-db");
Let bodyParser = require(“body-parser”)
```

Here we added the express framework to create a router object, the JSON database that we made earlier and a body parser to handle the post request’s data. Remember to export your router variable as well. Following steps will guide you in adding all the essential routers for a basic app.
 
- - - -

### Steps
Add these codes after your app.get(‘/’). at the end of these steps you will be able to search, read, create and delete the notes.


1. The route will get your search term and use it to get the notes using the get **notes(searchTerm**) function in the database afterward it renders the **notes.ejs** and passes the data to it.

```js
app.get("/notes", (req, res) => {
    const searchTerm = req.query.searchTerm;
    const notes = database.getNotes(searchTerm);
    res.render("notes.ejs", {
        notes,
    });
})

```


2. The code below will get the note’s id from the URI parameter, send it to the **getNote()** function that we just made in the database. if there was no result passes us a 404 error and if there was it will render the **singleNote.ejs**. 


```js
app.get("/notes/:id", (req, res) => {
    const id = +req.params.id
    const note = database.getNote(id)
    if (!note) {
        res.status(404).render("note404.ejs")
        return
    }
      res.render("singleNote.ejs" , {
        note,
    });
})
```

💡 _You can define multiple route parameters in a URI. and store themm using `req.params.<parameter_name>`._  
💡 _In order to pass the variables from **server.js** to **.ejs** file you have to put the variable inside the callback function. (Step2)_



3. This route is pretty simple and it only render the **createNote.ejs** which contains the `post` form.


```js
app.get("/createNote", (req, res) => {
    res.render("createNote.ejs")
})
```

4.  Post request from the **createNote.ejs** form will execute this route which will retrieve the data from the form body and send them to the addNote in the database to create a new note.

```js
app.post("/notes", (req, res) => {
    const data = req.body
    database.addNote(data)

    res.redirect("/notes")
})
```  
💡 _The `req.body` object let us to access the data from client as part of the post request._


5. This route, the same as the other post route gets the notes id from the URI parameters. The difference is this time it passes the note to the delete function in DB and then redirects to the homepage.

```js
app.post("/notes/:id/delete", (req, res) =>{
    const id = +req.params.id
    database.deleteNote(id)

    res.redirect("/notes")
})

```
