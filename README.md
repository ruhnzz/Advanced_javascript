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


# DOM ELEMENT CREATION AND MANIPULATION – NOTES


1. createElement()

Definition
createElement() is used to create a new HTML element dynamically using JavaScript.

Syntax

```javascript
let element = document.createElement("tagName");
```

Example

```javascript
let h1 = document.createElement("h1");
```

Explanation
• A new `<h1>` element is created in memory
• It is **not visible on the webpage yet**
• It must be inserted into the DOM to appear

Interview Point
createElement() only creates the element but does not attach it to the document.

Example with text

```javascript
h1.textContent = "Hello DOM";
```

This adds text to the element.


2. append()

Definition
append() adds a new element at the **end of the selected parent element**.

Syntax

```javascript
parent.append(child);
```

Example

```javascript
document.body.append(h1);
```

Result
The `<h1>` element is added **at the bottom of the body**.

Features
• Can add multiple elements
• Can add text also
• Modern method


3. appendChild()

Definition
appendChild() adds a new child node to the **end of a parent element**.

Syntax

```javascript
parent.appendChild(child);
```

Example

```javascript
document.querySelector("body").appendChild(h1);
```

Result
The `<h1>` is added at the bottom of the body.

Interview Difference

appendChild()
• Adds only one node
• Older DOM method

append()
• Can add multiple nodes
• Can add text
• Modern method


4. prepend()

Definition
prepend() inserts a new element **at the beginning of the parent element**.

Syntax

```javascript
parent.prepend(child);
```

Example

```javascript
document.querySelector("body").prepend(h1);
```

Result
The element appears **at the top of the body**.

Example

Before

```
Hello 1
Hello 2
Hello 3
```

After prepend

```
Hello DOM
Hello 1
Hello 2
Hello 3
```


5. remove()

Definition
remove() deletes an element from the DOM.

Syntax

```javascript
element.remove();
```

Example

```javascript
h1.remove();
```

Explanation
• Removes the element completely from the webpage
• Called directly on the element

Important Interview Point

Wrong

```javascript
document.remove()
document.removeChild()
```

Correct

```javascript
element.remove()
```


6. removeChild()

Definition
removeChild() removes a child element from its parent.

Syntax

```javascript
parent.removeChild(child);
```

Example

```javascript
document.body.removeChild(h1);
```

But modern JavaScript usually uses:

```javascript
h1.remove();
```

because it is simpler.



7. Important Concept: DOM Manipulation Flow

To dynamically add elements we follow this process:

Step 1 – Create element

```javascript
let h1 = document.createElement("h1");
```

Step 2 – Add content

```javascript
h1.textContent = "Hello DOM";
```

Step 3 – Insert into DOM

```javascript
document.querySelector("body").append(h1);
```

Step 4 – Remove if needed

```javascript
h1.remove();
```


8. Common Use Cases (Real Projects)

These methods are used for:

• Adding new list items
• Creating dynamic cards
• Adding comments dynamically
• Rendering API data
• Building dynamic tables
• Creating modal dialogs

Example

```javascript
let li = document.createElement("li");
li.textContent = "New Item";
document.querySelector("ul").append(li);
```


9. Interview One-Line Answer

DOM element creation is done using `createElement()`, and elements can be inserted into the DOM using `append()`, `appendChild()`, or `prepend()`, and removed using `remove()` or `removeChild()`.


10. Key Differences Summary

createElement
Creates a new HTML element.

append
Adds element at end of parent.

appendChild
Adds single child at end.

prepend
Adds element at beginning.

remove
Removes element directly.

removeChild
Parent removes a specific child.

# DOM Styling and Class Manipulation

Definition
DOM styling means changing the appearance (CSS styles) of HTML elements using JavaScript.

JavaScript can modify:

* inline styles
* CSS classes
* attributes


1. Styling using .style property

Definition
The style property is used to apply CSS styles directly to an element using JavaScript.

Syntax

```javascript
element.style.property = "value"
```

Example

```javascript
let h1 = document.querySelector("h1");

h1.style.color = "red";
h1.style.backgroundColor = "yellow";
h1.style.border = "2px solid black";
h1.style.borderRadius = "50px";
h1.style.textAlign = "center";
```

Important rule

CSS properties written with hyphen (-) are converted to camelCase in JavaScript.

Examples

CSS → JavaScript

background-color → backgroundColor
border-radius → borderRadius
text-align → textAlign
font-size → fontSize


2. Styling using CSS classes (Best Practice)

Instead of applying many styles using `.style`, developers usually add or remove CSS classes.

Why this is better:

* cleaner code
* reusable styles
* separation of HTML, CSS, and JavaScript

Example CSS

```css
.styling{
    color: red;
    background-color: yellow;
    border: 2px solid black;
    border-radius: 50px;
    text-align: center;
}
```

Instead of writing many `.style` lines, we attach the class using JavaScript.


3. classList property

Definition
classList is a DOM property used to add, remove, or toggle CSS classes from an element.

Example

```javascript
let h1 = document.querySelector("h1");
```


4. classList.add()

Definition
Adds a class to the element.

Syntax

```javascript
element.classList.add("className")
```

Example

```javascript
h1.classList.add("styling");
```


5. classList.remove()

Definition
Removes a class from the element.

Syntax

```javascript
element.classList.remove("className")
```

Example

```javascript
h1.classList.remove("styling");
```


6. classList.toggle()

Definition
Toggle means switch.

If the class exists → it removes it
If the class does not exist → it adds it

Syntax

```javascript
element.classList.toggle("className")
```

Example

```javascript
h1.classList.toggle("styling");
```

This is commonly used for:

* dark mode
* show/hide menus
* interactive UI effects


7. Difference between classList and className

className

```javascript
h1.className = "styling"
```

* replaces all existing classes
* not flexible

classList

```javascript
h1.classList.add("styling")
```

* adds or removes classes individually
* safer and recommended


8. Why classList is preferred in real projects

Advantages

* clean code
* better performance
* reusable CSS
* easier maintenance

Example

Bad practice

```javascript
h1.style.color = "red"
h1.style.backgroundColor = "yellow"
```

Good practice

```javascript
h1.classList.add("styling")
```

---

Quick Interview Summary

DOM Styling
Changing the appearance of HTML elements using JavaScript.

.style
Used to apply inline CSS styles directly to an element.

classList
A DOM property used to manipulate CSS classes.

Methods of classList

* add()
* remove()
* toggle()

Best Practice
Use CSS classes with `classList` instead of many `.style` properties.


----------------------------------------------------------------------------------------------------------------------------------

# DOM Events and Event Listeners

1. Event

Definition
An event is an action or occurrence that happens in the browser, usually triggered by the user or the browser itself.

Examples of events

* click
* double click
* mouseover
* keypress
* submit
* input
* load

Example
Clicking a button or pressing a key is an event.


2. Event Listener

Definition
An Event Listener is a function that waits for a specific event to occur on an element and then executes some code in response.(action's reaction)

Syntax

```javascript
element.addEventListener("event", function)
```

Example
```html
<h1>Apple</h1>
```
```javascript
let h1 = document.querySelector("h1");

let changeRed = ()=>{
    h1.style.color = "red";
    h1.style.backgroundColor = "yellow";
}

h1.addEventListener("click", changeRed);
```

Explanation

When the user clicks the `<h1>` element:

* the event "click" occurs
* the function `changeRed()` runs
* the text becomes red and background becomes yellow


4. Important rule when using functions in event listeners

Do NOT write parentheses while passing the function only function name without parenthesis().

Correct

```javascript
h1.addEventListener("click", changeRed)
```

Wrong

```javascript
h1.addEventListener("click", changeRed())
```

Reason
If parentheses are used, the function executes immediately instead of waiting for the event.

5. removeEventListener()

Definition
removeEventListener() is used to remove an event listener from an element.

Syntax

```javascript
element.removeEventListener("event", functionName)
```

Example

```javascript
h1.removeEventListener("click", changeRed)
```

Important rule
The function must be declared separately to remove it.
Arrow functions written directly cannot be removed easily.


6. Multiple Event Listeners

An element can have multiple events.

Example

```javascript
let p = document.querySelector("p");

p.addEventListener("click", ()=>{
    p.style.color = "green";
});

p.addEventListener("dblclick", ()=>{
    p.style.color = "blue";
});
```

7. Common DOM Events

Mouse Events

* click
* dblclick
* mouseover
* mouseout

Keyboard Events

* keydown
* keyup
* keypress

Form Events

* submit
* input
* change
* focus
* blur

Browser Events

* load
* resize
* scroll

---

8. Best Practice (Important for interviews)

Instead of writing inline events in HTML like this:

```html
<button onclick="changeColor()"></button>
```

Use JavaScript event listeners:

```javascript
button.addEventListener("click", changeColor)
```

Advantages

* cleaner code
* better separation of HTML and JavaScript
* easier maintenance


Quick Interview Summary

Event
An event is an action performed by the user or browser.

Event Listener
A function that listens for an event and executes code when the event occurs.

addEventListener()
Used to attach an event to an element.

removeEventListener()
Used to remove an attached event from an element.

Important rule
Always pass the function reference (without parentheses).


Below are **clean, structured interview-friendly notes** based on your code. You can **directly copy-paste this into your GitHub README**.

---

# Common Events

## Important Rule about `this` in Events

### Works with normal functions

```javascript
function onClick(){
  this.style.color = "red";
}
```

### Works with function expressions

```javascript
let onClick = function(){
  this.style.color = "red";
}
```

### Does NOT work with arrow functions

```javascript
let onClick = ()=>{
  this.style.color = "red"; // ❌ this does not refer to the element
}
```

**Reason**

Arrow functions **do not have their own `this`**.

Instead, use the **event object**:

```javascript
let onClick = (e)=>{
  e.target.style.color = "red";
}
```

## Event Object

**Definition**

The **event object** contains information about the event that occurred.

It is automatically passed to the event handler.

Example:

```javascript
element.addEventListener("click", function(e){
  console.log(e);
});
```

Common properties:

```
e.target → element that triggered the event
e.key → key pressed
e.clientX → mouse X position
e.clientY → mouse Y position
e.data → typed character in input event
```


## 1. Click Event

Triggered when a user **clicks an element**.

Example:

```javascript
let h1 = document.querySelector("h1");

let onClick = function(){
  this.style.color = "red";
}

h1.addEventListener("click", onClick);
```

## 2. Input Event

Triggered **every time the user types in an input field**.

Example:

```javascript
let onInput = function(e){
  if(e.data !== null){
    console.log(e.data);
  }
}

document.querySelector("input").addEventListener("input", onInput);
```

`e.data` → the character typed by the user.


##  3. Change Event

Triggered when the **value of an input/select element changes and loses focus**.

Example:

```javascript
let onChange = function(e){
  console.log(e.target.value);

  document.querySelector("#change").textContent =
  `${e.target.value} Device Selected`;
}

document.querySelector("select").addEventListener("change", onChange);
```

Used with:

* `<select>`
* `<input>`
* `<textarea>`


## 4. Submit Event

Triggered when a **form is submitted**.

By default, submitting a form **reloads the page**.

To stop this behavior, use:

```
event.preventDefault()
```

Example:

```javascript
form.addEventListener("submit", function(e){
  e.preventDefault();
});
```


## Example Use Case – Dynamic Profile Card

Steps performed in the code:

1. Prevent form refresh using `preventDefault()`
2. Read input values
3. Create elements dynamically
4. Add profile image and user details
5. Append the card to the page
6. Reset the form fields

Example:

```javascript
let card = document.createElement("div");
card.classList.add("card");
```


## 5. Mouse Events

## Mouseover Event

Triggered when the **mouse enters an element**.

Example:

```javascript
box.addEventListener("mouseover", function(){
  this.style.backgroundColor = "yellow";
});
```


## Mouseout Event

Triggered when the **mouse leaves an element**.

Example:

```javascript
box.addEventListener("mouseout", function(){
  this.style.backgroundColor = "red";
});
```


## Mousemove Event

Triggered **whenever the mouse moves**.

Commonly used for:

* drag effects
* tracking mouse position
* games

Example:

```javascript
window.addEventListener("mousemove",(e)=>{
  box.style.top = e.clientY + "px";
  box.style.left = e.clientX + "px";
});
```

Important CSS requirement:

```
position: absolute
```


## 6. Keyboard Events

Keyboard events detect when keys are pressed.

Common keyboard events:

```
keydown
keyup
keypress
```


## Keydown Event

Triggered **when a key is pressed**.

Example:

```javascript
window.addEventListener("keydown",(e)=>{
  console.log(e.key);
});
```


## Keyup Event

Triggered **when the key is released**.

Example:

```javascript
window.addEventListener("keyup",(e)=>{
  k.textContent = e.key;
});
```

`e.key` → returns the key pressed.

Example output:

```
a
Enter
ArrowUp
Space
```


## Best Practices (Interview Important)

### 1. Prefer `addEventListener`

Avoid inline events like:

```html
<button onclick="clickMe()">
```

Use:

```javascript
button.addEventListener("click", clickMe);
```


### 2. Use normal functions when `this` is needed

Arrow functions do not bind `this`.


### 3. Use `preventDefault()` for forms

Prevents page reload.


### 4. Use event object when needed

Example:

```
e.target
e.key
e.clientX
```


## Quick Interview Summary

Event
→ An action performed by the user or browser.

Event Listener
→ A function that runs when an event occurs.

Event Object
→ Contains information about the event.

Common Events

```
click
input
change
submit
mouseover
mouseout
mousemove
keydown
keyup
```

Important Methods

```
addEventListener()
preventDefault()
```

You can copy-paste these **short interview-friendly notes** for **Event Bubbling**.


# Event Bubbling 

### Definition

**Event Bubbling** is a mechanism in the DOM where an event starts from the **target element** and then propagates (bubbles) upward through its **parent elements** until it reaches the root (`document`).

In simple words:

> When an event happens on a child element, it also triggers the event on its parent elements.


## Event Bubbling Flow

Example DOM structure:

```
body
 └── div.nav
      └── button
```

If the **button is clicked**, the event flow will be:

```
button → div.nav → body → document
```

The event starts from the **target element** and moves upward.


### Example

```javascript
document.querySelector(".nav").addEventListener("click", ()=>{
  alert("Clicked on nav");
});
```

HTML:

```html
<div class="nav">
  <h1>Event Bubbling</h1>
  <a href="">Home</a>
  <a href="">About</a>
  <button>Click me</button>
</div>
```

### Behavior

Even though the event listener is attached only to `.nav`, clicking any child element will trigger the event.

Examples:

Clicking:

```
Home
About
Button
```

Output:

```
Clicked on nav
```

This happens because of **event bubbling**.


### Important Concept: `event.target`

`event.target` returns the **actual element where the event occurred**.

Example:

```javascript
document.querySelector("ul").addEventListener("click",(e)=>{
  console.log(e.target);
});
```

If the user clicks:

```
<li>Apple</li>
```

`event.target` will return:

```
<li>Apple</li>
```


### Why Event Bubbling is Useful

Event bubbling allows us to use **Event Delegation**, where we attach a single event listener to a parent element instead of multiple child elements.

Example:

```javascript
document.querySelector("ul").addEventListener("click",(e)=>{
  e.target.classList.toggle("lt");
});
```

Here one listener on `ul` handles clicks for all `li`.


### Stopping Event Bubbling

Sometimes we want to prevent the event from moving to parent elements.

We can use:

```
event.stopPropagation()
```

Example:

```javascript
child.addEventListener("click", (e) => {
  console.log("Child clicked");
  e.stopPropagation();
});
```

Now the event will **not reach the parent elements**.
In event bubbling, both child and parent event listeners execute when the child is clicked. To stop the parent listener from executing, we use event.stopPropagation().


### Quick Interview Summary

Event Bubbling
→ A process where an event starts from the **target element** and propagates upward through its **parent elements** in the DOM.

Event Flow

```
Target Element → Parent → Body → Document
```

Common Methods

```
event.target
event.stopPropagation()
```

##  Event Target

### Definition

`event.target` refers to the **actual element where the event occurred**.

Example:

```javascript
document.querySelector("ul").addEventListener("click",(e)=>{
  console.log(e.target);
});
```

If you click:

```
<li>Apple</li>
```

`e.target` will be:

```
<li>Apple</li>
```


#  Event Delegation

### Definition

**Event Delegation** is a technique where we attach a **single event listener to a parent element** to handle events for multiple child elements using **event bubbling**.

This improves performance and reduces code duplication.


# Example of Event Delegation

HTML

```html
<ul>
  <li>Apple</li>
  <li>Ball</li>
  <li>Cat</li>
  <li>Dog</li>
</ul>
```

Instead of writing event listeners for each `<li>`:

❌ Bad approach

```javascript
li1.addEventListener(...)
li2.addEventListener(...)
li3.addEventListener(...)
```

✅ Good approach

```javascript
document.querySelector("ul").addEventListener("click",(e)=>{
  e.target.classList.toggle("lt");
});
```

CSS

```css
.lt{
  text-decoration: line-through;
}
```

### Behavior

When any `<li>` is clicked:

```
Apple → gets strike-through
Ball → gets strike-through
Cat → gets strike-through
Dog → gets strike-through
```


# Why Event Delegation is Useful

Advantages:

1. **Better performance**
   Only one event listener is used instead of many.

2. **Less code**
   No need to attach listeners to every element.

3. **Works for dynamically added elements**

Example:

If a new `<li>` is added later, it will still work without adding another listener.


# Important Terms

### Target Element

The element that **actually triggered the event**.

```
e.target
```

### Parent Element

The element where the **event listener is attached**.


# Example Flow

If user clicks:

```
<li>Cat</li>
```

Event flow:

```
li → ul → div → body → document
```

Because of this bubbling, the `ul` listener can detect the click.

# Quick Interview Summary

**Event Bubbling**

An event propagation mechanism where the event moves from the **target element to its parent elements**.

**Event Delegation**

A technique of attaching a **single event listener to a parent element** to manage events for its children using **event bubbling**.

**event.target**

Returns the **element that triggered the event**.

**stopPropagation()**

Stops the event from bubbling to parent elements.


✅ **Real-World Use Cases**

Event delegation is used in:

* Todo lists
* Table row actions
* Dynamic menus
* Comment systems
* Infinite scrolling lists

# Event Capturing 

## Definition

**Event Capturing** is a phase of the DOM event flow where the event travels from the **top-level element (document)** down to the **target element**.

It is also called the **capture phase**.



# Event Flow in the DOM

Whenever an event occurs, it goes through **two phases**:

```
1. Capturing Phase  → Top → Target
2. Bubbling Phase   → Target → Top
```

Example DOM structure:

```
document
  ↓
html
  ↓
body
  ↓
div.a
  ↓
div.b
  ↓
div.c
  ↓
button (target)
```

Event flow:

```
Capturing Phase: document → html → body → a → b → c → button
Bubbling Phase : button → c → b → a → body → html → document
```


# Default Behavior

By default, **event listeners execute during the bubbling phase**.


# Enabling Event Capturing

To run an event listener during the **capturing phase**, we pass `true` as the third argument.

Syntax:

```javascript
element.addEventListener("event", handler, true);
```

Example:

```javascript
a.addEventListener("click", ()=>{
  alert("a clicked");
}, true);
```

Here the event listener runs **during the capturing phase**.

---

# Example Behavior

HTML structure:

```
a
 └── b
      └── c
           └── button
```

Code:

```javascript
a.addEventListener("click", ()=>{
  alert("a clicked");
}, true);

b.addEventListener("click", ()=>{
  alert("b clicked");
});

c.addEventListener("click", ()=>{
  alert("c clicked");
});

btn.addEventListener("click",(e)=>{
  alert("btn clicked");
  e.stopPropagation();
});
```

When clicking the **button**, execution order will be:

```
a clicked   (capturing phase)
btn clicked (target)
```

Because `stopPropagation()` stops the event before bubbling continues.

## Important Points

• Every DOM event goes through **two phases**: capturing and bubbling.

• **Capturing phase runs first**, then bubbling phase runs.

• By default, event listeners execute in **bubbling phase**.

• To activate capturing phase, pass **`true`** in `addEventListener`.

• `stopPropagation()` prevents the event from moving to parent elements.

---

## Quick Interview Summary

**Event Capturing**

A process where the event travels from the **top of the DOM tree to the target element** before bubbling back up.

Syntax:

```javascript
element.addEventListener("click", handler, true);
```

#  Form Validation

## 1. Definition

Form validation is the **process of checking whether the user input data is correct and complete before submitting the form**.


## 2. Purpose of Form Validation

* Ensures **correct data entry**
* Prevents **invalid or empty inputs**
* Improves **user experience**
* Reduces **server load**
* Increases **application security**


## 3. Types of Form Validation

### 1️⃣ Client-Side Validation

* Performed in the **browser**
* Implemented using **JavaScript**
* Faster because no server request is needed

Examples:

* Email format check
* Password length validation


### 2️⃣ Server-Side Validation

* Performed on the **server**
* Implemented using languages like:

  * PHP
  * Python
  * Java
  * Node.js

Used for **security and database validation**.



## 4. Common Validation Checks

Some commonly validated fields include:

* Required fields
* Email format
* Password strength
* Phone number format
* Username length
* Input range


## 5. Techniques Used in Form Validation

### 1️⃣ JavaScript Validation

Uses JavaScript functions to check user input.

Example:

```
if(email == ""){
   alert("Email required")
}
```


### 2️⃣ Regular Expressions (Regex)

Used to check **patterns in strings**.

Example:

```
/^[^\s@]+@[^\s@]+\.[^\s@]+$/
```

Used for:

* Email validation
* Password validation
* Phone numbers


### 3️⃣ HTML5 Validation Attributes

HTML provides built-in validation attributes:

| Attribute    | Purpose              |
| ------------ | -------------------- |
| required     | field must be filled |
| pattern      | checks regex pattern |
| minlength    | minimum characters   |
| maxlength    | maximum characters   |
| type="email" | validates email      |

Example:

```
<input type="email" required>
```


## 6. Error Messages

Validation should display **clear error messages** to guide the user.

Example:

* "Please enter a valid email address"
* "Password must be at least 8 characters"



## 7. Advantages of Form Validation

* Improves **data accuracy**
* Prevents **incorrect submissions**
* Saves **server resources**
* Provides **better user interaction**


## 8. Best Practices

* Validate both **client-side and server-side**
* Use **clear error messages**
* Use **regex for pattern validation**
* Prevent form submission using `preventDefault()` in JavaScript
* Reset error messages when user edits input









































