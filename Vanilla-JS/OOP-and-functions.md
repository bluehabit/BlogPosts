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
  
A callback function is a function passed into another function as an argument, which is then called inside the outer function to complete some kind of routine or action.

Example:


  
### Anonymous inline function callback
  
![anonymous-inline-function-callback](http://imgur.com/u0GgT6n.png)


### Anonymous Callback vs Named Callback 

![anonymous-inline-vs-named-callback](http://imgur.com/Tci3Ggu.png)
