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
