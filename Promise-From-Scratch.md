## Preparation 

Before we jump in how to create a promise from scratch, we need to work through a few simple examples. I will attempt to isolate one concept at a time, and in the final code we will implement everything we discussed for increased complexity.

Very important to understand in JS functions are just values that can be passed around, just like a number, string, object etc.  

## Classes and Prototypes

Methods that are shared on the prototype are typically called `public methods` while those that are created for each object instance are `private methods`. 

![f](https://imgur.com/L1dsO0E.png)


## Creating a Promise from Scratch

You can **route** callbacks by passing through multiple parameters that are also functions (callback functions). Use a `if/else` block to check a condition `if` the condition is true then we call `func1(value)`, `else` we call `func2(value)`.

## Simple Callback Example

Callbacks are very useful for `asynchronous` code where there may be a delay between when we send a request to a server, and when we receive that response. Javascript is a single threaded language but utilizes a stack, queue and event loop to process code in an `asynchronous` manner. 

Callbacks are useful for passing values through. Those values can be anything a variable, object, boolean, string, a function or even a function with its own additional parameters. 

In the example below, the function `func1` that is passed through as a callback has its own parameter `num` that we can use with the callback. We also wrap the code in a `setTimeout` to simulate a delay from the server to help demonstrate Javascripts async capabilities. Check it out.

![f](https://imgur.com/21by1dx.png)

## Callback Example 2

![f](https://imgur.com/6BysFG0.png)

* the `class` Parrot is the the `higher order function`. Callbacks are always called within a higher order function. The higher order function in this case is the class.
* The callback is called within the higher order function on this line `callback(this.onResolve, this.onReject)`
* The `callback` parameter holds the entire function definition that is passed through 
```
(function(resolve, reject){
		if(randomNumber > .05){
			resolve(parrotObj, 15);
		} else {
			reject('there was an error');
		}
```

## Callback Example 3

![f](https://imgur.com/1DrvZwQ.png)


## Callbacks and the Box Metaphor

The way I like to imagine it is callback functions are like storing items inside a UPS box. They are packaged inside a factory, shipped around the country, and the opened at a *later* time once the user receives them. This is just like asynchronous functions.

With asynchronous functions, we *call the higher order function* that is when we store the information that will be called back *later* within the higher order function itself (remember the higher order function receives the callback as an argument). When we pass our callback through as a parameter that is like storing items in our box, getting them ready for shipment. We are storing the items, shipping it, and it will eventually be delivered and opened at a later period in time. 

After the stack is cleared and we receive a response from the server, we can deliver that data to our end user at a later point in time. That is when we call the callback function from within our higher order function, that is like opening the *box*. The user can get a pair of scissors, cut off the tape, and finally open the box to retrieve and use the items that they ordered.

![f](https://imgur.com/WvVbrBp.png)


## Constructor Functions, Bind and the Keyword This


Example 1 works, but Example 2 does not why is that?

![f](https://imgur.com/gSlFLCo.png)

![f](https://imgur.com/CAFcLNe.png)

That is because `this.printContext` is just referring to the function definition itself. Because you are giving `printContext` to your callback, when you try to call it in the anonymous callback, `this` has changed to the anonymous callback. To fix this we `bind` it to the new instance of the class. 

In other words, inside the callback `this` just refers to the function definition itself. Because inside the callback you are not calling `this.printContext' directly, but rather a reference to it passed into your callback as an argument.

However, if you defined `this.printContext with an *arrow function*, it would work without bind because arrow functions will bind the keyword this for you.

```
this.printContext = () => {
   console.log(this, 'is a new pipe'); 
}
```

## Bind

The `bind` function returns a new `bound function`, it is a copy of the function that it is targeting only the value of the keyword `this` is changed.

![f](https://imgur.com/LFedm9n.png)

![f](https://imgur.com/z09rdJo.png)

![f](https://imgur.com/2fitfny.png)

Use `bind` when you want the function to later be called within a specific context. Use `call` or `apply` when you want to invoke the function immediately and modify the context.

## This

What does `this` mean in JavaScript? Same thing it does in the English language. It doesn't mean anything without *context*. If you say to a friend "I don't like *this*" we have no context and no way of knowing what exactly `this` refers to. You have to infer from the context to get the value.

![f](https://imgur.com/8bHBCln.png)

## Setting Scope

The way you call the function, is what sets the scope in JS and also what the context of `this` refers. 

## Method Chaining 

### What is Method Chaining?

Method chaining is a technique that can be used to simplify code in scenarios involving calling multiple functions on the same object consecutively. For instance this code snippet in jQuery. 

`$('#my-div').css('background','blue').height(100).fadeIn(200);`

Or like this

`str.replace('k', 'R').toUpperCase().substr(0,4)`

Here is another good example of why we use method chains

![f](https://imgur.com/Uroij5n.png)

The typical way to enable method chaining is to return the current object at the end of every function.

![f](https://imgur.com/U6XqRUM.png)

![f](https://imgur.com/65wK8SK.png)


Resource: https://schier.co/blog/2013/11/14/method-chaining-in-javascript.html

## How Bind Works

![f](https://imgur.com/VM2IFyA.png)

## Build a Promise from Scratch

•	The onResolve function has a try/catch block if there is an error once the user is able to retrieve information from the server. In our code snippet example the `catch` portion of the block will never execute. To confirm, just place some dummy code like a `console.log` within.
•	`catch` is part of the object method chain. Just like the `then` portion of the method chain, all we are doing is pushing function definitions that will be executed later. These all occur before the callbacks take place

1.	We call `makeApiCall` which returns a new simple promise, this happens immediately. The callback function inside will run 2,000 ms later.
2.	While we are waiting on the response, we go ahead and start building our promise chain. Because makeApiCall() `returns` a promise object, we can chain .then on it. All the `.then` function does is take a callback function definition, and push it to the promiseChain. `.catch` is also part of this chain just in case the response fails. Just like `.then`, `.catch` pushes a callback function as well that will be called back later if needed. Remember, anytime we are dealing with a method chain we have to return `this`. As a result if you check the class `.then` and `.catch` return `this`.
3.	Next we invoke a callback function depending on the apiRequest status code. If it was successful then we go through `this.onResolve` and the whole promise chain with a `forEach` and execute the callback functions. 
4.	In the event the response fails, `.catch` which was already run, sets the value of `this.handleError` to the callback function passed through it. We use that with `this.onReject` to call that function


Resource: https://levelup.gitconnected.com/understand-javascript-promises-by-building-a-promise-from-scratch-84c0fd855720

