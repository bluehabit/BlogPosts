## What is Node

Takes code written in JS and converts it to machine level code, that makes it quick enough to configure servers, query databases and more. Node is a javascript runtime which uses v8 engine, which is open source, and written in C++ to compile code to machine code . In the browser the global object we work with is `window` here in node it is the `global` object. For another similar comparison we can view and manipulate the DOM in the browser using the `document`. object, here in node we have something similar `process`. 

## Why Node?

`non-blocking I/O` - I/0 reading or writing to database, that is I/0 or input output.This could be database read write request, or making http request to another web server such as google map API for user current location. But I/O takes time. Non blocking makes it *great* for I/O applications. 

`NPM` - On `npmjs.com` is the largest ecosystem of open source libraries in the world. This is what makes Node fantastic, the cherry on top the community. People working everyday creating solutions to common problems like validating objects, or serving up content live using sockets. If you are trying to solve a problem that seems pretty broad, chances are its already solved on npm. For example if I want to validate some objects 

![f](https://imgur.com/R5qdHqJ.png)

`event-driven` -Its called `blocking` because while we are fetching from the database, which is an I/O operation, our application cannot do anything else. Sitting idle for database to respond, and can't even do something simple like adding two numbers together and printing them to the screen. **Blocking everything happens in order**. 

`non-blocking` first thing we calll `getUser` function for `user1`, but we are not waiting, we are kicking off the event. This is part of the `event loop` in node js. Notice we are just *starting the request* we are not *waiting for data*. The next thing we do, and this may suprise you, is we are not printing `user1` to the screen because we are still waiting for the db response. Instead we start process of fetching our user with the id of `321`, this is kicking off another event. Starting events are NOT I/O operations, waiting for the databse is I/O. Next up, we print `sum`. It doesn't care about the previous events for user objects, they are unrelated so no need for users to come back to print thte sum variable. **Non blocking we start events attaching callbacks, and the callbacks get fired later**. We still print out `user1` and `user2` but we do it once the data comes back. Inside of Node JS the `event loop` attaches a listener for the event to finish, in this case for the database to respond back, when it does it calls the callback. 

Down below we have a dotted box. This is simulated time for our event to get responsed to. Using non blocking doesn't make our operations faster, but it allows us to run more than one operation at the same time. 

Now imagine a webserver that is blocking, every user that made a request would be blocking, so it would have to spin off another thread to accompany more queries. However, node is single threaded, but since its non blocking i/o its not a problem. In a blocking pattern we could handle 2 requests on 2 separate threads but that doesn't scale well. Because for each request we would have to beef up CPU and RAM resources for the application. 

![f](https://imgur.com/nZLWstN.png)

## `require`

Allows us to load in functions that come bundled in with Node, for example the http module that lets us make a web server or fs module to access file system for our machine. We can also import 3rd party libraries such as express so we can write less code. And lastly we are going to use `require` to require our own files. This is going to allow us to break up our application to smaller files which is essential for real world apps. If you have all your code in one file it will be hard to test, maintain and update.

We can view a complete set of all the built in modules by visiting https://nodejs.org/api/

![f](https://imgur.com/GWZBSpe.png)

![f](https://imgur.com/cGSrPGq.png)

`./` indicates a `relative path` meaning the same directory we are already in. 

## `module.exports` 

![f](https://imgur.com/6rpfuQg.png)

After we use `require` we can use `module.exports` to export variables or functions so we can access them from our main file.

Shorthand

![f](https://imgur.com/9hkMlf0.png)


## Getting started with `npm`

When you install `node` it also comes with `npm`. It stands for `node package manager`, but that has since turned into a joke. Many front end frameworks like jquery and react now live on npm as well. 

### `npm init`, creating `package.json`

Will prompt you with some questions to fill out about your project.

![f](https://imgur.com/xplDlDa.png)

This creates a `pacakage.json` 

![f](https://imgur.com/a/7vqV6.png)

## Finding 3rd Party Packages / Libraries

When choosing a new package to consider, I like to see how many downloads a project has and when it was last updated.

![f](https://imgur.com/aJ4HngP.png)

### Install , `--save` flag and `node_modules` folder.

`--save` flag will update the contents of the `package.json` folder.

![f](https://imgur.com/cQoKDFl.png

All installed packages will go into the `node_modules` folder 

![f](https://imgur.com/lsVMsVf.png)

When you take your node project and put it on gitHub or sending it to a folder, the node modules folder shouldn't be taken with you. We have defined the modules, and their versions in the `package.json dependencies` object. This means we could delete the `node_modules` folder completely. When we want to get the content of the `node_modules` folder back all we have to do is run `npm install`. Without any names or flags this is going to run your `package.json` file grab all of your `dependencies` and install them. With `gitHub` instead of deleting the `node_modules` folder you are just going to ignore it from being added to your repository. 

The way the `node_modules` folder is generated can also be different depending on which version of `npm` you install. 

### Dependencies 

After installing our latest package, `lodash` if we revisit our `package.json` file we can see it created a new object called `dependencies` and it added `lodash` and the current version we installed to it.

![f](https://imgur.com/7BK8PiK.png)

next we can `require` our package. `_` is a common name for the `lodash` library. 

![f](https://imgur.com/FqtxLIB.png)

Sometimes the `documentation` will be easily accessible on the packages NPM page. In the case of `lodash`, it is not but it has a link to the website that will provide us with the docs.

![f](https://imgur.com/xujezlK.png)

### nodemon (node mon)

`nodemon` is a NPM program that constantly listens for changes on our app. When we save, and it detects changes, it will automatically rerun the app. You can start it with `nodemon (your_app.js here)`

![f](https://imgur.com/1BdOrJO.png)

### Passing Arguments through the CLI

Another built in `module` that comes with node is `process`. We are going to be working with `process.argv` specifically. 

![f](https://imgur.com/gnnWwfJ.png)

The arguments are a vector, but basically work like a JS array.  We can see *all* arguments by using `process.argv` and logging it to the console. 

![f](https://imgur.com/bSMVw12.png)

Notice how we can pass through arguments, `--title="secrets 2"` is an argument. The problem is that its not very easy to use, here we have to parse out the key which is `title` and value which is `secrets 2`. Plus when you factor in the different styles you can use to pass through valid arguments things can get messy for developers, for example `--title "secrets 2"` with no equal sign is valid. You would have to parse and account for these changes. To fix this we will use a 3rd party module called `YARGS` to make parsing these arguments effortless, istead of getting back a string, we will get back an object that will hold title and its contents. 

![f](https://imgur.com/lz767Sd.png)

### Yargs

![f](https://imgur.com/Jjo9JHk.png)

![f](https://imgur.com/MIdBaGs.png)

### Using your own 3rd Party Modules

First me must create a new `variable` that will hold the location of where are other `js` file is stored. We will use the `require` keyword to do this that comes with node. `var notes = require('./notes.js')`. Since we are storing the value of `require('./notes.js')` inside of the variable `notes` in our global scope, that is how we will use it.

For example: 
```
if (command === 'add'){
	notes.addNote(argv.title, argv.body);
} 
```

![f](https://imgur.com/7LwLzdd.png)


### JSON (Javascript Object Notation)

Notice the use of `"` double quoation marks. This is a requirement. 

Stringifying the object

![f](https://imgur.com/icQkmOF.png)

Serializing the text back to an Object

![f](https://imgur.com/OMEny18.png)


### Read Write and parse JSON from a File Exercise

![f](https://imgur.com/fA40jMA.png)




