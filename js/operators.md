# Operators in Javascrtips



## Contents
- delete
- instanceof 
- Operator precedence & associativity



## delete

`delete` operator is used to delete object properties.

It behave differently with differnet type of variables.

### Object

1. delete object properties. It completely remove properties not only value and return true/false

```js
let x = {
	name = 'anil'
	age = 37
}

delete x.name

console.log(x) // {age: 37}

console.log(delete x.lastName) // true

```

2. if property doesn't exists, returns true
3. Can't delete complete object
4. Delete only instance memeber. Can not delete prototype member untill unless explicity passed with __proto__ property.

`delete emp1.__proto__.company //true`


### Varirables

- delete can't delete variable declared with `var/let/const`
- variables declared without using `var/let/const` keyword can be deleted.

```js

y = 20
deleted y // true
console.log(y) // error x is not defined
```


### Array

- Can't delete complete array
- Array element can be deleted but it leves that undex 'empty' => `undefined`

```js

let arr = [1, 2, 3, 4]

delete arr[1] // true

console.log(arr)  //[1, empty, 3, 4]

arr[1] //undefined
```


### Built-in Objects

- properties of built-in objects can be deleted but not recomended.



### Object with custome property descriptor

- can not delete if 'configurable' is set to 'false'



### functions local variable passed in param

```js

var output = (function(x){
    delete x;
    return x;
  })(0);
  
  console.log(output); //0

```

Here variable is in function not deleted.



## Operators

* Nullish Coalescing Operators - ??
* Ternary Operator

### Nullish coalescing operator ??
  
```js
  let a
  x = a ?? 0
  // x = 0
  
  a = 10
  x =  a ?? 0 // Assign value of a to x only if a is not undefined or null else asign 0
  //x = 10

```


* Ternary Operator
  
  

## Does JS have types?

Some may argue that JS is untyped or that it shouldn’t call its type system types. It doesn’t require you to declare a type when making a variable like in some other strongly typed languages i.e `int x = 10` I ( and the [JS specs](http://www.ecma-international.org/ecma-262/#sec-ecmascript-data-types-and-values) ) would argue that JS does have types.

JS is both **dynamically typed** and **weakly typed**.

### Statically Typed

JS is not statically typed unless you’re using a language, tool such as [Typescript](https://www.typescriptlang.org/) or [Flow](https://flow.org/) that compiles to JS code. But we’ll briefly cover it for comparison reasons.

Statically typed means the **type is enforced** and won’t change so easily. All variables must be declared with a type.

int x = 5

string y = 'abc'

### Dynamically Typed

Dynamically typed languages **infer variable types at runtime**. This means once your code is run the compiler/interpreter will see your variable and its value then decide what type it is. The type is still enforced here, it just decides what the type is.

var a = 1 // int  
b = 'test' // string  
// etc

### Weakly Typed

Weakly typed languages **allow types to be inferred as another type**. For example, `1 + '2' // '12'` In JS it sees you’re trying to add a number with a string — an invalid operation — so it coerces your number into a string and results in the string ‘12’.

**Note :

1. `undefined` variable is declared but not assigned.
2. `undefined` can be assigned but not recommended.

### `typeof` operator

Can be used in two form of sytax

1. As an operator : `typeof x`
2. As a function: `typeof(x)`

```javascript
typeof undefined // "undefined"

typeof 0 // "number"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"  (1)

typeof null // "object"  (2)  //Why ???

typeof alert // "function"  (3)

typeof Infinity // number
```

1. `Match` is a built-in object that provides mathematical operations.
2. `typeof null` is `object`. That's wrong. it is an officially recognized error in `typeof`, kept for compatibility. Of course, `null` is not an object. It is a special value with a separate type of its own.
3. The result of `typeof alert` is a `function`, because `alert` is a function of the language.



JIT(just in compilation) Compilation