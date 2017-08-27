### `new Date()`

Creates a `date object`

```
var aNewDate = new Date();
//Sun Aug 27 2017 12:12:29 GMT-0500 (Central Daylight Time)
//console.dir(aNewDate)
//__proto__: Object (date object)
```

### `Date.now`

Creates a number in milliseconds

```
var aDateNow= Date.now();
//1503853960824
//typeof aDatenow  -->
```

```
var startTime = Date.now();
// 1503855242925
var stopTime = Date.now();
// 1503855249902

var difference = stopTime - StartTime;
//6977 or 6.977 seconds
```
