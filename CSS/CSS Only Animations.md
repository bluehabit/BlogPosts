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

To give you a finer level of detail lets look at some simple code that I put together. I quickly introduced an ID to each input element allowing me to quickly grab them from the DOM using JS.

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

### Building Radio and Checkbox Inputs
Lets being by practicing building a few input radio elements. We are going to create a collection of gem stones that a user can select from. We will begin with creating our first input element, a topaz. 

```
<input type="radio" id='topaz'>
```

Next lets add a label for our input. The `for` attribute will specify which radio button the label is intended for. The `for` label for the input element needs to be the same as the target input elements id, lets do that now. **It should be stressed at this point, that it is critical that the input element comes first, followed by the label element, otherwise erratic behavior will occur**. 

```
<input type="radio" id='topaz'>
<label for="topaz">Topaz</label>
```

If the user clicks the *Topaz* label, it will not check the radio input as well. Lets create two more input elements and labels for *Amethyst* and *Diamond*. 

```
<input type="radio" id='topaz' name='gem-stones'>
<label for="topaz">Topaz</label>

<input type="radio" id='amethyst' name='gem-stones'>
<label for='amethyst'>Amethyst</label>

<input type="radio" id='diamond' name='gem-stones'>
<label for='diamond'>Diamond</label>
```

Notice in the above example how we added a new attribute to each radio input. The `name` attribute we gave the value of `gem-stones`, effectivley creating a collection of items that are related. Having a collection is useful because it only allows the user to select *one* item at a time. 

As you can see in the finished example below, when we click an input elements label it will automatically select the corresponding radio button, and we can only select one input element at a time.

http://codepen.io/bluehabit/pen/WpBbNG

## CSS Class & Id Selectors

For the sake of being through lets quickly review class and Id selectors. Ids are unique, only one element within the document may have a given ID. In CSS they can be targeted with `#`. On the other hand, multiple elements on the page can share the same class. If you need a refresher, take a look at the example markup below. 

http://codepen.io/bluehabit/pen/vxwOyx

## CSS Type Selectors

There are X type selectors, each of which are very important for building CSS only web components and animations.

### DOM Tree
Before we can start building dazzling web components, we must first understand how to select very specific elements on the DOM. We will perform advanced selections using CSS combinators that will be discussed in greater detail below. But before we do that lets review the idea of the Document Object Model Tree. 

We can think of the DOM as a giant tree. With firm roots planted in the soil with branches reaching uptowards the sky. Each branch forks outward and forges its own path.The root of our tree is the `html` tag. Everything else is a descendant that originates from it. Lets take a look at what an actual DOM tree might look like with the help of this diagram. 

![DOM-tree](http://imgur.com/2iEmXaT.png)

In this example we can see a fairly typical HTML structure. Here the `nav` tag that is serving as the parent element. Everything **below** this `nav` tag is considered a descendant. The `ul` tag is a descendant of the parent element `nav` and also its child. 

The `ul` then has descendants of its own in the form of `li` and `a` tags. However, the `li` items are its direct children. Notice how the `li`s are all on the same level. Because they are on the same level, and share a parent element, these are all siblings. 

### CSS Combinators
Combinators are symbols that explain the relationship between selectors. There are 4 combinators that we will review. 

### Adjacent Sibling Selector +
For siblings, look for multiple elements on the *same level* sharing the *same parent*. 

### General Sibling Selector ~
For siblings, look for multiple elements on the *same level* sharing the *same parent*. 

### Child Selector >
Look one level directly below the current parent element. 

### Descendant Selector
Follow the branches of a parent element to identify all of its descendants. 

### Combinator Examples

Lets put this into practice and work through a few examples selecting elements using combinators. Before we begin, this will be the starting structure of our HTML before any CSS styling is applied. http://codepen.io/bluehabit/pen/RpmWVe

Lets begin by using a **descendant** selector to target all `li`s that are a descendant of a `ul` tag, and make them have the `background-color` `#4d74f0`. 

![example1](http://imgur.com/OAFEj3P.png)

If we carefully read through this, lets see how it works out. First we are targeting the class `.penguinInformation` then we are using the child selector `>` to target all `p` tags of that are children of that class.

![example2](http://imgur.com/znTukAD.png)

Lets look at our next selector, we are targeting the `.penguinInformation`, and once again using the child selector `>` to target all `p` tags that are direct children of the class specified. In addition, we are now using the adjacent sibling selector `+` to select all `h3` tags that are adjacent siblings to the `p` tags. 

![example3](http://imgur.com/cS8taNG.png)

Lastly, we will target all `label` elements that are general siblings of the `.penguinInformation` class. We will do this using the general sibling selector symbol `~`. 

![example4](http://imgur.com/DaxGIDl.png)

The final result should look something like this, http://codepen.io/bluehabit/pen/aJeZNv.

### Pseudo Classes 

Pseudo classes are designed to define special states of an element. For example, the pseudo classs `:hover` will apply a specific CSS styling when the user hovers the element targeted by the selector. Let's take a look at some of the other more commonly used pseudo classes. In the markup below.

http://codepen.io/bluehabit/pen/EWJZLQ

Pay special attention to `:nth-child` pseduo class. Notice we can pass it the value `even` or `odd` to specify which list items are affected by the rules. In addition to that, we can also target a specific child as shown with:

```
ul.ice-animals li:nth-child(3){
  color: white;
}
```
This makes the third list item 'Walrus' the color white. 

### :checked Pseudo Class
Guess what else is a pseudo class that we eluded to earlier? `:checked`. This is pseudo selector will play an important role managing states moving forwards. Lets target our earlier examples with CSS


## Click Pseudo Class?

As you sort through the basic pseudo-classes you may notice there is a lack of a ':click' selector. Something that occurs when the user clicks on an element. The closest thing we have to a `:click` is `:active`. Unfortunatley, it does not work for most of my animation needs. With `:active` the user has to hold the action for the animation to continue. For example clicking your mouse on a button and holding it there. 

### 
The solution to this problem is what we eluded to earlier. We will utilize the different states of the `input` radio or checkbox elements based on if they have been checked or not. This is how we will register clicks. 

**show strike-through example here**


## display: block & display: none

### State & Class Selectors

## The Building Blocks

