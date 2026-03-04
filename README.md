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

Shows: <h1 id="first">hello1</h1>


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

# TEXT MANIPULATION IN DOM 

What is Text Manipulation?

Definition:
Text manipulation means changing the content of an HTML element dynamically using JavaScript.

Example:

```html
<h1>Hello</h1>
```

Using JS, we change it to:

Hello World
```js
let val = document.querySelector("h1")
    console.dir(val)
```

within dropdown we found 
* innerHTML: "Hello"
* innerText: "Hello"
*  textContent:"Hello"
  
 form above drop down we can confirm that val is object because it has properties
1. innerHTML

Definition:
innerHTML gets or sets the HTML content inside an element.

Example:

```js
val.innerHTML = "<i style='color:red'>Hello World</i>";
```

Important points:

* Parses HTML
* Can insert tags
* Can insert styled content
* Risk of XSS if using user input

2. innerText

Definition:
innerText gets or sets the visible text content of an element.

Example:

```js
val.innerText = "Hello World";
```

Important:

* Ignores hidden elements
* Respects CSS styles
* Does not parse HTML

3. textContent

Definition:
textContent gets or sets all text inside an element, including hidden text.

Example:

```js
val.textContent = "Hello World";
```

Important:

* Faster than innerText
* Does NOT consider CSS
* Does NOT parse HTML


 Difference Between innerHTML, innerText, textContent

Feature Comparison:

innerHTML

* Parses HTML
* Can add tags
* Slower
* Security risk with user input

innerText

* Only visible text
* Respects CSS
* Slower than textContent

textContent

* All text
* Ignores CSS
* Fastest
* Safest for plain text

Interview Answer:

Use innerHTML when you need to insert HTML.
Use textContent when inserting plain text (recommended).


 Important Concept

DOM elements are objects.

You confirmed this by:

```js
console.dir(val);
```

Because you saw properties like:

* innerHTML
* innerText
* textContent

So when we manipulate the DOM, we are modifying object properties.

10. Interview One-Line Summary

Text manipulation in DOM is done by modifying properties like innerHTML, innerText, and textContent of DOM element objects.

Very good 👏
Now you're learning real DOM control. This is an important interview topic.

Let’s convert your code into clean, interview-friendly notes.


# ATTRIBUTE MANIPULATION IN DOM

1. What is an Attribute?

Definition:
An attribute provides additional information about an HTML element.

Example:

```html
<a href="https://google.com">Click</a>
```

Here:

* href is an attribute
* "[https://google.com](https://google.com)" is its value

Attributes are written inside the opening tag.


2. Why Attribute Manipulation?

We manipulate attributes when we want to:

* Change links dynamically
* Add/remove classes
* Enable/disable inputs
* Add custom data attributes
* Modify images (src)
* Change form behavior


3. Selecting the Element

```js
let a = document.querySelector("a");
```

This selects the first anchor tag and returns a DOM element object.

You verified this using:

```js
console.dir(a);
```

Important concept:
DOM elements are JavaScript objects with properties and methods.


4. setAttribute()

Definition:
setAttribute() sets or updates an attribute on an element.

Syntax:

```js
element.setAttribute("attributeName", "value");
```

Example from your code:

```js
a.setAttribute("href","https://github.com");
```

What happens?

* If attribute exists → value is updated
* If attribute does not exist → attribute is created

Interview Point:
setAttribute always works at the HTML attribute level.

5. getAttribute()

Definition:
getAttribute() returns the value of a specified attribute.

Syntax:

```js
element.getAttribute("attributeName");
```

Example:

```js
let attributeValue = a.getAttribute("href");
console.log(attributeValue);
```

Output:
[https://github.com](https://github.com)

If attribute does not exist → returns null

6. removeAttribute()

Definition:
removeAttribute() removes an attribute from an element.

Syntax:

```js
element.removeAttribute("attributeName");
```
Example:

```js
a.removeAttribute("href");
let att = a.getAttribute("href");
console.log(att); // null
```

After removal:

* The anchor tag is no longer clickable
* getAttribute("href") returns null


7. Direct Property vs setAttribute (Important Interview Question)

```

Direct Property:

```js
a.href = "https://google.com";
```

* Works with DOM properties
* Often gives fully resolved URL
* More common in modern JS

setAttribute:

```js
a.setAttribute("href","https://github.com");
```

* Works directly on HTML attribute
* More generic
* Can set custom attributes

Interview Answer:

Use direct property for standard attributes like:

* href
* src
* value
* checked

Use setAttribute when:

* Setting custom attributes
* Dynamically adding attributes
* Working generically


8. Commonly Manipulated Attributes

Links:

```js
a.href
```

Images:

```js
img.src
```

Inputs:

```js
input.value
input.disabled
```

Classes:

```js
element.className
element.classList
```

9. Important Interview Concept

Attributes vs Properties

Attribute:

* Defined in HTML
* Accessed via getAttribute()

Property:

* Exists on DOM object
* Accessed via dot notation

Example:

```js
a.getAttribute("href");  // attribute
a.href;                  // property
```

Sometimes property value may differ slightly (like full URL formatting).


11. Interview One-Line Summary

Attribute manipulation in DOM is done using setAttribute(), getAttribute(), and removeAttribute() to dynamically modify HTML element attributes at runtime.


















