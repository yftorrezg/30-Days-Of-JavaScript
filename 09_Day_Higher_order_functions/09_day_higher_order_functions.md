# Day 9

[<< Day 8](../08_Day_Objects/08_day_objects.md) | [Day 10 >>](../10_Day_Sets_and_Maps/10_day_Sets_and_Maps.md)

## Higher Order Function

### Callback

```js
// a callback function, the name of the function could be any name
const callback = (n) => {
  return n ** 2
}
​
// function that takes other function as a callback
function cube(callback, n) {
  return callback(n) * n
}
​
console.log(cube(callback, 3))
```

### Returning function

```js
// Higher order function returning an other function
const higherOrder = n => {
  const doSomething = m => {
    const doWhatEver = t => {
      return 2 * n + 3 * m + t
    }
    return doWhatEver
  }
  return doSomething
}
console.log(higherOrder(2)(3)(10))
```

```js
const numbers = [1, 2, 3, 4, 5]
const sumArray = arr => {
  let sum = 0
  const callback = function(element) {
    sum += element
  }
  arr.forEach(callback)
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

```js
const numbers = [1, 2, 3, 4]
​
const sumArray = arr => {
  let sum = 0
  arr.forEach(function(element) {
    sum += element
  })
  return sum

}
console.log(sumArray(numbers))
```

```sh
15
```

### Setting time

In JavaScript we can execute some activities in a certain interval of time or we can schedule(wait) for some time to execute some activities.

- setInterval
- setTimeout

#### Setting Interval using a setInterval function

In JavaScript, we use setInterval higher order function to do some activity continuously with in some interval of time. The setInterval global method take a callback function and a duration as a parameter. The duration is in milliseconds and the callback will be always called in that interval of time.

```js
// syntax
function callback() {
  // code goes here
}
setInterval(callback, duration)
```

```js
function sayHello() {
  console.log('Hello')
}
setInterval(sayHello, 1000) // it prints hello in every second, 1000ms is 1s
```

#### Setting a time using a setTimeout

In JavaScript, we use setTimeout higher order function to execute some action at some time in the future. The setTimeout global method take a callback function and a duration as a parameter. The duration is in milliseconds and the callback wait for that amount of time.

```js
// syntax
function callback() {
  // code goes here
}
setTimeout(callback, duration) // duration in milliseconds
```

```js
function sayHello() {
  console.log('Hello')
}
setTimeout(sayHello, 2000) // it prints hello after it waits for 2 seconds.
```

## Functional Programming

Instead of writing regular loop, latest version of JavaScript introduced lots of built in methods which can help us to solve complicated problems. All builtin methods take callback function. In this section, we will see _forEach_, _map_, _filter_, _reduce_, _find_, _every_, _some_, and _sort_.

### forEach

_forEach_: Iterate an array elements. We use _forEach_ only with arrays. It takes a callback function with elements, index parameter and array itself. The index and the array optional.

```js
arr.forEach(function (element, index, arr) {
  console.log(index, element, arr)
})
// The above code can be written using arrow function
arr.forEach((element, index, arr) => {
  console.log(index, element, arr)
})
// The above code can be written using arrow function and explicit return
arr.forEach((element, index, arr) => console.log(index, element, arr))
```

```js
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => console.log(num))
console.log(sum)
```

```sh
1
2
3
4
5
```

```js
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => sum += num)

console.log(sum)
```

```sh
15
```

```js
const countries = ['Finland', 'Denmark', 'Sweden', 'Norway', 'Iceland']
countries.forEach((element) => console.log(element.toUpperCase()))
```

```sh
FINLAND
DENMARK
SWEDEN
NORWAY
ICELAND
```

### map

_map_: Iterate an array elements and modify the array elements. It takes a callback function with elements,  index , array parameter and return a new array.

```js
const modifiedArray = arr.map(function (element, index, arr) {
  return element
})
```

```js
/*Arrow function and explicit return
const modifiedArray = arr.map((element,index) => element);
*/
//Example
const numbers = [1, 2, 3, 4, 5]
const numbersSquare = numbers.map((num) => num * num)

console.log(numbersSquare)
```

```sh
[1, 4, 9, 16, 25]
```

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const namesToUpperCase = names.map((name) => name.toUpperCase())
console.log(namesToUpperCase)
```

```sh
['ASABENEH', 'MATHIAS', 'ELIAS', 'BROOK']
```

```js
const countries = [
  'Albania',
  'Bolivia',
  'Canada',
  'Denmark',
  'Ethiopia',
  'Finland',
  'Germany',
  'Hungary',
  'Ireland',
  'Japan',
  'Kenya',
]
const countriesToUpperCase = countries.map((country) => country.toUpperCase())
console.log(countriesToUpperCase)

/*
// Arrow function
const countriesToUpperCase = countries.map((country) => {
  return country.toUpperCase();
})
//Explicit return arrow function
const countriesToUpperCase = countries.map(country => country.toUpperCase());
*/
```

```sh
['ALBANIA', 'BOLIVIA', 'CANADA', 'DENMARK', 'ETHIOPIA', 'FINLAND', 'GERMANY', 'HUNGARY', 'IRELAND', 'JAPAN', 'KENYA']
```

```js
const countriesFirstThreeLetters = countries.map((country) =>
  country.toUpperCase().slice(0, 3)
)
```

```sh
 ["ALB", "BOL", "CAN", "DEN", "ETH", "FIN", "GER", "HUN", "IRE", "JAP", "KEN"]
```

### filter

_Filter_: Filter out items which full fill filtering conditions and return a new array.

```js
//Filter countries containing land
const countriesContainingLand = countries.filter((country) =>
  country.includes('land')
)
console.log(countriesContainingLand)
```

```sh
['Finland', 'Ireland']
```

```js
const countriesEndsByia = countries.filter((country) => country.endsWith('ia'))
console.log(countriesEndsByia)
```

```sh
['Albania', 'Bolivia','Ethiopia']
```

```js
const countriesHaveFiveLetters = countries.filter(
  (country) => country.length === 5
)
console.log(countriesHaveFiveLetters)
```

```sh
['Japan', 'Kenya']
```

```js
const scores = [
  { name: 'Asabeneh', score: 95 },
   { name: 'Lidiya', score: 98 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const scoresGreaterEighty = scores.filter((score) => score.score > 80)
console.log(scoresGreaterEighty)
```

```sh
[{name: 'Asabeneh', score: 95}, { name: 'Lidiya', score: 98 },{name: 'Martha', score: 85},{name: 'John', score: 100}]
```

### reduce

```js
arr.reduce((acc, cur) => {
  // some operations goes here before returning a value
 return 
}, initialValue)
```

```js
const numbers = [1, 2, 3, 4, 5]
const sum = numbers.reduce((acc, cur) => acc + cur, 0)

console.log(sum)
```

```js
15
```

### every

_every_: Check if all the elements are similar in one aspect. It returns boolean

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const areAllStr = names.every((name) => typeof name === 'string') // Are all strings?

console.log(areAllStr)
```

```sh
true
```

```js
const bools = [true, true, true, true]
const areAllTrue = bools.every((b) => b === true) // Are all true? 

console.log(areAllTrue) // true
```

```sh
true

```

### find

_find_: Return the first element which satisfies the condition

```js
const ages = [24, 22, 25, 32, 35, 18]
const age = ages.find((age) => age < 20)

console.log(age)
```

```js
18
```

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const result = names.find((name) => name.length > 7)
console.log(result)
```

```sh
Asabeneh
```

```js
const scores = [
  { name: 'Asabeneh', score: 95 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const score = scores.find((user) => user.score > 80)
console.log(score)
```

```sh
{ name: "Asabeneh", score: 95 }
```

### findIndex

_findIndex_: Return the position of the first element which satisfies the condition

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const ages = [24, 22, 25, 32, 35, 18]

const result = names.findIndex((name) => name.length > 7)
console.log(result) // 0

const age = ages.findIndex((age) => age < 20)
console.log(age) // 5
```

### some

_some_: Check if some of the elements are similar in one aspect. It returns boolean

```js
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const bools = [true, true, true, true]

const areSomeTrue = bools.some((b) =>  b === true)

console.log(areSomeTrue) //true
```

```js
const areAllStr = names.some((name) => typeof name === 'number') // Are all strings ?
console.log(areAllStr) // false
```

### sort

#### Sorting string values

```js
const products = ['Milk', 'Coffee', 'Sugar', 'Honey', 'Apple', 'Carrot']
console.log(products.sort()) // ['Apple', 'Carrot', 'Coffee', 'Honey', 'Milk', 'Sugar']
//Now the original products array  is also sorted
```

#### Sorting Numeric values

```js
const numbers = [9.81, 3.14, 100, 37]
// Using sort method to sort number items provide a wrong result. see below
console.log(numbers.sort()) //[100, 3.14, 37, 9.81]
numbers.sort(function (a, b) {
  return a - b
})

console.log(numbers) // [3.14, 9.81, 37, 100]

numbers.sort(function (a, b) {
  return b - a
})
console.log(numbers) //[100, 37, 9.81, 3.14]
```

#### Sorting Object Arrays

```js
objArr.sort(function (a, b) {
  if (a.key < b.key) return -1
  if (a.key > b.key) return 1
  return 0
})

// or

objArr.sort(function (a, b) {
  if (a['key'] < b['key']) return -1
  if (a['key'] > b['key']) return 1
  return 0
})

const users = [
  { name: 'Asabeneh', age: 150 },
  { name: 'Brook', age: 50 },
  { name: 'Eyob', age: 100 },
  { name: 'Elias', age: 22 },
]
users.sort((a, b) => {
  if (a.age < b.age) return -1
  if (a.age > b.age) return 1
  return 0
})
console.log(users) // sorted ascending
// [{…}, {…}, {…}, {…}]
/* 
0:(2) {name: "Elias", age: 22}
1:(2) {name: "Brook", age: 50}
2:(2) {name: "Eyob", age: 100}
3:(2) {name: "Asabeneh", age: 150} */
```

[<< Day 8](../08_Day_Objects/08_day_objects.md) | [Day 10 >>](../10_Day_Sets_and_Maps/10_day_Sets_and_Maps.md)
