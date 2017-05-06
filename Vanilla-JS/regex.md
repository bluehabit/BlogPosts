## Regex

```
//Matching a set of characters
console.log(/[0123456789]/.test("in 1992"));
// → true
console.log(/[0-9]/.test("in 1992"));
// → true
/[3-6]/.test("1992");
// → false, read the range of characters, is there a 4, 5, or 6
// inside of 1992? No, return false

/[2-6]/.test("1992");
// → true, read the range of characters, is there  a 2,3,4,5,6
//digit within 1992? Yes, return true.

('c'|'d').test('clown');
```

```
var re = /[^a-zA-Z]/
re.test('005555');
//→ true

var re = /[0-3a-z]/
re.test('05 hello');
//→ true
//looks for the number 0-3 or any letter lower case a-z
re.test('55 HELLO');
//→ false
// false because the number 5 is not 0-3 and a-z is lower case
//and HELLO is capitalized

//operators
// ? preceding character is optional
var re = /bana?na/
re.test('banana');
//→ true
re.test('banna');
//→ true
re.test('banaana');
//→ false

// + one or more of the previous characters
var re = /bana+na/;

re.test('banana');
//→ true
re.test('banaana');
//→ true
re.test('banna');
//→ false
re.test('banaaaana');
//→ true
```

```
var re = /^(ba|na)+$/
//+ indicates one or more of the previous group of characters
//so must have a ba or na
//that is why 'ba' and 'na' pass

//translation: must begin with ba|na and end with ba|na

re.test('banana');
re.test('nababa');
re.test('baba');
re.test('nana');
re.test('ba');
re.test('na');

var re = /(^jav|script$)/
//translation: must begin with jav or end with script
re.test('javscript');
//→ true
re.test('python');
//→ false
re.test('pythonscript');
//→ true

var re = /^(ba|na$)/
re.test('banana');
re.test('ba');
re.test('na');
re.test('ba');
//→ true


//rules
?
//the preceding character is optional, or group of characters
+
//one or more of the previous character, or group of characters
*
//* zero or more of the previous character, or group of characters

var re = /^JavaScript/

//indicates beginning of a string
var re = /Javascript$/
//indicates end of a string

//Special Character Codes:
\d any digit (same as [0-9])
\D anything BUT a digit (same as ^[0-9]), remember ^ before brackets inverts
\w A "word character" (same as [A-Za-z0-9_]) 
\W A "nonword character" (same as [^A-Za-z0-9_])

var re = /\d/
re.test('1');
//→ true
re.test('onetwothree');
//→ false

var re = /\D/
re.test('abc');
//→ true
re.test('12');
//→ false


//Adding Modifiers
var re = /Test[0-9]+/;
//→ true “Test2” only
var re = /Test[0-9]+/i; //i is case INSENSITIVE modifier
//→ true “test1” only
var re = /Test[0-9]+/gi; //gi is global and insensitive
//→ true “test1”, “Test2”, and “TEST3”



//Regular expression built in methods and properties

//match()
'I went to the store to buy some eggs'.match(/egg/)
// ["egg", index: 32, input: "I went to the store to buy some eggs"]

var myString = 'I went to the store to buy some eggs';
var re = /egg/
myString.match(re);
//["egg", index: 32, input: "I went to the store to buy some eggs"]

//.exec
var match = /\d+/.exec("one two 100");
console.log(match);
//["100", index: 8, input: "one two 100"]


function checkPhoneNumber(phoneNo){
	var phoneRE = /^\(\d\d\d\) \d\d\d-\d\d\d\d$/;
}

//translation: 
//^ must begin with ( character
//then it must be followed by a digit, digit, digit, and another )
//then a space followed by a digit, digit, digit then a hyphen
//followed by a digit, digit, digit and then finally ending
//with a digit

//remove all spaces from text
var myString = 'hello there young man'
myString.replace(/\s/g, '');
//"hellothereyoungman"

var re = /\$\$\$/
var re.match('show me the $$$');
//→ true


function checkPhoneNumber(phoneNo) {
  var phoneRE = /^\(\d\d\d\) \d\d\d-\d\d\d\d$/; 
  if (phoneNo.match(phoneRE)) {
    return true; 
  } else {
    alert( "The phone number entered is invalid!" );
    return false;
  }
}
```
