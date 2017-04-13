# Nodelists vs HTML Collections

This sort of confused me too on my own learning, as you pointed out `forEach` is listed as current method for `nodeLists` on MDN.

To use `forEach` consider the following DOM manipulation snippet:

HTML
```
<ul id='myUL'>
	<li>Red</li>
	<li>Blue</li>
	<li>Yellow</li>
</ul>
```
JS
```
var ul = document.getElementById('myUL')
var ulList = ul.children
//ulList is a HTMLCollection
```
`ul.children` is a `HTMLCollection`, not a `nodeList`.  We can verify this using `instanceof`. 

```
console.log(ulList instanceof HTMLCollection) -> true
```
Oh, another interesting `instanceof` is `element`. For example `console.log(ul instance HTMLElement) ->true`

Note, `typeof` will not work for determining this, as it only works on primitive values. Alternatively, you can also use the `dir` command to check the type as shown below:

![example1](http://imgur.com/zxqg2L0.png)

We can convert `ulList`, a `HTMLCollection`, into an array so we can use `forEach` on it. To convert this`HTMLcollection` into an array we can use the built in method `Array.from()` as shown in the following code:

```
var ul = document.getElementById('myUL')
var ulList = ul.children
//ulList is a HTMLCollection

var array = Array.from(ulList);
//convert HTML collection into array

array.forEach(function(item){
	console.log(item)
})

//<li>Red</li>
//<li>Blue</li>
//<li>Yellow</li>
```

This allows us to use `forEach` to loop through each item. But consider if you did not first convert `ulList` and left it as an `HTMLcollection`. 

```
var ul = document.getElementById('myUL')
var ulList = ul.children
//ulList is a HTMLCollection

nodeList.forEach(function(item){
   console.log(item)
})
//generates error
```
Every array is an object in the weird world of JS land, but most objects are not arrays.

As @dan_wellman  indicated, there are a few datastructures in the DOM api that *kinda* look like arrays, but really aren't, which is what makes this confusing.

When in doubt, you can always use a good old fashioned `for` loop to avoid these issues. For example:
```
for(var i = 0; i < ulList.length; i++){
	console.log(ulList[i])
}

//<li>Red</li>
//<li>Blue</li>
//<li>Yellow</li>

```

**Working Directly With a NodeList**
If you want to work directly with a nodeList, they are returned by using `document.querySelectorAll` and `Node.childNodes`, as shown below.

```
var ul = document.getElementById('myUL');
var nodeList = document.querySelectorAll('li');

nodeList.forEach(function(item){
	console.log(item);
})
```
![example2](http://imgur.com/QygMJ29.png)
----

![example3](http://imgur.com/Imo1oTy.png)
