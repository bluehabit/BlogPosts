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

Creates a number in milliseconds, does *NOT* give you a `date object`! You can even verify this on the MDN page.

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

![s](http://imgur.com/As1eeSD.png)

### How many `ms` are in `2.4 minutes`?

We can set up a `proportion`. 1 is to 60,000 `as` 2.4 is to ? or `x`. A fraction, equality sign, and fraction means we will `cross multiply`. 

![s](http://imgur.com/fB6E97Y.png)

