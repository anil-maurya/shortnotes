# JavaScript Variables & Scopes

In this Section, read about

Variables
	1. var
	2. let
	3. const

Scopes
  Global Scope
  Block Scope
  Function Scope
  Lexical Scope -- Read More in clousers.md

---
## Scope

ECMAScript 6 is also known as ES6 and ECMAScript 2015.

Before ES2015(ES6 or ECMASript 2015), JavaScript had only two types of scope: 
  - Global Scope 
  - Function Scope. 

Variables declared Globally (outside any function) have Global Scope.
Global variables can be accessed from anywhere in a JavaScript program.

Variables declared Locally (inside a function) have Function Scope.
Local variables can only be accessed from inside the function where they are declared.

ES2015 introduced two important new JavaScript keywords: let and const & block level scope.
  - Global Scope
  - Block Scope

let & const are block level scoped.


## Var vs Let

`var` is function scoped. if we declare variable within function it is limited to function only. It doesn't update global variable.


```javascript

var myName = 'Anil'

function getName(name){
	var myName = name //Reasigned and hence will not update global variable
	console.log(myName)
}

setName('Sunil') // Sunil

console.log(myName) //'Anil'


// But in case of if -- Block scope


if (myName === 'Anil') {
	var myName = 'Sunil'
	console.log(myName) //Sunil
}

console.log(myName) // Sunil

```


`let` is block scoped

if we declare variable using `let` keyword its scope will be block level not global level.


### Scoping Rule

let allows you to declare variables that are limited to the scope of a block statement, or expression on which it is used, 
unlike the var keyword, which defines a variable globally, or locally to an entire function regardless of block scope. 
The other difference between var and let is that the latter is initialized to a value only when a parser evaluates it.

Just like const the let does not create properties of the window object when declared globally (in the top-most scope).

At the top level of programs and functions, let, unlike var, does not create a property on the global object. For example:

```javascript
var x = 'global';
let y = 'global';
console.log(this.x); // "global"
console.log(this.y); // undefined
```

### Redeclaration

Redeclaring with `let or const`: 
1. the same variable with `let` or `const` within the same function or block scope raises a SyntaxError.
2. We can redeclare with `var` keyword

```javascript
if (x) {
  let foo;
  let foo; // SyntaxError thrown.
}
```

You may encounter errors in switch statements because there is only one block.

```javascript
let x = 1;
switch(x) {
  case 0:
    let foo;
    break;
    
  case 1:
    let foo; // SyntaxError for redeclaration.
    break;
}
```

However, it's important to point out that a block nested inside a case clause will create a new block scoped lexical environment, which will not produce the redeclaration errors shown above.

```javascript
let x = 1;

switch(x) {
  case 0: {
    let foo;
    break;
  }  
  case 1: {
    let foo;
    break;
  }
}
```


### Temporal Dead Zone

Unlike variables declared with var, which will start with the value undefined, let variables are not initialized until their definition is evaluated. Accessing the variable before the initialization results in a `ReferenceError`. The variable is in a "temporal dead zone" from the start of the block until the initialization is processed.

```javascript

function do_something() {
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  var bar = 1;
  let foo = 2;
}

```

### The temporal dead zone and typeof

Unlike with simply undeclared variables and variables that hold a value of undefined, using the typeof operator to check for the type of a variable in that variable's temporal dead zone will throw a ReferenceError:

```javascript

// prints out 'undefined'
console.log(typeof undeclaredVariable);

// results in a 'ReferenceError'
console.log(typeof i);
let i = 10;

```



### References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_dead_zone


## const

Variables defined with const behave like let variables, except they cannot be reassigned.
JavaScript const variables must be assigned a value when they are declared.

The keyword const is a little misleading.

It does NOT define a constant value. It defines a constant reference to a value.

Because of this, we cannot change constant primitive values, but we can change the properties of constant objects.

### Constant Objects can be cahnged

```javascript
// You can create a const object:
const car = {type:"Fiat", model:"500", color:"white"};

// You can change a property:
car.color = "red";

// You can add a property:
car.owner = "Johnson";

```

But constant object can not be reassigned

```javascript

const car = {type:"Fiat", model:"500", color:"white"};
car = {type:"Volvo", model:"EX60", color:"red"};    // ERROR

```


### Constant Arrays can Change

```javascript
// You can create a constant array:
const cars = ["Saab", "Volvo", "BMW"];

// You can change an element:
cars[0] = "Toyota";

// You can add an element:
cars.push("Audi");

```

But you can NOT reassign a constant array:


## Hoisting


In JavaScript we can refer to a variable/function declared later, without getting an exception. This concept is known as `hoisting` and the variable is `hoisted`.

However, variables that are hoisted return a value of undefined. So even if you declare and initialize after you use or refer to this variable, it still returns `undefined`.

Conceptually, for example, a strict definition of hoisting suggests that variable and function declarations are physically moved to the top of your code, but this is not in fact what happens. Instead, the variable and function declarations are put into memory during the compile phase, but stay exactly where you typed them in your code.



1. Variable Hoisting
2. Function Hoisting


## Variable hoisting

**Only declaration is hoisted**

IN CASE OF VAR

JavaScript only hoists declarations, not initializations. If a variable is declared and initialized after using it, the value will be undefined. 

For example:

```js

console.log(notDefined) // ReferenceError: notDefined is not defined

console.log(num); // Returns undefined, as only declaration was hoisted, no initialization has happened at this stage 
var num; // Declaration
num = 6; // Initialization

````


**Hoisting works within scope**

```js

console.log(p)  // undefined
console.log(c)  // ReferenceError: c is not defined

if (true) {
  var p;
  p = "something"
}
   
```
Here p is hoisted because variables declared with var are function scope and here p is declared within if which is global scope.


IN CASE OF LET/CONST

Hoisting doesnt seems to work with LET/CONST because it throws errors in both cases, only error changes


```js

console.log(alien); //Uncaught ReferenceError: alien is not defined

console.log(counter) //Uncaught ReferenceError: Cannot access 'counter' before initialization
let counter = 1;
```



## Function hoisting

IN CASE OF FUNCTION DECLARATION

functions declaration get hoised like `var`. We can use reference functions before declaring them.



```js

foo() // 'Foo...'

function foo(){
    console.log('Foo...')
}


bar() //Uncaught TypeError: bar is not a function. (Not hoisted)

if(true){
    function bar(){
        console.log('bar....')
    }
}

bar() // 'bar....'

// bar() is available here because of scope. It is not hoisted to global scope. it is alreay in global scope.
```


IN CASE OF FUNCTION EXPRESSION

Function expressions and arrow functions aren’t hoisted.


```js
let x = 20,
    y = 10;

let result = add(x,y); //Uncaught TypeError: add is not a function

console.log(result);

var add = function(x, y) {
return x + y;
}
```

Arrow functions

```js

let x = 20,
    y = 10;

let result = add(x,y);
console.log(result);

var add = (x, y) => x + y;


```