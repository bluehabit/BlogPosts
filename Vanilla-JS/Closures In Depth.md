## Closures In Depth

A closure is when a parent function returns another function; however, the returned inner function still has access to its parent functions scope including variables and arguments. 

Whenever we have a function that returns another function we have the possiblity of creating a closure. If the returned function has access to the parent function / outerscope variables or arugments then that is considered an example of closure. The closure 'scopes' the outer functions variables and arguments. This allows us to create `private variables` which we will discuss in detail in a moment. Quick note, the terms outerfunction and parent function are synonymous.

Lets take a look at a brief example of closure.

![f](https://imgur.com/7W3uikq.png)

The function `count` returns another function, in this case an anonymous function. Please note, whatever comes after the `return` keyword is returned by the function. In our example, `function(){return ++count;};}` comes immediatley after the `return` keyword. Using the `return` `keyword` in Javascript will exit the function.

Let's go ahead and call `count` and see what happens: 

![f](https://imgur.com/tgbxSpz.png)

The parent function runs, it gets to the `return` statement and the parent function then exits and returns the inner function as expected.

This has the potential to create closure, all that is left is for the inner function to make use of a variable and or argument from the parent functions scope and this will meed the requirements of a closure. And we can see here that it does, the inner function is accessing the outer functions variable `count`. 

When we run the function `count()` it scopes the `var count` from the parent function. The function immediately returns another function, an anonymous one. Remember, whatever comes after the `return` keyword is returned by the function. WHat we are returning here is a `function definition`, to be more precise: 

```
function(){
  return ++count;
};
```

## Scopes and Instances

Whenever we create a closure it scopes the parent functions variables and or arguments. Calling our closure function creates an `instance` of that scope. In our case calling the function `count()`  will scope the variable count and create a new instance. But to access these instances we need to save them to a variable.

To increment our scoped variable `count` we simply need a way to repeatedly use the scope that was created. We will store instances of the function `count()` inside variables, that is what creates our instances. We can create as many instances of `count()` as we would like, we just need to save it to a variable. Each variable is a seperate instance of the private variable `count`. 

![f](https://imgur.com/IxE1pIz.png)

All that really matters, is that calling `count()` is in a scope with access to the actual `count` function, and for the result of `count()` to be stored so you can reuse it. 

If you were to not store it, you can still do stuff like this: `count()()` and it will return 1, but you can only do that once.  ONce this has run, you will have lost your instance of the scope since it is not being saved anywhere. Everytime you call the function `count()` you re-initialize your scope. 

![f](https://imgur.com/5jZKqc4.png)

The value of the `test` variable holds a function definition. This means `test` is now a function expression, one of the features that makes functions in JS first class objects.

![f](https://imgur.com/bUDEB0H.png)

`test` holds the `anonymous function` that was returned by `call()`. We can execute, or call, this `anonymous function` by running `test()`:

```
return function(){
  return ++count;
};
```

We could even do something like this if we wanted, but its not adviseable.

![f](https://imgur.com/PW7iYrr.png)

You could also see our `count` function written a different way, but the same concepts apply.

![f](https://imgur.com/4iNb9M3.png)



> Whenever we call the closure function, it creates a new instance of the scope. AKA scoping the variable for short.




