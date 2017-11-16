## Protip

![f](https://imgur.com/ymFVVsE.png)

## `new Date()`

Creates a `date object`

```
var aNewDate = new Date();
//Sun Aug 27 2017 12:12:29 GMT-0500 (Central Daylight Time)
//console.dir(aNewDate)
//__proto__: Object (date object)
```

### Date Object `methods`

```
var aDate = new Date();
a.getSeconds(); --> 56
a.getMinutes(); --> 37
a.getMilliseconds(); --> 80
a.getHours(); --> 12
```

### `Date.parse()`

Takes a date object, and converts it to milliseconds. 

```
Date.parse(a);
//1503855476000
```

Can also use...

### `Date.getTime();`

```
a.getTime();
////1503855476000
```

## `Date.now`

Creates a number in milliseconds, does *NOT* give you a `date object`! You can even verify this on the MDN page. This number is continously growing, because it is recording time in MS that have elapsed since 1 January 1970 00:00:00 UTC. This creates an interesting problem in the year 2038 where 32 bit systems will run out of storage to hold this number.

![date-now](http://imgur.com/uSlC1uG.png)

```
var aDateNow= Date.now();
//1503853960824
//typeof aDatenow  --> number
```

```
var startTime = Date.now();
// 1503855242925
var stopTime = Date.now();
// 1503855249902

var difference = stopTime - StartTime;
//6977 or 6.977 seconds
```

### `%` Modulus 

Reminder, `%` is the `remainder`. 

```
6%2 = 0; //2 evenly divides into 6, no remainder
12%5 = 2; //5 goes into 12 twice, with 2 remainder
11%3 = 2; //3 goes into 11 three times, with 2 remainder
```

## Time Conversion Math

`milli` - has a latin root stands for `thousandths`
`1ms` = `1/1,000` second

### `unit factors` and `setting up a proportion`

### How many `seconds` are in `2.5 days`? 

Notice we are moving from a larger unit (days) to a smaller unit (seconds) so our numbers will be in the `numerator`. 

![s](http://imgur.com/vXXadFt.png)


### How many `days` are in `62,000,000ms`?

![s](http://imgur.com/qUuQRxx.png)

### How many `seconds` are in `5,200ms`?

#### Solution 1:

![s](http://imgur.com/As1eeSD.png)

##### Solution 2:

![s](http://imgur.com/8nnXDI0.png)

### How many `ms` are in `2.4 minutes`?

We can set up a `proportion`. 1 is to 60,000 `as` 2.4 is to ? or `x`. A fraction, equality sign, and fraction means we will `cross multiply`. 

![s](http://imgur.com/fB6E97Y.png)

### Creating a Function to Convert `ms` to time

![t](http://imgur.com/nlM3v7l.png)


```
function timeDifference(startTime, endTime){
	var difference = endTime - startTime;
	convertTime(difference);
	return difference; 
}
```

### Recursive Methods

![x](http://imgur.com/lP3Zn09.png)


### Modify

// var time = new Date();
// var time = time.getTime();


// var a = Date.now();
// var a = JSON.stringify(a);


// Date.parse('Aug 9, 1995');
// //807937200000 

// Date.parse('Wed, 09 Aug 1995 00:00:00 GMT');
// //807926400000

// Date.parse('Thu, 01 Jan 1970 00:00:00');
// //14400000 

// ---------------------------------------------

// new Date(1324339200000).toUTCString()

// var a = Date.now();
// var b = new Date(a).toUTCString();
// "Thu, 07 Sep 2017 21:37:02 GMT"

// ----------------------------------------------

// var a = Date.now();
// //1504820475119
// var b = new Date(a).toString()
// //"Thu, 07 Sep 2017 21:41:15 GMT"
// var c = Date.parse(b);
// //1504820475000


// ----------------------------------------------

// var x = new Date();

// myVar = x.toString();
// "Thu Sep 07 2017 16:45:26 GMT-0500 (Central Daylight Time)"


//https://www.timeanddate.com/time/map/

//https://stackoverflow.com/questions/6525538/convert-utc-date-time-to-local-date-time

//https://stackoverflow.com/questions/4673527/converting-milliseconds-to-a-date-jquery-js

//https://stackoverflow.com/questions/8579861/how-to-convert-milliseconds-into-a-readable-date

//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify

//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/now

//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse

//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getUTCDate

//https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toString
