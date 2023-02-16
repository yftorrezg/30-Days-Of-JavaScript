# Day 13

[<< Day 12](../12_Day_Regular_expressions/12_day_regular_expressions.md) | [Day 14>>](../14_Day_Error_handling/14_day_error_handling.md)

## Console Object Methods

### console.log()

```js
console.log('30 Days of JavaScript')
```

```sh
30 Days of JavaScript
```

- Substitution

```js
console.log('%d %s of JavaScript', 30, 'Days')
```

```sh
30 Days of JavaScript
```

- CSS

```js
console.log('%c30 Days Of JavaScript', 'color:green') // log output is green
console.log(
  '%c30 Days%c %cOf%c %cJavaScript%c',
  'color:green',
  '',
  'color:red',
  '',
  'color:yellow'
) // log output green red and yellow text
```

### console.warn()

```js
console.warn('This is a warning')
console.warn(
  'You are using React. Do not touch the DOM. Virtual DOM will take care of handling the DOM!'
)
console.warn('Warning is different from error')
```

### console.error()

```js
console.error('This is an error message')
console.error('We all make mistakes')
```

### console.table()

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
console.table(names)
```

```js
const user = {
  name: 'Asabeneh',
  title: 'Programmer',
  country: 'Finland',
  city: 'Helsinki',
  age: 250
}
console.table(user)
```

```js
const countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo']
]
console.table(countries)
```

```js
const users = [
  {
    name: 'Asabeneh',
    title: 'Programmer',
    country: 'Finland',
    city: 'Helsinki',
    age: 250
  },
  {
    name: 'Eyob',
    title: 'Teacher',
    country: 'Sweden',
    city: 'London',
    age: 25
  },
  {
    name: 'Asab',
    title: 'Instructor',
    country: 'Norway',
    city: 'Oslo',
    age: 22
  },
  {
    name: 'Matias',
    title: 'Developer',
    country: 'Denmark',
    city: 'Copenhagen',
    age: 28
  }
]
console.table(users)
```

### console.time()

Starts a timer you can use to track how long an operation takes. You give each timer a unique name, and may have up to 10,000 timers running on a given page. When you call console.timeEnd() with the same name, the browser will output the time, in milliseconds, that elapsed since the timer was started.

```js
const countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo']
]

console.time('Regular for loop')
for (let i = 0; i < countries.length; i++) {
  console.log(countries[i][0], countries[i][1])
}
console.timeEnd('Regular for loop')

console.time('for of loop')
for (const [name, city] of countries) {
  console.log(name, city)
}
console.timeEnd('for of loop')

console.time('forEach loop')
countries.forEach(([name, city]) => {
  console.log(name, city)
})
console.timeEnd('forEach loop')
```

```sh
Finland Helsinki
Sweden Stockholm
Norway Oslo
Regular for loop: 0.34716796875ms

Finland Helsinki
Sweden Stockholm
Norway Oslo
for of loop: 0.26806640625ms

Finland Helsinki
Sweden Stockholm
Norway Oslo
forEach loop: 0.358154296875ms
```

According the above output the regular for loop is slower than for of or forEach loop.

### console.info()

It displays information message on browser console.

```js
console.info('30 Days Of JavaScript challenge is trending on Github')
console.info('30 Days Of fullStack challenge might be released')
console.info('30 Days Of HTML and CSS challenge might be released')
```

### console.assert()

The console.assert() methods writes an error message to the console if the assertion is false. If the assertion is true, nothing happens. The first parameter is an assertion expression. If this expression is false, an Assertion failed error message will be displayed.

```js
console.assert(4 > 3, '4 is greater than 3') // no result
console.assert(3 > 4, '3 is not greater than 4') // Assertion failed: 3 is not greater than 4

for (let i = 0; i <= 10; i += 1) {
  let errorMessage = `${i} is not even`
  console.log('the # is ' + i)
  console.assert(i % 2 === 0, { number: i, errorMessage: errorMessage })
}
```

### console.group()

The console.group() can help to group different log groups. Copy the following code and paste it on browser console to the groups.

```js
const names = ['Asabeneh', 'Brook', 'David', 'John']
const countries = [
  ['Finland', 'Helsinki'],
  ['Sweden', 'Stockholm'],
  ['Norway', 'Oslo']
]
const user = {
  name: 'Asabeneh',
  title: 'Programmer',
  country: 'Finland',
  city: 'Helsinki',
  age: 250
}
const users = [
  {
    name: 'Asabeneh',
    title: 'Programmer',
    country: 'Finland',
    city: 'Helsinki',
    age: 250
  },
  {
    name: 'Eyob',
    title: 'Teacher',
    country: 'Sweden',
    city: 'London',
    age: 25
  },
  {
    name: 'Asab',
    title: 'Instructor',
    country: 'Norway',
    city: 'Oslo',
    age: 22
  },
  {
    name: 'Matias',
    title: 'Developer',
    country: 'Denmark',
    city: 'Copenhagen',
    age: 28
  }
]

console.group('Names')
console.log(names)
console.groupEnd()

console.group('Countries')
console.log(countries)
console.groupEnd()

console.group('Users')
console.log(user)
console.log(users)
console.groupEnd()
```

### console.count()

```js
const func = () => {
  console.count('Function has been called')
}
func()
func()
func()
```

```sh
Function has been called: 1
Function has been called: 2
Function has been called: 3
```

### console.clear()

The console.clear() cleans the browser console.

```js
console.clear()
```

### console.trace()

The console.trace() method displays a custom message and the JavaScript call stack at the point where it was called.

```js
const func1 = () => {
  func2()
}
const func2 = () => {
  func3()
}
const func3 = () => {
  console.trace()
}
func1()
```

```sh
func3 @ VM123:6
func2 @ VM123:3
func1 @ VM123:1
(anonymous) @ VM123:9
```

[<< Day 12](../12_Day_Regular_expressions/12_day_regular_expressions.md) | [Day 14>>](../14_Day_Error_handling/14_day_error_handling.md)
