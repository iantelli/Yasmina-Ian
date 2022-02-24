---
layout: default
title: Setup
nav_order: 8
---

# Setup
- - - -

## Working directory/ Folder structure 

To start off, we’ll need to create somewhere to store our project files. Create a new empty folder anywhere on your PC.

> *Note: Ensure that your folder name does not have any spaces, this could cause some problems in the following step.*

Next, we’ll open up Visual studio code and set the working directory to the folder we have just created.

> **File -> Open Folder -> (Choose the folder we made)**

- - - -

## Package.json

We will need to open a new terminal for the following step. Once the terminal is open, running the following command line will initialize a new Node project: 
```
npm init -y
```

This command will create the package.json file needed for our project. You should now see the json file appear on the left. 

![package.json file](./assets/images/package.png)

- - - -

## Other Dependencies

Next, we’ll need to install express and ejs. This step is very simple and is done by running the following command in your terminal:
```
npm install -S express ejs
```

- - - -

## Index.ejs

After the installation, there a couple steps that are necessary to create a working page
1. Create a folder named **views** in the root folder
2. Create a file named **index.ejs** in the *views* folder we just created
3. Add the following contents into your *index.ejs* file:
```
<h1>Hello World!</h1>
```

![Working directory after installing dependencies and creating views folder and index.ejs.](./assets/images/directory.png)
*Working directory after installing dependencies and creating views folder and index.ejs.*

- - - -

## Server.ejs

Creating a basic local server that returns html to the user is very simple. Now, we will create a file called server.js in the root folder. Add the following content to your server.js file: 

```
const express = require('express')
const app = express()
const port = 8080
 
app.set("view engine", "ejs")
 
app.get('/', (req, res) => {
    res.render("index.ejs")
})
 
app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

![Working directory after installing dependencies and creating server.js, views folder and index.ejs.](./assets/images/finalDirectory.png)
*Working directory after installing dependencies and creating server.js, views folder and index.ejs.*

- - - -

## Final Step

Great work! If everything is working, our ejs page is now ready to view at [**http://localhost:8080/**](http://localhost:8080/)

![image of web browser displaying index.ejs](./assets/images/helloWorld.png)

Congratulations! We’ve now finished the setup for our project. In the next step, we’ll be adding a fake json database to our project. 