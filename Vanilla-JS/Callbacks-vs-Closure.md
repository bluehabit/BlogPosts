### Resources

https://medium.com/@odemeulder/i-never-understood-javascript-closures-9663703368e8

# Keys to Understanding Closure

![1key](https://imgur.com/FTIDlr1.png)

Notice here, how calling `function1()` just `returns function2` in this case, its just the function definition. Remember whatever comes after the word `return` is what the output is. 

![2key](https://imgur.com/WL3Bmap.png)

# Higher order functions

This is why functions in javascript are called `higher order functions` as they can be played around as though they are `variables`. The functions in javascript can be passed to another function as a parameter (`callback`), they can be `returned` by another function, they can be assigned to a `variable` using the assignment operator.

# Higher order function examples

### `Higher Order Functions Example 1`:
Passing a function to another function as a parameter, e.g. Callbacks

![example1](http://imgur.com/Qlnf7aR.png)

### `Higher Order Functions Example 2`:
Returning a function from within another function

![example2](http://imgur.com/eacdn88.png)

### `Higher Order Functions Example 3`:
they can be assigned to a variable using the assignment operator

![example3](http://imgur.com/w7CdNta.png)

The variable `sayHi` holds the `function definition`. 

![func-def](http://imgur.com/ZaZ6Y7C.png)

We can call the function and pass parameters to it just like normal.

![func-def2](http://imgur.com/scaKlea.png)

# Welcome to Flavor Town

![flavor-town](http://imgur.com/z6Ia4DD.png)

# Callbacks and Closures

In JavaScript, if you declare a function within another function, then the local variables can remain accessible after returning from the function you called. A function inside another function always creates a closure around variables in the outer scope. However, that closure only outlives the outer scope if the inner function escapes. Remember, when you `return` it exits the function and whatever is at the end of `return` is what the function spits back out. You must **return the function itself** for it to be a closure. Lets take a look at an example:

```
function myCity(cityName){
	var cityName = cityName;
	var state = 'texas';
	return printCity(cityName);
	//NOT a closure, have to return function itself

	function printCity(city){
		return 'I live in ' + city + ' within the state of ' + state; 
	}
}

```

This is not a closure. `return printCity(cityName)` is just calling the function like normal, but you are returning it. In the line `return printCity(cityName)` remember `return` just spits out what comes after it, in this case its just a normal functon call `printCity(cityName)`. If you want to turn this into a closure you would need to **return the function itself**. 

Within the `higherOrder` function you are explicitly passing the parameters (like `houseNum`, `street`, etc.) to the `callback function`.

This is similar to invoking regular functions with arguments/parameters. On the other hand, closures are invoked after their host/parent function is completely executed.

![img](http://imgur.com/biaR05g.png)

## Nested Functions

![nested](http://imgur.com/m3cC7NG.png)

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

![example](http://imgur.com/8kJeAgI.png)

![examples](http://imgur.com/uyUEG9m.png)


------

### Tricky Examples

![trick1](http://imgur.com/HZzMfvq.png)

Can verify using chrome dev tools that a function is actually a closure.

![trick0](http://imgur.com/bA236Pp.png)

------

![img](http://imgur.com/QRZooUH.png)

------

![img](http://imgur.com/YEhO2qt.png)

------

## Example 9

This is also an example of closure.

![img](http://imgur.com/injrehz.png)

![s](http://imgur.com/NyN6aqd.png)

Here `return` exits the function, whatever comes at the end of `return` is what the output of the funciton is. In this case what comes after `return`we have `say` which is just the function definition as we can see below.

![a](http://imgur.com/bUOaiyS.png)

Understand how a reference to a function is returned to a variable `(say2)` in the above code. Note `say` is a variable which holds an `anonymous function` e.g. `function(){console.log(text)}` 

## Example 10

All three global functions have a common reference to the same closure because they are all declared within a single call to `setupSomeGlobals()`.

The three functions have shared access to the same closure — the local variables of `setupSomeGlobals()` when the three functions were defined.

Note that in the above example, if you call `setupSomeGlobals()` again, then a new closure (stack-frame!) is created. The old `logNumber`, `increaseNumber`, `setNumber` variables are overwritten with new functions that have the new closure. (In JavaScript, whenever you declare a function inside another function, the inside function(s) is/are recreated again each time the outside function is called.)

The closure is the function itself wrapping up all the variables available in its scope and taking them with them. Returning a function as you describe is called a high order function.
this example you give does technically take advantage of a closure

------

## Example 11

![1](http://imgur.com/jKzPeGP.png)

![2](http://imgur.com/FYOokgA.png)

------

## Private Variables

In other languages there exists support for variables that cannot be modified externally, we call those private variables, but in JavaScript we don't have that built in, so we use closures to replicate this.

Here executing the function `counter` will `return` what comes after it, in this case an `anonymous function` that has the following `function(){return ++count;})`. When you run `counter()` it is just returning another functions definition (`closure`). The parent function has already `exited / returned` but we can still access the local variable of the parents scope which is `count`. 

![example1](http://imgur.com/TMKjRFb.png)

We can continue to use this closure to increment the private variable `count`. By using `counter1()`. 

![example2](http://imgur.com/XTsUm9j.png)

## Private Variables 2

![example3](http://imgur.com/Pm9Kvzj.png)

If you define variables without var, let, const they are put in the global scope which is important for reasons we will outline below.

`setUpGlobalVariable()` //this runs the function which has the variables `gPet` and `gChangePetName` declared WITHOUT the `var` keyword thus putting them in the `global` context

notice how if we try to access the variable pet without using closure it throws an error

the variable `pet` is scoped and set to `luna` and can only be accessed or modified via `closure`. 

#### Key Resource

How do closures work? https://stackoverflow.com/questions/111102/how-do-javascript-closures-work

Lexical Scope https://stackoverflow.com/questions/1047454/what-is-lexical-scope 

![key3](http://imgur.com/z7vPUtP.png)

![key4](http://imgur.com/xFpCTXF.png)

![crit](http://imgur.com/QLP1PGb.png)

![st-pepsi](http://imgur.com/sRtZLKa.png)


