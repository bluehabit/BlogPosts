## Ajax Overview

Before we walk through how to setup an AJAX request, lets first briefly discuss why we need it. AJAX, or `asynchronous javascript and XML`, allows us to retrieve or send information to a web server and process this response without having to reload a webpage. This is how we can work with API's, or what are sometimes referred to as live web services. It is important that it is `asynchronous` because when we work with a API, there will be a delay when the user will receive the response.

## HTTP request methods

![f](https://imgur.com/cf5IXIz.png)

We will work with `http request methods` to communicate with the server, to send or receive information. The two most common methods we will use are `GET`, to retrieve information from the server (for example getting the weather), and `POST` to send information to the server (for example writing to a database).

## `GET` Method Overview

We can setup a `local web server` using the NPM module `http-server` (https://www.npmjs.com/package/http-server) to retrieve local JSON files using the `GET` method. We can also practice using a live web service, where we make a request to a web server, and get JSON back as a response. For example querying the Open Movie Database, or a weather API. 

## Making our AJAX request

### The `XMLHttpRequest` Object

To begin a AJAX request, we must first begin using a `constructor` to create a new `xhr` object. This can be done with:
`var xhr = new XMLHttpRequest();`

### `.onload` event handler

Next we need to use the property `.onload` which is an event handler. We will assign this value to a function that will perform a certain task that it will only be triggered once when the request succeeds.

```
xhr.onload = function () {
    // do something with the response
};
```

## `xhr.open` Overview

After we attach an event handler to our xhr request we can open the connection using the `open` method. This will *initialize* the request, but it does not begin the request or send/receive any data. The `open` method has 2 parameters, the first of which is the `HTTP request method`. The most common http request methods are `GET` and `POST`. The next parameter is the `endpoint`. If we are running a local web server, this will be a local file within the directory, otherwise it will be a request to a web server in the form of a URL. 

`xhr.open('GET', 'http://www.omdbapi.com/?t=star+wars');`

##`xhr.send` Overview

In order to send or receive data after initializing our request with `xhr.open` we must send it. We can do this with:

`xhr.send();`

This method starts the AJAX process, and will trigger the `onload` event handler if the server responds successfully. Again AJAX is asynchronous, we made the request, but the request will not be received by the server instantly - and we dont know how long until we receive a response. Javascript will move on in the background while it waits on a response from the server, because `async` code is `non-blocking`. Compare this to `blocking` or `synchronous` code where we must go line by line in the program. In the case of a server request, if the program was going in a `synchronous` fashion we would be stuck waiting on the response (however long that may be) hanging up the rest of the program while we wait. 

### So Far...

So far this is what our code looks like, but we still need to handle the response:

```
var xhr = new XMLHttpRequest();
xhr.onload = function () {
    // do something with the response
};
xhr.open('GET', '/response.json');
xhr.send();
```

## Handling The Response

We will use the `status` on `xhr` to check for the HTTP status code. `200` for example indicates that the response was successful.  

```
var xhr = new XMLHttpRequest();
xhr.onload = function () {
    // do something with the response
    if (xhr.status === 200) {
        console.log(JSON.parse(xhr.response).data);
    }else {
        console.log('There was an error ' + xhr.status)
    }
};
xhr.open('GET', '/response.json');
xhr.send();
```

Otherwise, using `else` we can return an error message if the response was not successful. And thats the basic template for working with AJAX using the `XMLHttpRequest` object. 

## Finishing Up

Now that we have our AJAX request set up properly, lets make a few modifications so we query www.omdbapi.com to find the title star wars. And that is the basic workflow of sending an AJAX request.

```
//Simple xhr request
var xhr = new XMLHttpRequest();
xhr.onload = function () {
    if (xhr.status === 200) {
        console.log(JSON.parse(xhr.response));
    } else {
    	console.log('There was an error ' + xhr.status)
    }
};
xhr.open('GET', 'http://www.omdbapi.com/?t=star+wars&apikey=c5182e2a');
xhr.send();
```

### Title: Sending AJAX Requests
### Category: AJAX in Depth
