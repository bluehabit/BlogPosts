## When writing Sass, make DRY (short for Don’t Repeat Yourself) a focus and use Mixins, Inheritance, and Functions and Loops as you see feasible to make it as efficient as possible.

### Sass Directory

```
project
  |
  |-js
  └-scss
  |  |-main.scss
  |  |-buttons.scss
  |  └-forms.scss
  |-css
  |  |-main.css
  |  |-buttons.css
  |  └-forms.css
  └-index.html
```

### Watch entire Sass Directory using `sass --watch .`

![current-dir](http://imgur.com/3w3b91t.png)

If you are in its parent directory `sass --watch sassPrac:sassPrac`



### Issue

![sass-setup](http://imgur.com/SkhBls5.png)

`sass --watch scss:css`

This command will watch entire `directories` for changes in the `scss` and `css` directory, and update them accordingly. Note the default named output for sass `css` files is `input.css`. 

 If you don't have these directories and use `sass --watch scss:css` it will produce `error no such file or directory @ rb_sysopen -scss`.

### Sass to CSS converter: sassmeister

https://www.sassmeister.com/

### lists = arrays
### maps = objects


### Variables

Define variables with `$` for example `$myColor`. Then use the variable in your markup, `.button {background-color:$myColor};`. For best practice do not use a variable if the value will only be used once.

![declaring-variables](http://imgur.com/AKHOAQQ.png)

resulting output:

![output](http://imgur.com/enn4B1K.png)

In Sass you can always check your ouput.css file to see what your input.scss conditionals are doing.

### Nesting

Sass lets us nest CSS selectors in a manner similar to the way HTML is nested. Selector nesting offers a way for style sheet authors to compute long selectors by nesting shorter selectors within each other. For example:

![nested-sass](http://imgur.com/ssZ6xm3.png)

When nesting, it is possible to reference the corresponding selector using the & symbol. This is useful, for instance, when nesting pseudo-classes:

![nested-example2](http://imgur.com/nE48cf2.png)

### Partials

Partials are smaller Sass files included as part of a bigger Sass file. Partial filenames begin with an underscore:` _partial.scss`, `_buttons.scss`, `_forms.scss`, etc. The `_` is very important because it is the hint that lets Sass know that the file is only a partial file and that it *should not be generated into a CSS file*.

Other files include Sass partials by using the `@import` directive.

Please note that, unlike the CSS `@import` directive, the Sass import does not generate another `HTTP request`. The CSS `@import` generates a new HTTP request for each file imported (the browser does a round trip to the server for any CSS file), but the Sass `@import` generates no requests. The Sass preprocessor uses `@import` directives only to combine Sass files into a unique CSS file, which will not include any `@import`.

### Partials Directory

Set it up like this

![partial-directory](http://imgur.com/6jp709w.png)


## `special note:` 

You cannot go from global to partials with variables, in other words define variable in global scss file and use it in subsequent partial files. However, see below. The variables live within their own scope, that is restricted to the file. For example if I use `$myColor: red` and only define that in the main css file, but not the partial, it won't be able to read that and will throw an error. As you can see in the example below.

![partial2](http://imgur.com/CoiU0OK.png)

## `HOWEVER: ` 
You CAN define a variable in a partial file, and then use it in the global file.

![partial3](http://imgur.com/0CwxiKR.png)


### Interpolation aka `placeholders`

Sass supports variable interpolation using the `#{}` syntax. Interpolation, in computer programming, is the process of replacing a placeholder `(#{...})` with its corresponding value. *In Sass, this is useful when we want to use the content of a variable in selectors and property names*.

Input.scss:

![interpolation](http://imgur.com/DJpXJRw.png)

Output: 

![output](http://imgur.com/DJpXJRw.png)

Compiled into CSS: 

```
p.foo {
 border: 2px solid black;
 border-color: red;
}
```


### Mixins

Mixins let us make groups of CSS declarations that we can reuse throughout our site. Like functions, mixins can receive parameters.

To create a mixin, we use the `@mixin` directive, followed by a name and variables inside parentheses: `@mixin mixin-name($variable1, $variable2, ...).'`

To use a mixin (i.e., to embed its code) the `@include` directive is used, followed by the name of the mixin and its arguments.

![mixin](http://imgur.com/zP9ot5C.png)

![mixin2](http://imgur.com/X7AvzjA.png)

When you pass through values to a `mixin` make sure you don't use `" "` marks for example: 

![mixin3](http://imgur.com/2ToFOtk.png)

## Inheritance

Allows us to extend an elements style to another elemnt.

![inheritance](http://imgur.com/BPI75bv.png)

## Operators `+`, `-`, `*`, `/`, `%` and `( )`

## Creating a fluid grid using operators 

![fluid-grid](http://imgur.com/MXO4Sm2.png)

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


### `@media` Directive

![media](http://imgur.com/gSwpXoo.png)


### Custom Functions

![cfunction](http://imgur.com/O3f5D4o.png)

```
## Sass
> 1 Explain how traditional CSS and Preprocessed CSS workflows are different.

With traditional CSS, until very recently, it did not support variables. Writing with a preprocessor is not that much different - the syntax is just like regular CSS; however, we are able to use variable declarations, operations, functions, loops etc. 

First we start with our SCSS compatible file, then we export it to a preprocessor such as SASS or LESS which will generate our final CSS file. 

```

