## Building CSS Only Animations

Most of us learn the term *'separation of concerns'* when it comes to web development. In practice this means separating markup into its own html, the visual and aesthetic preferences into a CSS file, and the behavior and interaction of the program into a JavaScript file. However, we are going to do something a bit different. We are going to focus on building web components and animations using only CSS, no JavaScript required. More complex interactions may still require JS, and that is fine, but CSS has made it possible to do quite a bit without it - and that will be the focus of this blog post. 

When I initially transitioned from building web components interactivity in JavaScript to CSS only I was a bit perplexed. I struggled with the concept quite bit and often found myself questioning why I was bothering to learn this instead of writing a few lines of JavaScript instead. If this is you in the beginning, stick with it and you may learn a new trick or two and add new improvements to your work flow.  

It is my hope that this article will clearly illuminate and clear any confusion on the matter. As we move through the material you may find that I like to move from simple examples to more complex. If you find yourself already knowledgeable on a particular subject matter, or if a particular example is too rudimentary, please feel free to skip ahead. If not, please continue to hold the course as each section of this article builds on the previous. 

There will be several web components we build throughout this article such as: image galleries, tabs and accordions just to name a few. In the final section of this blog post we will explore animating a weather sequence by hand using SVGs and techniques we have learned in throughout this article.

Lets get started.

## State Change - The Heart of the Matter

![heart-beat](http://imgur.com/3e2imS2.gif)

When it comes to animation using CSS only there is one central concept that allows this to work. The idea is managing different **states** of HTML elements. The elements that we will pay particular attention to revolve around the `input` tag and its `type` attribute. 

To be more specific `<input type="radio">` and `<input type="checkbox" >`.

## Input Type: Radio and Checkbox

Every HTML element object has properties. HTML elements are just like any other object that we may be accustom to working within JavaScript, they have properties and methods. The property that we are particularly interested in for our purposes is `.checked`, this is something every input type of radio and checkbox have. We can leverage this to our advantage to manage the different states of our animation. 

In the case of the radio and checkbox input element they have two states, checked or unchecked. Just like a light switch that has two states, on or off.

To give you a finer level of detail lets look at some simple input elements. I added an ID to each input element allowing me to quickly grab them from the DOM using JS.

```
<input id='radio' type="radio">
<input id='checkbox' type="checkbox" >

var radio = document.getElementById('radio');
var checkbox = document.getElementById('checkbox');
```

### Console.dir()
We can use `console.dir()` to view all the methods and properties available to the HTML element object. In the example below, look at all the available methods and properties available to us on the HTML element radio object. The property that we are keenly of the HTML element object we are interested in is `.checked`.
![consoledir](http://imgur.com/9Ta5d6x.gif)

#### .checked

This will provide us with a boolean value indicating the status of a given input element. As you might expect, the value of `.checked` is false when the input element has not been selected, conversely it will become true once selected. See the animation below for clarification. 

![checked](http://imgur.com/ypB5rBp.gif)

Keep this in mind as we move to the next section. 

### Building Radio and Checkbox Inputs
Lets being by practicing building a few basic input radio elements. We are going to create a collection of gem stones that a user can select from. Each gem stone will be its own input element with an accompanying label. Let's begin with creating our first input element, a topaz. 

```
<input type="radio" id='topaz'>
```

Next lets add a label for our input. The `for` attribute will specify which radio button the label is intended for. The `for` label for the input element needs to be the same as the target input elements id, lets do that now. **It should be stressed at this point, that it is critical that the input element comes first in the markup, followed by the label element, otherwise erratic behavior may occur when we attempt to add animation later**. 

```
<input type="radio" id='topaz'>
<label for="topaz">Topaz</label>
```

If the user clicks the *Topaz* label, it will now check the corresponding radio input as well. Lets create two more input elements and labels for *Amethyst* and *Diamond*. 

```
<input type="radio" id='topaz' name='gem-stones'>
<label for="topaz">Topaz</label>

<input type="radio" id='amethyst' name='gem-stones'>
<label for='amethyst'>Amethyst</label>

<input type="radio" id='diamond' name='gem-stones'>
<label for='diamond'>Diamond</label>
```

Notice in the above example how we added a new attribute to each radio input. With the `name` attribute we gave the value of `gem-stones` to all items in the list, effectively creating a collection of items that are related. Having a collection is useful because it only allows the user to select *one* item at a time when using a radio input. 

As you can see in the finished example below, when we click a label it will automatically select the corresponding radio button with the matching `id`, and we can only select one input element at a time from a given collection.

Codepen: http://codepen.io/bluehabit/pen/qreqQE

## CSS Class & Id Selectors

For the sake of being thorough lets quickly review class and Id selectors. **Ids** are unique, only one element within the document may have a given ID. In CSS they can be targeted with `#` symbol. 

**Classes** On the other hand, can be assigned to multiple elements on the page. In CSS classes can be targeted with the `.` symbol. If you need a refresher, take a look at the example markup below showing the differences between ids and classes.

Codepe: http://codepen.io/bluehabit/pen/vxwOyx

### Document Object Model (DOM) Tree
Before we can start building web components, we must first understand how to drill down and select very specific elements on the DOM. We will learn to perform advanced selections using CSS combinators, but before we do that lets review the concept behind the Document Object Model. 

We can think of the DOM as a giant tree, with firm roots planted in the soil and branches reaching up towards the sky. Each branch forks outward and forges its own path towards the heavens. The root of our tree is the `html` tag. Everything else is a descendant that originates from it. Lets take a look at what an example DOM tree might look like with the help of this diagram. 

![DOM-tree](http://imgur.com/2iEmXaT.png)

In this example we can see a fairly typical HTML structure. Here the `nav` tag is serving as the parent element. Everything **below** this `nav` tag is considered a descendant. The `ul` tag is a descendant of the parent element `nav` and also its child. 

The `ul` then has descendants of its own in the form of `li` and `a` tags. However, the `li` items are its direct children. Notice how the `li`s are all on the same level. Because they are on the same level, and share a parent element, these are all siblings. 

### Type Selectors
There are 4 type selectors that we will review. 

### Adjacent Sibling Selector +
For siblings, look for multiple elements on the *same level* sharing the *same parent*. This selector will select an *adjacent* sibling. 

### General Sibling Selector ~
For siblings, look for multiple elements on the *same level* sharing the *same parent*. This selector will select all siblings.

### Child Selector >
Look one level directly below the current parent element, that is the child. 

### Descendant Selector (no symbol, use a space between two selectors)
*Any* node underneath a parent element can be considered a descendant. 

### Combinators

Combinators are symbols that explain the relationship between selectors. Lets put this into practice and work through a few examples. In addition, I highly suggest reading through the selectors through in your mind or out loud to very clearly identify what a given combinator is targeting. Before we begin, this will be the starting structure of our HTML before any CSS styling is applied. 

If you are unfamiliar with combinators, **please do not skip this section**. Not only is it paramount to the projects covered in this blog post, but these combinators will become an essential tool in your belt to select and manipulate the DOM using Javascript in more advanced projects. 

Codepen: http://codepen.io/bluehabit/pen/RpmWVe

Lets begin by using a **descendant** selector to target all `li`s that are a descendant of a `ul` tag, and then make them have the `background-color` `#4d74f0`. Note the space between the `li` tag and the `ul` tag indicates this is using the descendant selector.

```
ul li {
  background-color: #4d74f0;
}
```

![example1](http://imgur.com/OAFEj3P.png)

-----

For our next example we are targeting the class `.penguinInformation` then we are using the child selector `>` to target all `p` tags  that are children of that class and making them `color: pink`.

```
.penguinInformation > p {
	color: pink;
}
```

![example2](http://imgur.com/P9gJJJf.png)

-----

Lets look at our next selector, we are targeting the `.penguinInformation`, and once again using the child selector `>` to target all `p` tags that are direct children of the class specified. In addition, we are now using the adjacent sibling selector `+` to select all `h3` tags that are adjacent siblings to the `p` tags. 

```
.penguinInformation > p + h3 {
	color: green;
}
```


![example3](http://imgur.com/cS8taNG.png)

-----

Lastly, we will target all `label` elements that are general siblings of the `.penguinInformation` class. We will do this using the general sibling selector symbol `~`. 

```
.penguinInformation ~ label {
	color: gold;
}
```

![example4](http://imgur.com/DaxGIDl.png)

The final result should look something like the codepen below.

Codepen: http://codepen.io/bluehabit/pen/aJeZNv
-----

## Pseudo Classes 

Pseudo classes are designed to define special states of an element. For example, the pseudo classs `:hover` will apply a specific CSS styling when the user hovers over the element targeted by the selector. Let's take a look at some of the other more commonly used pseudo classes. In the markup below.

Codepen: http://codepen.io/bluehabit/pen/EWJZLQ

### :hover

When we hover over the text `Hover Over me!` the `background-color` changes to pink. 

```
.first-example:hover {
  background-color: #f11f82;
}
```

### :nth-child 

Pay special attention to `:nth-child` pseduo class. Notice we can pass it the value `even` or `odd` to specify which list items are affected by the rules. As we can see in the following examples:

```
ul.ice-animals li:nth-child(even) {
  background-color: #1f82f1;
  width: 20%;
}
```

and

```
ul.ice-animals li:nth-child(odd){
  background-color: #a686cd;
  width: 20%;
}
```


In addition to that, we can also target a specific child as shown with:

```
ul.ice-animals li:nth-child(3){
  color: white;
}
```
This makes the third list item 'Walrus' the color white. 

### :active

With the `:active` pseudo class, the effect only occurs while the user is holding down the mouse. If we go to the text `click & HOLD` and hold our mouse down, it will change the color.

```
.activeButton:active {
  background-color: #f11f82;
}
```
-----

## :before and :after

With these `:before` and `:after` its pretty common to use HTML entities. `:before` will insert content before each of the selected elements, while `:after` will insert content after the selected elements. 

Lets take a look at the example markup below:

Codepen: http://codepen.io/bluehabit/pen/RpXXwJ

## Unicode entities
Notice in the above code we are using unicode characters for our content. Unicode characters are symbols things like weather, telephones etc. First select the unicode character that you would like to use. For the `content` property set the value equal to `\` followed by the hex value of your unicode character. For example if I would like to use the heart symbol, your code will look like this `content: "\2764"`. 

Unicode Character Resources: 
* https://unicode-table.com/en/
* https://www.w3schools.com/charsets/ref_utf_symbols.asp

## :not
[description forthcoming]

Example Codepen: https://codepen.io/bluehabit/pen/PmPNNB

## Click Pseudo Class?

As you sort through the basic pseudo-classes you may notice there is a lack of a ':click' selector. Something that occurs when the user clicks on an element. The closest thing we have to a `:click` is `:active`. Unfortunately, it does not work for most animation requirements. With `:active` the user must hold the action for the animation to continue. For example clicking your mouse on a button and holding it there. 

												The solution to this problem is what we eluded to earlier, managing states of input elements. We will utilize the different states of the `input` radio or checkbox elements based on if they have been checked or not. This is how we will register when a user clicks the element. 

### :checked 
Introducing `:checked`. This pseudo selector will play an important role managing states. Like the other pseudo selectors, this helps identify a special state of the element. Lets revisit our gem stone collection example from earlier. 

### Managing States with :checked

![Gem-collection](http://imgur.com/xxCiS0G.gif)

As mentioned earlier, we will be adding interactivity and animations to CSS components by managing states. With the `input` element of type `checkbox` or `radio` the two states are simply checked (on) or unchecked (off). We will manage these states to add interactivity to our gem stone collection. Lets revisit our old example now, before we modify it further: http://codepen.io/bluehabit/pen/qreqQE

HTML
```
<div class='gems'>
  <input type="radio" id='topaz' name='gem-stones'>
  <label for="topaz">Topaz</label>
  
  <input type="radio" id='amethyst' name='gem-stones'>
  <label for='amethyst'>Amethyst</label>
    
  <input type="radio" id='diamond' name='gem-stones'>
  <label for='diamond'>Diamond</label>
</div>
```

Lets begin by using a CSS combinator to specifically target input elements that are in the checked state by using the `:checked` pseudo selector, this will appear as `input:checked`.  

This won't do much by itself. Next we will need to add some sort of visual indication that the item has been selected. We can do this by targeting an adjacent label. Adjacent? That sounds like one of the selectors we performed earlier, adjacent sibling selector, recall it uses the `+` symbol. Lets give this a try now. 

```
input:checked + label {
  background-color: #a686cd;
}
```

The CSS combinator identified above is looking for an `input` element that is in the `:checked` state. The `+` symbol indicates the adjacent sibling selector. Therefore it is looking for an adjacent sibling, in this case a `label`. Once it has been found, we will make the background color purple. This may not seem super exciting right now, but this is the framework that will enable us to create much more advanced user interaction later. 

Once finished it should look something like the below codepen if you would like to check your work. 

Codepen: http://codepen.io/bluehabit/pen/WpBbNG 

### Checked Attribute

One thing you may have noticed is that by default, when the user loads the page, no item is selected. If you would like an item to be selected by default we can utilize the `checked` attribute for the input element. Lets say we want topaz to be selected by default. We can revisit this line of code from the HTML `<input type="radio" id='topaz' name='gem-stones'>`

All we have to do is add the following attribute, `checked='checked'`. As we can see in the finished markup here `<input type="radio" id='topaz' name='gem-stones' checked='checked'>`. Compare your work to the codepen shown below. 

Codepen: http://codepen.io/bluehabit/pen/ZegLYN


## Skeleton Frameworks

![skeleton-framework](http://imgur.com/LdZnIKm.gif)

Lets continue building on the framework for more complex user interactions. This example will be the skeleton for building a CSS only tabs components, but this framework can have many more applications such as an image gallery, or accordion. We will combine what we learned in the previous example while introducing a few new ideas. 

Often when we select something, we want a particular action to take place. For example when we click a tab we expect new information to show up, and hiding the rest. We can create this behavior by adding seperate `div` container to store all of our content. This container will only show specific content when a specific input element is checked. 

Here will mark the beginning of the project if you would like to follow along. 

Codepen: http://codepen.io/bluehabit/pen/OmLdzN

The content below is the seperate `div` container. Notice how the content all has its own unique `id` assigned to it, for example: `furniture-content` or `kitchen-content`. 

```
<div class='content'>
	<div id='furniture-content'>
		<p>Stuff about furniture</p>
	</div>

	<div id='homedecor-content'>
		<p>Stuff about homedecor</p>
	</div>

	<div id='kitchen-content'>
		<p>Stuff about kitchens</p>
	</div>
</div>
```

We will manage the state changes for the inputs so its corresponding content in the container reveals itself.

### Setting Content to display:none

As you may have noticed all of this information: 'stuff about furniture', 'stuff about homedecor' and 'stuff about kitchens' is visible by default, we will need to change that. For this important step we will simply target the `.content` container and set its `divs` to `display:none`. We will use a combinator to accomplish this.

```
.content > div {
  display: none;
}
```

Lets read through this combinator to better understand it. We will be targeting the `.content` class and then use the `>` symbol to select its direct children of type `div`. For the elements selected with this combinator we will set their `display` to `none`. 


Its important here that we use the `display` property here and set its value to `none`. The reason for using `display` is it doesn't take up any space in the document when its value is set to `none`, it removes it from the normal flow. In contrast, if we were to use a property such as `visibility` and set it to `hidden` the text would still remain hidden; however, the content would be stacked on top of one another because it would still exist in the normal flow of the document.


### id:checked Combinator

The next very important concept is how we can use the type selector, in this case `id`, and combine it with a pseudo selector, in this case `:checked'`. 

Lets work through our first example. We only want the content for `furniture-content` to show up when its corresponding input element with the `id` of `furniture` is selected. We can provide this interactivity using the `id:checked` combinator.

```
#furniture:checked ~ .content #furniture-content {
  display: block;
}

```

Lets break it down and step through this code. We begin by using the `id` selector to select `#furniture`, while also utilizing the `:checked` pseudo selector to manage the state. We only want this behavior to occur when it is `:checked`. 

Then we use the `~` symbol to select its sibling with the class `.content`. From here there is a *space* between the elements indicating a descendent selector. Therefore, we are selecting all descendents of `.content` with the `id` of `#furniture-content`. When this item is selected we will set the `display` to `block` from `display: none`. 

Lets finish up the other selectors now. 

```
#furniture:checked ~ .content #furniture-content {
  display: block;
}

#homedecor:checked ~ .content #homedecor-content {
  display: block;
}

#kitchen:checked ~ .content #kitchen-content {
  display: block;
}
```

We now have our interactivity, with this simple scaffolding we have achieved the desired effect. Only specific content will reveal itself based on the input element that is selected.

### refactoring

There is nothing wrong with the above code, but we can refactor it a bit more so its more condensed. Lets do that now.

```
#furniture:checked ~ .content #furniture-content, 
#homedecor:checked ~ .content #homedecor-content, 
#kitchen:checked   ~ .content #kitchen-content {
  display: block;
}
```

Much more pleasant on the eyes. Lets take a look at the finished example below. 

Codepen: http://codepen.io/bluehabit/pen/OpKWyQ

### Examples Built with this Framework

Now that you understand the basic framework, lets take a look at some finished components to see what we can accomplish with it. Notice how many different types of components we have. While these examples may appear quite different, structurally they are nearly identical. They have been beautified to be visually pleasing, but the underlying foundation remains the same. 

### Accordion 
![accordion-demo](http://i.imgur.com/wIsaQi6.gif)

Codepen: http://codepen.io/bluehabit/pen/LWwxeW

### Image Gallery
![image-gallery](http://imgur.com/rBXH33r.gif)

Codepen: http://codepen.io/bluehabit/pen/VpoPQM

### Tabs
![tabs-demo](http://imgur.com/z6AhFmP.gif)

Codepen: http://codepen.io/bluehabit/pen/WpVRzm

## Framework for CSS Only Image	Carousel

![carousel-demo](http://i.imgur.com/hqmMYFN.gif)

Notice in the source code how we are setting the display of the left and right arrows to `display: none` as well as setting the slider image to `display: none`, as you can see below

```
   .group label {
    background-color: #69c;
    border: solid 1px black;
    display: none;
    height: 50px;
    width: 50px;
  }
```

```
  .group input ~ .content {
    border: solid 1px black;
    display: none;
    height: 350px;
    margin: 0px 60px;
    position: relative;
    width: 300px;
  }
```

The other important point is `<input>` and its corresponding `<label>` do not have to be adjacent to each other in the HTML markup. As we are accustomed to seeing, for example.

```
<input type='radio' id='topaz' name='gems'>
<label for='topaz'>Topaz</label>
```

Instead, they can be in different containers themselves. That is central to making this particular example work. As you can see in the source code:

```
    <div class="group">
      <input type="radio" name="test" id="0" value="0" checked='true'>
      <label for="4" class="previous">&lt;</label>
      <label for="1" class="next">&gt;</label>
      <div class="content">
        <p>panel #0</p>
        <img src="http://i.stack.imgur.com/R5yzx.jpg" width="200" height="286">
      </div>
    </div>
```
**Simple Example:**
![simple-example](http://imgur.com/mqkbJ8U.gif)

Check out a more simple example here: https://codepen.io/bluehabit/pen/NgpKxv

**Key to making this work:**
![key-example](http://imgur.com/YdfpBwm.png)

![key-animated](http://imgur.com/2qWgv2t.gif)

*Notice* how before we begin to style the carousel such that only one panel is visible at a time, the user click is already working correctly. If the user clicks `<` on the second panel it will correctly set the input of `id='1'` (the first panel) to checked. Similarly on the second panel if we click on `>` it will move forward to the next panel, selecting the input of `id='3'` Check out the `gif` image above. In other words, the `<label for>` acts as a button that changes something when the user clicks

Check out the exapmle here: https://codepen.io/bluehabit/pen/KqWPex


Codepen: https://codepen.io/bluehabit/pen/GErVja
Stackoverflow thread: https://stackoverflow.com/questions/30295085/how-can-i-make-an-image-carousel-with-only-css

**Final Basic Framework**
![final-skeleton](http://imgur.com/h8nbcFH.gif)

Demo: https://codepen.io/bluehabit/pen/dRvbwp


Other good resources: 

Excellent Example:
**http://www.cssscript.com/pure-css-image-carousel-with-arrows-bullets-navigation/**

http://qnimate.com/creating-a-slider-using-html-and-css-only/#prettyPhoto

https://www.smashingmagazine.com/2012/04/pure-css3-cycling-slideshow/

https://kmturley.blogspot.com/2015/02/responsive-css-only-carousel.html

https://stackoverflow.com/questions/21647389/implement-a-css-only-slideshow-carousel-with-next-and-previous-buttons

## Using Targeted URI's for Animations

Another state method we will utilize for building animations revolves around using the `href` attribute of `a` elements. Whenever you visit a link there is a unique fragment identifier. We can use the `id` to create a unique URI to visit that will result in a particular event occurring. In the case of our example, a modal alert that pops up to alert the user. One of the key components of building components using this method is the `:target` pseudo selector along with URI fragment identifiers that we will discuss in much greater detail. 

![target-uri](http://imgur.com/N0BmIKz.gif)

Codepen: http://codepen.io/bluehabit/pen/pPzzWp

## :target

The `:target` pseudo-class will look for an element with an `id` matching the fragment identifier of the URI of the document. Fragment identifier, URI what is all of this - let's take a quick look.

![fragment](http://imgur.com/kA5QI16.png)

Let's say you are visiting wikipedia to read more information about the history of the automobile. The main page you would likely land on is `https://en.wikipedia.org/wiki/Car`. Many times sections have their own unique ID, so that the user can click a particular link on the table of contents and the page will automatically jump to that section.

Lets continue looking at our wikipedia example. If we view the page source for different sections we can see a pattern emerging. Each section has its own unique ID that will serve as *fragment identifier*. 

`<h2><span class="mw-headline" id="History">History</span></h2>`

Notice the `id` of `History`, this will be the  *fragment identifier* in the URI for this section. 

`<h2><span class="mw-headline" id="Safety">Safety</span></h2>`

Notice the `id` of `Safety`, this will be the  *fragment identifier* in the URI for this section. 

`<h2><span class="mw-headline" id="Environmental_impact">Environmental impact</span></h2>`

Notice the `id` of `Environmental_impact`, this will be the  *fragment identifier* in the URI for this section. 

You get the idea. The point is we can target these *fragment identifiers* in our URIs to jump to specific sections of the page. From our root URL `https://en.wikipedia.org/wiki/Car` we can add the fragment identifiers to jump, all we are doing is providing the `id` as part of the fragment identifier to jump to that section. 

`https://en.wikipedia.org/wiki/Car#History` will jump to the History section, notice at the top of your browser how `#History` is added to the URI.

`https://en.wikipedia.org/wiki/Car#Safety` will jump to the Safety section, notice at the top of your browser how `#Safety` is added to the URI.

`https://en.wikipedia.org/wiki/Car#Environmental_impact` will jump to the Environmental Impact section, notice at the top of your browser how `#Environmental_impact` is added to the URI. 

Lets work through a basic example to see how we can use fragment identifiers. In the HTML we can see two `a` tags. 

```
<a href='#'>Home</a>
<a href='#alert1'>Click Me</a>
```

The `href` attribute with the value of `#` will take you to the same page. However, the second `a` tag has an `href` value of `#alert1` this is a fragment identifier. Notice our `div` has the `id` of `alert1`, the same as the fragment identifier value we provided. 

When we use `:target` we can now specify that specific fragment identifier. 

```
#alert1:target {
  background-color: pink;
}

```

When the `id` *alert1* is the `:target` it will change the background-color to pink. 

Codepen: http://codepen.io/bluehabit/pen/OmLLQb

## CSS Animations

CSS animations are made up of two basic building blocks.

**Keyframes** - define the stages and styles of the animation.

**Animation Properties** - assigned using the **@keyframes** to specific CSS elements and define how it will be animated.

### Building Block #1: Keyframes

Keyframes are the foundation of CSS animations. They define what the animation looks like at each stage of the animation timeline. Eacg stage of an animation is known as a keyframe. Each @keyframes is composed of:

* **Name of the Animation**: A name that describes the animation, for example `fadeOut`. 
* **Stages of thh Animation**: Each stage of the animation is represented as a percentage. `0%` represents the beginning state of the animation. `100%` represents the ending state of the animation. Multiple intermediate states can be added in between. Note, you can use the keyword `from` instead of `0%` and `to` instead of `100%`. 
* **CSS Properties**: The CSS properties defined for each stage of the animation timeline, each stage of the animation can have its own unique CSS properties.

![box-spin](http://imgur.com/39pnhqX.gif)

Lets take a look at a simple `@keyframes` I've created named *'rotate360'*. This `@keyframes` has two stages, aka 2 keyframes. At the first stage `0%` we have a `transform: rotate(0deg)`. In the final stage we set the transform value to `transform: rotate(360deg)`. The end result is the box rotating a full 360deg. 

Notice that the element we are targeting, in this case a `div` which representing a green box,  is where we specify the `animation` to occur. Not only that be also specify a `animation-duration`, `animation-timing-function` and `animation-iteration-count`. More on these properties later.


Element
```
div {
  animation: rotate360 3s linear infinite;
}
```

Animation
```
@keyframes rotate360 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

Codepen: http://codepen.io/bluehabit/pen/bqXqqG


### Building Block #2: Animation Properties

Once the `@keyframes` are defined, the animation properties must be added in order for your animation to function.

Animation properties do two things:

1. They assign the @keyframes to the elements that you want to animate.
2. They define how it is animated.

The animation properties are added to the CSS selectors (or elements) that you want to animate. You must add the following two animation properties for the animation to take effect:

* `animation-name`: The name of the animation, defined in the `@keyframes`
* `animation-duration`: The duration of the animation, in seconds (e.g., 5s) or milliseconds (e.g., 200ms

Lets take a look at a few commonly used animation properties individually. 

# Animation Properties

`animation-name` the name of the `@keyframes` animation you want to play

`animation-duration` can be in seconds for example `2s` or milliseconds `300ms` 

`animation-iteration-count` how many times the animation plays before stopping. 

`animation-direction` can take your animation and play it in `reverse`, `alternate` or `alternate-reverse` 

`animation-delay` delays the start of the animation by a specific amount of time. For example `2s` or milliseconds `300ms`

`animation-fill-mode` CSS animations by default do not effect the element until the first keyframe is played and stops once the last keyframe has finished. `animation-fill-mode` can override this behavior allowing to do things such as holding the last keyframe.

## Animation Property Shorthand

Animation properties also have a short hand version. 

Before:

```
.item:hover .ball{
  animation: motionBlur;
  animation-timing-function: ease;
  animation-duration: 1.3s;
  animation-iteration-count: 1;
  animation-fill-mode: forwards;
}
```

After:

```
.item:hover .ball {
  animation: motionBlur 1.3s 1 ease forwards;
}
```

## Animation Delay

`animation-delay` can set a delay before the animation plays. This is useful because we can reuse the same animation for multiple elements on the screen, but stagger them using `animation-delay`. 

Note in this example how I am giving a separate animation to the main `.container` so it fades in initially when the animation begins.

```
.container {
  animation: fadeIn 1s 1;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  } 
  to {
    opacity: 1; 
  }
}
```

Codepen: http://codepen.io/bluehabit/pen/zwOxNZ

## animation-fill-mode

`normal` Default behavior. Notice in the example below how once the animation completes, it resets to the first key frame. 

Codepen: http://codepen.io/bluehabit/pen/eWOVYG

`forwards` Useful for holding the last key frame of an animation. Notice how the ball remains at the right hand side of the screen.

Codepen: http://codepen.io/bluehabit/pen/ZKzrEJ


## Filter Properties

We can also use `filter` properties with our animations to create stunning effects.

## grayscale

![weth](http://imgur.com/0SPt9K3.gif)

Codepen: http://codepen.io/bluehabit/pen/WjevQo

## Animation Iteration Count

The `animation-iteration-count` 

`infinite`

`#` value

# filter: blur()

![motion-blur](http://imgur.com/6o4JRXV.gif)

Can blur pixels out. In this example using `blur` to mimic the effects of motion blur. 

Codepen: http://codepen.io/bluehabit/pen/GmKMLj

Codepen: http://codepen.io/bluehabit/pen/GmKMLj

-----


## TranslateX

![translateX](http://imgur.com/biPSpYR.gif)

Moves the element horizontally, left or right. 

Codepen: http://codepen.io/bluehabit/pen/OmLPrL

## TranslateY

![translateY](http://imgur.com/2RplRik.gif)

Moves the element vertically, up or down. 

Codepen: http://codepen.io/bluehabit/pen/OmLPdJ

## Scale

![scale](http://imgur.com/rSaxI2Z.gif)

Modifies the size of an element, it can either enlarge in size or shrink.

Codepen: http://codepen.io/bluehabit/pen/KmPKNr

## Rotate

![rotate](http://imgur.com/nzi2h7a.gif)

Defines an angle to rotate an element. There is also `rotateX`, `rotateY` and `rotateZ`. 

Codepen: http://codepen.io/bluehabit/pen/bqXqqG

## Opacity

![opacity](http://imgur.com/PpA3isn.gif)

Sets how transparent an element is on the scale from `0` to `1`. For example `opacity{0.25}`.

Codepen: http://codepen.io/bluehabit/pen/rmBaPG

## Cubic-bezier

Can be used to give your more control over your `animation-timing-function`. 

Before:
```
.item:hover .ball {
  animation: motionBlur 1.3s 1 ease;
}
```

After:
```
.item:hover .ball {
  animation: motionBlur 5.3s 1 cubic-bezier(.09,1.83,.37,.78);
}
```

## Transforms Shorthand
Transformations can all be written on a single line. Instead of putting each transformation on its own line.

Before:
```
transform: rotate(395deg);
transform: translate(130px, 120px);
transform: scale(.69)
```

After:
`transform: rotate(395deg) translate(130px, 120px) scale(.69)`.

## Animating SVGs

### Intro to SVGs

Next lets explore animating SVGs (scalable vector graphics). Unlike pixel based images that can become blurry and distorted once scaled beyond their intended resolution, SVGs can scale to any size small, or large, and still maintain their graphical fidelity. 

SVGs can be found all over the internet, a few of my favorite resources to download them include:
* http://www.flaticon.com
* http://fontawesome.io/

You can also create your own SVG graphics using Adobe Illustrator if that is your fancy.
After downloading a SVG you can open the source in your text editor and it may look a bit complicated. This will be the raw code that we paste into our HTML file.

![raw-svg](http://imgur.com/z5qviZQ.png)

If you have a copy of Adobe Illustrator you can actually view the different layers as they are named within the editor. This makes it easy to visualize what is what before you start targeting different sections in CSS. However, a good portion of the SVGs you download off the internet unfortunately will not be labeled. 

![svg-adobe](http://imgur.com/JJRBQmO.jpg)

Pictured above, opening a SVG image in Adobe Illustrator and viewing different layer names. 

### Targeting SVGs with CSS

Lets take a look at this SVG of a kiwi http://codepen.io/bluehabit/pen/vmBPLK. As you look through the HTML markup you will see different sections such as `path` and `ellipse` these represent different shape layers in the Adobe Illustrator document. Notice how the `path` has an `id` of `bird`, while the `ellipse` has an `id` of `shadow`. We can target these elements just like anything else with CSS and change their color. 

![kiwi](http://imgur.com/hVt9Mfa.png)

## Building a Weather Animation

Now that we know how to target SVGs with CSS lets put our animation skills to the test. Here is what we will be building:

![animated-weather](http://imgur.com/P3XLMzt.gif)

Finished Codepen: http://codepen.io/bluehabit/pen/mWgeRo

Lets Lets download the SVG weather pack found here and follow along http://www.flaticon.com/packs/weather-forecast-2 if you would like to follow along the SVGs from this pack that we will be using for our demo include `storm.svg` and `snowing.svg`. Alternatively, copy and paste the raw SVG code from the codepen here. The benefit to using this is the paths have already been assigned classes by me so they are easy to target. The raw SVG does not have names by default, and unless you have adobe illustrator to view the different paths, you will have to figure out which path represents what by trial and error. 

Raw SVG with edited path names: http://codepen.io/bluehabit/pen/vmBWzJ

Begin by pasting the raw `svg` code into our `index.html` file. 

First we will begin by setting the background to a dark grey color.
```
html {
	background-color: #121212;
}
```

As you may have noticed, these SVGs in there default state are huge. We will go ahead and start working directly with the individual SVGs now. Lets shrink their `width` and `height` to `90px` and set their fill color to `white`. `Fill` to set the color of SVG paths, instead of using properties such as `background-color`. Lastly we will add a bit of breathing room between the two clouds using `margin-left: 50px`.  

Notice how we are selecting these elements with a combinator as discussed earlier. We are selecting the `.weather` container and all of its direct children of type `svg` with the `>` symbol. 

```
.weather > svg {
	width: 90px;
	height: 90px;
	fill: white;
	margin-left: 50px;
}
```

Next we have a `div` container with a class of `.weather` that is storing our weather animations. We will go ahead and use this container to center our animations. 

```
.weather {
	width: 50%;
	margin: 0 auto;
	margin-top: 20%;
}
```

Here is what we have so far:

![clouds](http://imgur.com/UZ9hdri.png)

Our clouds are looking a bit stagnant, don't you think? Lets breathe some life into them and start animating. First lets define our animation using `@keyframes`, I am going to call this animation `cloudBreath`. Next we will set 3 key frames the first at `0%`, the next at `50%` and the last at `100%`. 

As we transition through the key frames we are only modifying the `scale` of the element. The cloud shrinks and inflates slightly to give it a bit of life. 

```
@keyframes cloudBreath{
	0%{
		transform: scale(1.12);
	}
	50%{
		transform: scale(1.2);
	}
	100%{
		transform: scale(1.12);
	}
}
```

Next we need to add the animation to our clouds. I have targeted the specific paths in the raw SVG and assigned them the classes `.cloud` and `.cloud2` both of these represent the two different cloud shapes in the SVG. Lets go ahead and give them `animation: cloudBreath 2s ease infinite`. We will use `infinite` for the `animation-iteration-count` so the animation loops continuously over and over again. 

```
.cloud{
	animation: cloudBreath 2s ease infinite;
}
```

Next we can recycle the same animation and use it for `cloud2` only we will add a slight delay to the animation so it doesn't perfectly sync up with the other clouds animation. We will use `animation-delay: .3s`

```
.cloud2{
	animation: cloudBreath 2s ease infinite;
	animation-delay: .3s;
}
```

As you may have noticed there is some clipping occurring from the animation. The clouds seem to be cut off by a wall, as you can see in the example below. We can fix this by adding some breathing room to the SVGs with some `padding`. 

#### Clipping Example
![clipping-example](http://imgur.com/a2Ki810.gif)

```
svg{
  padding: 35px;
}
```

What you should have so far:

![example-so-far](http://imgur.com/WXiBdCx.gif)

### Animating Lightning Bolts

Lets continue building up our animation by adding life to the lighting bolts. Lets create a new `@keyframes` with the name `thunderClap1`. One thing that may appear new at this juncture is the stacked key frames at the top. This is a preference, if you have multiple key frames that will do the same thing you can stack them on top of one another. To bring the lightning bolts to life the main thing we are going to do is use `transform: translateX(50px)` and `transform: translateY(70px)` to move them downward. While this is occurring we adjust the `opacity` at various points so they appear to flicker. 

```
@keyframes thunderClap1 {
	0%, 31%, 35%, 40%{
		opacity: 0;
	}

	32%{
		opacity: 1;
	}

	41%{
		opacity: .55;
	}
	100%{
		opacity: 0;
		transform: translateX(50px);
		transform: translateY(70px);
	}
}
```

Now lets grab our thunder bolt shapes in the SVG with their classes `.bolt1` and `.bolt2`. Just like we did with the cloudBreath animation. We will make the animation loop indefinitely by giving it the value of `infinite` for `animation-iteration-count`. To reuse the the same animation for `.bolt2` we will stagger the animation by giving it a slight delay `animation-delay: .5s`. 

```
.bolt1 {
	animation: thunderClap1 ease-in-out 2.2s infinite;
	transform: translateY(-50px);
}

.bolt2{
	animation: thunderClap1 ease-in-out 2.2s infinite;
	animation-delay: .5s;
	transform: translateY(25px);
}
```

One thing you might notice is `transform: translateY(-50px)` and `transform: translateY(25px)` in the selectors shown above. What we are doing here is using `translate` to adjust the default positioning of the SVG shapes so they are more staggered before the animation begins. Similar to giving a parent element a position of `relative` and a child element you want to reposition `absolute` and using `top, left, right, bottom` to finely adjust its position. 

#### Before

![thunder-before](http://imgur.com/HVoszA9.png)

#### After

![thunder-after](http://imgur.com/svqWVII.png)

Here is what you should have so far:

![thunder-bolt](http://imgur.com/wNj048X.gif)

### Animating Snow Flakes

Lets get started animating the snow flakes. To do this we are going to create a new `@keyframes` with the name `snowflake` for our new animation. To bring life to the snow flakes we will predominantly be using `transform: rotate` to make the snowflakes appear to spin as they flutter towards the ground. For a final touch we will add `opacity:0` and `scale(.69)` to make the snowflakes shrink and disappear as they approach the ground. 

```
@keyframes snowflake {
	0%{
		transform: rotate(180deg);
	}

	95% {
		transform: rotate(395deg) translate(130px, 120px) scale(.69);
	}
  100%{
    opacity: 0;
  }
}
```

```
.snowflake1, .snowflake2, .snowflake3 {
	animation: snowflake 3s ease infinite;
	transform-origin: center;
}
  
.snowflake3 {
	animation: snowflake 3s ease infinite;
  	animation-delay: .34s;
	transform-origin: center;
}
  
 .snowflake2 {
	animation: snowflake 3s ease infinite;
  	animation-delay: .48s;
	transform-origin: center;
}
```

One important thing to note when using `transform: rotate` you need to specify where the `transform-origin` is. By using `transform-origin: center` it anchors the rotate to the center of each snowflake. Otherwise, strange undesirable rotations may occur. 

If you don't use `transform-origin: center` this happens, while an interesting effect, its not quite what we are trying to achieve.

![strange-transform](http://imgur.com/rDIv1CL.gif)




Here is what your final animation should look like:

![final-animation](http://imgur.com/XwmTj1T.gif)


## Additional Resources

* http://animista.net/
* https://robots.thoughtbot.com/css-animation-for-beginners#building-block-1-keyframes

