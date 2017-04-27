> And when a man writes, he thinks harder ... or maybe just more specifically
> -Mike Hanlon, It

placeholder - working on word.docx.

## SASS

Variables make our code much easier to maintain, and less cumbersome to update. For instance, let's say we had a large CSS file where we wanted to update all instances of the color of `pink` to `#ee1786` for all the different components on the site. To do this by hand could be tedious.
Instead, using a CSS preprocessor we can declare a variable and have all of our components reference this exact color. Now we only have to update it in one spot and it will propagate throughout the whole page.

```
@mixin box-shadow {
  -webkit-box-shadow: 10px 10px 31px 0px rgba(0,0,0,0.75);
  -moz-box-shadow: 10px 10px 31px 0px rgba(0,0,0,0.75);
  -ms-box-shadow: 10px 10px 31px 0px rgba(0,0,0,0.75);
  box-shadow: 10px 10px 31px 0px rgba(0,0,0,0.75);
}
 
div.tab {
  /* Here we include the box-shadow mixin */
  @include box-shadow;
  background-color: grey;
  width: 200px;
  padding: 10px;
  p { /* Nesting: this will generate a "div.panel p" selector */
    font-weight: bold;
  }
}
```

