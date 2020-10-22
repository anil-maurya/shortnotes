# JavaScript Basics

JavaScript is a general pupose programming language which can run both on server-side using node and client side using browser.

It is a lightweight interpreted but uses JIT(just-in-time) Compiling to improve performance,  single-threaded, & support multi-pradigms


## ECMAScript

The full form of ECMA is European Computer Manufacturer's Association. ECMAScript is a Standard for scripting languages such as JavaScript, JScript, etc. It is a trademark scripting language specification. JavaScript is a language based on ECMAScript. A standard for scripting languages like JavaScript, JScript is ECMAScript. JavaScript is considered as one of the most popular implementations of ECMAScript.

Whether ECMAScript is the language and JavaScript is a dialect is arguable, but not important. If you continue to think like this it might confuse you. There is no compiler out there that would run ECMAScript, and I believe JavaScript is considered the Language which implements a standard called ECMAScript.

## ECMAScript Versions

**ES6 | ECMAScript 2015**
The 6th edition, initially known as ECMAScript 6 (ES6) then and later renamed to ECMAScript 2015, was finalized in June 2015

- `class` declaration
- ES6 Modules like `import & exports`
- Iterator and `for...of`
- generators 
- arrow functions `()=>{...}`
- `let` & `const` kyword
- `promises`
- Reflections
- proxies
- template litersl for strings

**ES7 | ECMAScript 2016**

- block-scoping of vairables and functions
- destrucucturing patterns
- exponentiaion operator `**` : equivalent to `Math.paw`
- `await`, `async`
- `Array.prototype.includes`
- Decorator


**ES8 | ECMAScript 2017**
- Object.values
- Object.entries
- Object.getWonPropertyDescriptors
- `aysnc/await` constructions which use generators and promieses.
- concurrency and atomics.

**ES9 | ECMAScript 2018**
- spread operator `...`
- `Promise.prototyype.finally`

**ES10 | ECMAScript 2019**
- `Array.prototype.flat`
- `Array.protoype.flatMap`
- `Array.sort`
- `Object.fromEntries`

**ES11 | ECMAScript 2020**

- Primitive `BigInt` . Number bigger than (2^53+1 to -2^53-1)
- Null Coalescing syntax `??` & `?` for object.child

```js
false ?? "string" // -> false
NaN ?? "string" // -> NaN
undefined ?? "string" // -> "string"

//Opetional Chaining
person?.address?.zipcode

````

## Literlas in Javascript

Literals represent values in JavaScript. These are fixed values—not variables—that you literally provide in your script.

Types of literals

* Array literals : []
* Boolean literals : true/false
* Floating-point literals : 
* Numeric literals : 1, 2, 3
* Object literals  : {}
* RegExp literals  : /ab+c/;
* String literals  : "", ''


## Data types

1. Value Types  or Primitives
   
   1. Number
   2. String
   3. Boolean
   4. Symbol
   5. undefined
   6. null
   7. bigint

2. Reference Type
   - Object
   - Function
   - Array

Primitives vs Reference

Primities are copied by their value and Objects are copied by their reference

## Primitives

These six types are considered to be *primitives*. A primitive is not an object and has no methods of its own. **All *primitives are immutable***.

1. [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) — true or false
2. [Null](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/null) — no value
3. [Undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined) — a declared variable but hasn’t been given a value
4. [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) — integers, floats, etc
5. [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) — an array of characters i.e words
6. [Symbol](https://hacks.mozilla.org/2015/06/es6-in-depth-symbols/) — a unique value that's not equal to any other value

7. BigInt

In JavaScript, the `number` can not represent integer values larger than (2^53-1) or less than-(2^53-1). It is a technical limitation causedd by their internal representation.

A `BigInt` value is created by appending `n` to the end of an integer.

```
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

## Objects
Everything else is an **Object** type.

There are 6 types of objects:
- Object
- Date
- Array
- String
- Number
- Bolean

There are constructors to create these types Like -

- Boolean()

- Number()

- Symbol()

Although we need not to use these constructors to create primitives excepts `Symbol`


## "use strict"

* The `use strict` directive switches the engine to modern mode, changing the behaviour of some built-in features.

* Strict mode is always place at the top of a script of function.

* Strict mode is supported by all modern browsers.****

**Why Strict mode ?**

* Strict mode makes it easier to write "secure" JavaScript.

* Strict mode changes previously accepted "bad syntax" into real errors.

* Using variable without declaration `x = 3.14 ` throw an error, making it impossible to accidentally create a global variable. Earlier we could do that.

* In normal JavaScript, a developer will not receive any error feedback assigning values to non-writable properties.

* In strict mode, any assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object, will throw an error.



**What changes in `strict mode`**

* Can not use undeclared variable `x = 3.5 // throws error`

* Using object without declaring it, is not allowed

* Deleting variable , object or function not allowed

* duplicating parameter names in function is not allowed

* Octal numeric literals are not allowed. `var x = 010;`

* Octal escape character are not allowed `var x = "\010"`

* Writing to a read-only property is not allowed: 

```js
"use strict";
var obj = {};
Object.defineProperty(obj, "x", {value:0, writable:false});

obj.x = 3.14;            // This will cause an error
```

Writing to a get-only property is not allowed:

```js
"use strict";
var obj = {get x() {return 0} };

obj.x = 3.14;       
```



The words `eval, arguments, with` are not allowed as variable name.

Future proof : 

Keywords reserved for future JavaScript versions can NOT be used as variable names in strict mode.

These are:

- implements
- interface
- let
- package
- private
- protected
- public
- static
- yield

## Map & Set

Map is a collection of keyed data items, just like an Object. But the main difference is that Map allows keys of any type.

Methods and properties are:

* `new Map()` – creates the map.
* `map.set(key, value)` – stores the value by the key.
* `map.get(key)` – returns the value by the key, undefined if key doesn’t exist in map.
* `map.has(key)` – returns true if the key exists, false otherwise.
* `map.delete(key)` – removes the value by the key.
* `map.clear()` – removes everything from the map.
* `map.size` – returns the current element count.

```js
let map = new Map();

map.set('1', 'str1');   // a string key
map.set(1, 'num1');     // a numeric key
map.set(true, 'bool1'); // a boolean key

// remember the regular Object? it would convert keys to string
// Map keeps the type, so these two are different:
alert( map.get(1)   ); // 'num1'
alert( map.get('1') ); // 'str1'

alert( map.size ); // 3

```

Note - 

Although map[key] also works, e.g. we can set map[key] = 2, this is treating map as a plain JavaScript object, so it implies all corresponding limitations (no object keys and so on).

So we should use map methods: set, get and so on.


### Iteration over Map
For looping over a map, there are 3 methods:

* `map.keys()` – returns an iterable for keys,
* `map.values()` – returns an iterable for values,
* `map.entries()` – returns an iterable for entries [key, value], it’s used by default in for..of.


The iteration goes in the same order as the values were inserted. Map preserves this order, unlike a regular Object.


## Set

A Set is a special type collection – “set of values” (without keys), where each value may occur only once.

Its main methods are:

* `new Set(iterable)` – creates the set, and if an iterable object is provided (usually an array), copies values from it into the set.
* `set.add(value)` – adds a value, returns the set itself.
* `set.delete(value)` – removes the value, returns true if value existed at the moment of the call, otherwise false.
* `set.has(value)` – returns true if the value exists in the set, otherwise false.
* `set.clear()` – removes everything from the set.
* `set.size` – is the elements count.

The main feature is that repeated calls of set.add(value) with the same value don’t do anything. That’s the reason why each value appears in a Set only once.

For example, we have visitors coming, and we’d like to remember everyone. But repeated visits should not lead to duplicates. A visitor must be “counted” only once.

```js
let set = new Set();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

// visits, some users come multiple times
set.add(john);
set.add(pete);
set.add(mary);
set.add(john);
set.add(mary);

// set keeps only unique values
alert( set.size ); // 3

for (let user of set) {
  alert(user.name); // John (then Pete and Mary)

```

### Iteration over set

```js
let set = new Set(["oranges", "apples", "bananas"]);

for (let value of set) alert(value);

// the same with forEach:
set.forEach((value, valueAgain, set) => {
  alert(value);
});

```


## Operators

### Arithmetic Operators

    +	Addition

    -	Subtraction

    *	Multiplication

    **	Exponentiation (ES2016)

    /	Division

    %	Modulus (Division Remainder)
    
    ++	Increment
    
    --	Decrement

### Assignment Operators

    =	x = y	x = y
    
    +=	x += y	x = x + y

    -=	x -= y	x = x - y

    *=	x *= y	x = x * y

    /=	x /= y	x = x / y
    
    %=	x %= y	x = x % y
    
    **=	x **= y	x = x ** y


### Comparison Operators

    ==	equal to
    
    ===	equal value and equal type
    
    !=	not equal

    !==	not equal value or not equal type

    >	greater than
    
    <	less than
    
    >=	greater than or equal to

    <=	less than or equal to
    
    ?	ternary operator
    
    ??  Nullish coalescing operator  | null or undefined

    ?.  Optional Chaining Operator : The optional chaining operator (?.) permits reading the value of a property located deep within a chain of connected objects without having to expressly validate that each reference in the chain is valid. Checks of null or undefined.

###  Logical Operators

    &&	logical and  => Breaks on fist falsy expression(returning false), If falsy not found returns true.

    ||	logical or   => Breaks on first truty expression(returning true), If truthy not found return false

    !	logical not    => Reverse

    !! Double Not    => coerces the value on the rightside into boolean 

```js
console.log(!!null); //logs false
console.log(!!undefined); //logs false
console.log(!!''); //logs false
console.log(!!0); //logs false
console.log(!!NaN); //logs false
console.log(!!' '); //logs true
console.log(!!{}); //logs true
console.log(!![]); //logs true
console.log(!!1); //logs true
console.log(!![].length); //logs false
```

### Type Operators

    typeof	Returns the type of a variable

    instanceof	Returns true if an object is an instance of an object type

The instanceof operator tests to see if the prototype property of a constructor appears anywhere in the prototype chain of an object. The return value is a boolean value. 

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);
// expected output: true

console.log(auto instanceof Object);
// expected output: true
```

### Grouping Operator

The grouping operator `( )` controls the precedence of evaluation in expressions.

```js

console.log(1 + 2 * 3); // 1 + 6
// expected output: 7

console.log(1 + (2 * 3)); // 1 + 6
// expected output: 7

console.log((1 + 2) * 3); // 3 * 3
// expected output: 9

console.log(1 * 3 + 2 * 3); // 3 + 6
// expected output: 9

```

## Numbers


Extra large or extra small numbers can be written with scientific (exponent) notation:

```js
var x = 123e5;    // 12300000
var y = 123e-5;   // 0.00123
```


The JavaScript Number type is a double-precision 64-bit binary format IEEE 754 value, like double in Java or C. This means it can represent fractional values, but there are some limits to what it can store. A Number only keeps about 17 decimal places of precision; arithmetic is subject to rounding. The largest value a Number can hold is about 1.8×10308. Numbers beyond that are replaced with the special Number constant Infinity.

- **+ Operator**

  5 + 2 + "20" = "720"

  The JavaScript interpreter works from left to right.


- **NaN - Not a Number**
  NaN is a JavaScript reserved word indicating that a number is not a legal number.
  Trying to do arithmetic with a non-numeric string will result in NaN (Not a Number):


- **Infinity**

  Infinity (or -Infinity) is the value JavaScript will return if you calculate a number outside the largest possible number.


- **Hexadecimal**

  JavaScript interprets numeric constants as hexadecimal if they are preceded by 0x.

  `var x = 0xFF;   x will be 255`


> **Note** 
  Never write a number with a leading zero (like 07).
  Some JavaScript versions interpret numbers as octal if they are written with a leading zero.

### Number Methods

* toString()

```js
var x = 123;
x.toString();            // returns 123 from variable x
(123).toString();        // returns 123 from literal 123
(100 + 23).toString();   // returns 123 from expression 100 + 23
```


* toExponential() : returns a string, with a number rounded and written using exponential notation.

```js
var x = 9.656;
x.toExponential(2);     // returns 9.66e+0
x.toExponential(4);     // returns 9.6560e+0
x.toExponential(6);     // returns 9.656000e+0

```
The parameter is optional. If you don't specify it, JavaScript will not round the number.


* toFixed() :  returns a string, with the number written with a specified number of decimals(after decimal point)

* toPrecision() : returns a string, with a number written with a specified length (complete lenght of result)

```js

var x = 9.656;
x.toPrecision();        // returns 9.656
x.toPrecision(2);       // returns 9.7
x.toPrecision(4);       // returns 9.656
x.toPrecision(6);       // returns 9.65600

```

* valueOf()

```js
var x = 123;
x.valueOf();            // returns 123 from variable x
(123).valueOf();        // returns 123 from literal 123
(100 + 23).valueOf();   // returns 123 from expression 100 + 23

````
JavaScript calls the valueOf method to convert an object to a primitive value. You rarely need to invoke the valueOf method yourself; JavaScript automatically invokes it when encountering an object where a primitive value is expected.


Global JavaScript Methods

these are global methods and need not to call with .dot Notation

* Number() : Returns a number, converted from its argument.
* parseInt() : Parses its argument and returns a floating point number
* parseFloat() : Parses its argument and returns an integer



## Type Conversion

### Type Coercion

Type coercion is the automatic or implicit conversion of values from one data type to another (such as strings to numbers). Type conversion is similar to type coercion because they both convert values from one data type to another with one key difference — type coercion is implicit whereas type conversion can be either implicit or explicit


```js

const value1 = '5';
const value2 = 9;
let sum = value1 + value2;

console.log(sum); //59

```

In the above example, JavaScript has coerced the 9 from a number into a string and then concatenated the two values together, resulting in a string of 59. JavaScript had a choice between a string or a number and decided to use a string.

The compiler could have coerced the 5 into a number and returned a sum of 14, but it did not. To return this result, you'd have to explicitly convert the 5 to a number using the Number() method:


```js
sum = Number(value1) + value2;

```

### String Conversion
Global method `String()` can be used to convert any type to string

`toString()` method can be used to convert a number or Object any datatype except 'undefined' and 'null' to String `toString` method.

String conversion happens when we need the string form of a value.

We can also call the String(value) function to convert a value to a string:

String conversion is mostly obvious. A false becomes "false", null becomes "null", etc.


### Numeric Conversion

We can use the Number(value) function to explicitly convert a value to a number:

* Number(undefined)	=> NaN
* Number(null) =>	0
* true and false	=> 1 and 0
* string	Whitespaces from the start and end are removed. If the remaining string is empty, the result is 0. Otherwise, the number is “read” from the string. An error gives NaN.

```js

Number("            ") // 0

Number("2")     // 2

Number("z") //NaN

```

parseInt() - parses a string and returns a whole number. Spaces are allowed. Only the first number is returned:

```js
parseInt("10");         // returns 10
parseInt("10.33");      // returns 10
parseInt("10 20 30");   // returns 10
parseInt("10 years");   // returns 10
parseInt("years 10");   // returns NaN 

```
parseFloat() : parses a string and returns a number. Spaces are allowed. Only the first number is returned:

```js
parseFloat("10");        // returns 10
parseFloat("10.33");     // returns 10.33
parseFloat("10 20 30");  // returns 10
parseFloat("10 years");  // returns 10
parseFloat("years 10");  // returns NaN
```


Note - We can use `+` operator to convert string to number and its fastest. 

## Events
[ReadMore](events.md)