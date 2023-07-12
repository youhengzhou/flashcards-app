# JavaScript Array Functions: forEach, map, reduce, filter, and Sets

JavaScript provides several built-in functions to work with arrays, including forEach, map, reduce, and filter. Additionally, JavaScript introduced Set objects in ES6, which can be used to perform operations common in set theory.

# forEach

The forEach function is used to iterate over an array and execute a function on each element. Unlike map, forEach does not return a new array. It's typically used when you want to perform an operation using each item in an array but don't need to create a new array as a result (stackoverflow.com).

```
const array = [1, 2, 3, 4, 5];
const square = number => console.log(number * number);
array.forEach(square); // logs 1, 4, 9, 16, 25
```

# map

The map function is used to create a new array by performing a function on each element in an original array. The original array is not mutated (freecodecamp.org, stackoverflow.com).

```
const array = [1, 2, 3, 4, 5];
const square = number => number * number;
const squaredArray = array.map(square);
console.log(squaredArray); // logs [1, 4, 9, 16, 25]
```

# reduce

The reduce function is used to transform an array into a single value. It does this by applying a function to each element in the array, from left to right, and accumulating the result (freecodecamp.org).

```
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((result, item) => result + item, 0);
console.log(sum); // logs 10
```

# filter

The filter function creates a new array with all elements that pass a test provided as a function. The original array is not mutated (freecodecamp.org).

```
const numbers = [1, 2, 3, 4, 5];
const isEven = number => number % 2 === 0;
const evenNumbers = numbers.filter(isEven);
console.log(evenNumbers); // logs [2, 4]
```

# Set

A Set object lets you store unique values of any type. With ES6's Set, it's easy to compute a set difference, and it's reportedly faster than indexOf for large arrays (stackoverflow.com).

```
let a = new Set([1, 2, 3, 4]);
let b = new Set([5, 4, 3, 2]);

let a_minus_b = new Set([...a].filter(x => !b.has(x)));
let b_minus_a = new Set([...b].filter(x => !a.has(x)));
let a_intersect_b = new Set([...a].filter(x => b.has(x)));
let a_union_b = new Set([...a, ...b]);

console.log(...a_minus_b);     // logs {1}
console.log(...b_minus_a);     // logs {5}
console.log(...a_intersect_b); // logs {2,3,4}
console.log(...a_union_b);     // logs {1,2,3,4,5}
```

In conclusion, JavaScript provides a rich set of functions and objects to work with arrays and sets. These tools can make your code more readable, maintainable, and efficient (digitalocean.com, freecodecamp.org, stackoverflow.com).

# JavaScript Algorithm Involving Dictionaries and Classes

# Creating a Dictionary Class

First, we need to define a Dictionary class. This class will have a table object property to store the key-value pairs and a toStrFn function to convert the keys into strings. This is necessary as JavaScript is not strongly typed, and we cannot guarantee that the key will be a string. Converting the key to a string makes it easier to search and retrieve values from the dictionary dev.to, dev.to.

```
class Dictionary {
    constructor(toStrFn = defaultToString) {
        this.table = {};
        this.toStrFn = toStrFn;
    }
}

function defaultToString(item) {
    if (item === null) {
        return 'NULL';
    } else if (item === undefined) {
        return 'UNDEFINED';
    } else if (typeof item === 'string' || item instanceof String) {
        return `${item}`;
    }
    return item.toString();
}
```

# Adding Methods to the Dictionary Class

We can add several methods to the Dictionary class to allow us to interact with the dictionary dev.to.

- set(key, value): This method is used to add a new element to the dictionary. If the key already exists, the existing value will be overwritten with the new one.

```
set(key, value) {
    if (key != null && value != null) {
        const tableKey = this.toStrFn(key);
        this.table[tableKey] = {key, value};
        return true;
    }
    return false;
}
```

- keyValues(): This method returns an array of all key-value pairs of the dictionary.

```
keyValues() {
    return Object.values(this.table);
}
```

- keys(): This method returns an array of all the keys the dictionary contains.

```
keys() {
    return this.keyValues().map(valuePair => valuePair.key);
}
```

- values(): This method returns an array of all the values of the dictionary.

```
values() {
    return this.keyValues().map(valuePair => valuePair.value);
}
```

- forEach(callback): This method iterates over every key-value pair in the dictionary and applies a callback function dev.to.

```
forEach(callback) {
    let keyValuePairs = this.keyValues();
    for (let index = 0; index < keyValuePairs.length; index++) {
        const result = callback(keyValuePairs[index].key, keyValuePairs[index].value);
        if (result == false) {
            break;
        }
    }
}
```

With this Dictionary class, we can store key-value pairs, iterate over them, and perform operations on them. This is a fundamental part of many algorithms in JavaScript.

In JavaScript, Object-Oriented Programming (OOP) is implemented differently compared to other languages. JavaScript is a prototype-based language, not a class-based language [0]. However, it does provide mechanisms to use OOP concepts, and these include objects and classes [1].

# practice

Based on the information found, here are some JavaScript algorithm questions that test your knowledge on data structures like arrays, sets, and functions like forEach, map, reduce, filter:

```
{
  code: `
  const numbers = [1, 2, 3, 4, 5];
  const square = number => number * number;
  const squaredArray = numbers.map(square);
  console.log(squaredArray);
  `,
  answer: `[1, 4, 9, 16, 25]`,
}
```

```
{
  code: `
  const numbers = [1, 2, 3, 4, 5];
  const isEven = number => number % 2 === 0;
  const evenNumbers = numbers.filter(isEven);
  console.log(evenNumbers);
  `,
  answer: `[2, 4]`,
}
```

```
{
code: ` const numbers = [1, 2, 3, 4];
  const sum = numbers.reduce((result, item) => result + item, 0);
  console.log(sum);
`,
answer: `10`,
}
```

```
{
  code: `
  let a = new Set([1, 2, 3, 4]);
  let b = new Set([5, 4, 3, 2]);

  let a_minus_b = new Set([...a].filter(x => !b.has(x)));
  let b_minus_a = new Set([...b].filter(x => !a.has(x)));
  let a_intersect_b = new Set([...a].filter(x => b.has(x)));
  let a_union_b = new Set([...a, ...b]);

  console.log(...a_minus_b);
  console.log(...b_minus_a);
  console.log(...a_intersect_b);
  console.log(...a_union_b);
  `,
  answer: `1, 5, 2,3,4, 1,2,3,4,5`,
}
```

# Objects in JavaScript

An object in JavaScript is a unique entity that contains properties and methods [1]. Objects are everywhere in JavaScript, and almost every element is an object, whether it's a function, an array, or a string [1].

You can create an object like this:

```
let names = {
    fname: "Dillion",
    lname: "Megida"
}
console.log(names.fname); // Dillion
console.log(names.hasOwnProperty("mname")); // false
```

In this example, the object names has only two properties - fname and lname [0].

# Classes in JavaScript

Classes are blueprints of an object [1]. A class can have many objects because the class is a template while objects are instances of the class or the concrete implementation [1].

Classes were introduced in ECMAScript 2015 as a syntactical sugar over JavaScript’s existing prototype-based inheritance. The class syntax does not introduce a new object-oriented inheritance model to JavaScript but provides a simpler and clearer syntax to create objects and deal with inheritance [1].

You can create a class like this:

```
class Name {
    constructor(var) {
        this.var = var;
    }
}
```

In this example, Name is a class with a constructor that initializes a property var [2].

You can define methods, getters, and setters in a class like this:

```
class Name {
    constructor(var) {
        this.var = var;
    }
    // defining method
    method() {
        //Code Here
    }
    // defining getter method
    get method() {
        //Code Here
    }
    // defining setter method
    set method(value) {
        this.var = value;
    }
}
```

In this example, method() is a method of the class, get method() is a getter method, and set method(value) is a setter method [2].

# Prototypal Inheritance

In JavaScript, all objects have access to the Object's prototype. They do not possess these properties, but are granted access to the properties in the prototype [0]. This is called Prototypal Inheritance (or Prototypal Delegation) [3].

# Conclusion

Understanding the JavaScript approach to Object-Oriented Programming, especially its use of objects, classes, and prototypal inheritance, is crucial for any developer. These concepts form the foundation of how JavaScript manages and organizes data, which is key to building efficient and effective applications.
