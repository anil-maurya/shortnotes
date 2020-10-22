# OOP

Object Oriented Programming : Style of programming/Programing Paradigm

**Pradigms**

1. Procedural Programming
2. Object Oriented Programming
3. Functional Programming


Building Blocks of OOP

* classes  (Blueprint)

* objects (Instance)

* methods (Behaviours)

* attributes (data)

## Four Main Principals

1. Ecapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

## Encapsulation

is the one of core concepts of Object Oriented Programming. 

It is the mechanism of wrapping data and code that works on the data into a single unit known as class.

Example : We have a capsule named as class and it has two Parts - data and methods.

```
         ___
        |   |
        |___|  Data
  Class |   |
        |___|  Methods
```

**Why Encapsulation**

- Security - Controlled Access
- Hide Implementation and Expose Behaviour
- Loose Coupling - Modify the implementation anytime

```javascript
class Person{

    constructor (
        let name, age;
    )

    setName(name){
        this.name = name;
    }

    setAge(age){
        this.age = age;
    }

    getName(){
        return this.name;
    }

    getAge(){
        return this.age;
    }
}
```

## Abstraction

"Hide details and show only essentials"

Hiding details and exposing only information which is required to user. 

**ABSTRACTION** is the concept of object-oriented programming that "shows" only essential attributes and "hides" unnecessary information. The main purpose of abstraction is hiding the unnecessary details from the users. Abstraction is selecting data from a larger pool to show only relevant details of the object to the user. It helps in reducing programming complexity and efforts. It is one of the most important concepts of OOPs.

### Encapsulation vs Abstraction vs Data Hiding

In OOP terminology we can describe it as below.
Encapsulation : Wrapping up of data and methods into a single unit is Encapsulation. In a class we combine data(variables ) and method that are operated on that data. (e.g. Class)

Abstraction : It is an act of representing only the essential things without including background details. Like we are providing only method declaration in interface not method body (e.g. Interface)

Information Hiding : It is a concept that can be use for hiding data from external world. And that can be achived using Encapsulation and Abstraction.


```js

function Circle(radius) {
    this.radius = radius

    let defaultLocation = { x: 0, y: 0 }

    let computeOptimumLocation = function(factor){
        //
    }

    this.draw = function() {
        let x, y;

        computeOptimumLocation(0.1)
        console.log('draw')
    }
}

const circle = new Circle(10)
circle.draw()

```

To apply abstraction, we need to hide properties from object. To do this we don't attach them to 'this'

Here

`defaultLocation` and `computeOptimumLocation` are private memebers and not accessible from outside. 

How methods have access to these private properties ? 

This is because of closure. Actually scope dies but closure is preserved.



## Polymorphism

Polymorphism means existing in many forms. Variables, functions, and objects can exist in multiple forms in Java and Python. There are two types of polymorphism which are run time polymorphism and compile-time polymorphism. Run time can take a different form while the application is running and compile-time can take a different form during compilation.

An excellent example of Polymorphism in Object-oriented programing is a cursor behavior. A cursor may take different forms like an arrow, a line, cross, or other shapes depending on the behavior of the user or the program mode. With polymorphism, a method or subclass can define its behaviors and attributes while retaining some of the functionality of its parent class. This means you can have a class that displays date and time, and then you can create a method to inherit the class but should display a welcome message alongside the date and time. The goals of Polymorphism in Object-oriented programming is to enforce simplicity, making codes more extendable and easily maintaining applications.


## Classes in JavaScript

An Object consists of data and behavior(Properties and methods.)

A `class` in an program-code-template for creating objects.

Instantiation is the realization of an object from a class.


ES6, also known as ECMAScript2015, introduced classes. Prior to ES6, JavaScript had no classes. To mimic a class, we often use a constructor function. [Read More](functions.md) [and](object.md)

Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 classalike semantics.


Classes are in fact "special functions", and just as you can define function expressions and function declarations

Why Classes ?
classes provide a very well defined methodology for organizing your objects properties and behaviors. They lend themselves to Object Oriented Programming . 

### Creating a Class

Class can be created in two ways

1. Class Declaration
2. Cleass Expression


```js
//Class Declaration

class Reactangle {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
}

// Class expression

const Reactangle = class {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }


    // class method
    getArea() {
        return this.height * this.width
    }
}

// Instantiation

const p = new Reactangle()
console.log(p.getArea())

```

### Some Properties

#### Hoisting
Classes are not hoisted unlike function declaration. Throws `ReferenceError`

#### Strict Mode

The body of a class is executed in strict mode, i.e., code written here is subject to stricter syntax for increased performance, some otherwise silent errors will be thrown, and certain keywords are reserved for future versions of ECMAScript.

#### Methods are non-enumerable
Class methods are non-enumerable. In case constrcutor function, we have to use `Object.defineProperty()` method to make a property non-enumerable.

#### `new` keyword

calling the class constructor without the new operator will result in an error `Uncaught TypeError:`

#### First-Class citizen

JavaScript class is a first-class citizen. It means that you can pass a class into a function, return it from a function, and assign it to a variable.

#### Singleton

You can use the class expression to create singleton by calling the class constructor immediately. To do this, you use the new operator with a class expression and include the parentheses at the end of class declaration as in the following example.


```js

let app = new class {
    constructor(name) {
        this.name = name;
    }

    start() {
        console.log(`Starting the ${this.name}....`);
    }
}('Awesome App');


app.start(); // Starting the Awesome App....

```

#### Classes Are Functions

if we check typeof class, it return `function`

```js

const x = function() {};

const y = class {};

Object.getPrototypeOf(y) === Object.getPrototypeOf(x) // true

console.log(typeof x) // "function"
console.log(typeof y) // "function"

// But call can't be invoked without using new

y() // TypeError

```

### Properties / Fields

Class fields are variables that hold information. Fields can be attached to 2 entities:

1. Fields on the class instance
2. Fields on the class itself (aka static)


The fields also have 2 levels of accessibility:

1. Public: the field is accessible anywhere
2. Private: the field is accessible only within the body of the class

#### Public instance fields/Properties

```js

class User {
  constructor(name) {
    this.name = name;
  }
}

const user = new User('Jon Snow')
user.name // 'Jon snow'

```

Here `name` is public field because we can access it outside of the User class body.


When the fields are created implicitly inside the constructor, like in the previous scenario, it could be difficult to grasp the fields list. You have to decipher them from the constructor’s code.

A better approach is to explicitly declare the class fields. No matter what constructor does, the instance always has the same set of fields.


```js
class User {
  name = 'Unkown';
  
  constructor(name) {
    this.name = name;
  }
}

const user = new User('Jon Snow');
user.name; // => 'Jon Snow'

```


#### Private Instance fields

To implement encapsulation/hide internal data of an object, we use private fields
These are the fields that can be read and change only within the class they belong to. The outside world of the class cannot change private fields directly.

```js

class User {
  #name;

  constructor(name) {
    this.#name = name;
  }

  getName() {
    return this.#name;
  }
}

const user = new User('Jon Snow');
user.getName(); // => 'Jon Snow'

user.#name;     // SyntaxError is thrown

````

`#name` is a private field. You can access and modify #name within the body of the User. The method getName() (more about methods in next section) can access the private field #name.

But if you try to access the private field #name outside of User class body, a syntax error is thrown: SyntaxError: Private field '#name' must be declared in an enclosing class.


#### Staic Properties
Static properties are properties which can be called directly on Class and `static` keyword is used to define it

```js

class Animal {
    static plannet = "Earth";

}

console.log(Animal.plannet)
```

#### Public static fields

```js
class User {
  static TYPE_ADMIN = 'admin';
  static TYPE_REGULAR = 'regular';

  name;
  type;

  constructor(name, type) {
    this.name = name;
    this.type = type;
  }
}

const admin = new User('Site Admin', User.TYPE_ADMIN);
admin.type === User.TYPE_ADMIN; // => true

```


#### Private static fields
```js
class User {
  static #MAX_INSTANCES = 2;
  static #instances = 0;
  
  name;

  constructor(name) {
    User.#instances++;
    if (User.#instances > User.#MAX_INSTANCES) {
      throw new Error('Unable to create User instance');
    }
    this.name = name;
  }
}

new User('Jon Snow');
new User('Arya Stark');
new User('Sansa Stark'); // throws Error

````

#### Protected Properties

We can use protected properties like private one as above. 
Protected properties are usually prefixed with an underscore `_`.

That is not enforced on the language level, but there’s a well-known convention between programmers that such properties and methods should not be accessed from the outside.

```js
class CoffeeMachine {
  _waterAmount = 0;

  set waterAmount(value) {
    if (value < 0) throw new Error("Negative water");
    this._waterAmount = value;
  }

  get waterAmount() {
    return this._waterAmount;
  }

  constructor(power) {
    this._power = power;
  }

}

// create the coffee machine
let coffeeMachine = new CoffeeMachine(100);

// add water
coffeeMachine.waterAmount = -10; // wouldnt update _waterAmount


````

Other than this trick we can use setter which throw error on setting value of water.



### Methods

#### Constructor Method
The constructor method is a special method for creating and initializing an object created with a class.

Only single `constructor` can exist in a `class`. `SyntaxError` is thrown if class contains more than one `constructor` method.

`super` keyword to call the construcotr of the super class.



#### Prototype Method/ Instance Method

Regular methods, are declared without using `function` keyword.


#### Static Methods

The `static` keyword defines a static method for a class. Static methods are called without instantiating their class and cannot be called through a class instance. 

Static methods are often used to create utility functions for an application.

```js

class Reactangle {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }

    // method 
    calcArea() {
        return this.height * this.width;
    }

    // Static Method

    static location(a, b) {
        const dx = a.x - b.x;
        const dy = a.y - b.y;
        return Math.hypot(dx, dy);
    }
}


// Calling static method

const p1 = new Reactangle(5, 10);
const p2 = new Reactangle(10, 20);

p1.location; //undefined, Call call on object

console.log(Reactangle.location(p1, p2)) // Call on class directly

```

#### Getter and Setter

Using getter we can call method as properties (without using ()) and using setter methods we can call setter method as it was properties. 

To create a getter and setter, we can use `get` and `set` keywords followed by a space and an identifier.

```js

class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    get fullName() {
        return `${this.firstName} ${this.lastName}`
    }

    set fullName(str) {
        let names = str.split(' ');
        if(names.lenght ==2 ) {
            this.firstName = names[0];
            this.lastName = names[1];
        }else{
            throw 'Invalid name format';
        }
    }
}

let marry = new Person('Mary', 'Doe');
console.log(marry.fullName) // Marry Doe

// set new name

marry.fullName = 'Marry William';
console.log(marry.fullName) // Marry william

```

#### Computed member names

We can use variable to create properties and methods.

```js
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    get [name](){
        return `${this.firstName} ${this.lastName}` 
    }
}


const p1 = new Person('Anil', 'Maurya')
console.log(p1.fullName)

```


#### Binding `this`

When a static or prototype method is called without a value for `this`, such as by assigning a variable to the method and then calling it, the `this` value will be undefined inside the method. This behavior will be the same even if the "use strict" directive isn't present, because code within the class body's syntactic boundary is always executed in strict mode.

```js

class Animal { 
    speak() {
        return this;
    }

    static eat() {
        return this;
    }
}

let obj = new Animal();

obj.speak(); // the Animal object

let speak = obj.speak;
speak(); // undefined

Animal.eat() // class Animal
let eat = Animal.eat;
eat(); // undefined


//Binding this, We can rewrite

class Animal {
    speak() {
        return  this;
    }

    static eat() {
        return this;
    }
}


```


```js

const obj = {
  foo() {
    return 'bar';
  }
};

console.log(obj.foo());
// expected output: "bar"

```



### Inheritance Using class AKA Classical Inheritance

We use `extends` keyword to extend a class to another class. and `super` keyword is used to call parent class construcotr. 

```js

class Animal {
    constructor(legs) {
        this.legs = legs;
    }

    walk() {
        console.log(`walking on ${this.legs} legs`)
    }
}


//Inheriting Animal class

class Bird extends Animal {
    constructor(legs) {
        super(legs);
    }

    fly() {
        console.log('Flying');
    }
}

let bird = new Bird(2);

bird.walk();
bird.fly();

```
#### Overriding a method

We can re-implement a method in child class which is already implemented in parent class.

```js

class Animal {

  constructor(name) {
    this.speed = 0;
    this.name = name;
  }

  run(speed) {
    this.speed = speed;
    alert(`${this.name} runs with speed ${this.speed}.`);
  }

  stop() {
    this.speed = 0;
    alert(`${this.name} stands still.`);
  }

}

class Rabbit extends Animal {
  hide() {
    alert(`${this.name} hides!`);
  }

  stop() {
    super.stop(); // call parent stop
    this.hide(); // and then hide
  }
}

let rabbit = new Rabbit("White Rabbit");

rabbit.run(5); // White Rabbit runs with speed 5.
rabbit.stop(); // White Rabbit stands still. White rabbit hides!

``` 

#### Overriding constructor

According to the specification, if a class extends another class and has no constructor, then the following “empty” constructor is generated:

```js

class Rabbit extends Animal {
  // generated for extending classes without own constructors
  constructor(...args) {
    super(...args);
  }
}

```

Now overriding constructor 

```js
class Rabbit extends Animal {

  constructor(name, earLength) {
    super(name)
    this.speed = 0;
    this.name = name;
    this.earLength = earLength;
  }

  // ...
}

// Doesn't work!
let rabbit = new Rabbit("White Rabbit", 10); // Error: this is not defined.
```

Note - Constructors in inheriting classes must call super(...), and (!) do it before using this.


#### Overriding Class Fileds

#### Inheritance of static properties and methods

Static properties and methods are inherited.


```js

class Animal {
    static plannet = "Earth";

    constructor(name, speed) {
        this.name = name;
        this.speed = speed;
    }

    run(speed = 0) {
        this.speed += speed;
        console.log(`${this.name } runs with speed ${this.speed}.`);
    }

    static compare(animalA, animalB) {
        return animalA.speed - animalB.speed
    }
}

// Inherit from Animal

class Rabbit extends Animal {
    hide() {
        console.log(`${this.name} hides !` );
    }
}

let rabbits = [
    new Rabbit("White Rabbit", 10),
    new Rabbit("Black Rabbit", 5) 
];

rabbits[0].run() // White Rabbit runs with speed 10.
console.log(Rabbit.plannet) //Earth

```

### Accessing Parent instance.

We can access the parent method inside of a child method, we can use `super`

```js

class User {
  name;

  constructor(name) {
    this.name = name;
  }

  getName() {
    return this.name;
  }
}

class ContentWriter extends User {
  posts = [];

  constructor(name, posts) {
    super(name);
    this.posts = posts;
  }

  getName() {
    const name = super.getName();
    if (name === '') {
      return 'Unknwon';
    }
    return name;
  }
}

const writer = new ContentWriter('', ['Why I like JS']);
writer.getName(); // => 'Unknwon'

````

### Object type checking: instanceof
object instanceof Class is the operator that determines if object is an instance of Class.

```js
class User {
  name;

  constructor(name) {
    this.name = name;
  }

  getName() {
    return this.name;
  }
}

const user = new User('Jon Snow');
const obj = {};

user instanceof User; // => true
obj instanceof User; // => false

```

instanceof is polymorphic: the operator detects a child as an instance of the parent class.

```js

class User {
  name;

  constructor(name) {
    this.name = name;
  }

  getName() {
    return this.name;
  }
}

class ContentWriter extends User {
  posts = [];

  constructor(name, posts) {
    super(name);
    this.posts = posts;
  }
}

const writer = new ContentWriter('John Smith', ['Why I like JS']);

writer instanceof ContentWriter; // => true
writer instanceof User;          // => true

```


## Inheritance

There are two type of inheritance

1. Classical Inheritance
2. Prototypical Inheritance


Javascript support prototypical inheritance. 

Read more about prototypes in object.md