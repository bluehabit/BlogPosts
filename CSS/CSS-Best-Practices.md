### Autoprefixer

Some newly introduces css properties (such as Flexbox and CSS transitions) don't have build-in standardized support across different browsers, and some properties have different implementations. To address this, vendor prefixes were added to these properties.  These prefixes let a browser render its own version of a certain property until its standardized. 

https://github.com/sindresorhus/sublime-autoprefixer

another tool https://autoprefixer.github.io/

You can also use `code pens` autoprefixer.

![code-pen-autoprefixer](http://imgur.com/kR81dZ5.png)

### CSS minification

#### Two methods `minify` or `compress`

#### Minify

To `minify` your code, means to remove any `white space`, thereby making the final file the web page renders smaller, decreasing loasd times. Note, the final output will also have comments removed.

https://cssminifier.com/

Before/After minification

![minify](http://imgur.com/ZIMQwJU.png)

#### Compress

https://csscompressor.com/

### CSS Resets & Normalization

#### CSS Normalization

This will make sure your website appears consistant accross all major browsers. It provides a basic foundation to build upon, with some inherit styling provided.

https://necolas.github.io/normalize.css/


#### CSS Reset

Resets will strip all default styling from the page, giving an author a blank canvass. This means removing basic styling from `h1` through `h6`, `em` and `strong`. 

http://meyerweb.com/eric/tools/css/reset/
