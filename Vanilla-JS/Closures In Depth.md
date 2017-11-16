One thing that was confusing me in my studies was how closures and callback functions can be used together. Particularly with `addEventListener` since we are not easily able to peer under the hood. As a result I started writing some notes to myself about closures in general and closures used with callback functions. It ended up being pretty long, so I figured I would turn this into a 'blog post' to help cement my knowledge. Thought I would share it here as well, maybe it will help a student or two. 

Anyways for those of you who are much more experienced than me please let me know if there are any errors in my logic, or suggestions, or more examples to add. Guide below.

---------------------
## Closures In Depth

* What is a closure?
* Private Variables
* Instances of Scopes
* Using closures and callback functions together

A closure is when a *parent function returns another function*; however, the returned inner function still has access to the parent functions scope, including variables and arguments and uses them. 

Whenever we have a function that returns another function we have the *possibility* of creating a closure. If the returned function accesses the outer functions variables or arguments then that is considered a closure. Closures will 'scope' the outer functions variables and arguments. The inner function will be able to access these variables or parameters even after the parent function has already returned. Sometimes this is referred to as creating `private variables` which we will discuss in further detail later. Quick note, the terms outer function and parent function are synonymous in this post.

Lets take a look at a brief example of closure.

![f](https://imgur.com/7W3uikq.png)

The function `count` returns another function, in this case an anonymous function. Please note, whatever comes after the `return` keyword is returned by the function. In our example, `function(){return ++count;};}` comes immediately after the `return` keyword. When the `return` `keyword` is used it will exit the function.

Let's go ahead and call `count` and see what happens: 

![f](https://imgur.com/tgbxSpz.png)

The parent function runs, it gets to the `return` statement and the parent function then exits and returns the inner function as expected.

This now has the potential to create closure, all that is left is for the inner function to make use of a variable and or argument from the parent functions scope and this will meet the requirements for a closure. And we can see here that it does, the inner function is accessing the outer functions variable `count` by incrementing it with `++count`. 

When we run the function `count()`  it scopes `var count` from the parent function. The function then immediately returns another function, an anonymous one. Remember, whatever comes after the `return` keyword is returned by the function. This could be a boolean value, number, string, object etc. or another function as is the case with closures.

What we are returning here in this example is a `function definition`, to be more precise: 

```
function(){
  return ++count;
};
```

## Scopes and Instances

Whenever we create a closure it scopes the parent functions variables and or arguments. Calling our closure function, `count()`, creates an `instance` of that scope. In other words, calling `count()`  will scope the variable `count` and create a new instance of that scope. But to access these instances we need to save them to a variable.

> Whenever we call the closure function, it creates a new instance of that scope. AKA scoping the variable.

To increment our scoped variable `count` we simply need a way to repeatedly use the scope that was created. We will store instances of the function `count()`'s scope inside variables. Every time we call `count()` it creates a new instance. We can create as many instances of `count()`'s scope as we would like. Each variable is a separate instance of the private variable `count`. 

![f](https://imgur.com/IxE1pIz.png)

The value of the `test` variable holds a function definition. Just like earlier, when `count()` is called, it goes through line by line, the program sees the 'return' keyword and the inner function is returned. Only difference is now we are saving this to variable. This means `test` is now a function expression, one of the features that makes functions in JS first class objects. Because `test` is now a variable holding a function definition (aka a function expression) we can now call it with `test()`.

![f](https://imgur.com/bUDEB0H.png)

The variable `test` holds the `anonymous function` that was returned by `call()`. We can execute, or call, this `function definition` stored within the `test` variable by calling it, just like a regular function by using `test()`. The value of the `test` variable holds a function definition. This means `test` is now a function expression, one of the features that makes functions in JS first class objects.

![f](https://imgur.com/IxE1pIz.png)

```
return function(){
  return ++count;
};
```

All that really matters, is that calling `count()` is in a scope with access to the actual `count` function, and for the result of `count()` to be stored so you can reuse it. 

If you were to not store it, you can still do stuff like this: `count()()` and it will return `1`.  Once this has run, you will have lost your instance of the scope since it is not being saved anywhere. Every time you call the function `count()` you re-initialize your scope. 

![f](https://imgur.com/5jZKqc4.png)

We could even do something like this if we wanted, but it's not advisable.

![f](https://imgur.com/PW7iYrr.png)

## Named Inner Functions

You could also see our `count` function written a different way, but the same concepts apply. This example uses named functions instead of anonymous functions.

![f](https://imgur.com/4iNb9M3.png)

Just be careful you return the inner functions `function definition`, do not attempt to call it here.

## Scoping Arguments

Whenever a function receives an argument, **just consider it to be an automatically declared variable**. Using this logic, closures will not only scope variables from the parent scope, but arguments as well. As alluded to earlier.

![f](https://imgur.com/ynchAF2.png)

Here we slightly modified the code to accept an additional argument. Even though the parent function has already returned, we still have access to the `string` argument, as well as the variable `count`. 

### Another Example

Lets look at another example where we scope a functions arguments.

![f](https://imgur.com/itw2ggi.png)

## Callbacks that Utilize Closures

Now things get a little bit more complicated. Callbacks can also utilize closures. 

![f](https://imgur.com/AhbzcuU.png)

Just like before we have a `closure function` named `increaseCount()`. Running `increaseCount()` will scope our variable `count`. Also like before we will store scope instances within a variable, in this case `myInstance`. The main difference here is the addition of `higherOrder` which is a `higher order function`, meaning it accepts another function as an argument. 

`increaseCount()` gets called within `higherOrder` as a `callback function`.

This example is pretty simple, and contrived, but it is helpful to understand before we move on. The most important thing to remember here is again, the variable `myInstance` contains an **instance of the scope**. 

### Very Important

`myInstance` contains the scope (`whatever calls the closure function creates an instance of the scope!`). We are merely passing the scope, contained within the variable `myInstance` to `higherOrder`, which calls it for you.

## `addEventListener` and Closure

Continuing with our example of callbacks and closures working together, lets take a look at `addEventListener`. After all, one of the parameters for `addEventListener` is a `callback function`. But before we do that, lets look at a 'fake' event listener that uses `setInterval`. **The main point of this example is how we can store and re-use instances of scope**.

![f](https://imgur.com/1V0q2dF.png)

Just like before we have a `closure function` `increaseCount` which returns another function that has access to its parent functions scope. We will store an instance of this scope in the variable `counter` by calling `increaseCount()`. We can then pass this instance of the scope to the higher order function `fakeEventListener`. 

Inside `fakeEventListener` we have `setIterval` which also takes a callback function as an argument. Inside the callback we are going to pass through the `counter` variable **which itself is just a reference to a scope instance**.

**Special Note:** We cannot use the `return` keyword within the inner function because `setInterval` is an asynchronous operation.

![f](https://imgur.com/s5hMN3k.png)

## Another way to write our `fakeEventListener`

Just to be thorough lets again revisit an alternative way of writing this function using a named function, instead of an anonymous one. 

![f](https://imgur.com/6JOz3IF.png)

## `addEventListener`

Time for the big guns, lets look at closures and callbacks used together in `addEventListener`. 

![f](https://imgur.com/0emR8CM.png)

Just like in our previous example using `setInterval` here we are passing around a scope instance. `button` stores the inner function that was created when you call `clickedEventFunction()`. That function has a scoped `count` variable. **Here instead of storing it inside of a global variable, we are instead storing it inside of an object (e.g. `button`)**. 

In addition, we can also access the `event object` just like usual. Only this time we will pass it as an argument to the returned inner function.

![f](https://imgur.com/wsQDk0T.png)

## Cool Applications of Closures

In this example we use closure to scope the argument `id` (returning an anonymous function), this allows us to increment it and give a unique id to each item within the array of objects. Normally for each item `id` would be  re-initialized every time through. Instead, we use closure to return the inner function and scope the `id` argument from its parent. This allows us to increment it, just like we did with the `counter()` examples. If we did not do this, `id` would be equal to `0` for each item in the array of objects. Remember, we can essentially think of an argument passed to any function as a declared variable and treat it as such.

![f](https://imgur.com/sYA9PjA.png)

## More Examples

![f](https://imgur.com/AgEkhY4.png)

Notice in this example we are returning an object. 

![f](https://imgur.com/IIpIA13.png)

![f](https://imgur.com/Jjoj4VE.png)



