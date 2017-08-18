### Issue

![sass-setup](http://imgur.com/SkhBls5.png)

`sass --watch scss:css`

This command will watch entire `directories` for changes in the `scss` and `css` directory, and update them accordingly. Note the default named output for sass `css` files is `input.css`. 

 If you don't have these directories and use `sass --watch scss:css` it will produce `error no such file or directory @ rb_sysopen -scss`.

### Sass to CSS converter: sassmeister

https://www.sassmeister.com/

### lists = arrays
### maps = objects


### Declaring Variables
![declaring-variables](http://imgur.com/AKHOAQQ.png)

resulting output:

![output](http://imgur.com/enn4B1K.png)

In Sass you can always check your ouput.css file to see what your input.scss conditionals are doing.

### Interpolation aka `placeholders`
![interpolation](http://imgur.com/ulgbP5z.png)

### Mixins
![mixin](http://imgur.com/zP9ot5C.png)

![mixin2](http://imgur.com/X7AvzjA.png)

Mixins let us make groups of CSS declarations that we can reuse throughout our site. Like functions, mixins can receive parameters.

To create a mixin, we use the `@mixin` directive, followed by a name and variables inside parentheses: `@mixin mixin-name($variable1, $variable2, ...).'`

To use a mixin (i.e., to embed its code) the `@include` directive is used, followed by the name of the mixin and its arguments.

## Operators `+`, `-`, `*`, `/`, `%` and `( )`

## Sass Control Directives: `@if`, `@for`, `@each` and `@while`

### `@if`

![if](http://imgur.com/MrbDrW4.png)

### `@if`, `@else if`, `@else`

![if2](http://imgur.com/H6FFjkD.png)

### Conditional Statements Used with Mixins!

![conditional-with-mixin](http://imgur.com/ph97fDO.png)

### Loops, `@for` and `@each` and `@while`

For uses a counter to loop through a given number of times. Each applies to each item in the array or object.

![for](http://imgur.com/aMm0OSr.png)

#### List Example

![each](http://imgur.com/qwLBEZH.png)

#### Map Example

![map](http://imgur.com/QJagTwP.png)

### Functions

![functions](http://imgur.com/MTnlqaB.png)

### Putting it all together 

![summary](http://imgur.com/RDU8yEC.png)

![summary2](http://imgur.com/pB0nNEm.png)

### Using mixins within loops and conditional statements

Must declare the mixin first, then it can be called later as shown below.

![mixin-ex2](http://imgur.com/iM429pi.png)



```
## Sass
> 1 Explain how traditional CSS and Preprocessed CSS workflows are different.

With traditional CSS, until very recently, it did not support variables. Writing with a preprocessor is not that much different - the syntax is just like regular CSS; however, we are able to use variable declarations, operations, functions, loops etc. 

First we start with our SCSS compatible file, then we export it to a preprocessor such as SASS or LESS which will generate our final CSS file. 

```

