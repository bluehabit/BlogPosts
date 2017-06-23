### Nested Objects

```
	var myPerson = {
		name: 'George',
		sex: 'Male',
		married: false,

		yell: function(input){
			var input = input;
			input = input.toUpperCase();
			return input + '!';
		},

		whisper: function(input){
			var input = input;
			input = input.toLowerCase(input);
			return input + ' sshhh...';
		},

		parrot: {
			name: 'luna',
			color: 'Turquoise',

			squawk: function(){
				return 'SQQQUAAWWWKKK';
			}
		}
	}

	// myPerson.yell('jane')
	//-> JANE!

	//myPerson.parrot.name
	//-> 'luna'

	//-> "SQQQUAAWWWKKK"
  ```
  
### Callback functions
  
A callback function is a function passed into another function as an argument, which is then called inside the outer function to complete some kind of routine or action. The higher order function is always the function that takes another function as a parameter. The callback function always gets called within the higher order function as a parameter. Callbacks are often used to deal with *asynchronous code*.

### Named Callback vs Inline Anonymous Callback 

![inline](http://imgur.com/7SefXfO.png)


### Callback Functions as the ONLY parameter within a Higher Order Function

```
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```


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


### Truthy and Falsey
