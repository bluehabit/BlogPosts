# Table of Contents
1. [Operators & Truthy Falsy Values](#operators)
   * [Unary](#unary-operator)
   * [Logical](#logical)
2. [Arrays](#arrays)
   * [Array of Objects](#array-of-objects)
   * [Reduce](#reduce)
   * [Filter](#filter)
   * [Combining Filter & Reduce](#combining-filter-and-reduce)
   * [Map](#map)
3. [Objects](#object)
   * [New Keyword](#the-`new`-keyword)
   * Object Literal
   * [Classes using Object Constructors](#classes-using-object-constructors)
   * [Prototype and the Prototype Chain](#prototype-and-the-prototype-chain)
   * [Nested Objects](#nested-objects)
   * ['This'](#the-keyword-this)
   * [Call](#call)
   * [Apply](#apply)
   * [Bind](#bind)
4. [Function Basics](#functions) 
   * [Parameters](#parameters)
   * [Function Expressions](#function-expressions)
   * [Return KW and Routing](#the-return-keyword-and-routing-functions)
5. [Callbacks](#callbacks-in-detail)
   * [Named vs Anonymous](#callbacks-can-be-named-or-anonymous)
5. [Closures](#closure-in-detail)
   * [Private](#why-private-variables)
   * [Parameter Closure](#parameter-closure) 
   * [Function Closure](#function-closure)
   * [Scopes and Instances](#scopes-and-instances)

# External Blog Posts2
(for example async blog post that you wrote)

![divider-bar](https://imgur.com/wbdDPMR.png)


# Operators

### Falsy Values

`false`, `null`, `undefined`, `0`, `NaN`, `''`, `""`

### Unary Operator

Can convert string values to numbers by using the `+` unary operator.

![f](https://imgur.com/PHCbRZF.png)

Can also use the `Number` function

![f](https://imgur.com/XsL2PMW.png)

And a practical application using a regex expression to parse a string representation of date into a number in milliseconds in epoch time. We can convert the epoch time into a `new Date`. 

![f](https://imgur.com/sWUA51r.png)

### Logical
Why does this work? Pay special attention to the line `(obj[currentValue] || 0)`

![f](https://imgur.com/2J3ny1t.png)

Explanation:

![f](https://imgur.com/hBXV9sb.png)

With the `||` operator the first *truthy* value.  If both values are falsy, it will return the last item. 

![f](https://imgur.com/l3AcQGG.png)

![f](https://imgur.com/nPw25ah.png)

![f](https://imgur.com/zIY8gFV.png)

![f](https://imgur.com/99ixexZ.png)

In traditional programming, operators such as && and || returned a boolean value (true or false). This is not the case in javascript. Here it returns the actual object, not a true / false. To really explain this, I first have to explain what is truthy and what is falsy.

The logical OR operator, `||`, is very simple after you understand what it is doing. If the first object is truthy, that gets returned. Otherwise, the second object gets returned.

### Logical AND, &&

The logical AND operator, &&, works similarly. If the first object is falsy, it returns that object. If it is truthy, it returns the second object.

![f](https://imgur.com/qjdqhDL.png)

### Logical NOT, !

Unlike && and ||, the ! operator DOES turn the value it receives into a boolean. If it receives a truthy value, it returns false, and if it receives a falsy value, it returns true.

`read more here:` http://www.nfriedly.com/techblog/2009/07/advanced-javascript-operators-and-truthy-falsy/

`more` https://medium.com/@joshpitzalis/the-trouble-with-loops-f639e3cc52d9

`more` https://medium.freecodecamp.org/reduce-f47a7da511a9

Here is an explanation of what is going on.

![f](https://imgur.com/3ZsoSZ7.png)



### Ternary Operator

Can help make our code more concise and possibly eliminate the need for an `if` `else` block.

Before:

![f](https://imgur.com/zyOAYMx.png)

After: 

![f](https://imgur.com/iWUjmaY.png)

Output:

![f](https://imgur.com/2epLRvX.png)

More examples:

![f](https://imgur.com/yEmhCfP.png)

![f](https://imgur.com/E7SRIjM.png)

![f](https://imgur.com/WJPYX2P.png)

![f](https://imgur.com/Tit56Ne.png)

![divider-bar](https://imgur.com/wbdDPMR.png)

### Increment Values

In addition to using `++` or `--` to increment. You can also use another `variable` to increment by. 

![f](https://imgur.com/JXNGUns.png)

# For Loops

![f](https://imgur.com/JNFrDMq.png)


# Arrays

Individual items within an array are known as `elements` or array elements.

### Removing Items from an Array

![f](https://imgur.com/avU9nKy.png)

### Using splice()

![f](https://imgur.com/pXe7d7u.png)

![f](https://imgur.com/yvStkgs.png)

### Array of Objects

![f](https://imgur.com/8f40um2.png)

## Functional Programming Array: `forEach`, `Map`, `Reduce`, `Filter`

### Protip! All of these array methods, iterate through EVERY SINGLE ARRAY ITEM

Remember these are all ARRAY methods, therefore you want an array to use these. The input could strictly be an array, or it could be an array that's part of an object etc.

Please note, when using these array methods, they are callbacks so you must `return` something or the function will not work correctly. 

Relying on loops can become a problem because loops are synchronous. This means that they can only manipulate data that already exists. You run into problems when you have to deal with asynchronous data, like events that have not happened yet.

Asynchronous programming is much easier than it sounds. You can build a lot of asynchronous programs by using the Map, Reduce and Filter methods.

We are using the following dataset for these exercises

![f](https://imgur.com/mhAhFjz.png)

### `Reduce`

**Use it when:** You want a total based on values in an array.
 The default name for the first parameter is `accumulator` according to the documentation. However, I prefer using something that is more descriptive so I know how its being used. For example, if I am reducing to an array, I will use `array` as the parameter name, `object` if object and so forth as shown below. 

When using reduce, you must always `return` the `total` parameter. 

#### How `reduce` works

The `accumulator` parameter, named `total` below, does not accumulate on its own. You must add the `currentValue` to track correctly.

A simple `reduce` to get the sum total of numbers in an array.

![f](https://imgur.com/wSdC6AH.png)

I prefer to write the above code like this instead.

![f](https://imgur.com/OWY6xH8.png)

Lets log it to the console to make it more obvious

![f](https://imgur.com/Gqj3zPX.png)

Now, lets try to `reduce` without adding `currentValue` progressively to `total`. 

![f](https://imgur.com/bpqB4RE.png)


#### Reduce for finding Average

First lets look at this example that just returns the last item in an array.

![f](https://imgur.com/t2xvur0.png)

Next lets expand on the code a code a bit so it returns the average.

![f](https://imgur.com/dnRZqRJ.png)

We can refactor this code by using the `index` parameter.

![f](https://imgur.com/Ve2N9uH.png)

#### Another Example Average Using `reduce()`

![f](https://imgur.com/i93gbcO.png)


### Doubling Array Values

https://imgur.com/AI6bmMB

----

Short hand:

![f](https://imgur.com/nBVmif4.png)

Long Hand:


Reduce returning an object, special note. We can do the syntax a few different ways.

Longer method:

![f](https://imgur.com/5zXIXCR.png)

Shorter method: 

![f](https://imgur.com/BGpMRhu.png) 

## `Filter`

**Use it when**: You want to remove unwanted values from an array.

![f](https://imgur.com/XcOc688.png)

### Combining Filter and Reduce

For the more *simple* examples, it would make more sense to use map or filter because they are simpler to use. The benefit of using reduce comes into play when you want to map and filter together and you have a lot of data to go over.

If you chain map and filter together you are doing the work twice. You filter every single value and then you map the remaining values. With reduce you can filter and then map in a single pass.

![f](https://imgur.com/jjcayxO.png)


### More examples combining Filter and Reduce

Before we go into this next set of examples, lets look at the behavior of `forEach` and how we use it on objects that contain arrays as properties.

![f](https://imgur.com/UuPEj01.png)

and

![f](https://imgur.com/M6KfrWi.png)

An easier way to write the above `forEach` loop would be written like this in my opinion, compared to what the original blog post author wrote.]

![f](https://imgur.com/QFFORgR.png)

We can build on this logic to make it a bit more advanced, this will return an array that contains all the colors. 

![f](https://imgur.com/KLFDGi5.png)

Here is another example of using `reduce` with our own filter method inside. Again, we can use `filter` and `reduce` separately, and that works fine for small data sets. But once we start working with large amounts of data its more performance efficient to combine them.

![f](https://imgur.com/O5gy8Xs.png)

Here is the explanation simplified, 

![f](https://imgur.com/dAx6kF5.png)

### Even more Examples Combining Filter and Reduce

![f](https://imgur.com/l8YxT1e.png)

And another example

![f](https://imgur.com/I5cbeX0.png)

another

![f](https://imgur.com/ke5wFbg.png)

Here is a more elegant solution for the above code snippet. Keeping our code more dry by creating a variable `doubleNumber` which stores the results of `currentNumber *2`.
--

Notice, when using `reduce` or `filter` we `return` something for each item in the array. We can do this with `forEach` loops as well

![f](https://imgur.com/4gff8IP.png)


![f](https://imgur.com/A9gcv01.png)
  
### Keep this in mind with Reduce

![f](https://imgur.com/bwQ2Wa4.png)

and some more reduce pro tips

![f](https://imgur.com/gdWESs0.png)

## `Map`

**Use it when**: You want to modify all values in an array to another set of values.

![f](https://imgur.com/UPUFDEM.png)


### Secondary Functional Programming Methods `Sort`, `Some`, `Every`, `Find`, `FindIndex`

These secondary functional programming methods are not used as much as the primary ones (`reduce`, `map` etc.) but they are still worth learning about.


### Nice refactor

![f](https://imgur.com/sVcPe53.png)

Nice

![f](https://imgur.com/C6ZwEM3.png)

Nice

![f](https://imgur.com/ly80zaa.png)

![divider-bar](https://imgur.com/wbdDPMR.png)

# Objects

## Object, Array, String Literals vs Constructor Function

In javascript, mostly everything is an object from arrays to strings. Because of this we can use either a constructor function or a literal to create them.

In most situations, it is most beneficial to create an item using the literal notation. But in some situations it is highly beneficial to use the a constructor function. One such example is [creating object classes with constructor functions](#Classes-using-Object-Constructors). 

To get started creating with a constructor function we use the `new` keyword. For example `new Object`, `new Array` or `new String`. The value of `this` changes when we use the `new` keyword to represent the object that was just created.

## Object Functions / methods

Notice the color changes to green for object **methods** as opposed to properties. A method is a function of the object, some sort of action. Notice in the below example `parrot.yell` is a method on the parrot object that executes a function.

![f](https://imgur.com/mGJ8vhu.png)


## The `new` keyword

When the `new` keyword is used, a new object is created out of thin air. And inside the function definition the keyword `this` refers to the new object that was just created.

![f](https://imgur.com/kpSNs5N.png)

* creates a new object out of thin air
* sets value of the keyword `this` inside the function to be the object created
* adds the line `return this` to the end of the function
* adds a property on to the object called `__proto__` which links the 
*  property on the constructor function to the empty object

In this modified example we push the `new` objects to an array. This is an array of objects. Using an array of objects is very powerful, because it allows us to use array properties and methods to move through our list of objects. For example having an array of objects of green pipes for a Mario game or Flappy Bird

In this example we use a the `forEach` method to loop over every item within the array.

Also note, each object created using a `class` (discussed later) or using the constructor function has the `__proto___` property added which links that object to the constructor function that created it.

![f](https://imgur.com/tUUe66a.png)

![f](https://imgur.com/qWDNuJl.png)

![f](https://imgur.com/1M5aYl7.png)

![f](https://imgur.com/0DtUNo7.png)

![f](https://imgur.com/edbnyIS.png)

### Very Important

![f](https://imgur.com/EsMLNGE.png)

![f](https://imgur.com/cONHiez.png)

![f](https://imgur.com/xk38wTW.png)

![f](https://imgur.com/Lozj1cS.png)

### Object

#### Constructor Function

![obj-constructor](https://imgur.com/fUG2gaR.png)

![f](https://imgur.com/EUSmXy5.png)

#### Literal

![obj-literal](https://imgur.com/1LiEz3j.png)

### Array

#### Constructor Function

`var myArr = new Array; //-> []`

#### Literal

`var myArray = [0,1,2,3]`


### String

#### Literal

`var myDog = 'Spot'` 

#### Constructor Function

```
var myDog = new String('Spot')
//String {0: "S", 1: "p", 2: "o", 3: "t", length: 4, [[PrimitiveValue]]: "Spot"}
```

## Classes using Object Constructors

To utilize classes/constructor functions we must do two things. 1) create a constructor function 2) push new items created from the constructor function to an array of objects.

![f](https://imgur.com/9GgSS6L.png)

Using the object constructor we can create what are known as classes. Constructor functions will create instances of the object. It is customary to capitalize the first letter of the variable name to indicate it is a class. Note, in the example below the object constructor function is embedded within another object, `Parrot`. Notice that `Parrot` has the first letter capitalized to indicate it is a constructor function. 

## Mission Critical on Classes

![f](https://imgur.com/s2cvC2R.png)

![constructor1](https://imgur.com/i6DT4ki.png)

## ES2015 Classes

![f](https://imgur.com/EUSmXy5.png)

![f](https://imgur.com/yKepDkw.png)

![f](https://imgur.com/vJ80nYC.png)

![f](https://imgur.com/a4Azp6t.png)


## Constructor Pattern Continued

A constructor function is a single object that we can use as a base to create more objects that are similar. Think of it like a cloning machine. We can replicate as many copies as we would like of a given object, and each copy is its own separate instance. 

Here is an example in Javascript:

![constructor2](https://imgur.com/AxlLuAg.png)

In the example above we create a constructor function and give it four properties, by using the `this` keyword we are binding or assigning those properties to the instance of `Bullet`.

**Note**: By convention and best practice in Javascript, you should start all constructor functions with a capital letter.

As we can see we are even able to assign functions as properties on our constructor. We then create two new instances of the Bullet Class, bullet1 and bullet2. In Javascript we can use the “new” keyword to create new instances of the class object. You also might notice that we are able to pass in arguments on the fly, this makes it so not all of our instances have to be exactly the same.

Once we create the instance of our class we can then call any of the methods that are on the object. In the example above we call the location method on our object and get back a console log of our coordinates.

There is just one problem with our constructor function above, when you place a function inside of a constructor it recreates that function over and over every instance that gets created. As you can imagine, if you had thousands of instances, this could become a pretty big problem (speed and optimization). Thankfully Javascript has a solution for this problem.

We can use the prototype, this will create only 1 function, no matter how many instances you create. The function is set aside in a little box (figuratively speaking) and can be used by all of the instances when needed.

An example of how the prototype can help us optimize our previous code:

![constructor3](https://imgur.com/wVlNk0j.png)

Its pretty easy to use the prototype in Javascript but is still considered on of the more complicated parts of the language that most people don’t know much about. Using the prototype can be a good way to show off your Javascript knowledge, but also improves the performance of your code by a handful.

## Why the Constructor Pattern?

Imagine we wanted to make a few house objects, each house will have a bedroom, bathroom, and a sqFt. 

![f](https://imgur.com/bpivtAq.png)

What if we had to create, 50, 100 or more of these house objects! That would be crazy.

Instead we can use a constructor function to create instances of that object. The constructor function serves as a blue print to stamp out as many instances as required. 

![f](https://imgur.com/JJ20xXU.png)

## Constructor Function Refactors

Here we have two constructor functions, notice they share many similar properties. Only one property will be different `numWheels`. 

![f](https://imgur.com/ok3vZrT.png)

We can refactor this to DRY up our code. 

![f](https://imgur.com/Ieu8D5P.png)

We can even refactor this further using apply. 

![f](https://imgur.com/oZ2qvuQ.png)

Quick overview of the `arguments` keyword if you are not familiar with it

![f](https://imgur.com/nNltvw7.png)

## Classes and more Constructor Function Examples

![f](https://imgur.com/zD1O24m.png)

![f](https://imgur.com/qjV0m5u.png)

![f](https://imgur.com/9JI863V.png)

## Prototype and The Prototype Chain

`Object prototype property`- is an object that can have methods and properties placed on it, these properties and methods are shared among all objects when the new keyword is used to create an object from the constructor function.

![f](https://imgur.com/CgaokOG.png)

Here we see, for `lucas` and `el` under `__proto__` both instances came from the `constructor: Person`

![f](https://imgur.com/rrAk9ze.png)

These objects created from the constructor function have a *dynamic* link between them and the original constructor function. Any properties or methods that are added to the original constructor function are automatically shared with objects it creates! A dynamic link. This is called the `prototype chain`. Check out an example below, we add a new property to the `Person` constructor function and it is automatically added to instances of that object.

![f](https://imgur.com/IDopzoc.png)

This happens with everything in javascript, behind the scenes new objects are being created as instances using the `new` keyword. Check it out.

![f](https://imgur.com/UXdWILE.png)


![f](https://imgur.com/GQ3HJK4.png)

Lets look at a useful way to use the `prototype chain` to make our programming more efficient. 

![f](https://imgur.com/LXuuZir.png)

Another Example

![f](https://imgur.com/YF1DcLM.png)

Another Example

![f](https://imgur.com/hNuUgJq.png)


## Nested Objects

Object properties can hold many different values, from arrays to function to other objects as you can see below. 

![f](https://imgur.com/72Hey7D.png)

## The Keyword `this` 

The keyword this is determined by the *context* in which it was called. There are a few rules to keep in mind when determining the value of the keyword `this`.

1. global
2. object / implicit
3. explicit
4. new keyword

## Global Rule

When we see the keyword `this` in the global context, its value refers to the global object, which in the browser environment refers to the window object.

When the value of `this` is just floating around within the global scope its in the wild. In comparison to declaring the keyword `this` inside an object

![f](https://imgur.com/6L9o7Ao.png)

![f](https://imgur.com/eVsQHuu.png)

## Object Rule (implicit)

When the keyword `this` is found inside a declared object, the value of the keyword `this` will always be the closest parent object

![f](https://imgur.com/LMqlQ54.png)

Nested Object Example:

![f](https://imgur.com/BuVNBw4.png)

#### Another Example

![f](https://imgur.com/gyTvOkZ.png)

Within `person.dog.sayHello` the value of `this` is looking to the *closest parent object* which in this case is dog. What if we wanted our `sayHello` method to return `'hello chris'` instead of `'hello undefined'` we would need some way of explicitly changing the value of the keyword this. And that is where we will introduce binding the keyword `this` using `call, apply` and `bind`

## Call

Arguments are passed as **comma separated values**.

![f](https://imgur.com/awpurKh.png)

Lets take a look at another example, we will refactor the code to make it more DRY using `call`. 

Here we have two functions that do the same thing on both objects. `sayHi`. Lets refactor a bit.

![f](https://imgur.com/9ExJgT1.png)

Now, lets refactor. We will use `call` to change the value of the object the keyword `this` refers to.

![f](https://imgur.com/zigFXf2.png)


## Apply

Arguments are passed as an **array**

Almost identical to `call`. We only start to see a difference when we start to add arguments. 

`apply` works like `call`, only we can pass through an array as an argument. In the case of apply we pass all the arguments as values in an array. So instead of comma separated arguments, we just put them in an array. 

![f](https://imgur.com/R4V9ARP.png)


## Bind


`bind` works just like `call`, but instead of calling the function right away it returns a function definition. With the keyword this set to the value of the `thisArg`.

A common use case is when you do not know how many arguments are going to be passed to a function. 

When you dont know all the arguments that will be passed to a function its common to use bind. We dont call it right away, instead we bind it with some of the parameters set we call this partial application. Again whats neat about bind, is we dont need to know all the parameters to the function when we bind it, only need to know the `thisArg` the value of what we want the keyword this to be

![f](https://imgur.com/LR4Pznu.png)

![divider-bar](https://imgur.com/wbdDPMR.png)

# Functions

Function help keep our code DRY, instead of having to write the same code over and over again. 

I like to think of functions as a factory. After all the processes within the factory complete, there will be some form of final output.

 Lets take for an example an ice cream factory. The ultimate job of the factory is to output ice cream, but before the ice cream can be made you must complete a few steps within the ice cream factory. First you must blend the ice cream mixture, pasteurize the mix, add liquid flavors and colors, freeze, add finish with the addition of fruit nuts and other toppings. And finally you package it up and have your final output, ice cream ready for distribution. 

![icecream](http://imgur.com/Iue6zw4.png)

In the case of Javascript the function will `return` something that you can use for later. Just like factories in real life, it is recommended that your functions specialize in performing a particular action.


## Parameters

Functions can also accept one or more inputs, they can do this through parameters. I like to think of parameters just like regular variables in JS. Just like variables,  a parameter acts as a placeholder for a value. You can also have functions that have no parameters as well, as shown in our example below.

![f](https://imgur.com/LkL5tVh.png)

For a simple example of a function with a parameter, here is a function named `add` that will add two numbers together. It accepts two parameters `number1` and `number2`. When we call the function using `add(1,3)` we are passing the value `1` to the parameter `number1`, and passing the value `3` to `number2`. The function stores these values for us, just like a variable. 

![functions](https://imgur.com/wsX86yJ.png)

### Arguments as Automatically Declared Variables

![f](https://imgur.com/tyaI5Bt.png)

Whenever a function receives an argument, just consider it to be an automatically declared variable.



### Functions are Reusable 

And we can **reuse** that same function again, and again and again and pass new numbers through as parameters, by simply calling the function and passing in new values as shown below. Just like an ice cream factory that continues to produce ice cream. This prevents us from having to repeat our code over and over.

![func1](https://imgur.com/vOqFmtk.png)

### Accessing Arguments from a Parameter

![f](https://imgur.com/rNZbK9X.png)

### Function Expressions
Functions can also be assigned to a variable using the assignment operator. This is known as a function expression, something that makes functions in JS a first class object (we will discuss this in more detail later).

Also note, if you use a function expression, the variable containing the function must be declared before you attempt to call the function as the below example shows.

![f](https://imgur.com/Wh8jUeV.png)

![func2](https://imgur.com/3uaFCBV.png)

![f](https://imgur.com/ZYRlASz.png)


Here is another example of a function with parameters using strings. This is a simple function that will log something to the console. In this case our function `printString` will console.log to the console. 

![func3](https://imgur.com/oolZxdk.png)

We have a function called `printString` here that has a parameter named `string`. It will hold the value of the variable `myString`. 

`printString(myString)` calls the function and passes through the value of `(myString)` as the parameter. As a result it will `console.log` `Hello there` to the console. 

The parameter `string` is holding the value of a string itself, therefore we have access to different string properties and methods such as `length`.

![func4](https://imgur.com/5ibJf6X.png)

In this case the parameter `string` is once again holding the value of `myString`. When it gets passed through the function it is checking the parameter `string.length`, so it gives us the length of `Hello There` which is 11. 

Parameter names are also arbitrary just like variables, they can be named whatever you would like. See the below example where I replaced the parameter name with something ridiculous, in this case `pinkDinosaur`. 

![func5](https://imgur.com/QNeNMTJ.png)

Another Example

![f](https://imgur.com/b5nGhaX.png)


## The Return Keyword and Routing Functions

Lets look at another example, with the function `numFactory`. This simple function just takes a users `num` as a parameter and increments it by one using `num ++`. But before it does that, it checks the `typeof` user input to verify that it is indeed a number. The end output is the users number incremented by one, that is what is `returned` as the output of the function. Just like the ice cream from the factory example. 

Whenever javascript sees the `return` function within a function it will automatically exit the function so keep that in mind. Because of this we can use `return` to route and determine the output paths of our function. In the example below *if the users number is `typeof` number* then we will exit the function and `return num++`. Otherwise, if the user input is not a number we will exit the function and `return` 'please enter a number'. 

Note, whatever comes *after* the keyword `return` is returned. This could be a number, a variable, a function call with a parameter etc. *Everything* you see after the keyword `return` will be the output of that function.

![numFactory](https://imgur.com/2YweOOn.png)

## Anonymous Self Invoking Functions

We can also have `anonymous functions` that do not have a name declared. In the example below, we have a self invoking self invoking anonymous function.

![f](https://imgur.com/ybb3Wrg.png)

## In Javascript Functions are First Class *Objects*

In Javascript functions can be played around with as if they were variables in several different ways. 

First class in simple terms means  *“being able to do what everyone else can do.”* **Functions can be assigned to variables, they can be passed around as arguments (`callback functions`). They can even be assigned as the return values of other functions (`closure`)**. Below we will quickly overview how functions are first class objects, and we will discuss each one in further detail later.

### Function calls inside `if` statements

![f](https://imgur.com/UH7hA6C.png)

### Callbacks

![f](https://imgur.com/b8zUDxZ.png)

![f](https://imgur.com/fseNSQy.png)

1) Functions in Javascript can be passed to another function as a parameter, known as a `callback`, to other functions. The function that accepts another function as a parameter is known as the `higher order function`. The `callback` is then "called back" within the higher order function itself. 

Anonymous inline function

![f2](https://imgur.com/n0H0R8N.png)

Named callback function

![f](https://imgur.com/Tmw9Yty.png)


### Closure

2) Functions can be `returned` by another function. This is known as `closure`. This also lets us create `private variables` in JS, a concept we will explore in more detail later.

![f3](https://imgur.com/wXpuE6F.png)

### Functions Assigned to Variables
### AKA Function Expressions

3) Functions can also be assigned to a `variable` using the assignment operator. This is known as a `function expression`. 

![f4](https://imgur.com/vFxGhBk.png)

We can call the function and pass parameters to it just like normal.

![f](https://imgur.com/mLf0rP5.png)

Notice the variable `sayHi` holds the value of a `function definition`. 

![f](https://imgur.com/WXl2xeM.png)

Also note, if you use a function expression, the variable containing the function must be declared before you attempt to call the function as the below example shows.

![f](https://imgur.com/Wh8jUeV.png)

## Functions Advanced 

### Nested Functions
Functions can also be nested within one another, as shown below. This example uses `closure`, don't stress over it too much if its confusing at this point in time, you will learn more about it later in the chapters. 

![f1](https://imgur.com/eJ5nqUM.png)

![divider-bar](https://imgur.com/wbdDPMR.png)

## Callbacks in Detail

![f](https://imgur.com/eZ9HX1s.png)

With that behind and our understanding how `callbacks` are an example of how functions are first class in javascript,  lets go more in depth on how `callbacks` work and work through additional examples. The function that accepts another function as a parameter is known as the higher order function. 

## Callbacks, a Visual Representation 

![f](https://imgur.com/RNcXVOv.png)

## Callbacks can be `Named` or `Anonymous`

With callbacks we can design them to be named, or anonymous. Both of these function examples will have he same output.

**Named Callback Function**

![callback1](https://imgur.com/3dqZ8bO.png)

**Anonymous Inline Callback Function**

![callback2](https://imgur.com/NM8JlRw.png)

Notice how the function is *'called back'* within the higher order function. 

### Anonymous Inline Functions should Clue you In that a Callback Function is being used

Anytime you see an `anonymous` function inline that is a clue to you that a `callback` is being used. See the portion of the images outlined in red. The part highlighted is an `anonymous inline function` a big clue that a callback function is being utilized.

Lets take a look at a few examples of `anonymous inline functions`

![example-1](http://imgur.com/trkBk6E.png)

In our first example above, this should look familiar its our own callback function we built in an earlier example. 

![example-2](http://imgur.com/t98z1AT.png)

These last two examples using `setTimeout` and `addEventListener` are using built in functions. We can see both functions use inline anonymous functions as callbacks. 

if we visit the MDN page of `setTimeout` we can see more details on the various parameters included with each built in function. 

![mdn](http://imgur.com/atPIg9q.png)


Notice how the `setTimeout` function has built in parameters to use. You can see the parameters and what they do on the MDN page under `parameters`. 

Notice the first parameter, `function` (highlighted in red) accepts a function that will execute after a certain amount of time expires. In the case of our example, it will `console.log("inside the callback")`.

The second parameter, `delay` (highlighted in blue) uses time in milliseconds that will add a delay until the function is called. 

Using built in functions like `addEventListener` and `setTimeOut` are common examples of `callbacks` you will encounter *"in the wild"*.  

![example-3](http://imgur.com/c1DpFN4.png)


Another example of an inline anonymous callback function. Notice the pattern? See how the parameter is holding the anonymous function `function(){console.log('you clicked my button!');}` More of these examples will make sense once you complete the `Document Object Model` chapters where you will get regular practice using these.

## Key Callback Example

Key illustration here, notice how the callback function itself can have its own parameters since it is a function itself.The callback itself is also a function, and it has its own parameters `errMessage` and `resultObj` 

![f](https://imgur.com/AdufGNw.png)

## Designing Callback Functions

### Custom forEach Function

When designing callback functions, they typically do one thing. For example below we create our own version of a `forEach` using a callback. All it does is iterate through an array and implement a callback on it. 

Inside the callback, that's where we define what happens next. In this case for each array item, we are getting `string.length`. 

![f](https://imgur.com/1v17OBi.png)

As we loop through the array, the callback parameter `arrayItem` will hold the value `array[i]`, when looped through using `stringArr`, it will hold the value of `array[0]`, `array[1]` and `array[2]`

![f](https://imgur.com/YTAztTL.png)

### Custom Filter Function


![f](https://imgur.com/8q7tapD.png)


We can refactor the `if` statement to be a bit shorter and just write it like this.

![f](https://imgur.com/LYbo0ao.png)

### Custom Filter Function (more advanced)

This variant is slightly more advanced, it uses the `Array.isArray()` method to verify the input is indeed an array. 

![f](https://imgur.com/jeO68wS.png)

## More Callback Examples

Callback Filtering out Odd Numbers

![f](https://imgur.com/LcvEr3x.png)


Callback Example

![f](https://imgur.com/IHBiAox.png)

## More Callback goodness

![f](https://imgur.com/CWi8V1X.png)

Lets translate this. The higher order function receives another function as an argument, this is known ad the callback function. At some point the callback function is executed within the containing function (higher order function). The callback has access to variables normally outside of its own scope. In this example the callback function `printCity` has access to the `city` variable since it was defined within the higher order functions scope. 

Normally `printCity` does not have access to such a variable.

## Parameters All Sorts of Values

Callback function holding an object as the parameter

![f](https://imgur.com/Ye4iApj.png)


Callback function holding an array as the parameter

![f](https://imgur.com/AnaoaGT.png)

## New Callback

A callback is simply a function that  gets passed to another function (called the higher order function)as a parameter. When the callback is passed to the higher order function it is stored as a function definition, and is not executed until the callback function is called. When building a callback function it is customary to put the callback in as the last parameter.

Anonymous Callback Function

![f](https://imgur.com/9JIV1gw.png)

Named callback function

![f](https://imgur.com/mlzISu4.png)

### Stepping through a Callback

![f](https://imgur.com/JRTFkyD.png)

![f](https://imgur.com/zdHWp2p.png)

![f](https://imgur.com/52TjY3x.png)

## Alternative Callback Explanation

![f](https://imgur.com/Uw9F3wM.png)

Here we have a higher order function `filter` which accepts a callback as an argument.

Remember whenever a function receives an argument, just consider it to be an automatically declared variable within that functions context. In our case, the parameter `callback` is a automatically declared variable. We pass through the value of a `function definition`. 

![f](https://imgur.com/LJokZgA.png)

The parameter `callback` is holding the value of a `function definition`. Just like a normal function we must call it with `()` to activate it.

![f](https://imgur.com/cZBZVfU.png)

When we call `callback` with (), inbetween the paranthesis we pass through our arguments array[i], i, array.

Another example:

![f](https://imgur.com/BAwXGmF.png)

![divider-bar](https://imgur.com/wbdDPMR.png)

# Closure in Detail

For a function to be considered a closure, you must return the function *itself*.

In other words you must exit the parent function by using the return keyword. Even though the function has already returned another function, we still have access to the parent functions variables and parameters.  Remember whatever comes after the `return` keyword is returned, along with exiting the function. In this case the `return` keyword is returning a *whole* **function definition**. 

### Closure Example

Here we have a function `counter` with a local variable `count`. 

When we call the function `counter()` it will `return` and exit the function. Remember, whatever comes after the keyword `return` is returned. In this case it is the entire function definition:

```
return function(){
	return ++count;
}
```

`count` is an example of a `private variable`, because we can only access it through its closure. IT does not exist in the global scope. You might say the variable `count` is scoped to the function `counter`. 

![f](https://imgur.com/AEovlqB.png)

We will save the function call `counter()` to a variable `counter1`. That way when we call `counter1` it executes the function that increases the count with `return ++count`. Recall, `count` does not exist in this functions scope, rather it exists within its parents functions scope even though it as already exited, this is known as `closure`.


![f](https://imgur.com/71ysAxe.png)

We can continue to use this closure to increment the private variable count. By using `counter1()`.

![f](https://imgur.com/oYu4jf2.png)


 You might hear the term `local scope`, `lexical environment` but don't let that confuse you it just refers the `functions scope`. A scope is everything the function has access to. Closures have access to not only their own variables, but variables and parameters (remember parameters can contain anything from objects, arrays, strings to other functions) that are defined within the parent function. 


Any nested function has the *potential* to be a closure, if the function itself is returned. 

## Whats NOT a Closure

At first this example may appear to look like a closure, but it's not, lets explore why. 

![f](https://imgur.com/nCUYHXb.png)

`testAB` has the potential but it is not a closure, since it is not being returned. Closures are functions which exist outside of their parent scope by means of returning them and making them available even after the outer function is completely executed. This is not an example of a closure, because you aren't returning the `testAB` function itself, but you are returning the value returned by `testAB` function. 


### Example 1

I found a really ugly example of a code snippet on stack overflow that nonsensically creates global variables inside of a functions local scope, nonetheless I think it is a good example for further learning.

![f](https://imgur.com/OjYNN75.png)

If you define variables without var, let, const they are put in the global scope which is important for reasons we will outline below.

`setUpGlobalVariable()` this runs the function which has the variables `gPet` and `gChangePetName` declared WITHOUT the `var` keyword thus putting them in the global context.

notice how if we try to access the variable pet without using closure it throws an error. the variable pet is scoped and set to luna and can only be accessed or modified via closure

 ![f](https://imgur.com/iujSns0.png)


All examples above represent only first-order functions. You can even go higher and you may find yourself with some clever code where a callback is "returned" in a from the executing function in a way that it becomes a "closure" and is executed after the executing function is completed.


## Why Private Variables

Private variable is used when you don't want it be exposed and accessible outside of its own relevant functions. i.e. protected. IOTW, private variable is not supposed to be accessed from outside context. If you want to be able to modify it, you'll have to provide the required function from the proper context. Just like you did in the returned function in your example code.


### Accessing Private Variables

![f](https://imgur.com/UmG0ZUn.png)

Initially, this may not appear to be a closure because we are not returning a function. No matter, anytime you `return` and exit the parent function, and are able to access the parent functions scope still - it is closure. We can verify with Chrom Dev Tools.

![f](https://imgur.com/FbUpJKk.png)

### Parameter Closure

For closure to occur it does not have to be a function definition that is returned. In addition to functions, it can also be a functions parameter, or even another function if we save it to a variable. 

![f](https://imgur.com/sK4UKXn.png)

![f](https://imgur.com/48x4h73.png)

Verifying we have closure in Chrome Dev Tools. 

![f](https://imgur.com/H7G2jbo.png)

### Function Closure

![f](https://imgur.com/c2HMiNg.png)

![f](https://imgur.com/FDgkmmp.png)

Verifying we have closure in Chrome Dev Tools

![f](https://imgur.com/J2cz13l.png)

Another Example

![f](https://imgur.com/FeBQOmi.png)

## Callbacks are Closure?

![f](https://imgur.com/6POlvXl.png)

## Advanced Closure

The reason we have to rely on closure for these examples is because the the function is instantiated for every key, so `id` never changes.  In other words the variable is within the scope of the function and will remain the same every time.

Same situation with the `forEach` loop we will use closure to solve this as well. Same story, function is instantiated every time through, so the value of `id` will never change.

The standard fix for that is to use a closure, like we will in this example, or simply stick the used var in a higher scope. For example the global scope. 


![f](https://imgur.com/xIPHP1k.png)

This is the named function example, we will look at this with an anonymous function in a moment. First Lets break this down, the `var addIncreasingIdFromZero` holds the function call `makeAddIncreasingIdFn(0)` passing the value `0` for the `id` parameter. 

Because this function immediately returns, the value of `addIncreasingIdFromZero` is the function definition itself that was returned. As shown below:

![f](https://imgur.com/Fq8Kxct.png)

Because of `return` we are exiting the parent function scope. But this has created a `closure` We still have access to the parameter `id` even though the function has already returned.



This example behaves the same way, only we are now using an anonymous function for the callback. 

![f](https://imgur.com/b6XQ9LH.png)

It may look a bit confusing, but its not too bad lets step through. Here we have an anonymous callback function `function(id)` which we immediately return with another function just like our previous example.

At the end of the function we have several parenthesis. What we are doing is immediately calling our function and passing through the value `0`. Lets look at a more basic example.

![f](https://imgur.com/hCehmmX.png)


No we can compare that to our more advanced example. Same thing. 

![f](https://imgur.com/zKdky1l.png)


Same logic for using a closure to create a private variable only using `forEach` as an example.

![f](https://imgur.com/hRviEXW.png)

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

![divider-bar](https://imgur.com/wbdDPMR.png)


resources on currying

https://medium.com/@kevincennis/currying-in-javascript-c66080543528

https://medium.com/@kbrainwave/currying-in-javascript-ce6da2d324fe

https://www.sitepoint.com/currying-in-functional-javascript/

https://www.sitepoint.com/currying-in-functional-javascript/

http://www.crockford.com/javascript/www_svendtofte_com/code/curried_javascript/index.html

resources on closure

https://medium.com/@odemeulder/i-never-understood-javascript-closures-9663703368e8

games for regex

https://regexcrossword.com/

https://alf.nu/RegexGolf

https://regexone.com/
 
## Nested For Loops

![f](https://imgur.com/BKX8xSx.png)

## Concise Coding

Can just use the return statement if its a boolean value, instead of doing the whole `if` `else` block

![f](https://imgur.com/7aGtvCJ.png)

Here using a specific condition to just return and exit the function

![f](https://imgur.com/G9r5HFk.png)

### string.slice

![f](https://imgur.com/ViWl0sm.png)

## Template Literal multi-line strings

![f](https://imgur.com/xxzxkCD.png)

## Template Literals

![f](https://imgur.com/htzqPfO.png)

## Reading MDN

![f](https://imgur.com/LvmW1p5.png)

## Window Object - Where Global Variables are Saved

Special note here if you DO NOT want to expose your variables to other 3rd party modules you can wrap them in a IIFE. On the other hand if you intentionally want to expose your variables, then disregard.

![f](https://imgur.com/BhSVXv9.png)

### Asynchronous Code

#### Async Code a Quick History

A quick history of asynchronous code. Originally it started with nested callback functions (like the house function below); however, this lead to a situtaion known as callback hell where the functions were nested so deep they would become unruly. As a fix for this `promises` were introduced. Further improvements were made in `ES2017` with `async/await`. In addition that, we also have the `fetch` API.

A common application for `callbacks` is asynchronous code. This will come a bit later in the chapters, so don't stress over it for now. But when interacting with other databases or APIs there is often a small amount of delay before we get our information back from the server. An example of this could be retrieving the current temperature from a weather API. 

A common callback structure you might see utilizing callbacks might look like the below code. For simplicity's sake this code is done synchronously. 

![houseF](https://imgur.com/9RQEXLi.png)

Notice here how the callback function ` function(errMessage, result)` holds *two* parameters `errMessage` and `result`. Just like a normal function, a callback function can have as many parameters as you would like.
 **Edit**: Note to self,1  add more examples of this later, a callback with multiple parameters. 2 the 'basics' of functions "blog post" you wrote before. 3. closure and the keyword this. 4. Javascript "classes" using ice cream example

At least that is how I see it, I am not as experienced as the others who have already replied to you. So if anyone more experienced sees errors in my post, please notify me and I will update my post.

## This is & test


## API's

![f](https://imgur.com/iDw6r4s.png)

![f](https://imgur.com/jgc6vlK.png)

## Arrow Functions

![f](https://imgur.com/xaLyXeM.png)

