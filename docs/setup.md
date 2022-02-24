---
layout: default
title: Setup
nav_order: 2
---

# Setup
- - - -

TABLE OF CONTENTS

* [Working Directory/Folder Structure](#working-directory/folder-structure)
* [Package.json](#packagejson)
* [Other Dependencies](#other-dependencies)
* [Index.ejs](#indexejs)
* [Server.ejs](#serverejs)
* [Final Steps](#final-step)

## Working directory/Folder structure 
<br>
To start off, we’ll need to create somewhere to store our project files. Create a new empty folder anywhere on your PC.

> *Note: Ensure that your folder name does not have any spaces, this could cause some problems in the following step.*

Next, we’ll open up Visual studio code and set the working directory to the folder we have just created.

> **File -> Open Folder -> (Choose the folder we made)**

- - - -

## Package&#46;json 
<br>

The Package.json file is a must have for any project. It helps the user understand what your project is in just a few words. 
1. Open a new terminal 
2. Once the terminal is open, run the following command line: 
```
npm init -y
```

This command will create the package.json file needed for our project. You should now see the json file appear on the left. 

![package.json file](https://github.com/iantelli/Yasmina-Ian/blob/gh-pages/assets/images/package.png?raw=true)

- - - -

## Other Dependencies
<br>
Next, we’ll need to install express and ejs. 

* This step is very simple and is done by running the following command in your terminal:


```
npm install -S express ejs
```

- - - -

## Index&#46;ejs
<br>
After the installation, there a couple steps that are necessary to create a working page

1. Create a folder named **views** in the root folder
2. Create a file named **index.ejs** in the *views* folder we just created
3. Add the following contents into your *index.ejs* file:

```
<h1>Hello World!</h1>
```


![Working directory after installing dependencies and creating views folder and index.ejs.](https://github.com/iantelli/Yasmina-Ian/blob/gh-pages/assets/images/directory.png?raw=true)

:bulb: *This is what the working directory should look like after installing dependencies and creating views folder and index.ejs.*

- - - -

## Server&#46;ejs
<br>
Creating a basic local server that returns html to the user is very simple.

1. Create a file called server.js in the root folder. 
2. Add the following content to your server.js file: 

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

![Working directory after installing dependencies and creating server.js, views folder and index.ejs.](https://github.com/iantelli/Yasmina-Ian/blob/gh-pages/assets/images/finalDirectory.png?raw=true)
<br>
:bulb: *This is what the working directory should look like after installing dependencies and creating server.js, views folder and index.ejs.*

- - - -

## Final Step
<br>

We're almost done our setup! 

1. Open up the terminal
2. Run the following command line to start our local server:

```
node server.js
```

Great work! If everything is working, our ejs page is now ready to view at [**http://localhost:8080/**](http://localhost:8080/)

![image of web browser displaying index.ejs](https://github.com/iantelli/Yasmina-Ian/blob/gh-pages/assets/images/helloWorld.png?raw=true)

Congratulations! We’ve now finished the setup for our project. In the next step, we’ll be adding a fake json database to our project. 