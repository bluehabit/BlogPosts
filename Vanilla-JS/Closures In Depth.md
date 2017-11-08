## Closures In Depth

A closure is an inner function that has access to its parent functions scope after the parent function has already returned. Whenever we have a function that returns another function we have the possiblity of creating a closure. If the returned function has access to the parent function / outerscope variables or arugments then that is considered an example of closure. The closure 'scopes' the outer functions variables and arguments. This allows us to create `private variables` which we will discuss in detail in a moment. Quick note, the terms outerfunction and parent function are synonymous.

Lets take a look at a brief example of closure.

![f](https://imgur.com/7W3uikq.png)

The function `count` returns another function, in this case an anonymous function. Please note, whatever comes after the `return` keyword is returned by the function. In our example, `function(){return ++count;};}` comes immediatley after the `return` keyword. Using the `return` `keyword` in Javascript will exit the function.

Let's go ahead and call `count` and see what happens: 

![f](https://imgur.com/tgbxSpz.png)

As expected calling the outer function returns another function. 

This has the potential to create closure, all that is left is for the inner function to make use of a variable and or argument from the parent function. Lets do that now. 

creates our instances. Each instance will scope the variable count. We created these scoped variables and instances through closure. In order to do this we must return a function. 
