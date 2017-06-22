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
