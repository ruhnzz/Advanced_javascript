# Advanced_javascript

# DOM MANIPULATION 

1. What is DOM?

DOM stands for Document Object Model.

Definition :
DOM is a programming interface for HTML documents that represents the page as a tree of objects so JavaScript can access and modify content, structure, and styles dynamically.

Browser converts HTML into a tree structure like:

Document
└── html
└── body
├── h1
├── h1
└── h1

Each element becomes a node (object).



2. document object

Definition:
The document object represents the entire HTML page loaded in the browser. It is the root object of the DOM and allows JavaScript to access and manipulate all elements in the webpage.

In simple words:

document = whole web page

It is the entry point to access and manipulate DOM.


3. Selecting Elements in DOM

These are called DOM Selector Methods.
```html
<h1 id="first">hello1</h1>
    <h1 class="second">hello2</h1>
    <h1>hello3</h1>
```

A) getElementById()

Definition:
Selects a single element using its id attribute.

```js
document.getElementById("first")
```

Important points:

* Returns a single element
* ID must be unique
* Fastest selector

Interview tip:
It returns an Element object, not an array.


B) getElementsByClassName()

Definition:
Selects all elements that match a class name.

```js
document.getElementsByClassName("second")
```

Important:

* Returns HTMLCollection
* It is array-like but NOT an actual array
* It is live (updates automatically if DOM changes)

Interview question:
Difference between HTMLCollection and Array?
HTMLCollection does not have array methods like map(), filter().


C) querySelector()

Definition:
Selects the first element that matches a CSS selector.

```js
document.querySelector("h1")
```

Important:

* Uses CSS selectors
* Returns only the first match
* Very flexible

Examples:

```js
document.querySelector("#first")
document.querySelector(".second")
document.querySelector("h1")
```

---

D) querySelectorAll()

Definition:
Selects all elements matching a CSS selector.

```js
document.querySelectorAll("h1")
```

Important:

* Returns NodeList
* Not exactly an array, but supports forEach
* Static (does NOT auto update like HTMLCollection)


4. console.log vs console.dir

A) console.log()

Prints element as HTML tag view.

```js
console.log(document.getElementById("first"))
```

Shows:

<h1 id="first">hello1</h1>


B) console.dir()

Prints element as a JavaScript object with properties.

```js
console.dir(document.getElementById("first"))
```

Best for debugging because:

* Shows properties
* Shows methods
* Shows attributes
* Shows event listeners

Interview tip:
Use console.dir() when you want to inspect element properties.


5. HTMLCollection vs NodeList

Feature comparison:

HTMLCollection

* Returned by getElementsByClassName
* Live collection
* No forEach in older browsers
* Array-like

NodeList

* Returned by querySelectorAll
* Static collection
* Supports forEach
* More modern


6. DOM Node Types (Important Concept)

Every element in DOM is a node.

Common node types:

* Document node
* Element node
* Text node
* Attribute node

Example:

```html
<h1>Hello</h1>
```

"h1" → element node
"Hello" → text node


7. Why DOM Manipulation is Important?

It allows:

* Changing content
* Changing styles
* Adding elements
* Removing elements
* Handling user events
* Building interactive UI


8. Interview Quick Revision Summary

What is DOM?
Tree representation of HTML.

How do you select elements?

* getElementById
* getElementsByClassName
* querySelector
* querySelectorAll

Difference between querySelector and getElementById?

* getElementById → only id
* querySelector → any CSS selector

Difference between HTMLCollection and NodeList?

* HTMLCollection → live
* NodeList → static

When to use console.dir?
To inspect element properties.






