# Events

Events are actions or occurrences that happen in the system. In the world of programming, HTML events are something that happens to the HTML elements. But when JavaScript is used in HTML pages, it can react to these events.


## Events Types

* mouse events (MouseEvent): 
	- mousedown
	- mouseup
	- click, 
	- dblclick
	- mousemove
	- mouseover
	- mousewheel
	- mouseout
	- contextmenu

* touch events (TouchEvent):
	- touchstart
	- touchmove
	- touchend
	- touchcancel

* keyboard events (KeyboardEvent)
	-keydown
	- keypress
	- keyup

* form events: 
	- focus
	- blur
	- change
	- submit

* window events: 
	- scroll 
	- resize 
	- hashchange
	- load 
	- unload


## Event Handeling

To perform some action on event, we attache event handler/event listener to element.

### Event Listner/Event Handler

An event listener is a function with an explicit name if it is resuable or an anonymous function in case it is used one time.

An event listner is also known as an event handler

Three ways to assign event handlers

1. HTML Event handle attributes
2. DOM level 0 event handler
3. DOM level 2 event handler


## HTML even handler attributes

Event handlers typically have names that begin with on, for example, the event handler for the click event is onclick.

```html

<input type="button" value="Save" onclick="alert('Clicked!')">

<!-- OR ---- -->

<script>
    function showAlert() {
        alert('Clicked!');
    }
</script>

<input type="button" value="Save" onclick="showAlert()">

```

Notes 

- The code in the event handler can access the event object without explicitly defining it
- `this` value inside the event handler is equivalent to the event’s target element
- the event handler can access the element’s properties


```html

<input type="button" value="Save" onclick="alert(event.type)">
<input type="button" value="Save" onclick="alert(this.value)">
<input type="button" value="Save" onclick="alert(value)">

```

Assigning event handlers using HTML event handler attributes are considered as bad practices and should be avoided as much as possible

1. the event handler code is mixed with the HTML code, which will make the code more difficult to maintain and extend.

2. it is a timing issue. If the element is loaded fully before the JavaScript code, users can start interacting with the element on the webpage which will cause an error.


## DOM level 0 event handler

We can assign event handller function to element's event property 

```js

let btn = document.querySelector('#btn');

btn.onclick = function() {
    alert('Clicked!');
    alert(this.id);
};

```


## DOM level 2

DOM Level 2 Event Handlers provide two main methods for dealing with the registering/deregistering event listeners:

1. `addEventListener()` - Register an event handler
2. `removeEventListner()` - Remove an event handler


Add EventListener accept three arguments -

1. event
2. handler function
3. true/false -  (default - false)
	- true : call the event handler during the capture phase 
	- false : call the event handler during the bubble phase

It is possible to add multiple event handlers to handle a single event, like this:


```js

let btn = document.querySelector('#btn');

btn.addEventListener('click', function(event) {
    alert(event.type); // click
});

btn.addEventListener('click',function(event) {
    alert('Clicked!');
});

```

removeEventListener() method

Why ?

If we don't remove eventListner but element is get removed it will coninue occupying memory. To free the unused memory it is important to remove event listener.


```js

let btn = document.querySelector('#btn');

// add the event listener
let showAlert = function() {
    alert('Clicked!');
};
btn.addEventListener('click', showAlert);

// remove the event listener
btn.removeEventListener('click', showAlert);

// anonymous event listener

let btn = document.querySelector('#btn');
btn.addEventListener('click',function() {
   alert('Clicked!');
});

// won't work
btn.removeEventListener('click', function() {
   alert('Clicked!');
});


```

## Object Handlers

We can assign not just a function, but an object as an event handler using addEventListener. When an event occurs, its handleEvent method is called.

```html
<button id="elem">Click me</button>

<script>
  let obj = {
    handleEvent(event) {
      alert(event.type + " at " + event.currentTarget);
    }
  };

  elem.addEventListener('click', obj);
</script>


<!-- Example 2 -->

<button id="elem">Click me</button>

<script>
  class Menu {
    handleEvent(event) {
      switch(event.type) {
        case 'mousedown':
          elem.innerHTML = "Mouse button pressed";
          break;
        case 'mouseup':
          elem.innerHTML += "...and released.";
          break;
      }
    }
  }

  let menu = new Menu();
  elem.addEventListener('mousedown', menu);
  elem.addEventListener('mouseup', menu);
</script>

````


## Event Object

When a event heppens, browser creates an event object and passes to event handler as an argument.

```html

<input type="button" value="Click me" id="elem">

<script>
  elem.onclick = function(event) {
    // show event type, element and coordinates of the click
    alert(event.type + " at " + event.currentTarget);
    alert("Coordinates: " + event.clientX + ":" + event.clientY);
  };
</script>

```

Some properties of event object

1. type 					- type of event - 'click'
2. currentTarget 			- Returns the element whose event listeners triggered the event. Returns current target.
3. target          		    - Returns the element that triggered the event. It doesn't changes in casee of bubbled/captured 
3. relatedTarget			- Where are you comming from or where were you.
4. stopPropagation()		- Prevents further propagation of an event during event flow
5. stopImmediatePropagation()	- Prevents other listeners of the same event from being called
6. preventDefault()				- Cancels the event if it is cancelable, meaning that the default action that belongs to the event will not occur


## Event Propagation

Event propagation is a mechanism that defines how events propagate or travel through the DOM tree to arrive at its target and what happens to it afterward.


Deals with the three event phases

1. capturing : In the capturing phase, events propagate from the Window down through the DOM tree to the target node
2. taget phase : 
2. bubbling : In the bubbling phase, the exact opposite occurs. In this phase event propagates or bubbles back up the DOM tree, from the target element up to the Window


### Capturing events 

handeling bubbling phase

```js
let btn = document.querySelector('#btn');

btn.addEventListener('click', function() {
   alert('Clicked!');
}, false);
```

handeling capture fase

```js
let btn = document.querySelector('#btn');

btn.addEventListener('click', function() {
   alert('Clicked!');
}, true);

```


### Accessing event phase
We can use `eventPhase` property of `event` obejct

* 1 => Capturing
* 2 => Taget
* 3 => Bubbling


### Stoping event propagation

we can use event.stopEventPropagation() method to stop event propagation.

preventDefault vs. stopPropagation

preventDefault stop default behaviour like <a> tags default behaviour is to open link. 


## Event Delegation


Event delegation refers to the technique of reducing the number of event listeners attached to the document by attaching just one listener to a containing element and testing in the handler where that event has bubbled up from.

suppose we have multiple elements which get added and removed within `div`. So in case insttead of adding event listener on every elements we can add event listner to `div` element and by using `event.taget` we can find which element was clicked.  



## Custom Event

Creating custom event

1. Create event object
	- `new Event('explode')`
	- `new CustomeEvent('explode', {detail: {speed:20, volume: 40}})`

2. Add event listner for 'explode'
3. dispatch evetn

```js

let born = new Event('born')

let died = new CustomeEvent('died', {detail: Date.now()});

// Dispatch event

let p = document.createElement('p');

p.addEventListener('born', function(){
	console.log('Event Born')
})

p.dispatchEvent(born)

```


## Keyboard Events

```js

let txt = document.getElementById('txt');
txt.addEventListener('keydown', anyKey);


function anyKey(ev){
	let target = ev.currentTarget
	let tag = target.tagName
	// different browser use deff property
	let charCode = ev.char || ev.charCode || ev.which;

	// Get actuall character
	let s = String.fromCharCode(charCode)
	console.log(s)
}

```



## Context Menu

we can add event listner to `contextmenu` and prevent default to stop default menu.



## window.onerror

```js

window.addEventListener('error', function(ev){
	console.log('Error occured');
	ev.preventDefault();
})

```