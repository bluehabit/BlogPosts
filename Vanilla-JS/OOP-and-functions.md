### Nested Objects

![nested-object](http://imgur.com/JXmv5Ah.png)
  
### Callback functions
  
A callback function is a function passed into another function as an argument, which is then called inside the outer function to complete some kind of routine or action. The higher order function is always the function that takes another function as a parameter. The callback function always gets called within the higher order function as a parameter. Callbacks are often used to deal with *asynchronous code*.

### Named Callback vs Inline Anonymous Callback 

![inline](http://imgur.com/7SefXfO.png)


### HouseExample

![house](http://imgur.com/S6rwsib.png)

### House Named Function Callback

![named-house](http://imgur.com/uOvSljc.png)


### Callback Functions as the ONLY parameter within a Higher Order Function

![example](http://imgur.com/U8uFeIZ.png)

Example:

### Anonymous inline function callback
  
![anonymous-inline-function-callback](http://imgur.com/u0GgT6n.png)


### Anonymous Callback vs Named Callback 

![anonymous-inline-vs-named-callback](http://imgur.com/Tci3Ggu.png)


### Callback functions can have their own Parameters

![own-parameters](http://imgur.com/3zEydcd.png)


### Spotting an Inline Anonymous Function Callback in the Wild

![wild](http://imgur.com/dEnvVlf.png)


### More Examples

Regular Parameter: 

![color-example](http://imgur.com/v58SzKh.png)

Object Parameter: 

![color-example2](http://i.imgur.com/DOpfudo.png)

Array Parameter: 

![color-example3](http://imgur.com/DOpfudo.png)

### Callback(item)

![callback-item](http://imgur.com/UFQjhQk.png)

### Equality Operators

![equality-operators](http://imgur.com/rpgIUqB.png)

### Variant

![variant](http://imgur.com/0df8crS.png)

![variant2](http://imgur.com/VepzS7z.png)

This is why **callbacks** work so well with **asynchronous** code. With async code you might make a request to an API somewhere, and when it receives your query and sends the data back that could be some amount of time in the future. What did callbacks do for us? They let us get information out of another functions scope. 

The higher order function has access to the callback function within its scope. So when the data from the API comes back inside the callback function you can do stuff with it. 

### Callback Function Workflow

![callback-workflow](http://imgur.com/ISoW7bV.png)

### isNaN()

```
var string = 'dog'
isNaN(string);

//--> true


var num = 1;
isNaN(num);

//--> false;
```

### For Each

![for-each-example](http://imgur.com/IyNIHwC.png)

![parameters](http://imgur.com/VAdnpnf.png)
Check parameters on MDN to see what each does 

### AddEventListener

![example](http://imgur.com/MT0kSLE.png)

#### Console.dir() to see methods and properties on the HTML element Object

![dir](http://imgur.com/OP50Bim.png)

**Important**: Remember under the hood on `addEventListener` the value of `this` is reassigned to the HTML element object using call, apply or something.

![button](http://imgur.com/9Bbolle.png)

### Good Example

![good-example](http://imgur.com/P6Emvgb.png)

### ProTip

![protip1](http://imgur.com/vInrEDA.png)

![protip2](http://imgur.com/yDvgb9P.png)

![protip3](http://imgur.com/mpRIlRh.png)

See more of this example here https://codepen.io/bluehabit/pen/MoOaao

### Normal vs Arrow Functions

![example](http://imgur.com/t8iXoNa.png)

### Real Life Example Callbacks

```
 var request = require('request');

 function getWeather(lat, lng, callback){

  request({
    url: 'https://api.darksky.net/forecast/5d1fb3bcf4dc2e2d15f360bfa6488109/'+lat+','+lng,
    json: true
  }, function(error, response, body){
    if(error){
      callback('unable to connect to weather server');
    } else if(response.statusCode === 400){
      callback('unable to fetch weather from this location');
    } else if(response.statusCode === 200){
     return callback(undefined, body.currently.temperature)
    }
  });

 }

 module.exports.getWeather = getWeather;

```

```
QUnit.test('bind', function(assert) {
    var context = {name: 'moe'};
    var func = function(arg) { return 'name: ' + (this.name || arg); };
    var bound = _.bind(func, context);
``

### Truthy and Falsey

```
<button id='button'>hey there</button>

<script>
var button = document.getElementById('button');

button.addEventListener('click', function(event){

	higherOrder(event.screenX)

	function higherOrder(callback){
		console.log(callback)
	}
})


</script>
```

### Get Coordinates Example using Event Object

![event-object](http://imgur.com/N8UlB4I.png)
