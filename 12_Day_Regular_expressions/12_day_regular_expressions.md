# 📘 Day 12

[<< Day 11](../11_Day_Destructuring_and_spreading/11_day_destructuring_and_spreading.md) | [Day 13 >>](../13_Day_Console_object_methods/13_day_console_object_methods.md)

## Regular Expressions

To declare a string we use a single quote, double quote a backtick to declare a regular expression we use two forward **slashes** and an optional **flag**. The flag could be ``g, i, m, s, u or y``.

### Flags

- ``g``: a global flag which means looking for a pattern in whole text
- ``i``: case insensitive flag(it searches for both lowercase and uppercase)
- ``m``: multiline

### Creating a pattern with RegExp Constructor

```js
// without flag
let pattern = 'love'
let regEx = new RegExp(pattern)
```

```js
let pattern = 'love'
let flag = 'gi'
let regEx = new RegExp(pattern, flag)
```

```js
let regEx = new RegExp('love','gi')
```

### Creating a pattern without RegExp Constructor

```js
let regEx= /love/gi
```

```js
let regEx= new RegExp('love','gi')
```

### RegExpp Object Methods

#### Testing for  a match

*test()*:Tests for a match in a string. It returns true or false.

```js
const str = 'I love JavaScript'
const pattern = /love/
const result = pattern.test(str)
console.log(result)
```

```sh
true
```

#### Array containing all of the match

*match()*:Returns an array containing all of the matches, including capturing groups, or null if no match is found.

```js
const str = 'I love JavaScript'
const pattern = /love/
const result = str.match(pattern)
console.log(result)
```

```sh
["love", index: 2, input: "I love JavaScript", groups: undefined]
```

```js
const str = 'I love JavaScript'
const pattern = /love/g
const result = str.match(pattern)
console.log(result)
```

```sh
["love"]
```

*search()*: Tests for a match in a string. It returns the index of the match, or -1 if the search fails.

```js
const str = 'I love JavaScript'
const pattern = /love/g
const result = str.search(pattern)
console.log(result)
```

```sh
2
```

#### Replacing a substring

*replace()*: Executes a search for a match in a string, and replaces the matched substring with a replacement substring.

```js
const txt = 'Python has ever created.\
I recommend python for a first programming language'

matchReplaced = txt.replace(/Python|python/, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript has ever created.I recommend python for a first programming language
```

```js
const txt = 'Python  created.\
I recommend python for a first programming language'

matchReplaced = txt.replace(/Python|python/g, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript  created.I recommend JavaScript for a first programming language
```

```js
const txt = 'Python  created.\
I recommend python for a first programming language'

matchReplaced = txt.replace(/Python/gi, 'JavaScript')
console.log(matchReplaced)
```

```sh
JavaScript  created.I recommend JavaScript for a first programming language
```

```js

const txt = '%I a%m te%%a%%che%r% a%n%d %% I l%o%ve te%ach%ing.\
T%he%re i%s n%o%th%ing as m%ore r%ewarding a%s e%duc%at%i%ng a%n%d e%m%p%ow%er%ing \
p%e%o%ple.\
I fo%und te%a%ching m%ore i%n%t%er%%es%ting t%h%an any other %jobs.\
D%o%es thi%s m%ot%iv%a%te %y%o%u to b%e a t%e%a%cher.'

matches = txt.replace(/%/g, '')
console.log(matches)  
```

```sh
I am teacher and  I love teaching.There is nothing as more rewarding as educating and empowering people.I found teaching more interesting than any other jobs.Does this motivate you to be a teacher.
```

* []:  A set of characters
  * [a-c] means, a or b or c
  * [a-z] means, any letter a to z
  * [A-Z] means, any character A to Z
  * [0-3] means, 0 or 1 or 2 or 3
  * [0-9] means any number 0 to 9
  * [A-Za-z0-9] any character which is a to z, A to Z, 0 to 9
* \\:  uses to escape special characters
  * \d mean: match where the string contains digits (numbers from 0-9)
  * \D mean: match where the string does not contain digits
* . : any character except new line character(\n)
* ^: starts with
  * r'^substring' eg r'^love', a sentence which starts with a word love
  * r'[^abc] mean not a, not b, not c.
* $: ends with
  * r'substring$' eg r'love$', sentence ends with a word love
* *: zero or more times
  * r'[a]*' means a optional or it can occur many times.
* +: one or more times
  * r'[a]+' means at least once or more times
* ?: zero or one times
  *  r'[a]?' means zero times or once
* \b: word bounder, matches with the beginning or ending of a word
* {3}: Exactly 3 characters
* {3,}: At least 3 characters
* {3,8}: 3 to 8 characters
* |: Either or
  * r'apple|banana' mean either of an apple or a banana
* (): Capture and group

![Regular Expression cheat sheet](../images/regex.png)

Let's use example to clarify the above meta characters

### Square Bracket

Let's use square bracket to include lower and upper case

```js
const pattern = '[Aa]pple' // this square bracket means either A or a
const txt = 'Apple fruits. An old cliche says an apple a day keeps the  doctor way. '
const matches = txt.match(pattern)

console.log(matches)  
```

```sh
["Apple", index: 0, input: "Apple fruits. An old cliche says an apple a day keeps the  doctor way.", groups: undefined]

```

```js
const pattern = /[Aa]pple/g // this square bracket means either A or a
const txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. '
const matches = txt.match(pattern)

console.log(matches)  
```

```sh
["Apple", "apple"]
```

If we want to look for the banana, we write the pattern as follows:

```js
const pattern = /[Aa]pple|[Bb]anana/g // this square bracket mean either A or a
const txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. Banana is easy to eat too.'
const matches = txt.match(pattern)

console.log(matches)  
```

```sh
["Apple", "banana", "apple", "banana", "Banana"]
```

Using the square bracket and or operator , we manage to extract Apple, apple, Banana and banana.

### Escape character(\\) in RegExp

```js
const pattern = /\d/g  // d is a special character which means digits
const txt = 'This regular expression example was made in January 12,  2020.'
const matches = txt. match(pattern)

console.log(matches)  // ["1", "2", "2", "0", "2", "0"], this is not what we want
```

### One or more times(+)

```js
const pattern = /\d+/g  // d is a special character which means digits
const txt = 'This regular expression example was made in January 12,  2020.'
const matches = txt. match(pattern)
console.log(matches)  // ["12", "2020"], this is not what we want
```

### Period(.)

```js
const pattern = /[a]./g  // this square bracket means a and . means any character except new line
const txt = 'Apple and banana are fruits'
const matches = txt.match(pattern)

console.log(matches)  // ["an", "an", "an", "a ", "ar"]
```

```js
const pattern = /[a].+/g  // . any character, + any character one or more times 
const txt = 'Apple and banana are fruits'
const matches = txt.match(pattern)

console.log(matches)  // ['and banana are fruits']
```

### Zero or more times(*)

Zero or many times. The pattern may not occur or it can occur many times.

```js

const pattern = /[a].*/g  //. any character, + any character one or more times 
const txt = 'Apple and banana are fruits'
const matches = txt.match(pattern)

console.log(matches)  // ['and banana are fruits']

```

### Zero or one times(?)

Cero o uno veces. El patrón puede **no ocurrir o puede ocurrir** una vez.

```js
const txt = 'I am not sure if there is a convention how to write the word e-mail.\
Some people write it email others may write it as Email or E-mail.'
const pattern = /[Ee]-?mail/g  // ? means optional
matches = txt.match(pattern)

console.log(matches)  // ["e-mail", "email", "Email", "E-mail"]

```

### Quantifier in RegExp

We can specify the length of the substring we look for in a text, using a curly bracket. Let us see, how ot use RegExp quantifiers. Imagine, we are interested in substring that their length are 4 characters

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\\b\w{4}\b/g  //  exactly four character words
const matches = txt.match(pattern)
console.log(matches)  //['This', 'made', '2019']
```

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\b[a-zA-Z]{4}\b/g  //  exactly four character  words without numbers
const matches = txt.match(pattern)
console.log(matches)  //['This', 'made']
```

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\d{4}/g  // a number and exactly four digits
const matches = txt.match(pattern)
console.log(matches)  // ['2019']
```

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /\d{1,4}/g   // 1 to 4
const matches = txt.match(pattern)
console.log(matches)  // ['6', '2019']
```

### Cart ^

- Starts with
  
```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /^This/ // ^ means starts with
const matches = txt.match(pattern)
console.log(matches)  // ['This']
```

- Negation

```js
const txt = 'This regular expression example was made in December 6,  2019.'
const pattern = /[^A-Za-z,. ]+/g  // ^ in set character means negation, not A to Z, not a to z, no space, no comma no period
const matches = txt.match(pattern)
console.log(matches)  // ["6", "2019"]
```

### Exact match

It should have ^ starting and $ which is an end.

```js
let pattern = /^[A-Z][a-z]{3,12}$/;
let name = 'Asabeneh';
let result = pattern.test(name)

console.log(result) // true
```

[<< Day 11](../11_Day_Destructuring_and_spreading/11_day_destructuring_and_spreading.md) | [Day 13 >>](../13_Day_Console_object_methods/13_day_console_object_methods.md)
