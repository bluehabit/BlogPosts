![regex-tips](http://i.imgur.com/5vmtCtQ.png)

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

```
var re = /^[^c|d]$/
re.test('c');
//false
re.test('d');
//false
re.test('x');
//true
re.test('g');
//true


var re = /[^abc|xyz]/
re.test('abc');
//false
re.test('xyz');
//false
re.test('efg');
//true

var re = /^[^abc|xyz]+$/
re.test('reel');
//true
re.test('goat');
//false
re.test('zebra')
//false
re.test('yoyo');
//false
re.test('milk');
//true

var re = /^[^c|d]*$/
re.test('apple');
//true
re.test('boat');
//true
re.test('dog');
//false

var re = /^([^abc|xyz])+$/
//can also write it like this with ()
//I guess that means *?+ applies to brackets like paranthesis


//! neative lookahead what the fuck does that mean
var re = /\b(?!girl)\w*friend\b/ig
re.test('boyfriend')
//true
re.test('girlfriend')
//false
//http://stackoverflow.com/questions/6308334/regex-find-all-matching-words-that-that-dont-begin-with-a-specific-prefix

```

### Exact Match Patterns

We can create a literal regex like this 

`var pattern = /modern developer/`

In this case, the pattern would only match if the target string contains the exact words “modern developer” in that order with a single space character between them. It would match `'I am a modern developer'`. 


### The `test` Method

We can use this to verify whether a string contains a pattern. It takes a single parameter, which is the string to test. Its useful because it returns a boolean, which we can use in a conditional statement.


```
var testString = 'I am a modern developer',
    pattern = /modern developer/;
 
console.log(pattern.test(testString)); // true
```


### Regular Expression Properties

`global` - `g` flag, makes the pattern match *all* occurrences rather than stopping at the first match.

```
var string = 'I am a modern developer, a modern developer I am';
var pattern = /modern developer/g;

console.log(pattern.test(string));
```

`ignoreCase` - `i` flag, makes pattern ignore casing of the match, will be `true` or `false` depending on whether the flag is used.

```
var string = 'I am a Modern developer';
var pattern = /modern developer/i;

console.log(pattern.test(string));
```

We can also pass flags to the regex constructor
`var pattern = new RegExp('modern developer', 'i')`




`lastIndex` - when the `g` flag is used, multiple matches may be found on a string; this property is used to keep track of the index at which to start matchinf from in succussive searches. Initially this property is set to `0`.

`multiline` - `m` flag, makes the pattern match accross multiple lines instead of just the first line. 

`source` - contains regular expression text

`sticky` - `y` flag, When testing for patterns within the same string multiple times, when the sticky flag is used, the regular expression will remember the last matching pattern within the string, and a second search will start from the last matched instance of the pattern within the string.

`unicode` - `u` flag

Flags always exist on the regex object and will be set to `true` or `false` dpeending on whether the flag was set. For example if we dont use the `g` flag the property will be set to false.

```
var testString = 'I am a modern developer',
    pattern = /modern developer/;
 
console.log(pattern.global); // false
```

## Special Characters

### Character Sets

Characters sets allow us to match any characters within a particular **set**. A set can be a *specific group of characters* like `abc` or a range of characters like `A to Z`. 

### Standard Character Sets

We specify a characer set using square brackets. Note you just have to match one letter in the set, thats it, it does *NOT* have to be inclusive.

```
var string = 'abc 123 xyz';
var pattern = /[xyz]/;

console.log(pattern.test(string));
//true

var string2 = 'z123';
console.log(pattern.test(string));
//true
```

### Ranges

We can also supply a range of characters as the character set. 

```
var string = '123 ***';
var pattern = /[a-z][A-Z]/;

console.log(pattern.test(string));
//true
```

We can also *combine* ranges. To test for any lowercase or uppercase letter, we could use the expression `/[a-zA-Z]/`.

This example only matches numbers or hyphens
```
var testString = 'ab-cd',
    pattern = /[0-9-]/;
 
console.log(pattern.test(testString)); // true
```

#### Negated Character Sets

A negated character set means that we want to match any character that is not in the set.

```
var testString = '12345',
    pattern = /[^a-z]/;
 
console.log(pattern.test(testString)); // true
```

#### Alternation

We can use the special pipe character `|` to specify an OR statement in a regular expression. For example, to match either the word “modern” or the word “developer,” we could use the pipe symbol:

```
var testString = 'I am not a designer',
    pattern = /modern|developer/;
 
console.log(pattern.test(testString)); // false
```

#### Quantifiers

### `*` 

matches the character or set it follows zero or more times.


```
var testString = 'I am a modern developer',
    pattern = /a*/;
 
console.log(pattern.test(testString)); // true
```

Here `a` appears at least once, and `x` appears zero times.
```
var testString = 'I am a modern developer',
    pattern = /ax*/;
 
console.log(pattern.test(testString)); // true
```

However this will not match, the regular expression `/axe*/` is saying to match the letter a followed by the letter x, and followed by one or more e characters. 

```
var testString = 'I am a modern developer',
    pattern = /axe*/;
 
console.log(pattern.test(testString)); // false
```
----- 

`+` matches the character or set it folls one or more times
`?` matches the caracter or set it follows zero or more times
`{n}` matches the character or set it follows `n` times exactly
`{n,}` matches the character or set it follows at least `n` times
`{n,m}` matches the character or set it follows at least `n` times and at most `m` times

```
var testString = 'I am a modern developer',
    pattern = /e+/;
 
console.log(pattern.test(testString)); // true
```

This fails, becuase there are no occurrences of the character `e` followed by one or more `x` characters.

```
var testString = 'I am a modern developer',
    pattern = /ex+/;
 
console.log(pattern.test(testString)); // fails
```
















