## Runtime

Something that is part of Javascript only at runtime that is under the hood that you as a developer has no direct access to.

## Callback Functions

A callback function is a function that is passed to another function (the higher order function) as a parameter and then invoked by that function.

The higherOrder function receives the callback function as an argument and it is called within the body of the higher order function.

Callbacks are NON BLOCKING. This is what makes it asynchronous. The program can move on while it waits for a callback function to return. 

Previously it was only possible to handle asynchronous code using callbacks which lead to a bunch of nested functions known as callback hell. Next we had promises, and its successor async/await.

![f](https://imgur.com/CGTI9Ks.png)

![f](https://imgur.com/G4m3ZnG.png)

![f](https://imgur.com/HyBERpj.png)

```
function callback(){
	console.log('Coming from the callback')
}

function higherOrder(fn){
	console.log('About to callback');
	fn();
	console.log('callback has been invoked')
}

higherOrder(callback);
```

## What are callbacks used for?

* Advanced Array Methods
* Browser Events (click, submit, onload)
* AJAX requests
* React Development 


```
var numbers = [1,2,3,4,5]

//whatever you pass through as an argument to the callback
//function you can access when you call the function
//in this case array[i] the array item and i the index
function myFilter(array, callback){
	for(var i = 0; i < array.length; i++){
		callback(array[i], i);
	}
}


myFilter(numbers, function(num, index){
	if(num % 2 === 0){
		console.log(num, 'is even at index', index);
	}
});

//->2,4
```

![f](https://imgur.com/9nn3rfy.png)

## The Stack Overview TLDR

* Javascript reads from the top to the bottom. The stack, que, event loop all of that has to do with FUNCTION calls not function definitions. Function definitions will be skipped over.
* Each individual function gets placed on the stack as a `stack frame`
* All function calls, including built in methods like `console.log()` or `string.split()` get placed on the stack
* with async code such as setTimeout with a delay of `0` does NOT get invoked immediatley, the way to read it is INVOKE that callback function **after the stack is empty**
* **All** callback functions get placed on the Queue
* Remember we exit from a function with `return` that clears it from the stack


## The Stack and the Heap

What is the stack?
* an ordered data structure
* keeps track of functions we call
* part of javascript `runtime` (meaning something you do not have direct access to)

### How your Code Changes the Stack

Whenever you invoke a function, the details of the invocation (function call) are saved to the top of the stack (pushed to the top)

Whenver a function returns (exits) the information about the invocation is taken off the top of the stack (popped off the top)

The stack is processed from *top* to *bottom*

![f](https://imgur.com/30iqyJ9.png)

## Stack Frames

On the stack, each individual function call is called a `stack frame`. 

![f](https://imgur.com/NKeIj68.png)

Each individual stack frame is keeping track of:

* the function that was invoked
* the parameters that were passed to that function
* current line number to return to once the function finishes

## Heap 

![f](https://imgur.com/Bcj3Iu1.png)

The heap is an area in memory where the data is stored. 

![f](https://imgur.com/vLHLTPa.png)

When we make a new variable by `reference` we are not creating something new on the heap, we are just referencing that SAME AREA IN MEMORY.

Creating a variable actually creates an area in the memory.

## Stack Example

Very important **every function call adds to the stack!**. That is not just custom functions that you build yourself, but built in functions as well such as those found on arrays. 

In our example below `sentence.split` is a function invocation so it gets placed on the stack

![f](https://imgur.com/kWcxEJy.png) 

Notice it has how `sentence.split` has `?` for the line number to return to. That is because its 'under the hood' of javascript we don't know where it is.

## Async

If you have a function that makes a request to the server, but who knows how long it will take to get a response. Javascript continues to execute other unrelated code while waiting on that response. 

## Forced Async Examples setTimeout and SetInterval

`setTimeout` and `setInterval` are great functions to illustrate asynchronous code.


## setTimeout

A function that asynchronously invokes a callback after a delay in milliseconds 

![f](https://imgur.com/Mr8JRTF.png)

Notice in the anonymous callback version, just like the named version, the first parameter that setTimeout accepts is a callback. The second parameter is the delay in MS. Notice the order is the same, we just pass through an anonymous function instead of a named function.

## Clearing setTimeout

Use the `clearTimeout` method. 

![f](https://imgur.com/bZROQL7.png)

## setInterval

Similar to `setTimeout`, but `setInterval` will continuously invoke the callback every x ms.

We can cancel `setInterval` with `clearInterval`


## Event Loop and the Queue 

## Queue 

The Queue is an ordered list of functions waiting to be placed on the stack. Functions in the queue are processed on a first in, first out basis (FIFO)

## Event Loop

Functionality in the JavaScript `runtime` that checks the queue when the stack is empty. If the stack is empty, the front of the queue is placed on the stack

![f](https://imgur.com/GUQ4qeW.png)

## Queue Example

Most people would look at this example and think that `console.log('Hello World');` happens immediately however that is not the case.


Callback functions are always placed in the queue? 

![f](https://imgur.com/etkFFCC.png)

## Javascript is a Single Threaded Language

This means code in JS is executed in a linear manner. Code that is running cannot be interrupted by something else going on in the program.

## Promises

![f](https://imgur.com/CHjqXfH.png)

A promise is an object that represents a task that will be completed in the future.

Analogy: Taking a number at a government office before you can get helped. The piece of paper  you get is like your promise. The help you get at the counter is like the invocation of your callback.

Lets reiterate, a `promise` is nothing special its just a plain old javascript object with special methods that allow you to execute code synchronously. It will do things in order even though their is a delay. 

## Creating a Promise

![f](https://imgur.com/IBUqKBc.png)

We create a promise using the promise constructor. Promises are functions that have one parameter, a callback function with two arguments (`resolve` and `reject`).

 The callback function is the asynchronous component of promises. Depending on what happens with the task will determine what is invoked. If the task is successful `resolve` will be invoked, if it fails `reject` will be invoked.

When `resolve` finishes, that is when we use the `then` method which is another asynchronous piece of code. 

Again `.then` callback function gets invoked whenever `resolve` is invoked.

## Promise Handling Errors

`reject` can also be invoked from a promise

![f](https://imgur.com/Kdihdss.png)

`catch` is the callback that will be invoked whenever `reject` is invoked from within the promise.

![f](https://imgur.com/GJTy0st.png)

![f](https://imgur.com/DFI35Xi.png)


## Asynchronous Promises 

![f](https://imgur.com/liPENqX.png)
