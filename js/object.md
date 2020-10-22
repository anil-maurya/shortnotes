# Javascript - Object

Object in javascript is collection of key value pair.

Object is a non-primitive data type in JavaScript. It is like any other variable, the only difference is that an object holds multiple values in terms of properties and methods. Properties can hold values of primitive data types and methods are functions.



## Creating Object

1. Using Object Literal
2. Using Factory functions
3. Constrcutors functions


### Using Object Literal

```js
const circle = {
	radius: 1,
	location: {
		x : 1,
		y : 2
	},
	draw : function(){
		console.log('draw')
	}
}
````

Here : radius & location are properties and draw is methods


### Creating Object using Factory functions

Problem with object literal : If we need to create multiple objects with same methods and properties in Object literal method we need to create same code again and again and if later there is any change we need to update all object. To solve this problem we use factory functions 


```js

function createCircle(radius){
	let circle = {};
	circle.radius = radius;
	circle.draw = function() {
				console.log('draw')
			}
	return circle
}

const circle = createCircle(5)
const circle2 = createCircle(10)

```

### Creating Object using Constructor Function

- Constractor functions name start with capital letter.
- Always use `new` keyword
- return statement is not used.

```js

function Circle(radius) {
	// const this = {}       Performed automatically by javascript
	this.radius = 'radius';
	this.draw  = function(){
		console.log('draw')
	}
	// return this   Performed automatically by javascript
}

const another = new Circle(2)

````

When a function is called with the new keyword, couple of things happen behind the scenes:

- A new empty object is created
- The context object this is bound to the new empty object
- The new object is linked to the function’s prototype property
- this is automatically returned unless another value is returned explicitly from the function


### Constrcutor property

Every object in javascript has a constuctor property that references to the function which was used to create that object.

- When object is created using object literal syntax, build in `Object` constcutor is used.

```js
const x = {}

// Internally it works like ...
const x = new Object()

```

Some built-in constructors
- Object  
- String  
- Number  
- Boolean
- Error

Instead of using these built in constructor functions we use literals to create object like

- instead of `new Object()`  use object literal `x = {}`

- instead of `new String()`  use String literal `'', ""`

- instead of `new Boolean()`  use Boolean literal `true/false`


## Functions are object

see more details in `functions.md`


## Adding Properties to Object

Objects in Javascript are Dynamic, Means we can add properties to object on the fly.

`obj.property = value`


## Accessing Properties of Object

- Dot Notation
- Bracket Notation
  - When we want to use dynamic property Name
  - When property name is not valid identifier. Means it has '-' or space in between of property.


## Deleting Property

 `delete object.property`


## Enumerating Object Properties

Iterating over properties

```js

for (let key in circle) {
    console.log(key)
}

// Iterating only properties not methods

for (let key in circle) {
	if (typeof circle[key] !== 'function') {
			console.log(circle[key])		
	}
}

// All keys

Object.keys(circle)

Object.values(circle)

// Check existance of property or method

if ('radius' in circle) {
	console.log('circle has a radius')
}

```

## Prototype




## Getters and Setters

Some time we want to give access of private properties to users but don't want to change it.
Setters are functions which is use to set properties.


```js
function Circle(radius){

	let defaultLocation = {x: 0, y: 0}

	Object.defineProperty(this, 'defaultLocation', {
		get : function() {
			return defaultLocation;
		}
		set : function(value) {
			if(!value.x || !value.y)
				throw new Error('Invalid Location.');

			defaultLocation = value 
		}
	})
}

```


## Prototype or Prototype Object

Prototype is just a regular object that is associated with every functions and objects by default except the root prototype (Prototype iteself).

All JavaScript objects inherit properties and methods from a prototype.

“Every Object is linked to a prototype object from which it can inherit properties. All objects created from object literals are linked to Object.prototype, 
an object that comes standard with JavaScript.


Get prototype of any object x

`Object.getPrototypeOf(x) or x.__proto__`


## Prototypal Inheritance

When we access property or method of any object Javascript engine looks for
the property in the object itself but if it doesn't find it looks into the
prototype of the object and until root object.


* object (created with object literals) 
		=> Object Prototype
* Object (created with constructor) 
	inherits => Constructor prototype 
		inherits=> Object Protottype

* function => Function Prototype => Object Prototype

* array => Array Prototype => Object Prototype 


* If object is created using object literal then its prototype is Object Prototype.
* If object is created using constructor its prototype is constructor. For example circle is created using Circle constructor

circle => Circle Prototype => Object Prototype


## Property Descriptor

Every property of object in javascript has some properties which describe its behaviour. These properties of object properties are known as Property Descriptor.

- `enumerable` - enable/disable enumeration. if false Object.keys(object) will not return this property.
- `configurable` - Make delete proof
- `writable` - Enable/disable wirte, change value
- `value` - value of property

Reading Property Descriptor of object-

```js
const object1 = {
  property1: 42
};

const descriptor = Object.getOwnPropertyDescriptor(object1, 'property1');

console.log(descriptor)
// configurable: true
// enumerable: true
// value: 42
// writable: true

```

Changing Property Descriptor

```js

const object1 = {};

Object.defineProperty(object1, 'property1', {
  value: 42,
  writable: false
});

object1.property1 = 77;
// throws an error in strict mode

console.log(object1.property1);
// expected output: 42

```


## Instance Members vs Prototype members.

Property which is direct member of object is instance member and property of prototype is prootype memebr

```js

function Circle(radius){
	this.radius = radius  // Instance member
}

Circle.prototype.draw = function(){
	console.log('draw')
}

const c = new Circle()

//Here radius is instance member and 'draw' is prototype member

```

Object.keys(c) - only returns instance members not circle members.

For key in returns instance and prototype members both.

for (let key in c ){
	console.log(key)
}

Note - Avoid Extending built-in prototype objects. Don't modify objects you dont' own.



## Creating Prototypal Inheritance

The Object.create() method creates a new object, using an existing object as the prototype


```js

function Shape(){

}

Shape.prototype.duplicate = function(){
	console.log('duplicate')
}

function Circle(radius){
	this.radius = radius
}


Circle.prototype = Object.create(Shape.prototype)


Circle.prototype.draw = function() {
	console.log('draw')
}

const s = new Shape()
const c = new Circle()

```


## Any object prototype depends upon its way of creation

1. Object literals – {};

If we creates an object by using object literals than Object.prototype link will be automatically created. Here we don’t have ability to select our {prototype} link, it will always points to Object.prototype.


2. Object.create() method

If we creates an object by using Object.create() method than we have ability to choose prototype property of our object. By passing object as parameter of create method we can select prototype of our created object .We can also create an object without {prototype} property. For Example : 
	
	* var obj = Object.create(Object.prototype);  Here obj {prototype} is Object.prototype. 

	* var obj = Object.create(null); Here obj {prototype} is null.

3. Constructor way  new Const() – 

If we are creating our object by using any constructor function than Constructor prototype will become our object {prototype}. In JavaScript functions are special kind of objects, apart from {prototype} hidden link they also have one more prototype property which is accessible for user. A simple function structure will look like the following Images: 

## Values vs Reference type

Primitives are copied by value and objects are copied by reference


## Object Methods

1. Object.create()
2. Object.assign()
3. Object.getOwnPropertyDescriptor()
4. Object.defineProperty()
5. Object.defineProperties()



## Copying object in javaScript

We have three options to copy an object

1. use spread operator {...}
2. using Object.assign() method
3. use JSON.stringify() and JSON.parse() method

```js

const person = {
    firstName: 'John',
    lastName: 'Doe'
};


// using spread ...
let p1 = {
    ...person
};

// using  Object.assign() method
let p2 = Object.assign({}, person);

// using JSON
let p3 = JSON.parse(JSON.stringify(person));

```


Both spread (...) and Object.assign() perform a shallow copy while the JSON methods carry a deep copy.


Unlike primites when we use = 'assignment operator' to copy the value, it will not copy the value but both will reference to same object in memory.

### shallow copy vs deep copy

In shallow copy first level properties are copied by value but deeper level properties and methods are copied by reference.


```js

const person = {
	'name' : 'anil',
	'age' : 37,
	'family': {
		member1 : "Suneel",
		member2 : "Shyamu",
		member3 : "Ramu"
	}
}


const copyCat = {...person}

console.log(person === copyCat) // false

console.log(copyCat) // Same as person

person.name = 'Anil Maurya' //Updating paerson

console.log(copyCat) // Can object not updated

// Updating nested object
person.family.member1 = "Suneel Maurya" // updating person object

console.log(copyCat) // cat object updated.

```

Same thing happen with `let copyCat = Object.assign({}, obj1)`

Deep copy
JSON methods to carry a deep copy the person object

```js
let person = {
    firstName: 'John',
    lastName: 'Doe',
    address: {
        street: 'North 1st street',
        city: 'San Jose',
        state: 'CA',
        country: 'USA'
    }
};


let copiedPerson = JSON.parse(JSON.stringify(person));

copiedPerson.firstName = 'Jane'; // disconnected

copiedPerson.address.street = 'Amphitheatre Parkway';
copiedPerson.address.city = 'Mountain View';

console.log(person); // No change in person object.
````