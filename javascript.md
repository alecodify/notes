# Javascript

## let and const

let: Block-scoped, can be updated but not re-declared within the same block.
const: Block-scoped, cannot be updated or re-declared. It creates a constant reference to a value.

- var is function-scoped or globally scoped, while let and const are block-scoped.
- var allows re-declaration, but let and const do not.

```code
let a = 10;
if (true) {
  let a = 20; // This `a` is only within the block.
  console.log(a); // 20
}
console.log(a); // 10
```

```code
const b = 10;
b = 20; // Error: Assignment to constant variable
```

## Arrow Function

Arrow functions are a shorter way to write function expressions and also handle the this keyword differently.

- Arrow functions do not have their own this context; they inherit this from the parent scope (lexical scoping).
- Traditional functions create their own this context.

```code
// Traditional function
function sum(a, b) {
  return a + b;
}

// Arrow function
const sum = (a, b) => a + b;
```

## Template Literals

It allow embedded expressions inside strings, using backticks (`) and ${ } for interpolation.

- It allow multi-line strings and interpolation, whereas normal strings (' ' or " ") do not without using concatenation.

```code
let name = "John";
let greeting = `Hello, ${name}!`;
console.log(greeting); // "Hello, John!"
```

## Default Parameters

You can set default values for function parameters if they are not provided.

- In ES5, you would have to manually check for undefined and set defaults inside the function. ES6 handles this more cleanly.

```code
function greet(name = 'Guest') {
  console.log(`Hello, ${name}!`);
}

greet(); // "Hello, Guest!"
greet('John'); // "Hello, John!"
```

## Destructuring Assignment

It allows you to unpack values from arrays or properties from objects into distinct variables.

```code
// Array Destructuring
const numbers = [1, 2, 3];
const [first, second] = numbers;
console.log(first, second); // 1, 2

// Object Destructuring
const person = { name: 'John', age: 30 };
const { name, age } = person;
console.log(name, age); // John, 30
```

## Rest and Spread Operators

Rest operator (...) gathers the remaining elements of an array or object into a new array or object. Spread operator (...) spreads an array or object into individual elements.

- Rest collects multiple elements into one.
- Spread expands elements from one source into another.

```code
// rest
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}
console.log(sum(1, 2, 3)); // 6

// spread
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
console.log(arr2); // [1, 2, 3, 4, 5]
```

## Classes

class keyword as syntactic sugar over JavaScript's prototype-based inheritance model.

```code
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hello, ${this.name}`);
  }
}

const john = new Person('John');
john.greet(); // "Hello, John"
```

## Modules

ES6 modules allow you to export and import functionality between JavaScript files. Modules provide a built-in way of organizing code into reusable chunks, replacing previous methods like using require().

```code
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

import { add, subtract } from './math.js';
console.log(add(2, 3)); // 5
```

## Promises

Promises provide a better way to handle asynchronous operations compared to callbacks. Promises avoid "callback hell" and make asynchronous code more readable.

```code
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Data fetched');
    }, 1000);
  });
};

fetchData()
  .then(data => console.log(data))  // "Data fetched"
  .catch(error => console.error(error));
```

## For-of Loop

The for-of loop provides a simpler way to iterate over iterable objects like arrays.

```code
const array = [1, 2, 3];
for (let value of array) {
  console.log(value); // 1, 2, 3
}
```

## map()

This method creates a new array by applying a function to each element of an existing array. It does not modify the original array.

```code
const numbers = [1, 2, 3, 4];
const squaredNumbers = numbers.map(num => num * num);
console.log(squaredNumbers); // [1, 4, 9, 16]
console.log(numbers); // [1, 2, 3, 4] (original array is unchanged)
```

- map() takes a callback function and applies it to each element.
- In this example, each number is squared, and the resulting array is [1, 4, 9, 16].

## filter()

This method creates a new array with all elements that pass a test (i.e., the callback function returns true for that element). It does not modify the original array.

```code
const numbers = [1, 2, 3, 4, 5, 6];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4, 6]
```

- filter() checks each element of the array and returns only those elements that satisfy the condition.
- Here, the callback checks if each number is even (num % 2 === 0), so the result is [2, 4, 6].

## reduce()

This method executes a reducer function (that you provide) on each element of the array, resulting in a single output value. It can be used to sum up numbers, concatenate strings, or perform more complex operations.

```code
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
console.log(sum); // 10
```

- The reduce() method takes two arguments: a callback and an initial value (here 0).
- The callback is executed on each element of the array, and the result is accumulated (stored in accumulator).
- This adds all numbers in the array to give a sum of 10.

## forEach()

This method executes a provided function once for each array element. It is primarily used for side effects (e.g., logging values). It does not return anything and does not create a new array.

```code
const numbers = [1, 2, 3, 4];
numbers.forEach(num => console.log(num * 2)); // Logs 2, 4, 6, 8
```

- forEach() is similar to a for loop, but it is more concise and specific to arrays.
- It doesn't return a new array or any value, just executes the function for each element.

## find()

This method returns the first element in an array that satisfies the provided testing function. If no element matches the condition, it returns undefined.

```code
const numbers = [5, 12, 8, 130, 44];
const found = numbers.find(num => num > 10);
console.log(found); // 12 (the first number greater than 10)
```

- find() is useful when you want to locate a single element based on a condition.
- In this case, it returns the first number greater than 10, which is 12.

## findIndex()

This method returns the index of the first element that satisfies the provided testing function. If no element matches, it returns -1.

```code
const numbers = [5, 12, 8, 130, 44];
const index = numbers.findIndex(num => num > 10);
console.log(index); // 1 (index of the first number greater than 10)
```

## some()

This method checks if at least one element in the array satisfies the provided testing function. It returns true if any element passes the test; otherwise, it returns false.

```code
const numbers = [1, 2, 3, 4];
const hasEvenNumber = numbers.some(num => num % 2 === 0);
console.log(hasEvenNumber); // true (since there are even numbers)
```

## every()

This method checks if all elements in the array satisfy the provided testing function. It returns true if all elements pass the test; otherwise, it returns false.

```code
const numbers = [1, 2, 3, 4];
const allEven = numbers.every(num => num % 2 === 0);
console.log(allEven); // false (not all numbers are even)
```

## sort()

This method sorts the elements of an array in place and returns the sorted array. By default, it sorts the elements as strings.

```code
const numbers = [40, 1, 5, 200];
numbers.sort();
console.log(numbers); // [1, 200, 40, 5] (sorted as strings)

numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 5, 40, 200] (sorted numerically)
```

## concat()

This method is used to merge two or more arrays. This method does not change the existing arrays but returns a new array.

```code
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const combined = array1.concat(array2);
console.log(combined); // [1, 2, 3, 4, 5, 6]
```

## slice()

This method returns a shallow copy of a portion of an array into a new array, without modifying the original array.

```code
const numbers = [1, 2, 3, 4, 5];
const sliced = numbers.slice(1, 3);
console.log(sliced); // [2, 3]
```

- slice(1, 3) extracts elements starting at index 1 up to (but not including) index 3.

## splice()

This method modifies the content of an array by removing or replacing existing elements and/or adding new elements in place.

```code
const numbers = [1, 2, 3, 4, 5];
numbers.splice(2, 1, 99); // at index 2, remove 1 element, and add 99
console.log(numbers); // [1, 2, 99, 4, 5]
```

- splice(2, 1, 99) means "remove 1 element at index 2 and insert 99 in its place".

## includes()

This method determines whether an array contains a specified element, returning true or false.

```code
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.includes(3)); // true
console.log(numbers.includes(6)); // false
```

## Difference b/w find() and filter()

find returns the first element in the array that satisfies the provided testing function.
find returns a single element (or undefined if no match is found).
find when you need to find one specific item from an array.

filter returns a new array containing all elements that satisfy the provided testing function.
filter returns an array, which may be empty if no elements match the condition.
filter when you want to get all elements that meet certain criteria.

```code
const users = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
  { id: 3, name: 'Charlie' },
  { id: 4, name: 'Bella' },
];

// Using find to get the first user whose name starts with 'B'
const foundUser = users.find(user => user.name.startsWith('B'));
console.log(foundUser);  // Output: { id: 2, name: 'Bob' }

// Using filter to get all users whose names start with 'B'
const filteredUsers = users.filter(user => user.name.startsWith('B'));
console.log(filteredUsers);  // Output: [{ id: 2, name: 'Bob' }, { id: 4, name: 'Bella' }]
```

```code
const numbers = [1, 3, 4, 6, 8, 9];

const foundNumber = numbers.find(num => num === 6);
console.log(foundNumber); // Output: 6

const filteredNumbers = numbers.filter(num => num === 6);
console.log(filteredNumbers); // Output: [6]
```

## Difference b/w map() and foreach()

map() creates a new array by applying a function to each element of the original array.
It returns a new array with the transformed elements.
When you need to transform each element in an array and get a new array with the results.

forEach() executes a provided function once for each array element but does not return anything.
forEach() does not return a new array. It just performs operations like logging or modifying elements.
When you want to iterate over an array but don't need a returned result (e.g., performing side effects like logging or updating a UI).

```code
const numbers = [1, 2, 3, 4];

// Using map to create a new array with numbers multiplied by 2
const doubled = numbers.map(num => num * 2);
console.log(doubled);  // Output: [2, 4, 6, 8]

// Using forEach to log each number (no return value)
numbers.forEach(num => console.log(num));
// Output: 
// 1
// 2
// 3
// 4
```
