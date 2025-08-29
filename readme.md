# JavaScript DOM & Events Interview Notes

## 1. Difference between `getElementById`, `getElementsByClassName`, `querySelector`, and `querySelectorAll`

### `getElementById(id)`
- Selects a single element by its **unique id**.  
- Returns the element or `null`.  
- Fastest method for ID-based selection.  

### `getElementsByClassName(className)`
- Selects **all elements** with the given class.  
- Returns a **live HTMLCollection** (updates automatically if DOM changes).  
- Access elements using index (e.g., `elements[0]`).  

### `querySelector(selector)`
- Selects the **first element** matching a **CSS selector** (`.class`, `#id`, `tag[attr]`, etc.).  
- Returns the element or `null`.  

### `querySelectorAll(selector)`
- Selects **all elements** matching a CSS selector.  
- Returns a **static NodeList** (does not update with DOM changes).  

---

## 2. How to Create and Insert a New Element into the DOM

1. **Create the element**  
   ```js
   const div = document.createElement("div");
   ```

2. **Set content or attributes**  
   ```js
   div.textContent = "Hello!";
   div.className = "box";
   ```

3. **Insert into the DOM**  
   ```js
   document.body.appendChild(div);
   // or parent.prepend(), parent.insertBefore()
   ```

4. **(Optional) Add styling or modify later**  
   ```js
   div.style.color = "red";
   div.classList.add("highlight");
   ```

---

## 3. What is Event Bubbling?

**Definition:**  
Event bubbling is when an event on a child element automatically "bubbles up" to its parent, then its ancestors, until reaching the `document` root.  

**How it works:**  
1. User clicks the innermost element.  
2. Its event handler runs first.  
3. Then the same event propagates upward, triggering handlers on parent elements (if any).  

---

## 4. What is Event Delegation? Why is it Useful?

**Definition:**  
Event delegation is attaching a **single event listener** on a parent element to handle events from its children, using event bubbling.  

**How it works:**  
1. Add the listener on a parent element.  
2. When a child is clicked, the event bubbles up to the parent.  
3. Inside the handler, use `event.target` or `.matches()` to check which child triggered it.  

**Advantages:**  
- **Fewer event listeners → better performance**.  
- **Works with dynamically added elements**.  
- **Simpler and cleaner code**.  

---

## 5. Difference between `preventDefault()` and `stopPropagation()`

### `preventDefault()`
- Stops the browser’s **default action** (e.g., preventing a form submission, disabling a link redirect).  

### `stopPropagation()`
- Stops the event from **bubbling up** to parent elements.  
