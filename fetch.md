## AJAX

AJAX is not a framework, technology, library, not a tool someone created. Its just an approach to web development, a concept. Using existing tools and technologies (like callbacks) , to build the structure of a website different.

### XMLHTTP Request

`XMLHTTP` requests allow you to make HTTP requests from the browser and updating the page without refreshing. With AJAX, websites can send and request data from a server *in the background* without disturbing the current page. And this lead to today's **single page apps**, and frameworks that help you manage them like react. One of the most important aspects of this is retrieving data from a server.

![f](https://imgur.com/BRKTJXx.png)

### Problems With XHR

1.	Syntax, ugly and bulky not succinct 
2.	largely byproduct by how old it was, written in a different time 16 years ago, not with single page apps in mind
3.	No streaming data (large amounts of data to stream in)


`XHR` gets a *face lift* with the `Fetch` API, cleaner syntax, more powerful.

In this demo that will look for the users number inside of Pi (over a billion digits), if this was XHR we would have to load ALL the data first, all the billion numbers. With fetch you can STREAM the data back and check along the way to see if you encountered the user substring. This is an example of `streaming data`. 

![f](https://imgur.com/DPztp01.png)

## Fetch

Fetch returns a `promise` for us. Fetch returns a `response object`. 

### Basic Fetch

![f](https://imgur.com/W0163jl.png)

![f](https://imgur.com/Nscc3K6.png)

### Parsing JSON with Fetch

![f](https://imgur.com/dV6QxRu.png)

Can use `.json()` to return a string as an object.

![f](https://imgur.com/TRVNFXS.png)

### Chaining .then

![f](https://imgur.com/dkD2l4K.png)


### Handling Fetch Errors with Catch

![f](https://imgur.com/bSxPDTt.png)

**Very Important:** instead of checking if a status code is 200, 400, 404 etc. Just use the built in property `.ok`

![f](https://imgur.com/v7W8v1A.png)

Why do we still see 'Everything is Fine' logged to the console? Rather what circumstances will we actually see .catch trigger? The promise will be rejected IF there is a problem with the request itself like users internet is off, problem connecting, or issue with credentials - but not with the actual response. If you put in a gibberish URL you would still see everything is fine. 

![f](https://imgur.com/amGk8QC.png)

![f](https://imgur.com/JrS5UkY.png)

Just like in the `simplePromise` example whatever you `return` from a `.then` chain gets passed onto the next `.then` in the chain. 

## Refactoring Fetch

![f](https://imgur.com/wDSxlA3.png)

Refactor using the above tips.

![f](https://imgur.com/khuytYr.png)

## Problems with Fetch

No support in `IE`. 

### Misc.

![f](https://imgur.com/HI5nRaO.png)



