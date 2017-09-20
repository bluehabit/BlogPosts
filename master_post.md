## Object, Array, String Literals vs Constructor Function

In javascript, since most things are an object from arrays to strings, we can use a object constructor function or a create a literal to make them. 

### Object

#### Constructor Function

![obj-constructor](https://imgur.com/fUG2gaR.png)

#### Literal

![obj-literal](https://imgur.com/1LiEz3j.png)


## Creating Classes with Object Constructor Functions

Will create an instance of the object. 

![obj-classes](https://imgur.com/lvvhZZp.png)


### Array


## Classes using Object Constructors

Using the object constructor we can create what are known as classes.

![constructor1](https://imgur.com/UzhJIr8.png)

## Constructor Pattern Continued

A constructor function is a single object that we can use as a base to create more objects that are similar. Think of it like a stamp head in a way, once we have the head created we can stamp out as many items as we want all from a single head. We essentially are able to clone the object or constructor function that was originally created.

Here is an example in Javascript:

```
var Bullet = function (x, y, color) {
    this.x = x;
    this.y = y;
    this.color = color;
    this.location = function () {
        console.log("x: " + x + " " + "y: " + y);
    };
};

var bullet1 = new Bullet(5, 10, "Green");
var bullet2 = new Bullet(20, 40, "Blue"); 

bullet1.location(); //Console Logs: x: 5 y: 10
```

In the example above we create a constructor function and give it four properties, by using the this keyword we are binding or assigning those properties to the instance of Bullet.

**Note**: By convention and best practice in Javascript, you should start all constructor functions with a capital letter.


![constructor2](https://imgur.com/AxlLuAg.png)

As we can see we are even able to assign functions as properties on our constructor. We then create two new instances of the Bullet Class, bullet1 and bullet2. In Javascript we can use the “new” keyword to create new instances of the class object. You also might notice that we are able to pass in arguments on the fly, this makes it so not all of our instances have to be exactly the same.

Once we create the instance of our class we can then call any of the methods that are on the object. In the example above we call the location method on our object and get back a console log of our coordinates.

There is just one problem with our constructor function above, when you place a function inside of a constructor it recreates that function over and over every instance that gets created. As you can imagine, if you had thousands of instances, this could become a pretty big problem (speed and optimization). Thankfully Javascript has a solution for this problem.

We can use the prototype, this will create only 1 function, no matter how many instances you create. The function is set aside in a little box (figuratively speaking) and can be used by all of the instances when needed.

An example of how the prototype can help us optimize our previous code:

![constructor3](https://imgur.com/xG7cfV1.png)

Its pretty easy to use the prototype in Javascript but is still considered on of the more complicated parts of the language that most people don’t know much about. Using the prototype can be a good way to show off your Javascript knowledge, but also improves the performance of your code by a handful.



## Functions

@hannah_herbst Hey Hannah, the way I like to think of parameters is just like regular variables in JS. Just like variables,  a parameter acts as a placeholder for a value. You can also have functions that have no parameters as well.

Function as you may recall are tools that we have so we do not have to keep writing the same code over and over again. 

For a simple example, here is a function that will add two numbers together

![functions](https://imgur.com/wsX86yJ.png)

And we can **reuse** that same function again, and again and again and pass new numbers through as parameters, by simply calling the function and passing in new values as shown below.

![func1](https://imgur.com/vOqFmtk.png)

We can even save the result inside of a variable. 

![func2](https://imgur.com/KcNlM0S.png)


----------------
Here is another example using strings. This is a simple function that will log something to the console. In this case our function `printString` will console.log to the console. 

![func3](https://imgur.com/oolZxdk.png)

We have a function called `printString` here that has a parameter named `string`. It will hold the value of myString. 

On the last line we have `printString(myString)` here we are calling the function and passing through the value of `(myString)` as the parameter. In other words the parameter of `string` is holding the value `myString` so it will console.log `Hello there` to the console. 

______________________________________

You can also add properties to parameters. For example if we modified the above code just a little bit we can find the length of a string. 

![func4](https://imgur.com/5ibJf6X.png)

In this case the parameter `string` is once again holding the value of `myString`. When it gets passed through the function it is checking the parameter `string.length`, so it gives us the length of `Hello There` which is 11. 

Parameter names are also arbitrary just like variables, they can be named whatever you would like. See the below example where I replaced the parameter name with something ridiculous, in this case `pinkDinosaur`. 

![func5](https://imgur.com/QNeNMTJ.png)

_____

Lastly, here is an example of a a function that does not have a parameter. It will simply keep logging > Hello! to the console each time it is called. 

![func6](https://imgur.com/bIUkRwS.png)

----


Hopefully that helps, let me know if it wasn't clear enough. For me sometimes reading the material or someone else's answer here on QA sometimes isn't enough. I like to do a lot of small scale projects where I do very small bits of code to help understand what is going on. Perhaps consider reading through the answers here and plugging in some of the code examples to deepen your understanding.

That is one concern I do have about the intro to JS chapter so far, is that it goes through the fundamentals quite quickly and if you do not already have a solid foundation (either through your own learning, tutorial websites etc.) then it could be a bit confusing.

## Functions Advanced 

Hey John, just going to expand on what has already been said a bit and provide some more examples. I am going to attempt to provide a thorough explanation that will both help you now, and later if you choose to revisit this text after learning some additional concepts. 

### Think of Functions as Factories
I like to think of functions as a factory. After all the processes within the factory complete, there will be some form of final output.

 Lets take for an example an ice cream factory. The ultimate job of the factory is to output ice cream, but before the ice cream can be made you must complete a few steps within the ice cream factory.  Within the factory you must first blend the ice cream mixture, pasteurize the mix, add liquid flavors and colors, freeze, add fruits, nuts and other toppings. And finally you package it up and have your final output, icecream ready for distribution. 

![icecream](http://imgur.com/Iue6zw4.png)

In the case of Javascript the function will `return` something that you can use for later. Just like factories in real life, it is recommended that your functions specialize to perform a particular action.

In Javascript functions can be played around with as if they were variables in several different ways.

Lets look at this example, with the function `numFactory`. This simple function just takes a users `num` and increments it by one using `num ++`. But before it does that, it checks the `typeof` user input to verify that it is indeed a number. The end output is the users number incremented by one, that is what is `returned` as the output of the function. Just like the ice cream from the factory example. 

Whenever javascript sees the `return` function within a function it will automatically exit the function so keep that in mind. Because of this we can use `return` to route and determine the output paths of our function. In the example below *if the users number is `typeof` number* then we will `return num++`. Otherwise, if the user input is not a number we will `return` 'please enter a number'. 

Note, whatever comes *after* the keyword `return` is returned. This could be a number, a variable, a function call with a parameter etc. *Everything* after the keyword `return` will be the output of that function.

![numFactory](https://imgur.com/2YweOOn.png)

### Nested Functions
Functions can also be nested within one another, as shown below. This example uses `closure`, don't stress over it too much if its confusing at this point in time, you will learn more about it later in the chapters. 

![f1](https://imgur.com/eJ5nqUM.png)

### Functions are first class objects in Javascript
First class in simple terms means  “*being able to do what everyone else can do*.” Function  can be assigned to variables, they can be passed around as arguments (`callback`). They can even be assigned as the return values of other functions (`closure`). 

1) The functions in javascript can be passed to another function as a parameter (`callback`) to other functions. The function that accepts another function as a parameter is known as the `higher order function`. 

![f2](https://imgur.com/n0H0R8N.png)

2) They can be `returned` by another function. This is an example of `closure`, I don't believe it has been discussed at this point in the chapters yet so I wouldn't worry too much about this example if you find it confusing at this point in time.

![f3](https://imgur.com/wXpuE6F.ong)

3) And they can also be assigned a `variable` using the assignment operator. 

![f4](https://imgur.com/vFxGhBk.png)

### Callbacks in Detail
With that behind and our understanding how `callbacks` are an example of how functions are first class in javascript,  lets go more in depth on how `callbacks` work and work through additional examples. 

## Callbacks can be Named, or Anonymous

### Named vs Anonymous Callback Functions

With callbacks we can design them to be named, or anonymous. Both of these function examples will have he same output.

**Named Callback Function**

![callback1](https://imgur.com/3dqZ8bO.png)

**Anonymous Inline Callback Function**

![callback2](https://imgur.com/NM8JlRw.png)


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

![houseF](https://imgur.com/a/qEo9u.png)

Notice here how the callback function ` function(errMessage, result)` holds *two* parameters `errMessage` and `result`. Just like a normal function, a callback function can have as many parameters as you would like.
 **Edit**: Note to self,1  add more examples of this later, a callback with multiple parameters. 2 the 'basics' of functions "blog post" you wrote before. 3. closure and the keyword this. 4. Javascript "classes" using ice cream example

At least that is how I see it, I am not as experienced as the others who have already replied to you. So if anyone more experienced sees errors in my post, please notify me and I will update my post.
