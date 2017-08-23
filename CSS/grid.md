#### CSS Grid

To convert an HTML container into a responsive `grid-based` container, we first set the `box-sizing` property for *all* HTML elements on the page to `border-box` to include the paddings and borders in the calculated height and width of the columns. 

```
* {
  box-sizing: border-box;
}
```

#### 12-Column Layouts

Why the number 12? Since a standard viewport is `960 px` wide, each column turns out to be `80 px`, or `8.33%` of the total width. The total width of all the columns in a row must strictly total 100%; in other words, the number of columns must add up to 12.

To implment we will create 12 column classes, one for each column size. Before we learn how to create this grid layout lets refresh the `*=` attribute selector in CSS.

#### CSS3 [attribute*=value] Selector


Source: https://www.w3schools.com/cssref/sel_attr_contain.asp

```
<div class='coffee'>
  <p>Yummy Coffee</p>
</div>

div[class*="coffee"] {
    background: #5e4423;
    color: white;
}
```

Now lets apply this to our grid.

```
[class*="col"] {
  float: left;
  padding: 10px;
  background-color: tomato;
  border: 2px solid black;
  opacity: 0.7;
}
```

The attribute selector picks all the classes with a value having common text `col`, and it assigns it the `float:left`. Each row must wrap within the container, ensuring the toal number of columns equals 12 and there are no gaps in the layout. To do this we createa CSS class rule named `container` as shown.

```
.container {
  display: block;
}
```

### Our Working Grid

https://codepen.io/bluehabit/pen/xLzyjO

Notice, again each column is `8.33%` wide. 

Column 1 - width: 8.33%
<hr>
Column 2 - width: 16.66%
<hr>
Column 3 - width: 25%
<hr>
Column 4 - width: 33.33%
<hr>
Column 5 - width: 41.66%
<hr>
Column 6 - width: 50%
<hr>
Column 7 - width: 58:33%
<hr>
Column 8 - width: 66.66%
<hr>
Column 9 - width: 75%
<hr>
Column 10 - width:83.33%
<hr>
Column 11 - width:91.66%
<hr>
Column 12 - width:100%

### Grid Framework, Skeleton

We can also leverage a framework that already has this functionality built in rather than making it ourselves. You can download skeleton here: http://getskeleton.com/

Once you download we only need to keep the `normalize.css` file and `skeleton.css`. Import using `@import url(skeleton.css)` or use `link` in the `header` section. 

An example of how we use this framework: 






