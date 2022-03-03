---
layout: default
title: Router
nav_order: 5
---

# Router
- - - -



### Overview 
The server.js file manages the application's endpoints and responds to the client requests through the routes. These routes get executed when the route is matched.

### Setup
Make sure you have all of these  requirements for creating before starting to code in server.js 
```
const express = require("express");
const router = express.Router();
let db = require("../fake-db");
Let bodyParser = require(“body-parser”)
```

Here we added the express framework to  create a router object , the JSON database that we made earlier and a body parser to handle the post request’s data. Remember to export your router variable as well.



### Clarification:

* **Parameters**: You can define multiple route parameters in a URL. We have the url of `/Notes/:Id `. Any number that goes in url instead of the `:id` parameter can get stored:
*  ⚠️

* **Integrate with ejs file:** If we we intend to use the variables of the router in our ejs file :

### Steps
Add these codes after your app.get(‘/’). at the end of these steps you will be able to search, read, create and delete the notes.


1. The route will get your search term  and usig it to get the notes using gteNotes(searchTerm) function in database afterward it renders the notes.ejs and passes the data to it.
app.get("/notes", (req, res) => {

```
app.get("/notes", (req, res) => {
    const searchTerm = req.query.searchTerm;
    const notes = database.getNotes(searchTerm);
    res.render("notes.ejs", {
        notes,
    });
})

```


2. The code below will get the note’s id form the url parameter, send it to the getNote() function that we just made in the database. if there was no result passes us an 404 error and if there was it will render the singleNote.ejs 
 o  app.get("/notes/:id", (req, res)


```
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




3. This route is pretty simple and it only render the createNote e.ejs which contains the ‘post’ form 
app.get("/createNote", (req, res) 




```
app.get("/createNote", (req, res) => {
    res.render("createNote.ejs")
})
```

4. Post request from the createNote form will execute this route which will retrieve the data from the form body and send them to the addNote in the database to create a new note.
 app.post("/notes", (req, res)

```
app.post("/notes", (req, res) => {
    const data = req.body
    database.addNote(data)

    res.redirect("/notes")
})
```


5. This route, the same as the other post toute gets the notes id from the uri parameters. The difference is this time it passes the note to the delete function in db and then redirects to the homepage.
.app.post("/notes/:id/delete", (req, res) => 

```
app.post("/notes/:id/delete", (req, res) =>{
    const id = +req.params.id
    database.deleteNote(id)

    res.redirect("/notes")
})

```
