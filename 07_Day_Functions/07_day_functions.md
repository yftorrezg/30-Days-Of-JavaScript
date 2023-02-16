# 📔 Day 7

[<< Day 6](../06_Day_Loops/06_day_loops.md) | [Day 8 >>](../08_Day_Objects/08_day_objects.md)

## Functions

### Function Declaration

```js
//declaring a function without a parameter
function functionName() {
  // code goes here
}
functionName(); // calling function by its name and with parentheses
```

### Function without a parameter and return

```js
// function without parameter,  a function which make a number square
function square() {
  let num = 2;
  let sq = num * num;
  console.log(sq);
}

square(); // 4
```

### Function returning value

```js
function addTwoNumbers() {
  let numOne = 2;
  let numTwo = 3;
  let total = numOne + numTwo;
  return total;
}

console.log(addTwoNumbers());
```

### Function with a parameter

```js
// function with one parameter
function functionName(parm1) {
  //code goes her
}
functionName(parm1); // during calling or invoking one argument needed

function areaOfCircle(r) {
  let area = Math.PI * r * r;
  return area;
}

console.log(areaOfCircle(10)); // should be called with one argument
```

### Function with two parameters

```js
function sumTwoNumbers(numOne, numTwo) {
  let sum = numOne + numTwo;
  console.log(sum);
}
sumTwoNumbers(10, 20); // calling functions
// If a function doesn't return it doesn't store data, so it should return

function sumTwoNumbers(numOne, numTwo) {
  let sum = numOne + numTwo;
  return sum;
}
console.log(sumTwoNumbers(10, 20));

function printFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
console.log(printFullName("Asabeneh", "Yetayeh"));
```

### Function with many parameters

```js
// function with multiple parameters
function functionName(parm1, parm2, parm3,...){
  //code goes here
}
functionName(parm1,parm2,parm3,...) // during calling or invoking three arguments needed


// this function takes array as a parameter and sum up the numbers in the array
function sumArrayValues(arr) {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
    sum = sum + arr[i];
  }
  return sum;
}
const numbers = [1, 2, 3, 4, 5];
    //calling a function
console.log(sumArrayValues(numbers));
```

### Function with unlimited number of parameters

#### Unlimited number of parameters in regular function

```js
// Let us access the arguments object
​
function sumAllNums() {
 console.log(arguments)
}

sumAllNums(1, 2, 3, 4)
// Arguments(4) [1, 2, 3, 4, callee: ƒ, Symbol(Symbol.iterator): ƒ]
```

```js
// function declaration
​
function sumAllNums() {
  let sum = 0
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i]
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4)) // 10
console.log(sumAllNums(10, 20, 13, 40, 10))  // 93
console.log(sumAllNums(15, 20, 30, 25, 10, 33, 40))  // 173
```

#### Unlimited number of parameters in arrow function

```js
// Let us access the arguments object
​
const sumAllNums = (...args) => {
 // console.log(arguments), arguments object not found in arrow function
 // instead we use a parameter followed by spread operator (...)
 console.log(args)
}

sumAllNums(1, 2, 3, 4)
// [1, 2, 3, 4]
```

```js
// function declaration
const sumAllNums = (...args) => {
  let sum = 0
  for (const element of args) {
    sum += element
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4)) // 10
console.log(sumAllNums(10, 20, 13, 40, 10))  // 93
console.log(sumAllNums(15, 20, 30, 25, 10, 33, 40))  // 173
```

### Anonymous Function

```js
const anonymousFun = function () { 
  console.log("I am an anonymous function and my value is stored in anonymousFun");
};
```

### Expression Function

```js
// Function expression
const square = function (n) {
  return n * n;
};

console.log(square(2)); // -> 4
```

### Self Invoking Functions

```js
(function (n) {
  console.log(n * n);
})(2); // 4, but instead of just printing if we want to return and store the data, we do as shown below

let squaredNum = (function (n) {
  return n * n;
})(10);

console.log(squaredNum);
```

### Arrow Function

```js
// This is how we write normal or declaration function
// Let us change this declaration function to an arrow function
function square(n) {
  return n * n;
}

console.log(square(2)); // 4

const square = (n) => {
  return n * n;
};

console.log(square(2)); // -> 4

// if we have only one line in the code block, it can be written as follows, explicit return
const square = (n) => n * n; // -> 4
```

```js
const changeToUpperCase = (arr) => {
  const newArr = [];
  for (const element of arr) {
    newArr.push(element.toUpperCase());
  }
  return newArr;
};

const countries = ["Finland", "Sweden", "Norway", "Denmark", "Iceland"];
console.log(changeToUpperCase(countries));

// ["FINLAND", "SWEDEN", "NORWAY", "DENMARK", "ICELAND"]
```

```js
const printFullName = (firstName, lastName) => {
  return `${firstName} ${lastName}`;
};

console.log(printFullName("Asabeneh", "Yetayeh"));
```

```js
const printFullName = (firstName, lastName) => `${firstName} ${lastName}`;

console.log(printFullName("Asabeneh", "Yetayeh"));
```

### Function with default parameters

```js
function greetings(name = "Peter") {
  let message = `${name}, welcome to 30 Days Of JavaScript!`;
  return message;
}

console.log(greetings());
console.log(greetings("Asabeneh"));
```

```js
function generateFullName(firstName = "Asabeneh", lastName = "Yetayeh") {
  let space = " ";
  let fullName = firstName + space + lastName;
  return fullName;
}

console.log(generateFullName());
console.log(generateFullName("David", "Smith"));
```

```js
function calculateAge(birthYear, currentYear = 2023) {
  let age = currentYear - birthYear;
  return age;
}

console.log("Age: ", calculateAge(1819));
```

```js
function weightOfObject(mass, gravity = 9.81) {
  let weight = mass * gravity + " N"; // the value has to be changed to string first
  return weight;
}

console.log("Newton: ", weightOfObject(100)); // 9.81 gravity at the surface of Earth
console.log("Newton: ", weightOfObject(100, 1.62)); // gravity at surface of Moon
```

Let us see how we write the above functions with arrow functions

```js
// syntax
// Declaring a function
const functionName = (param = value) => {
  //codes
};

// Calling function
functionName();
functionName(arg);
```

```js
const greetings = (name = "Peter") => {
  let message = name + ", welcome to 30 Days Of JavaScript!";
  return message;
};

console.log(greetings());
console.log(greetings("Asabeneh"));
```

```js
const generateFullName = (firstName = "Asabeneh", lastName = "Yetayeh") => {
  let space = " ";
  let fullName = firstName + space + lastName;
  return fullName;
};

console.log(generateFullName());
console.log(generateFullName("David", "Smith"));
```

```js
const calculateAge = (birthYear, currentYear = 2019) => currentYear - birthYear;
console.log("Age: ", calculateAge(1819));
```

```js
const weightOfObject = (mass, gravity = 9.81) => mass * gravity + " N";

console.log("Weight of an object in Newton: ", weightOfObject(100)); // 9.81 gravity at the surface of Earth
console.log("Weight of an object in Newton: ", weightOfObject(100, 1.62)); // gravity at surface of Moon
```

### Function declaration versus Arrow function

[<< Day 6](../06_Day_Loops/06_day_loops.md) | [Day 8 >>](../08_Day_Objects/08_day_objects.md)
