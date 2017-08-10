![programming-nutshell](http://imgur.com/RwCgkg6.png)

## FIND THIS!

Is there anything on MDN that explains that it does *NOT* have to be `document.querySelector` that you can use it on an HTML element object for exapmle `spanContainer.querySelector` to search within a certain container.

### Nested Objects

![nested-object](http://imgur.com/JXmv5Ah.png)
  
### Callback functions

Key Illustration here: Notice how since the higher order function which takes the function as a parameter, aka the callback, the callback can have its own parameters. 

**Designing your callback**:

![design-callback](http://imgur.com/HlPqyIx.png)

![key-illustration](http://imgur.com/4eq6DOT.png)
  
A callback function is a function passed into another function as an argument, which is then called inside the outer function to complete some kind of routine or action. The higher order function is always the function that takes another function as a parameter. The callback function always gets called within the higher order function as a parameter. Callbacks are often used to deal with *asynchronous code*.

**Another Callback example:**

![callback-example-2](http://imgur.com/4gnZRFp.png)

### Named Callback vs Inline Anonymous Callback 

![inline](http://imgur.com/7SefXfO.png)


### HouseExample

![house](http://imgur.com/S6rwsib.png)

### House Named Function Callback

![named-house](http://imgur.com/uOvSljc.png)


### Callback Functions as the ONLY parameter within a Higher Order Function

![example](http://imgur.com/WPfBD2u.png)

Same code, this time using a **anonymous callback function**

![anonymous-example](http://imgur.com/v6FPHJi.png)

Another Example:

![another-example](http://imgur.com/IttKey3.png)

### Anonymous inline function callback
  
![anonymous-inline-function-callback](http://imgur.com/u0GgT6n.png)


### Anonymous Callback vs Named Callback 

![anonymous-inline-vs-named-callback](http://imgur.com/Tci3Ggu.png)

Named callback function
![named-callback](http://imgur.com/a3sVfSQ.png)


### Callback functions can have their own Parameters

![own-parameters](http://imgur.com/3zEydcd.png)


### Spotting an Inline Anonymous Function Callback in the Wild

![wild](http://imgur.com/dEnvVlf.png)


### More Examples

Regular Parameter: 

![color-example](http://imgur.com/v58SzKh.png)

Object Parameter: 

![color-example2](http://i.imgur.com/DOpfudo.png)

Array Parameter: 

![color-example3](http://imgur.com/kfYrRhp.png)

### Callback(item)

![callback-item](http://imgur.com/UFQjhQk.png)

### Equality Operators

![equality-operators](http://imgur.com/rpgIUqB.png)

### Variant

![variant](http://imgur.com/0df8crS.png)

![variant2](http://imgur.com/VepzS7z.png)

This is why **callbacks** work so well with **asynchronous** code. With async code you might make a request to an API somewhere, and when it receives your query and sends the data back that could be some amount of time in the future. What did callbacks do for us? They let us get information out of another functions scope. 

The higher order function has access to the callback function within its scope. So when the data from the API comes back inside the callback function you can do stuff with it. 

### Callback Function Workflow

![callback-workflow](http://imgur.com/ISoW7bV.png)

### isNaN()

```
var string = 'dog'
isNaN(string);

//--> true


var num = 1;
isNaN(num);

//--> false;
```

### For Each

![for-each-example](http://imgur.com/IyNIHwC.png)

![parameters](http://imgur.com/VAdnpnf.png)
Check parameters on MDN to see what each does 

### AddEventListener

![example](http://imgur.com/MT0kSLE.png)

#### Console.dir() to see methods and properties on the HTML element Object

![dir](http://imgur.com/OP50Bim.png)

**Important**: Remember under the hood on `addEventListener` the value of `this` is reassigned to the HTML element object using call, apply or something.

![button](http://imgur.com/9Bbolle.png)

### Good Example

![good-example](http://imgur.com/P6Emvgb.png)

### ProTip

![protip1](http://imgur.com/vInrEDA.png)

![protip2](http://imgur.com/yDvgb9P.png)

![protip3](http://imgur.com/mpRIlRh.png)

See more of this example here https://codepen.io/bluehabit/pen/MoOaao

### Normal vs Arrow Functions

![example](http://imgur.com/t8iXoNa.png)

### Real Life Example Callbacks


### Truthy and Falsey


### Get Coordinates Example using Event Object

![event-object](http://imgur.com/yzggc9b.png) 


### Weather API Example

--find it it and insert here

### nodeLists are not LIVE

The `nodeList` returned by `document.querySelectorAll('.slider-marker > span')` is **not a live list**. Similarly, the Node returned by querySelector is not live. This means, chnages to the DOM for these elements will not change the list. Changes to `classList` however will be a live list. 

Instead for this project, we manually update the values everytime the user clicks the arrow in steps. 
![gif-steps](http://imgur.com/MGzQYRj.gif)

In other words a `nodeList` returned by `document.querySelector` or `document.querySelectorAll` returns the `nodeList` as it exists at that precise moment in time! It is not live.

See image below to demonstrate this:

![nodeLists-not-live](http://imgur.com/14JLPon.png)


### Adding Nodes to Document

HTML

![html](http://imgur.com/FoC1irT.png)

`method1` using `.createElement` and `.createTextNode`
![method1](http://imgur.com/mUE49vh.png)

`method2` using `.createElement` and `.innerHTML`
![method2](http://imgur.com/5HxoLZF.png)

`method3` using `.createElement` and `.innerText`
![method3](http://imgur.com/a9YyZzL.png)


### QuerySelector Relative to Parent

![querySelect](http://imgur.com/5mVAnKR.png)


### Double If Statement vs. Else If

![double-if](http://imgur.com/idVasYv.png)


### nextElementSibling ProTips 

![nextElementSibling](http://imgur.com/jtn1QMI.png)


### Carousel Logic

![logic](http://imgur.com/YPB3nDC.png)

JSFiddle: https://jsfiddle.net/c1yetpt8/

```
demo code
```

A simpler, more stripped down, bare bone example example right here:
https://jsfiddle.net/njtuuf0p/

And an another alternative way to code it, see highlighted text
![alternative](http://imgur.com/vynb5tC.png)

### `.parentElement`
