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
