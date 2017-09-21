### Functions Introduction 

Function as you may recall are tools that we have so we do not have to keep writing the same code over and over again. Sort of like the many moving parts that make up a factory. 

### Think of Functions as Factories
I like to think of functions as a factory. After all the processes within the factory complete, there will be some form of final output.

 Lets take for an example an ice cream factory. The ultimate job of the factory is to output ice cream, but before the ice cream can be made you must complete a few steps within the ice cream factory. First you must blend the ice cream mixture, pasteurize the mix, add liquid flavors and colors, freeze, add finish with the addition of fruit nuts and other toppings. And finally you package it up and have your final output, ice cream ready for distribution. 

![icecream](http://imgur.com/Iue6zw4.png)

In the case of Javascript the function will `return` something that you can use for later. Just like factories in real life, it is recommended that your functions specialize to perform a particular action.

## Parameters In Functions

Functions can also accept input, they can do this through parameters. I like to think of parameters is just like regular variables in JS. Just like variables,  a parameter acts as a placeholder for a value. You can also have functions that have no parameters as well, as we saw in our previous ice cream function. 

For a simple example, here is a function named `add` that will add two numbers together. It accepts two parameters `number1` and `number2`. When we call the function using `add(1,3)` we are passing the value `1` to the parameter `number1`, and passing the value `3` to `number2`. The function stores these values for us, like a variable. 

![functions](https://imgur.com/wsX86yJ.png)

And we can **reuse** that same function again, and again and again and pass new numbers through as parameters, by simply calling the function and passing in new values as shown below. Just like an ice cream factory that continues to produce ice cream.

![func1](https://imgur.com/vOqFmtk.png)

We can even save the result inside of a variable. 

![func2](https://imgur.com/KcNlM0S.png)


----------------
Here is another example using strings. This is a simple function that will log something to the console. In this case our function `printString` will console.log to the console. 

![func3](https://imgur.com/oolZxdk.png)

We have a function called `printString` here that has a parameter named `string`. It will hold the value of myString. 

On the last line we have `printString(myString)` here we are calling the function and passing through the value of `(myString)` as the parameter. In other words the parameter of `string` is holding the value `myString` so it will console.log `Hello there` to the console. 

______________________________________

The parameter `string` is holding the value of a string itself, therefore we have access to different string properties and methods such as `length` and `trim()`.

![func4](https://imgur.com/5ibJf6X.png)

In this case the parameter `string` is once again holding the value of `myString`. When it gets passed through the function it is checking the parameter `string.length`, so it gives us the length of `Hello There` which is 11. 

Parameter names are also arbitrary just like variables, they can be named whatever you would like. See the below example where I replaced the parameter name with something ridiculous, in this case `pinkDinosaur`. 

![func5](https://imgur.com/QNeNMTJ.png)

_____

Lastly, here is an example of a a function that does not have a parameter. It will simply keep logging `Hello!` to the console each time it is called. 

![func6](https://imgur.com/bIUkRwS.png)

## Another Example 

Lets look at another example, with the function `numFactory`. This simple function just takes a users `num` as a parameter and increments it by one using `num ++`. But before it does that, it checks the `typeof` user input to verify that it is indeed a number. The end output is the users number incremented by one, that is what is `returned` as the output of the function. Just like the ice cream from the factory example. 

Whenever javascript sees the `return` function within a function it will automatically exit the function so keep that in mind. Because of this we can use `return` to route and determine the output paths of our function. In the example below *if the users number is `typeof` number* then we will exit the function and `return num++`. Otherwise, if the user input is not a number we will exit the function and `return` 'please enter a number'. 

Note, whatever comes *after* the keyword `return` is returned. This could be a number, a variable, a function call with a parameter etc. *Everything* you see after the keyword `return` will be the output of that function.

![numFactory](https://imgur.com/2YweOOn.png)

## Anonymous Self Invoking Functions

We can also have `anonymous functions` that do not have a name declared. In the example below, we have a self invoking self invoking function.

![f](https://imgur.com/ybb3Wrg.png)

## In Javascript Functions are First Class *Objects*

In Javascript functions can be played around with as if they were variables in several different ways. 

First class in simple terms means  *“being able to do what everyone else can do.”* **Functions can be assigned to variables, they can be passed around as arguments (`callback functions`). They can even be assigned as the return values of other functions (`closure`)**. Below we will quickly overview how functions are first class objects, and we will discuss each one in further detail later.

### Callbacks

1) Functions in Javascript can be passed to another function as a parameter (`callback`) to other functions. The function that accepts another function as a parameter is known as the `higher order function`. 

![f2](https://imgur.com/n0H0R8N.png)

![f3](https://imgur.com/Vz4BeyI.png)

### Closure

2) They can be `returned` by another function. This is an example of `closure`.

![f3](https://imgur.com/wXpuE6F.png)

### Functions Assigned to Variables

3) And they can also be assigned to a `variable` using the assignment operator. 

![f4](https://imgur.com/vFxGhBk.png)

We can call the function and pass parameters to it just like normal.

![f](https://imgur.com/mLf0rP5.png)

Notice the variable `sayHi` holds the value of a `function definition`. 

![f](https://imgur.com/WXl2xeM.png)




## Functions Advanced 

### Nested Functions
Functions can also be nested within one another, as shown below. This example uses `closure`, don't stress over it too much if its confusing at this point in time, you will learn more about it later in the chapters. 

![f1](https://imgur.com/eJ5nqUM.png)


## Callbacks in Detail

With that behind and our understanding how `callbacks` are an example of how functions are first class in javascript,  lets go more in depth on how `callbacks` work and work through additional examples. 

## Callbacks can be `Named`, or `Anonymous`

### Named vs Anonymous Callback Functions

With callbacks we can design them to be named, or anonymous. Both of these function examples will have he same output.

**Named Callback Function**

![callback1](https://imgur.com/3dqZ8bO.png)

**Anonymous Inline Callback Function**

![callback2](https://imgur.com/NM8JlRw.png)

Notice how the function is *'called back'* within the higher order function. 


### Function Names are Arbitrary

Just like with variables, naming is arbitrary. You can name them whatever you like, but it should be descriptive so you understand what the variable contains. 

Parameter names in functions are arbitrary as well, you can name them whatever you want. Look how we take the existing named callback function example from earlier and notice how we change the names of variables and parameters to be nonsensical. It doesn't matter what the parameter name is *it will holds the same information*. 



![arbitrary](https://imgur.com/i2feylT.png)

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

----

![example-3](http://imgur.com/c1DpFN4.png)


Another example of an inline anonymous callback function. Notice the pattern? See how the parameter is holding the anonymous function `function(){console.log('you clicked my button!');}` More of these examples will make sense once you complete the `Document Object Model` chapters where you will get regular practice using these.


### Asynchronous Code

#### Async Code a Quick History

A quick history of asynchronous code. Originally it started with nested callback functions (like the house function below); however, this lead to a situtaion known as callback hell where the functions were nested so deep they would become unruly. As a fix for this `promises` were introduced. Further improvements were made in `ES2017` with `async/await`. 

A common application for `callbacks` is asynchronous code. This will come a bit later in the chapters, so don't stress over it for now. But when interacting with other databases or APIs there is often a small amount of delay before we get our information back from the server. An example of this could be retrieving the current temperature from a weather API. 

A common callback structure you might see utilizing callbacks might look like the below code. For simplicity's sake this code is done synchronously. 

![houseF](https://imgur.com/9RQEXLi.png)

Notice here how the callback function ` function(errMessage, result)` holds *two* parameters `errMessage` and `result`. Just like a normal function, a callback function can have as many parameters as you would like.
 **Edit**: Note to self,1  add more examples of this later, a callback with multiple parameters. 2 the 'basics' of functions "blog post" you wrote before. 3. closure and the keyword this. 4. Javascript "classes" using ice cream example

At least that is how I see it, I am not as experienced as the others who have already replied to you. So if anyone more experienced sees errors in my post, please notify me and I will update my post.


## Object, Array, String Literals vs Constructor Function

In javascript, mostly everything is an object from arrays to strings. Because of this we can use either a constructor function or a literal to create them.

In most situations, it is most beneficial to create an item using the literal notation. But in some situations it is highly beneficial to use the a constructor function. One such example is [creating object classes with constructor functions](#Classes-using-Object-Constructors). 

To get started creating with a constructor function we use the `new` keyword. For example `new Object`, `new Array` or `new String`. 

### Object

#### Constructor Function

![obj-constructor](https://imgur.com/fUG2gaR.png)

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

Using the object constructor we can create what are known as classes. Constructor functions will create instances of the object. It is customary to capitalize the first letter of the variable name to indicate it is a class. Note, in the example below the object constructor function is embedded within another object, `Parrot`. Notice that `Parrot` has the first letter capitalized to indicate it is a constructor function. 

![constructor1](https://imgur.com/i6DT4ki.png)

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

![constructor3](https://imgur.com/xG7cfV1.png)

Its pretty easy to use the prototype in Javascript but is still considered on of the more complicated parts of the language that most people don’t know much about. Using the prototype can be a good way to show off your Javascript knowledge, but also improves the performance of your code by a handful.

## Nested Objects

Object properties can hold many different values, from arrays to function to other objects as you can see below. 

![f](https://imgur.com/72Hey7D.png)

## Key Callback Example

Key illustration here, notice how the callback function itself can have its own parameters since it is a function itself.

![f](https://imgur.com/V2Oc6xM.png)


## More Callback Examples

Callback Filtering out Odd Numbers

![f](https://imgur.com/LcvEr3x.png)


Callback Example

![f](https://imgur.com/IHBiAox.png)

## Template Literals

![f](https://imgur.com/htzqPfO.png)

## Parameters All Sorts of Values


Callback function holding an object as the parameter

![f](https://imgur.com/Ye4iApj.png)


Callback function holding an array as the parameter

![f](https://imgur.com/AnaoaGT.png)
