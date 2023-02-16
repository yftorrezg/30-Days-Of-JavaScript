# Day 14

[<< Day 13](../13_Day_Console_object_methods/13_day_console_object_methods.md) | [Day 15>>](../15_Day_Classes/15_day_classes.md)

## Error Handling

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.log(err)
}
```

```sh
ReferenceError: fistName is not defined
    at <anonymous>:4:20
```

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.error(err) // we can use console.log() or console.error()
} finally {
  console.log('In any case I will be executed')
}
```

```sh
ReferenceError: fistName is not defined
    at <anonymous>:4:20
In any case it  will be executed
```

The catch block take a parameter. It is common to pass e, err or error as a parameter to the catch block. This parameter is an object and it has name and message keys. Lets use the name and message.

```js
try {
  let lastName = 'Yetayeh'
  let fullName = fistName + ' ' + lastName
} catch (err) {
  console.log('Name of the error', err.name)
  console.log('Error message', err.message)
} finally {
  console.log('In any case I will be executed')
}
```

```sh
Name of the error ReferenceError
Error message fistName is not defined
In any case I will be executed
```

```js
throw 'Error2' // generates an exception with a string value
throw 42 // generates an exception with the value 42
throw true // generates an exception with the value true
throw new Error('Required') // generates an error object with the message of Required
```

```js
const throwErrorExampleFun = () => {
  let message
  let x = prompt('Enter a number: ')
  try {
    if (x == '') throw 'empty'
    if (isNaN(x)) throw 'not a number'
    x = Number(x)
    if (x < 5) throw 'too low'
    if (x > 10) throw 'too high'
  } catch (err) {
    console.log(err)
  }
}
throwErrorExampleFun()
```

### Error Types

- **ReferenceError**: An illegal reference has occurred. A ReferenceError is thrown if we use a variable that has not been declared.

```js
let firstName = 'Asabeneh'
let fullName = firstName + ' ' + lastName
console.log(fullName)
```

```sh
Uncaught ReferenceError: lastName is not defined
    at <anonymous>:2:35
```

- **SyntaxError**: A syntax error has occurred

```js
let square = 2 x 2
console.log(square)
console.log('Hello, world")  // comillas
```

```sh
Uncaught SyntaxError: Unexpected identifier
```

- **TypeError**: A type error has occurred

```js
let num = 10
console.log(num.toLowerCase())
```

```sh
Uncaught TypeError: num.toLowerCase is not a function
    at <anonymous>:2:17
```

These are some of the common error you may face when you write a code. Understanding errors can help you to know what mistakes you made and it will help you to debug your code fast.

[<< Day 13](../13_Day_Console_object_methods/13_day_console_object_methods.md) | [Day 15>>](../15_Day_Classes/15_day_classes.md)