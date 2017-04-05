## CSS Only Animations

**Some cool animation example here**

Most of us learn the term 'seperation of concerns' when it comes to web developement. In practice this means seperating are text markup into structured html, the visual and aesthetic preferences into CSS, and the behavior and interaction of the program into Javascript. However, we are going to do something a bit different. We are going to focus on building web components and animations using only CSS for user interaction.

More complex interactions may still require JS, and that is fine, but CSS has made it possible to do quite a bit without it. Give it a try. 

When I initialliay transitioned from building web components in JS to CSS I was perplexed. I struggled with the concept quite bit and often found myself questioning why I was bothering to learn this instead of writing a few lines of Javascript instead. If this is you in the beginning, stick with it and you may learn a new trick or two.  

It is my hope that this article will clearly illuminate and clear any obfuscation on the matter. As we move through the material you may find that I like to move from simple to complex. If you find yourself already knowledgeable on the subject matter, please feel welcome to skip ahead. If not, please continue to hold the course as each section of this article is like a gear, with many required in unison to make the project work.

## At the Heart State Changes

**heart animation**

When it comes to animating using CSS only there is one central concept of critical importance that allows this to work. The idea is managing states of various HTML elements. The elements that we will pay particular attention to revolve around the `input` tag and its `type` attribute. 

To be more specific `<input type="radio">` and `<input type="checkbox" >`.

## Input Type: Radio and Checkbox
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

Keep this in mind as we move to the next section. 

## The Fundamental of CSS



### Pseudo Classes 

Pseudo classes are designed to define special states of an element. For example, the pseudo classs `:hover` will apply a specific CSS styling when the user hovers the element targeted by the selector. Let's take a look at some of the other more commonly used pseudo classes. 

Lets work through a few examples to help cement our understanding. 
http://codepen.io/bluehabit/pen/EWJZLQ

Guess what else is a pseudo class? `:checked`. This is pseudo selector will play an important role managing states moving forwards. 

## Click Pseudo Class?

As you sort through the basic pseudo-classes you may notice there is a lack of a ':click' selector. Something that occurs when the user clicks on an element. The closest thing we have to a `:click` is `:active`. Unfortunatley, it does not work for most of my animation needs. With `:active` the user has to hold the action for the animation to continue. For example clicking your mouse on a button and holding it there. 

The solution to this problem is what we eluded to earlier. We will utilize the different states of the `input` radio or checkbox elements based on if they have been checked or not. This is how we will register clicks. 

**show strike-through example here**

## CSS Combinators

## display: block & display: none

### State & Class Selectors

## The Building Blocks

