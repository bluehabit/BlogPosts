## Real World CSS Issues

![rl-issue1](http://imgur.com/Gu4aaow.png)

Solution:

![r1-solution](http://imgur.com/7LvnXWE.png)

Codepen (before solution applied): https://codepen.io/bluehabit/pen/ZJQqzx

### Z-index

![z-index](http://imgur.com/xSqo3JX.png)

Key here is to give all items with overlap a `position: relative` and then use `z-index` to specify the order in which they stack. 


### Centering Images

Remember, the default `display` of `img` elements is `inline-block`. Which will prevent `margin: 0 auto` from centering it. To fix it change it to `display: block` and then apply `margin: 0 auto`.

Before:
![before](http://imgur.com/gIwryXt.png)

After:
![after](http://imgur.com/N6976Ue.png)
