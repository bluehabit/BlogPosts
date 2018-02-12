## Regular Expressions

https://regex101.com/

Just like strings, arrays, or objects regular expressions can be created with the literal or constructor variant.

**Literal**

`var pattern = /a/;`

**Constructor**

`var pattern = new RegExp('a');`

### Exact Match Patterns

Matching an exact word or phrase.

`var pattern = 'My Bird Luna'`
`Looks for the exact phrase 'My Bird Luna'`

`var pattern = 'Luna'`


### Regex Flags

Flags go at the end of the regular expression. For example: 
`/blue/gi` indicating a global pattern search that is case insensitive.

Each one has unique properties.

`g` - global, find all matches

`i` - case insensitive 

`m` - multi-lline, pattern matches across multiple lines instead of just the first line

### Quantifiers

How many times a character, or sequence of characters, should be matched.

`*` - Matches character, or set of characters, *zero* or more times.

`+` - Matches character, or set of characters, *one* or more times.

`?` - Matches character, or set of characters, *zero* or more times.

`{n}` - Matches character, or set of characters, `n` times exactly.

`{n,}` - Matches character, or set of characters, at least `n` times.

`{n,m}` - Matches character, or set of characters, at least `n` times and at most `m` times.


### Boundaries

`^` - Matches from the beginning of the input, or from the beginning of the line if the `m` (multiline) flag is used.

`$` - Matches to the end of the input, or the end of the line if the `m` flag is used.

`\b` - Matches a *word boundary*. 

`\B` - Matches a non-word boundary. 

### Boundary Examples

Very common to confuse `\b` and `\B`. Please remember, `\b` searches for words based on word boundaries. Characters such as the space, `.` and `/` act as word boundaries. 

While `\B` searches WITHIN a word. 

![f](https://imgur.com/FCh69v3.png)

### Anchors 

`/^search phrase here$/` Using `^` and `$` together creates an anchor. 

### Capture Groups, AKA Grouping

Allows us to apply things like `quantifiers` to the whole group of characters. 

The matches made by a regular expression use up resources, so we should always use *non-capturing* groups unless we specifically need to access the matchd text. To turn a capturing group into a non-capturing group, we use `?:`. 

```
var testString = 'I am a modern developer',
    pattern = /(?:abc)*/;
 
console.log(pattern.test(testString)); // true
```


### Character Sets

Allow us to match any characters within a particular set. It can be a specific group of characters such as `[abc]` or a range such as `[A-Z]`.

### Negating Character Sets

Use the `^` character.

```
var testString = '12345',
pattern = /[^a-z]/

console.log(pattern.test(testString)) // true
```

### Or Statements

Using the `|` chracter.

`var pattern = /blue | purple/` 

Matches `blue` OR `purple`. 


### Assertions

Allow us to match patterns conditionally, we can match a token if it is followed by another particular token, or we can match a tokey only if it is NOT followed by another particular token. We can do this with `?=` and `?!`.

```
var testString = 'I am a modern developer',
    pattern = /developer(?= designer)/;
 
console.log(pattern.test(testString)); // false
```


```
var testString = 'I am a modern developer',
    pattern = /developer(?! desginer)/;
 
console.log(pattern.test(testString)); // true
```


### Character Classes

`.` - Matches any character

`[\b]` - Matches backspace

`\d` - Digit, this is equivalent to the `character set` `[0-9]`

`\D` - Negated digit class, matches any character that is NOT a numeric digit.

`\s` - single space character (white space)

`\S` - negated space character, matches anything not a single space.

`\w` - Matches any *alphanumeric character*, including the under score. Equivalent to the `character set` `[a-zA-Z0-9_]`

`\` - Used to *escape* special characters. For example to match a literal `*` character instead of using it a quantifier we use `/\*/` 


### Match

### Replace

## Examples

![f](https://imgur.com/L0nohK6.png)

![f](https://imgur.com/rm1dUxc.png)

![f](https://imgur.com/5VJJUzs.png)

![f](https://imgur.com/ycrXOHA.png)

![f](https://imgur.com/zeQFEbP.png)

### Assertion Positive Look Ahead Examples

![f](https://imgur.com/o64zhrS.png)

![f](https://imgur.com/CG5iZbb.png)

![f](https://imgur.com/3gwYuMY.png)

![f](https://imgur.com/GNgN3gp.png)

![f](https://imgur.com/0GlDS5I.png)

### Assertion Negative Look Ahead Examples

![f](https://imgur.com/LGqdVSd.png)

![f](https://imgur.com/TOLZMWT.png)

![f](https://imgur.com/wiBOjNQ.png)

### More examples and validators

![f](https://imgur.com/nlwnfNi.png)

![f](https://imgur.com/lXG4car.png)

![f](https://imgur.com/CNUdufv.png)

![f](https://imgur.com/nfKv67X.png)

![f](https://imgur.com/Wb2qoUP.png)

![f](https://imgur.com/NyNAhx2.png)



### Simple JSON Validator

![f](https://imgur.com/28Xme8h.png)

### Greedy vs Lazy

![f](https://imgur.com/ViwOeyN.png)

### `exec` for multiple matches

![f](https://imgur.com/NzRHu5v.png)


## Match

![f](https://imgur.com/pMMaJKQ.png)

## Epoch `match` Example

Parsing a string, and then using `match` array to convert it to a number value in milliseconds to use for epoch time and `new Date`. 

![f](https://imgur.com/ehgkUdl.png)

And another example

![f](https://imgur.com/pAEtcOF.png)

## Replace

![f](https://imgur.com/45ScJdO.png)

