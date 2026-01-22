
# ⚛️ What is React?

React is a **JavaScript library** used to build **user interfaces (UI)**, especially **single-page applications (SPAs)**.

It allows developers to create **reusable UI components** and efficiently update the screen when data changes.

---

## 🔹 Why React Exists

Before React:
- Developers manually updated the DOM
- UI code became complex and hard to maintain
- Small changes caused large performance issues

React solves this by:
- Breaking the UI into **components**
- Automatically updating the UI when state changes
- Making applications easier to reason about

---

## 🔹 Key Features of React

### 1️⃣ Component-Based Architecture
- UI is divided into **small, reusable components**
- Each component manages its own logic and UI

Example:
```js
function Button() {
  return <button>Click me</button>;
}
````

---



###  2️⃣ Virtual DOM

* React uses a **Virtual DOM** (in-memory representation of UI)
* Compares previous and current UI states
* Updates only the parts that changed

This improves performance.

---

### 3️⃣ State & Props

* **State** → data that changes over time
* **Props** → data passed from parent to child

React re-renders components when state changes.

---


### 4️⃣ Hooks (Modern React)

Hooks allow functional components to:

* Manage state
* Handle side effects
* Share logic

Example:

```js
const [count, setCount] = useState(0);
```

---


## 🔹 Where React is Used

* Web applications
* Dashboards
* Social media platforms
* SaaS products

Popular companies using React include:

* Facebook
* Instagram
* Netflix
* Airbnb

---

## 🔹 When to Use React

Use React when:

* Your UI changes frequently
* You need reusable components
* You are building complex front-end applications
---

## Better prepare first 
![Watch js basics](https://youtu.be/m55PTVUrlnA)
