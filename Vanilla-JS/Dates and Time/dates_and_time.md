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

Creates a number in milliseconds, does *NOT* give you a `date object`!

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
