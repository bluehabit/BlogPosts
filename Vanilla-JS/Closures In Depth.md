## Closures In Depth

A closure is when a parent function returns another function; however, the returned inner function still has access to the parent functions scope, including variables and arguments. 

Whenever we have a function that returns another function we have the *possiblity* of creating a closure. If the returned function accesses the outer functions variables or arugments then that is considered a closure. Closures will 'scope' the outer functions variables and arguments. The inner function will be able to acccess these variables or parameters even after the parent function has already returned. Sometimes this is referred to as creating `private variables` which we will discuss in further detail later. Quick note, the terms outerfunction and parent function are synonymous in this post.

Lets take a look at a brief example of closure.

![f](https://imgur.com/7W3uikq.png)

The function `count` returns another function, in this case an anonymous function. Please note, whatever comes after the `return` keyword is returned by the function. In our example, `function(){return ++count;};}` comes immediatley after the `return` keyword. When the `return` `keyword` is used it will exit the function.

Let's go ahead and call `count` and see what happens: 

![f](https://imgur.com/tgbxSpz.png)

The parent function runs, it gets to the `return` statement and the parent function then exits and returns the inner function as expected.

This now has the potential to create closure, all that is left is for the inner function to make use of a variable and or argument from the parent functions scope and this will meet the requirements for a closure. And we can see here that it does, the inner function is accessing the outer functions variable `count` by incrementing it with `++count`. 

When we run the function `count()` it scopes`var count` from the parent function. The function then immediately returns another function, an anonymous one. Remember, whatever comes after the `return` keyword is returned by the function. This could be a boolean value, number, string, object etc. or another function as is the case with closures.

What we are returning here in this example is a `function definition`, to be more precise: 

```
function(){
  return ++count;
};
```

## Scopes and Instances

Whenever we create a closure it scopes the parent functions variables and or arguments. Calling our closure function, `count()`, creates an `instance` of that scope. In otherwords, calling `count()`  will scope the variable `count` and create a new instance of that scope. But to access these instances we need to save them to a variable.

> Whenever we call the closure function, it creates a new instance of that scope. AKA scoping the variable.

To increment our scoped variable `count` we simply need a way to repeatedly use the scope that was created. We will store instances of the function `count()` inside variables, that is what creates our instances. We can create as many instances of `count()`'s scope as we would like. Each variable is a seperate instance of the private variable `count`. 

![f](https://imgur.com/IxE1pIz.png)

The value of the `test` variable holds a function definition. Just like earlier, when `count()` is called, it goes through line by line, the program sees the 'return' keyword and the inner function is returned. Only difference is now we are saving this to variable. This means `test` is now a function expression, one of the features that makes functions in JS first class objects.

![f](https://imgur.com/bUDEB0H.png)

The variable `test` holds the `anonymous function` that was returned by `call()`. We can execute, or call, this `function definition` stored within the `test` variable by calling it, just like a regular function by using `test()`. The value of the `test` variable holds a function definition. This means `test` is now a function expression, one of the features that makes functions in JS first class objects.

![f](https://imgur.com/IxE1pIz.png)

```
return function(){
  return ++count;
};
```

All that really matters, is that calling `count()` is in a scope with access to the actual `count` function, and for the result of `count()` to be stored so you can reuse it. 

If you were to not store it, you can still do stuff like this: `count()()` and it will return `1`, but you can only do that once.  ONce this has run, you will have lost your instance of the scope since it is not being saved anywhere. Everytime you call the function `count()` you re-initialize your scope. 

![f](https://imgur.com/5jZKqc4.png)

We could even do something like this if we wanted, but its not adviseable.

![f](https://imgur.com/PW7iYrr.png)

## Named Inner Functions

You could also see our `count` function written a different way, but the same concepts apply.

![f](https://imgur.com/4iNb9M3.png)

## Scoping Arguments

Whenever a function receives an argument, **just consider it to be an automatically declared variable**. Using this logic, closures will not only scope variables from the parent scope, but arguments as alluded to earlier and shown in the example below.

![f](https://imgur.com/ynchAF2.png)

Here we slighlty modified the code to accept an additional argument. Even though the parent function has already returned, we still have access to the `string` argument, as well as the variable `count`. 

## Callbacks that Utilize Closures

Now things get a little bit more complicated. Callbacks can also utilize closures. 

![f](https://imgur.com/AhbzcuU.png)

Just like before we have a `closure function` named `increaseCount()`. Running `increaseCount()` will scope our variable `count`. Also like before we will store scope instances within a variable, in this case `myInstance`. The main difference here is the addition of `higherOrder` which is a `higher order function`, meaning it accepts another function as an argument. 

`increaseCount()` gets called within `higherOrder` as a `callback function`.

This example is pretty simple, and contrived, but it is helpful to understand before we move on. The most important thing to remember here is again, the variable `myInstance` contains an **instance of the scope**. 

### Very Important

`myInstance` contains the scope. We are merely passing the scope, contained within the variable `myInstance` to `higherOrder`, which calls it for you.



