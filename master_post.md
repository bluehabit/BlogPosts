### Think of Functions as Factories

Function help keep our code DRY, instead of having to write the same code over and over again. 

I like to think of functions as a factory. After all the processes within the factory complete, there will be some form of final output.

 Lets take for an example an ice cream factory. The ultimate job of the factory is to output ice cream, but before the ice cream can be made you must complete a few steps within the ice cream factory. First you must blend the ice cream mixture, pasteurize the mix, add liquid flavors and colors, freeze, add finish with the addition of fruit nuts and other toppings. And finally you package it up and have your final output, ice cream ready for distribution. 

![icecream](http://imgur.com/Iue6zw4.png)

In the case of Javascript the function will `return` something that you can use for later. Just like factories in real life, it is recommended that your functions specialize in performing a particular action.

## Parameters In Functions

Functions can also accept one or more inputs, they can do this through parameters. I like to think of parameters just like regular variables in JS. Just like variables,  a parameter acts as a placeholder for a value. You can also have functions that have no parameters as well, as shown in our example below.

![f](https://imgur.com/LkL5tVh.png)

For a simple example of a function with a parameter, here is a function named `add` that will add two numbers together. It accepts two parameters `number1` and `number2`. When we call the function using `add(1,3)` we are passing the value `1` to the parameter `number1`, and passing the value `3` to `number2`. The function stores these values for us, just like a variable. 

![functions](https://imgur.com/wsX86yJ.png)

And we can **reuse** that same function again, and again and again and pass new numbers through as parameters, by simply calling the function and passing in new values as shown below. Just like an ice cream factory that continues to produce ice cream. This prevents us from having to repeat our code over and over.

![func1](https://imgur.com/vOqFmtk.png)

We can even save the result inside of a variable. 

![func2](https://imgur.com/3uaFCBV.png)


----------------
Here is another example of a function with parameters using strings. This is a simple function that will log something to the console. In this case our function `printString` will console.log to the console. 

![func3](https://imgur.com/oolZxdk.png)

We have a function called `printString` here that has a parameter named `string`. It will hold the value of the variable `myString`. 

`printString(myString)` calls the function and passes through the value of `(myString)` as the parameter. As a result it will `console.log` `Hello there` to the console. 

______________________________________

The parameter `string` is holding the value of a string itself, therefore we have access to different string properties and methods such as `length`.

![func4](https://imgur.com/5ibJf6X.png)

In this case the parameter `string` is once again holding the value of `myString`. When it gets passed through the function it is checking the parameter `string.length`, so it gives us the length of `Hello There` which is 11. 

Parameter names are also arbitrary just like variables, they can be named whatever you would like. See the below example where I replaced the parameter name with something ridiculous, in this case `pinkDinosaur`. 

![func5](https://imgur.com/QNeNMTJ.png)


## The `return` keyword

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

### Callbacks

1) Functions in Javascript can be passed to another function as a parameter, known as a `callback`, to other functions. The function that accepts another function as a parameter is known as the `higher order function`. The `callback` is then "called back" within the higher order function itself. 

![f2](https://imgur.com/n0H0R8N.png)


### Closure

2) Functions can be `returned` by another function. This is known as `closure`. This also lets us create `private variables` in JS, a concept we will explore in more detail later.

![f3](https://imgur.com/wXpuE6F.png)

### Functions Assigned to Variables

3) Functions can also be assigned to a `variable` using the assignment operator. 

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

With that behind and our understanding how `callbacks` are an example of how functions are first class in javascript,  lets go more in depth on how `callbacks` work and work through additional examples. The function that accepts another function as a parameter is known as the higher order function. 

## Callbacks, a Visual Representation 

![f](https://imgur.com/RNcXVOv.png)

## Callbacks can be `Named`, or `Anonymous`

### Named vs Anonymous Callback Functions

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

----

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

----

### Custom Filter Function


![f](https://imgur.com/8q7tapD.png)


We can refactor the `if` statement to be a bit shorter and just write it like this.

![f](https://imgur.com/LYbo0ao.png)
----

### Custom Filter Function (more advanced)

This variant is slightly more advanced, it uses the `Array.isArray()` method to verify the input is indeed an array. 

![f](https://imgur.com/jeO68wS.png)

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

To get started creating with a constructor function we use the `new` keyword. For example `new Object`, `new Array` or `new String`. The value of `this` changes when we use the `new` keyword to represent the object that was just created.


## The `new` keyword

When the `new` keyword is used, a new object is created out of thin air. And inside the function definition the keyword `this` refers to the new object that was just created.

![f](https://imgur.com/kpSNs5N.png)

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

## Why the Constructor Pattern?

Imagine we wanted to make a few house objects, each house will have a bedroom, bathroom, and a sqFt. 

![f](https://imgur.com/bpivtAq.png)

What if we had to create, 50, 100 or more of these house objects! That would be crazy.

Instead we can use a constructor function to create instances of that object. The constructor function serves as a blue print to stamp out as many instances as required. 

![f](https://imgur.com/JJ20xXU.png)

## the `new` keyword

* creates a new object out of thin air
* sets value of the keyword `this` inside the constructor function to be the object created
* adds the line `return this` to the end of the function
* adds a property on to the object called `__proto__` which links the prototype property on the constructor function to the empty object

![f](https://imgur.com/1M5aYl7.png)


## Constructor Function Refactors

Here we have two constructor functions, notice they share many similar properties. Only one property will be different `numWheels`. 

![f](https://imgur.com/ok3vZrT.png)

We can refactor this to DRY up our code. 

![f](https://imgur.com/Ieu8D5P.png)

We can even refactor this further using apply. 

![f](https://imgur.com/oZ2qvuQ.png)

Quick overview of the `arguments` keyword if you are not familiar with it

![f](https://imgur.com/nNltvw7.png)

## __Prototype__ & The Prototype Chain

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


## Nested Objects

Object properties can hold many different values, from arrays to function to other objects as you can see below. 

![f](https://imgur.com/72Hey7D.png)


## Closure in Detail

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

![f](https://imgur.com/R68ZaKP.png)

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

----
All examples above represent only first-order functions. You can even go higher and you may find yourself with some clever code where a callback is "returned" in a from the executing function in a way that it becomes a "closure" and is executed after the executing function is completed.


## Why Private Variables

Private variable is used when you don't want it be exposed and accessible outside of its own relevant functions. i.e. protected. IOTW, private variable is not supposed to be accessed from outside context. If you want to be able to modify it, you'll have to provide the required function from the proper context. Just like you did in the returned function in your example code.


###Accessing Private Variables

![f](https://imgur.com/UmG0ZUn.png)

Another Example

![f](https://imgur.com/FeBQOmi.png)

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






