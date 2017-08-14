# Callbacks and Closures

## Example 1

![example-1](http://imgur.com/exE3hzk.png)

Example of *nested* functions, but not a closure.

------

## Example 2

Lets explore how to make the previous example a closure.

![example-2](http://imgur.com/95YX2FN.png)


![example-3](http://imgur.com/e97f3nf.png)

The `return` keyword always **exits** the function. In this case, the `return` keyword is within the lexical scope of the parent function, `function1`, as a result it ends the whole function. 

