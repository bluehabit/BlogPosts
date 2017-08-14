#### Key Resource

How do closures work? https://stackoverflow.com/questions/111102/how-do-javascript-closures-work

Lexical Scope https://stackoverflow.com/questions/1047454/what-is-lexical-scope 

![key3](http://imgur.com/z7vPUtP.png)

![key4](http://imgur.com/xFpCTXF.png)

# Callbacks and Closures

`function block scopes are what you call a closure`

## Example 1

![example-1](http://imgur.com/exE3hzk.png)

Example of *nested* functions, but not a closure.

------

## Example 2

Lets explore how to make the previous example a closure.

![example-2](http://imgur.com/95YX2FN.png)


![example-3](http://imgur.com/e97f3nf.png)

The `return` keyword always **exits** the function. In this case, the `return` keyword is within the lexical scope of the parent function, `function1`, as a result it ends the whole function. 

## Notice What happens... 

When we remove the `return function2` line. It throws an error.

![example-3.5](http://imgur.com/pb00zWm.png)


## Closure Variations

![example-4](http://imgur.com/wxUij9y.png)


## Example 3

![example3](http://imgur.com/7xAjiXM.png)

Examine the scope, closure section of dev tools. 

![example-dev](http://imgur.com/VTDVEkQ.png)

Lets walk this through step by step.

1. the function `test()` runs and it `returns` another function, in this case just the function definition. Remember whatever comes directly after the `return` keyword is the output of the function, and the function will also exit. So it is literally returning what is after the keyword return:

```
  return function() {
    console.log(value);
  };
```
2. This is why we must do `test()()`. `test()` is just holding the function definition described above. So if its holing a function definition, we must call it with `test()()`. 

3. This is a `closure` because we already exited the function with the `return` keyword using `return function(){console.log(value)}`. But notice how we have access to the parent functions scope variable `value`.  


Here, we just call the function `test()`. Within that functions lexical scope it has `return function()`, thus thats what we get back out of the function. Look below `console.log(value)`. Because `return` exits the function and gives us something back. The anonymous function has access to its parent function and its variables, in this case `value`.  

![example(http://imgur.com/8kJeAgI.png)

![explanation](http://imgur.com/r9LZZh6.png)

====


