# Ajax (Asynchronous JavaScript and XML)

Read data from server asynchronously 



## Creating Request

```js

function loadDoc() {
  var xhttp = new XMLHttpRequest();
  
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}

```


### Request to server

- `.open('method', 'url', async)`

```js
xhttp.open("GET", "demo_get.asp", true);
xhttp.send();

// ..................

xhttp.open("POST", "ajax_test.asp", true);
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("fname=Henry&lname=Ford");

````


### AJAX response

- `onreadystatechange`

Defines a function to be called when the readyState property changes

- `readyState`	

Holds the status of the XMLHttpRequest.
	0: request not initialized
	1: server connection established
	2: request received
	3: processing request
	4: request finished and response is ready

- `status`
	- 200: "OK"
	- 403: "Forbidden"
	- 404: "Page not found"
	
- `statusText`

Returns the status-text (e.g. "OK" or "Not Found")

```js

loadDoc("url-1", myFunction1);

function loadDoc(url, cFunction) {
  var xhttp;
  xhttp = new XMLHttpRequest();
  
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      cFunction(this);
    }
  };
  xhttp.open("GET", url, true);
  xhttp.send();
}

function myFunction1(xhttp) {
  // action goes here
}
function myFunction2(xhttp) {
  // action goes here
}
```

Server Response Properties

- `responseText` 	get the response data as a string
- `responseXML`		get the response data as XML data


Server Response Methods


- `getResponseHeader()`		Returns specific header information from the server resource
- `getAllResponseHeaders()`		Returns all the header information from the server resource

```js

var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    document.getElementById("demo").innerHTML =
    this.getAllResponseHeaders();
  }
};


var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    document.getElementById("demo").innerHTML =
    this.getResponseHeader("Last-Modified");
  }
};
xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();


```


### handeling XML

```js

function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
    	myFunction(this);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}

function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";

  var x = xmlDoc.getElementsByTagName("CD");
  
  for (i = 0; i <x.length; i++) {
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  
  document.getElementById("demo").innerHTML = table;
}

// xml.responseXML return xml DOM Object

```


#### The XML DOM Object

All XML elements can be accessed through the XML DOM.

```js
txt = xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;


// or

txt = xmlDoc.querySelector("CD").textContent
```


### Handeling JSON

JSON: JavaScript Object Notation.

JSON is a syntax for storing and exchanging data.

JSON is text, written with JavaScript object notation.

Converting string to JavaScript Object

```js

let txt = '{"name": "Anil", "age": 37}'

// Convert to JavaScript Object

const obj = JSON.parse(txt)

// convert JavaScript object to string

let str = JSON.stringify(obj);
```


## fetch 