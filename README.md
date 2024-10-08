

# JavaScript Functions

## 1. Function Basics
A function is a block of reusable code designed to perform a specific task. Functions can take input, called parameters, and return an output.

## 2. Function Parameters vs. Arguments
- **Parameters** are variables listed in the function's definition.
- **Arguments** are the actual values passed to the function when it's invoked.

```javascript
function add(a, b) {  // a and b are parameters
  return a + b;
}

add(5, 3);  // 5 and 3 are arguments
```

## 3. Passing Values to Functions

### 3.1 Pass by Value
In JavaScript, **primitive types** (e.g., number, string, boolean, undefined, null, symbol, bigint) are passed by **value**. This means the function gets a copy of the original value, and any changes made to the parameter inside the function do not affect the original argument.

```javascript
function modifyValue(val) {
  val = 10;
}

let num = 5;
modifyValue(num);   // num is passed by value
console.log(num);   // Output: 5 (original value unchanged)
```

### 3.2 Pass by Reference
In JavaScript, **objects** (including arrays and functions) are passed **by reference**. This means the function gets a reference (or memory address) to the original object, and any changes made to the object inside the function will affect the original object.

```javascript
function modifyObject(obj) {
  obj.name = 'Suryakant';
}

let person = { name: 'John' };
modifyObject(person);
console.log(person.name);   // Output: 'Suryakant' (original object is modified)
```

## 4. Default Parameters
In ES6, you can define default values for parameters. If an argument is not provided, the default value is used.

```javascript
function greet(name = 'Guest') {
  console.log('Hello, ' + name + '!');
}

greet();            // Output: 'Hello, Guest!'
greet('Suryakant'); // Output: 'Hello, Suryakant!'
```

## 5. Rest Parameters (`...`)
Rest parameters allow you to pass an indefinite number of arguments to a function as an array. The syntax involves using the `...` operator.

```javascript
function sum(...numbers) {
  return numbers.reduce((total, number) => total + number, 0);
}

console.log(sum(1, 2, 3, 4));  // Output: 10
```

## 6. Arguments Object
In non-arrow functions, JavaScript provides a special `arguments` object, which contains all arguments passed to the function. It is an array-like object.

```javascript
function showArguments() {
  console.log(arguments); // Outputs an array-like object of all arguments
}

showArguments(1, 2, 3);  // Output: [1, 2, 3]
```
> **Note**: The `arguments` object is not available in arrow functions. For modern JavaScript, rest parameters are preferred over arguments.

## 7. Return Values
A function can return a value using the `return` statement. If no `return` is specified, the function returns `undefined`.

```javascript
function multiply(a, b) {
  return a * b;   // Returns the product of a and b
}

let result = multiply(2, 3);
console.log(result);  // Output: 6
```

## 8. Function Expressions vs. Function Declarations
A **function declaration** defines a function with a name:
```javascript
function sayHello() {
  console.log('Hello!');
}
```

A **function expression** assigns an anonymous function to a variable:
```javascript
const sayHello = function() {
  console.log('Hello!');
};
```

## 9. Arrow Functions
Arrow functions provide a shorter syntax for writing functions and have special behavior for `this` and `arguments` binding.

```javascript
const greet = (name) => {
  return 'Hello, ' + name + '!';
};

console.log(greet('Suryakant'));  // Output: 'Hello, Suryakant!'
```

Arrow functions have an implicit return when the function body has only one expression:
```javascript
const add = (a, b) => a + b;
console.log(add(3, 4));  // Output: 7
```

## 10. Higher-Order Functions
A **higher-order function** is a function that either takes another function as an argument or returns a function.

### Example (Passing a function as an argument):
```javascript
function greet(name) {
  return 'Hello, ' + name + '!';
}

function logGreeting(greetingFunction, name) {
  console.log(greetingFunction(name));
}

logGreeting(greet, 'Suryakant');  // Output: 'Hello, Suryakant!'
```

### Example (Returning a function):
```javascript
function multiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

let triple = multiplier(3);
console.log(triple(5));  // Output: 15
```

## 11. Closures
A **closure** is a function that retains access to variables from its parent scope, even after the parent function has returned.

```javascript
function outer() {
  let count = 0;

  return function() {
    count++;
    console.log(count);
  };
}

const increment = outer();
increment();  // Output: 1
increment();  // Output: 2
```

## 12. Anonymous Functions
An **anonymous function** is a function without a name. It can be assigned to a variable, passed as an argument, or used as an IIFE (Immediately Invoked Function Expression).

### Example (Function as an argument):
```javascript
setTimeout(function() {
  console.log('Hello after 3 seconds!');
}, 3000);
```

## 13. IIFE (Immediately Invoked Function Expression)
An IIFE is a function that runs immediately after it is defined. It is often used to avoid polluting the global namespace.

```javascript
(function() {
  console.log('This runs immediately!');
})();
```

## 14. Recursion
A **recursive function** is a function that calls itself until a condition is met.

```javascript
function factorial(n) {
  if (n === 1) return 1;  // Base case
  return n * factorial(n - 1);  // Recursive case
}

console.log(factorial(5));  // Output: 120
```

## Summary:
- **Parameters**: Placeholders in a function definition.
- **Arguments**: Actual values passed to the function.
- **Pass by Value**: Primitive types are passed by value, and changes inside the function don't affect the original variable.
- **Pass by Reference**: Objects (arrays, functions, etc.) are passed by reference, and changes inside the function affect the original object.
- **Rest Parameters**: Allows for collecting an arbitrary number of arguments into an array.
- **Closures**: Functions that retain access to their outer scope's variables.
