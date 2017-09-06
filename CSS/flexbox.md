## Using Flexbox and Grid Together 

https://twitter.com/guilh/status/860985527574700032

Awesome Guide on this
https://getflywheel.com/layout/combine-flexbox-and-css-grids-for-layouts-how-to/

# Flexbox

CSS Tricks a Complete Guide to Flexbox
https://css-tricks.com/snippets/css/a-guide-to-flexbox/


### Important!

The default for `flex` is `row` and `nowrap` just by setting the `display` to `flex`. 

### Also Important!

Also, only one `display` type per element. For example if you do something like the below markup - you will break your layout. Pick either `display: flex` or `display: inline-block`. One or the other.

![important](http://imgur.com/9BX5Get.png)




### Getting Started

To get started using Flexbox layout use the CSS property `display: flex` or `display: inline-flex`. Setting this property on the *parent* element will cause all its child elements to inherit the flex property. 

```
.flexbox-container{
  display: flex;
}
```


```
<div class='flexbox-container'>
   <ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>3</li>
   </ul>
</di
```

The `div` with the class of `flexbox-container` is the parent element or *flex container*, and its children the `li` will inherit the flex property, these are the *flex items*. 

**flex lines** === **axes (cross, major)**

## Flexbox Properties

### `flex-direction`

![flex-03](http://imgur.com/nGN5nyi.png)

`flex-direction` sets the orientation of the *flex items within the flex container*. We can align them horizontally using `flex-direction: row`, or we can align them vertically using `flex-direction: column`. 

# Main Axis

### `row`

The `flex-direction` property specifies how the flex items are laid out within a flex container. This is done by setting the direction of the flex containers primary axis. To set the direction to be horizontal, use the value `flex-direction: row` or `flex-direction: row-reverse`.

![flex-01](http://imgur.com/L9gio7G.png)

http://codepen.io/VagrantStory15/pen/YVzEoV

### `column` 

To put them in column order use `flex-direction: column` or `flex-direction: column-reverse` 

![flex-02](http://imgur.com/e5renw5.png)

http://codepen.io/VagrantStory15/pen/GmRyRy


### `flex-wrap`

`flex-wrap` defines whether the flex items are forced in a single line or can be flowed into multiple lines. The default value for `flex-wrap` is `nowrap`. *Make certain* that the direct parent is the *flex container* or else it may not work as shown below.

`nowrap` example: http://codepen.io/VagrantStory15/pen/EmxLXg
`wrap` example: http://codepen.io/VagrantStory15/pen/ybLjoL
`wrap-reverse` example: http://codepen.io/VagrantStory15/pen/WjNJEW

----

### `flex-flow`

Short hand for `flex-direction` and `flex-wrap` on a single line.

```
.flexbox-container{
  flex-flow: <flex-direction> || <flex-wrap>;
}
```

### `justify-content`

Helps redistribute the empty space remaining after *flex items* are positioned. Can sort of think of this as the `float: left` or `float: right` equivalent. The `justify-content` property aligns flex items along the **main axis** of the current line of the flex container.

`justify-content: flex-start`  http://codepen.io/VagrantStory15/pen/EmxLbN

![flex-06](http://imgur.com/QxBGIwF.png)

`justify-content: flex-end` http://codepen.io/VagrantStory15/pen/dWyeZZ

![flex-07](http://imgur.com/wac0rU5.png)

`justify-content: center`

![flex-08](http://imgur.com/oBRYUfr.png)

`justify-content: space-between`

![flex-09](http://imgur.com/0t5KmIr.png)

`justify-content: space-around`

![flex-10](http://imgur.com/ylpBCCO.png)

# Cross Axis

### `align-items` 

Similar to `justify-content` only it works with the **cross axis** instead. `align-items` can hold different values such as `stretch`, `flex-start`, `flex-end`, `center` and `baseline`. Must give the *flex items* a `flex:` value such as `1`. `flex: 1` means: `flex-grow: 1`, `flex-shrink: 1`, `flex-basis: 0%`

Good summary here: https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties#alignitems

CSS Tricks codepen here: https://css-tricks.com/almanac/properties/a/align-items/

Codepen: http://codepen.io/VagrantStory15/pen/JNjvqO 
**Important** In order to view the changes happening using `align-items` you must make sure the *flex container* is tall enough. To make these changes visible I had to make the height 20%. In codepen, that doesn't work for some reason so I had to use a fixed `height` of `200px`

![flex-11](http://imgur.com/uTv5tJH.png)

`align-items: flex-end`

![flex-12](http://imgur.com/7BQX92n.png)

`align-items: flex-start`

![flex-13](http://imgur.com/kyCwLmk.png)

`align-items: center`

![flex-14](http://imgur.com/cU7VNmI.png)


`align-items: stretch`

![flex-15](http://imgur.com/LzZ8EcJ.png)

This is the DEFAULT value if nothing else is applied. 

### `align-content` 

**NEED TO REREAD THESE PROPERTIES, CURRENTLY LOST ON THEM**

`align-content` is very similar to `align-items` only it doesn't align flex items, it aligns flex containers lines *within* the flex container. The size of the items are not modified when we use `align-content`; rather, the space between the items is distributed along the flex lines. `align-content` helps us align items along the flex lines.

The word is kind of confusing, even though it says 'content' in `align-content` we are actually adjusting the **flex lines**. 

# Flex ITEM properties

### `flex-grow`

![flex-16](http://imgur.com/0pCgyhO.png)

How much a flex item can *grow* in the main direction if there is free space. The default `flex-grow` value is `0`. If all flex items have the same `flex-grow` value, all items have the same size in the container. The growth in the size of the flex item will be relative to its adjacent siblings. 

### `flex-shrink`

Shrinks flex item relative to its neighbor. A value of `0` will make the item immune to shrinking, and a value of `1` indicates no change in size.

**Why is flex shrink not working?????** get this example to work: http://codepen.io/VagrantStory15/pen/XRWYPq

### `flex-basis`

Allows us to specify the size in absolute CSS units (pixels, em, rem etc.), the default value is `auto`. In this example setting the first child to be `250px` wide. 

![flex-17](http://imgur.com/FYPmOFA.png)

### `flex` shorthand

The `flex` property is the shorthand notation for `flex-grow`, `flex-shrink` and `flex-basis`. The syntax is as follows:
```
.flexbox-item{
  flex: auto | none || [<flex-grow> | <flex-shrink> | <flex-basis>];
}
```

For example `flex: auto (2, 1 auto)` is a valid value for the flex property


### `order` 

The `order` property controls the order in which the items will be laid out along the main axis. If no order is provided, they are positioned in the sequence of their *source order*. 

```
.flexbox-item{
  order: <integer>;
}
```

### `align-self` 

The best most convenient property saved for last. All the `ul li` have `align-items: center`, except for the first child we gave `align-self: stretch`. 

![flex-20](http://imgur.com/dzixI5f.png)

Syntax:
```
.flexbox-item{
  align-self:  auto | baseline | center | flex-end | flex-start | stretch;
}
```

## Flexbox realworld application

Before:https://codepen.io/bluehabit/pen/ZKVNjq
After: https://codepen.io/sbchittenden/pen/EmGLMR

**Alternative Solution** Using pseudo elements `:before` instead of a `div` inside of the `li` 
https://codepen.io/sbchittenden/pen/rmodPL

Another approach for bar graphs, melissa's example: 
https://codepen.io/anon/pen/JWgRaa?editors=0110

# CSS Grid System

The flexbox approach seems like the best approach, but it has poor support among modern web browsers. As a result its geared toward smaller components within a website, like a navigation bar. **To apply its logic to the entire site would cause the constant re-rendering of elements whenever the viewport resolution changed by even a slight margin.** What we really need is a grid structure that can act as a placeholder for elements.

## Grid Concept

The grid concept isa column-based layout for positioning elements on the viewport. This approach is called the **CSS Grid System**. The basic concept of a CSS based grid layout is the idea of the device width being split into a set of columns. A responsive grid has a 12-column layout that spans the total width of the device.

Before frameworks such as Bootstrp, 12 column layouts were implemented by writing custom CSS classes. 

## Implementing a Grid

First step
```
* {
  box-sizing: border-box;
}
```

There is a very important reason that we commonly use a 12 column layout. Since a standard viewport is `960` pixels wide, each `column` turns out to be `80` pixesl, or `8.33%` of the total width. Next we need a way to group columns together. 

What we will do is create a system of columns that can be grouped together according to the width requirements of the element it will hold. As a result we will create `12` CSS classes, one for each column size. If we need to create a placeholder that is eight columns wide, we can simply assign the value `col8` to the `class` of that particular element.

The caveat here is that the layout is 12 columsn wide and the columns need to be arranged next to each other. To achive this, we use the attribute selector to target all the column classes at once and float them to the left as shown in the code below.

```
[class*="col"] {
  float: left;
  padding: 10px;
  background-color: tomato;
  border: 2px solid black;
  opacity: 0.7;
}
```

The attribute selector picks all the classes with a value having a common text `col` and assigns it `float:left`. Each row must wrap within a container, **ensuring that the total number of columns equals 12 and there are no gaps in the layout**. To do this we create a CSS rule named `container`.

```
.container {
  display: block;
}
```

### Column Example Layouts

![col-a](http://imgur.com/78PjzHe.png)

and

![col-b](http://imgur.com/wy3PyZk.png)

