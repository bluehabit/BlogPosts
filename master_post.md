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

## Functions

@hannah_herbst Hey Hannah, the way I like to think of parameters is just like regular variables in JS. Just like variables,  a parameter acts as a placeholder for a value. You can also have functions that have no parameters as well.

Function as you may recall are tools that we have so we do not have to keep writing the same code over and over again. 

For a simple example, here is a function that will add two numbers together

```
function add(number1, number2){
	return number1 + number2;
}

add(1, 3);
//1 + 3 = 4, output is 4
```

And we can **reuse** that same function again, and again and again and pass new numbers through as parameters, by simply calling the function and passing in new values as shown below.

```
add(2, 3)
//2+3 = 5, output is 5
```

We can even save the result inside of a variable. 

```
var addNumbers = add(2, 3);
```


----------------
Here is another example using strings. This is a simple function that will log something to the console. In this case our function `printString` will console.log to the console. 

```
var myString = 'Hello there';

function printString(string){
   console.log(string);
}

printString(myString);
```

We have a function called `printString` here that has a parameter named `string`. It will hold the value of myString. 

On the last line we have `printString(myString)` here we are calling the function and passing through the value of `(myString)` as the parameter. In other words the parameter of `string` is holding the value `myString` so it will console.log `Hello there` to the console. 

______________________________________

You can also add properties to parameters. For example if we modified the above code just a little bit we can find the length of a string. 

```
var myString = 'Hello there';

function stringLength(string){
   console.log(string.length);
}

stringLength(myString);
```

In this case the parameter `string` is once again holding the value of `myString`. When it gets passed through the function it is checking the parameter `string.length`, so it gives us the length of `Hello There` which is 11. 

Parameter names are also arbitrary just like variables, they can be named whatever you would like. See the below example where I replaced the parameter name with something ridiculous, in this case `pinkDinosaur`. 

```
var myString = 'Hello there';

function stringLength(pinkDinosaur){
   console.log(pinkDinosaur.length);
}

stringLength(myString);
```
_____

Lastly, here is an example of a a function that does not have a parameter. It will simply keep logging > Hello! to the console each time it is called. 

```
function hello(){
	console.log('Hello!');
}

hello();
```
----


Hopefully that helps, let me know if it wasn't clear enough. For me sometimes reading the material or someone else's answer here on QA sometimes isn't enough. I like to do a lot of small scale projects where I do very small bits of code to help understand what is going on. Perhaps consider reading through the answers here and plugging in some of the code examples to deepen your understanding.

That is one concern I do have about the intro to JS chapter so far, is that it goes through the fundamentals quite quickly and if you do not already have a solid foundation (either through your own learning, tutorial websites etc.) then it could be a bit confusing.
