## CSS Only Animations
Most of us learn the term 'seperation of concerns' when it comes to web developement. In practice this means seperating are text markup into structured html, the visual and aesthetic preferences into CSS, and the behavior and interaction of the program into Javascript. However, we are going to do something a bit different. We are going to focus on building web components and animations using only CSS for user interaction.

More complex interactions may still require JS, and that is fine, but CSS has made it possible to do quite a bit without it. Give it a try. 

When I initialliay transitioned from building web components in JS to CSS I was perplexed. I struggled with the concept quite bit and often found myself questioning why I was bothering to learn this instead of writing a few lines of Javascript instead. If this is you in the beginning, stick with it and you may learn a new trick or two.  

It is my hope that this article will clearly illuminate and clear any obfuscation on the matter.

## State Changes

When it comes to animating using CSS only there is one central concept of critical importance that allows this to work. The idea is managing states of various HTML elements. The elements that we will pay particular attention to revolve around the `input` tag and its `type` attribute. 

To be more specific `<input type="radio">` and `<input type="checkbox" >`.

Every input HTML element object has properties. The property that we are particularly interested in is `.checked`, this is something every input type of radio and checkbox have. We can leverage this to our advantage to manage the different states of our animation.

To give you a finer level of detail lets look at some simple code that I put together. I introduced an ID to each input element allowing me to quickly grab them from the DOM using JS.

```
<input id='radio' type="radio">
<input id='checkbox' type="checkbox" >

var raido = document.getElementById('radio');
var checkbox = document.getElementById('checkbox');
```

#### Console.dir()
We can use `console.dir()` to view all the methods and properties available to the HTML element object. As you can see below, the property that we are interested in is `.checked`. 

![consoledir](http://imgur.com/9Ta5d6x.gif)

#### .checked
This will provide us with a boolean value indicating the status of a given input element.As you might expect, the value of `.checked` is false when the input element has not been selected, conversley it will become true if selected. See the animation below for clarification. 

![checked](http://imgur.com/ypB5rBp.gif)


## Input Type: Radio and Checkbox

## The Building Blocks

## State & Class Selectors



