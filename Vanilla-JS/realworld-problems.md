### Real World Trouble Shooting

![1](https://imgur.com/iasYhPa.png)

Why won't this code cycle through and make the text `red` then `black`? Its in this line of code 
```
	if(changeColor){
		makeRed(changeColor);
	}
```

Its only running the function `makeRed` and passing through the variable `if(changeColor)` is true.

------

### Trouble Shooting Stopwatch

#### Debug Solution 1:

Project Source: https://codepen.io/bluehabit/pen/jLoBxz

Was having a problem with the stop watch where the time would continue to display `0:0:0` even after hitting the start button. After debugging this I discovered it was because `updateTime` is being continously called, as a result `baseTime = Date.now()` keeps getting created over and over again. As a result, since `baseTime` doesn't hold the initial value, the `difference` between `baseTime` and `endTime` will be `0` because they are the same.

We can verify this in the debugger.

In the `updateTime` function I added the following code.
```
console.log(baseTime);
console.log(endTime);
debugger;
```

The `debugger` KW works just like a break point in dev tools. So everytime it hits this line, we can check the console to see what the values of baseTime and endTime are.

![example](https://imgur.com/Qn6OaU8.png)

#### Debug Solution 2, making `baseTime` a local variable inside the function: 


### Question: Is it possible to have devTools print the value of a `GLOBAL` variable along with a `LOCAL` variable inside a function? 
