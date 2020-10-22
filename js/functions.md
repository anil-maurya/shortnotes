# Functions

- A JavaScript function is a block of code designed to perform a particular task.
function is executed when "something" invokes it (calls it).


- Every `function` in JavaScript is a `Function object`.


- we use `console.dir(f)` where f is function to describe the function object

  - arguments: null
  - caller: null
  - length: 0
  - name: "f"


## Creating Function | Function declaration vs Function expression

```js

// Function declaration

function test(){
    ....
}


// Function expression

const test = function(){
    ...
}
```

* Function expressions in JavaScript are not hoisted, unlike function declarations. You can't use function expressions before you create them:

*  The main difference between a function expression and a function declaration is the function name, which can be omitted in function expressions to create anonymous functions. A function expression can be used as an IIFE (Immediately Invoked Function Expression) which runs as soon as it is defined.

## Calling functions

There are four ways we can call a function -

1. As a function  => ` sayHello() `
2. As a method    => `obj.sayHello()`
3. As a constructor   => `new Greeter()` 
4. via call() and apply()
5. with back tick => Tag Function


## Execution Context

1. Global context => window, in node global


## Arrow Functions

Arrow functions were introduced with ES6 as a new syntax for writing JavaScript functions. They save developers time and simplify function scope


An arrow function expression is a compact alternative to a traditional function expression, but is limited and can't be used in all situations.

### Differences & Limitations:

* Does not have its own bindings to this or super, and should not be used as methods.

* Does not have local variable `arguments`, or new.target keywords.
But can be achieved by

```js
var bar = (...arguments) => console.log(arguments);
```


* Not suitable for call, apply and bind methods, which generally rely on establishing a scope.

* Can not be used as constructors. But can be used like factory functions

```js

var setNameIdsEs6 = (id, name) => ({ id: id, name: name });

```

* Can't use as generator function and can not use yield, within its body.

* named functions we treat arrow expressions like variables


### Use cases of arrow functions

* One common use case for arrow functions is array manipulation and the like
* Promises and Callbacks


## `arguments` object

arguments is an Array-like object accessible inside functions that contains the values of the arguments passed to that function.

```js
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1

  console.log(arguments[1]);
  // expected output: 2

  console.log(arguments[2]);
  // expected output: 3
}

func1(1, 2, 3);
```


## `new.target`

The new.target pseudo-property lets you detect whether a function or constructor was called using the new operator. In constructors and functions invoked using the new operator, new.target returns a reference to the constructor or function. In normal function calls, new.target is undefined.

```js
function Foo() {
  if (!new.target) { throw 'Foo() must be called with new'; }
}

try {
  Foo();
} catch (e) {
  console.log(e);
  // expected output: "Foo() must be called with new"
}
```


## Generator Function

New feature in ES6. Generators are special types of function which returns iterator

```js

function *testGen(){
  yield 1
  yield 2
  yield 3
  yield 4 
}

const iterator = testGen()

iterator.next() // {value:1, done: false}
iterator.next() // {value:2, done: false}
iterator.next() // {value:3, done: false}
iterator.next() // {value:4, done: false}
iterator.next() // {value:undefined, done: true}

```


```js

function* genInfinity(){
  let num = 0
  while(true){
    yield num
    num += 1
  }
}

const iterator = testGen()

iterator.next() // {value:0, done: false}
iterator.next() // {value:1, done: false}
iterator.next() // {value:2, done: false}
iterator.next() // {value:3, done: false}
iterator.next() // {value:4, done: false}
```

* To create generator function we need to use * either at start of function keyword or start of function name

```js
    - function* generatorFunction()
    - function *generatorFunction()
```

* Generators are created by generator functions function* f(…) {…}.
* Inside generators (only) there exists a yield operator.
* The outer code and the generator may exchange results via next/yield calls.


## Constrcutor Function

Constructors are like regular functions, but we use them with the new keyword. There are two types of constructors: 

  1.  built-in constructors such as Array and Object, which are available automatically in the execution environment at runtime;
  2. custom constructors, which define properties and methods for your own type of object.


- Constractor functions name start with capital letter.
- Always use `new` keyword
- return statement is not used.

```js

function Circle(radius) {
  this.radius = 'radius';
  this.draw  = function(){
    console.log('draw')
  }
}

const another = new Circle(2)

````

When a function is called with the new keyword, couple of things happen behind the scenes:

- A new empty object is created
- The context object this is bound to the new empty object
- The new object is linked to the function’s prototype property
- this is automatically returned unless another value is returned explicitly from the function


## Factory Functions

A factory function is any function which is not a class or constructor that returns a (presumably new) object. In JavaScript, any function can return an object. When it does so without the new keyword, it’s a factory function.

```js

function person(firstName, lastName, age) {
  const person = {};
  person.firstName = firstName;
  person.lastName = lastName;
  person.age = age;
  return person;
}

const personObj = person("Anil", "Maurya", 37)
```



### `this`

* this keyword refers to an object, that object which is executing the current bit of javascript code.

* In other words, every javascript function while executing has a reference to its current execution context, called this. Execution context means here is how the function is called.

* Only matters How, when and from where the function is called, 

* does not matter where function is declared or defined.

Precedence of “this” keyword bindings
  
  => First it checks whether the function is called with new keyword.
  
  => Second it checks whether the function is called with call() or apply() method means explicit binding.

  => Third it checks if the function called via context object (implicit binding).
  
  => Default global object (undefined in case of strict mode).


- Functions --> Global
- Methods  --> Object
- Constructors --> Instance
- Arrow Functions - Arrow functions always bind to global object. 

Examples

```js

function Person(fn, ln) {
  this.first_name = fn;
  this.last_name = ln;

  this.displayName = function() {
    console.log(`Name: ${this.first_name} ${this.last_name}`);
  }
}

let person = new Person("John", "Reed");

person.displayName(); // Prints Name: John Reed

let person2 = new Person("Paul", "Adams");
person2.displayName(); // Prints Name: Paul Adams

person.displayName.call(person2); // Here we are setting value of this to be person2 object

```


#### Default and Implicit Binding

default binding of 'this'

  * In 'strict mode', default value of `this` is 'undefined' otherwise - Global object.

Implicit binding of 'this'
  
  * when there is an object property which we are calling as a method then that object becomes this object or execution context object for that method, it is implicit binding of this keyword.


#### Explicit Binding of 'this'

We can use `call(), apply(), bind()` methods to explicit bind 'this'. It is called explicit binding because we are passing 'this' to it.


```js

function bike() {
  console.log(this.name);
}

var name = "Ninja";
var obj1 = { name: "Pulsar", bike: bike };
var obj2 = { name: "Gixxer", bike: bike };

bike();           // "Ninja"
obj1.bike();      // "Pulsar"
obj2.bike();      // "Gixxer"



```



## Call & Apply

The call() method calls a function with a given this value and arguments provided individually.

With `call()` method, we can write a method that can be used on different objects.

`apply()` method works same as `call()` only difference is apply passes parameter as an array and call passes params individually.

```js

// Function without parameters
function greet(){
  console.log("Welcome, " + this.fName + " " + this.lName)
}

const person1 = {
  fName : "Anil",
  lName : "Maurya"
}

const person2 = {
  fName : "Suresh",
  lName : "Kala"
}

// Call
greet.call(person1); // Welcome, Anil Maurya
greet.call(person2); // Welcome, Suresh Kala

// Apply
greet.call(person1); // Welcome, Anil Maurya
greet.call(person2); // Welcome, Suresh Kala

// Function with parameters

function greet(dist, state, country){
  console.log("Welcome, " + this.fName + " " + this.lName)
  console.log("You are from " + dist + ", " + state + ", " + country)
}

greet.call(person1, "Bahraich", "UP", "India")

// Welcome, Anil Maurya
// You are from Bahraich, UP, India

greet.call(person2, "Gonda", "MP", "India")

// Welcome, Suresh Kala
// You are from Gonda, MP, India


greet.apply(person1, ["Bahraich", "UP", "India"])

// Welcome, Anil Maurya
// You are from Bahraich, UP, India

greet.apply(person2, ["Gonda", "MP", "India"])

// Welcome, Suresh Kala
// You are from Gonda, MP, India

```

## Bind method

By using `bind()` method we can bind any object to other function or method and the function will treat binded object as its own object.


Unlike `call(), apply()` methods, the `bind()` doesn't immediately execute the function. It just returns the function.

```js

let person = {
    name: 'John Doe',
    getName: function() {
        console.log(this.name);
    }
};

let person2 = {
  name : "Anil Maurya"
}

setTimeout(person.getName, 1000); //undefined

// Binding object to getName Method

let f = person.getName.bind(person);

setTimeout(f, 1000) //John Doe

// Another object

person2 = {
  name: "Radhe Radeh"
}


let f = person.getName.bind(person2);

setTimeout(f, 1000) //Radhe Radhe
```

## Callback
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.



```js

function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);

```

The above example is a synchronous callback, as it is executed immediately.



however, that callbacks are often used to continue code execution after an asynchronous operation has completed — these are called asynchronous callbacks. 

A good example is the callback functions executed inside a .then() block chained onto the end of a promise after that promise fulfills or rejects. This structure is used in many modern web APIs, such as fetch().

## Pure function

Functions which always returns same value  if input is same and don't have side-effect.


```js

const add = (x, y) => x + y;

add(2, 4); // 6

```

### Side-Effect of Functions

side-effect is any work a function performs that isn’t related to calculating the final output.

Few side effects -
  
  - Mutating your input
  - console.log
  - HTTP calls (AJAX/fetch)
  - Changing the filesystem (fs)
  - Querying the DOM


**“Impurely” Changing an Object**

```js
const impureAssoc = (key, value, object) => {
  object[key] = value;
};

const person = {
  name: 'Bobo'
};

const result = impureAssoc('shoeSize', 400, person);

console.log({
  person,
  result
});


// changing it to pure function


const pureAssoc = (key, value, object) => ({
  ...object,
  [key]: value
});

const person = {
  name: 'Bobo'
};

const result = pureAssoc('shoeSize', 400, person);

console.log({
  person,
  result
});

```
  

### Avoiding Side Effect

- By writing pure functions.


## IIFE - Immediately Invoked Function Expression

An IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.

```js
(function () {
    statements
})();

```

## Casecade Function, Methods Chaining

In a cascade, we can call many methods on the same object in sequence in a single statement.

Chaining Methods, also known as Cascading, means repeatedly calling one method after another on an object, in one continuous line of code.

The trick is that the method itself should only return `this`(object). That way, each time you chain these methods together, the object itself is the base of the call. This is how JQuery works.

```js
let obj = {
    name : "Anil Maurya",
    greet : function(){
      console.log('Good Morning ' + this.name)
      return this
  },
  tellName : function(){
    console.log('I am ' + this.name)
    return this
  },
  tellAge : function(){
    console.log('I am ' + 42 + ' years old')
    return this
  }
}

obj
 .greet()
 .tellName()
 .tellAge()

 ```



## Currying

In functional programming, currying is the process of converting a function, that takes multiple arguments at once, to a function that takes these arguments step by step.

```js

// Suppose we have normal function which takes 3 arguments

function add(a, b, c){
  return a + b + c;
}


console.log(add(5+7+9))

// Same function can be written using currying technique

function add(a){
  return function(b){
    return function(c){
      return a + b + c
    }
  }
}


// Calling 

console.log(add(5)(7)(9))


// Currying using arrow function

const add = a=>b=>c=>a+b+c

console.log(add(5)(7)(9))

```


## Memoizatin

Memoization is the programmatic practice of making long recursive/iterative functions run much faster.

When we input the same value into our memoized function, it returns the value stored in the cache instead of running the function again, thus boosting performance. No longer does your program have to recalculate every number to get a result.

Memoization is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again


```js
// a simple function to add something
const add = (n) => (n + 10);

add(9);

// a simple memoized function to add something
const memoizedAdd = () => {
  let cache = {};
  return (n) => {
    if (n in cache) {
      console.log('Fetching from cache');
      return cache[n];
    }
    else {
      console.log('Calculating result');
      let result = n + 10;
      cache[n] = result;
      return result;
    }
  }
}
// returned function from memoizedAdd
const newAdd = memoizedAdd();
console.log(newAdd(9)); // calculated
console.log(newAdd(9)); // cached

```


### Writing Memoized Function

```js
// a simple pure function to get a value adding 10
const add = (n) => (n + 10);

console.log('Simple call', add(3));
// a simple memoize function that takes in a function
// and returns a memoized function
const memoize = (fn) => {
  let cache = {};
  return (...args) => {
    let n = args[0];  // just taking one argument here
    if (n in cache) {
      console.log('Fetching from cache');
      return cache[n];
    }
    else {
      console.log('Calculating result');
      let result = fn(n);
      cache[n] = result;
      return result;
    }
  }
}
// creating a memoized function for the 'add' pure function
const memoizedAdd = memoize(add);
console.log(memoizedAdd(3));  // calculated
console.log(memoizedAdd(3));  // cached
console.log(memoizedAdd(4));  // calculated
console.log(memoizedAdd(4));  // cached



//Memoizing recursive function

const factorial = memoize(
  (x) => {
    if (x === 0) {
    return 1;
  }else {
    return x * factorial(x - 1);
  }
});
```


### When to memoize your functions

* In order to memoize a function, it should be pure so that return values are the same for same inputs every time

* Memoizing is a trade-off between added space and added speed and thus only significant for functions having a limited input range so that cached values can be made use of more frequently

* It might look like you should memoize your API calls however it isn’t necessary because the browser automatically caches them for you. See HTTP caching for more detail

* The best use case I found for memoized functions is for heavy computational functions which can significantly improve performance (factorial and fibonacci are not really good real world examples)

* If you’re into React/Redux you can check out reselect which uses a memoized selector to ensure that calculations only happen when a change happens in a related part of the state tree.



## Simple Function Composition

 function composition is a mechanism to combine simple functions to build more complicated ones. Like the usual composition of functions in mathematics, the result of each function is passed as the argument of the next, and the result of the last one is the result of the whole.


Function composition is the process of combining two or more functions to produce a new function. Composing functions together is like snapping together a series of pipes for our data to flow through.


## Recursive Function

Recursion is a technique for iterating over an operation by having a function call itself repeatedly until it arrives at a result. Most loops can be rewritten in a recursive style, and in some functional languages this approach to looping is the default.

Example :

Calculate factorial - of 10 => 1x2x3x4x5x6x7x8x9x10

```js
  function fact(num){
    if(num<=1){
      return 1
    }else{
      return num * fact(num - 1) 
    }
  }

```

### Tail Call optimization
One problem with contemporary implementations of JavaScript is that they don’t have a standard way to prevent recursive functions from stacking up on themselves indefinitely, and eating away at memory until they exceed the capacity of the engine. JavaScript recursive functions need to keep track of where they were called from each time, so they can resume at the correct point.



## Tagged Templates / Tagged Function
Another use case of template literals can be used to call a function.

```js
// typical function
function greet(){};

// Function to use with tagged tempalte

function greet(arr, nameArg, ageArg) {
  console.log(arr[0] + nameArg + arr[1] + ageArg + arr[2]);
}

// TAG FUNCTION

greet`I'am ${name}. I am ${age} years old.`

