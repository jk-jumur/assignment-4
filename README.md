# DOM Manipulation & Events Q&A

This document covers essential concepts of the Document Object Model (DOM) and Event handling in JavaScript.

---

### 1. Difference Between Selectors
Selecting the right element is the first step in DOM manipulation. Here’s how they differ:

* **`getElementById`**: The most direct way to grab an element. Since IDs are unique, it returns only **one** element. It’s also the fastest method performance-wise.
* **`getElementsByClassName`**: This looks for all elements with a specific class and returns them as an **HTMLCollection**. Note that this is a "live" collection, meaning if the DOM updates, the list updates too.
* **`querySelector`**: Very flexible. It uses CSS-style selectors (like `#id` or `.class`). It only returns the **first** matching element it finds.
* **`querySelectorAll`**: Similar to querySelector but returns **all** matches in a **NodeList**. Unlike HTMLCollections, NodeLists are static and don't change if the DOM updates later.

---

### 2. Creating and Inserting Elements
To add a new element to the page, we usually follow these three steps:

1.  **Creation**: Use `document.createElement('tagName')` to create the element in memory.
2.  **Customization**: Add text, classes, or attributes (e.g., `element.textContent = "Hello"`).
3.  **Insertion**: Attach it to the DOM using methods like:
    * `.appendChild()`: Adds it as the last child of a parent.
    * `.prepend()`: Adds it as the first child.
    * `.insertAdjacentElement()`: For more precise positioning (before, after, etc.).

---

### 3. Event Bubbling
**Event Bubbling** is the way events propagate through the DOM tree. When an event (like a click) happens on an element, it first triggers the handler on that specific element, then it moves up to its parent, then the grandparent, and so on, until it reaches the `window` object. 

Imagine it like a bubble rising from the bottom of a pool to the surface.

---

### 4. Event Delegation
Instead of adding an event listener to every single child element (which is bad for performance), we add **one** listener to their **common parent**. 

**Why it’s useful:**
* **Performance**: Uses less memory by handling multiple elements with one listener.
* **Dynamic Content**: If you add new child elements via JavaScript later, the parent's listener will still work for them automatically.

---

### 5. `preventDefault()` vs `stopPropagation()`
These two are often confused but serve different purposes:

* **`preventDefault()`**: This stops the **browser's default behavior**. For example, it prevents a link from opening a URL or a form from refreshing the page when you click "Submit."
* **`stopPropagation()`**: This stops the **Event Bubbling** process. It prevents the event from "climbing up" to parent elements. Use this when you want to trigger an event on a child without triggering the parent's event handler.