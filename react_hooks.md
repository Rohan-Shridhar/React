
# ⚛️ React Hooks – Personal Notes

This repository contains my **structured notes on React Hooks**, written while learning and practicing React with real projects.  
The goal is to understand **why hooks exist**, **when to use them**, and **common mistakes to avoid**, not just syntax.

---

## 📌 What are React Hooks?

React Hooks allow you to use **state, lifecycle behavior, and other React features** inside **functional components** without using class components.

> Hooks = State + Side Effects + Reusability for function components

---

## ⚠️ Rules of Hooks (Must Follow)

1. Call hooks **only at the top level**  
   - ❌ Not inside loops, conditions, or nested functions
2. Call hooks **only inside React function components or custom hooks**

Breaking these rules causes unpredictable behavior.

---

## 🔹 useState

### Purpose
Used to store and update **component-level state**.

### Syntax
```js
const [state, setState] = useState(initialValue);
````

### Example

```js
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>+</button>
```

### Key Points

* State updates are asynchronous
* Never mutate state directly
* Triggers re-render on update

### Common Use Cases

* Form inputs
* Counters
* Toggle states
* UI state management

---

## 🔹 useEffect

### Purpose

Handles **side effects** in React components.

### Common Side Effects

* API calls
* Timers
* Event listeners
* Subscriptions
* DOM updates

### Syntax

```js
useEffect(() => {
  // side effect
}, [dependencies]);
```

### Dependency Patterns

#### Run on every render

```js
useEffect(() => {
  console.log("Rendered");
});
```

#### Run only once (on mount)

```js
useEffect(() => {
  fetchData();
}, []);
```

#### Run when a value changes

```js
useEffect(() => {
  console.log(count);
}, [count]);
```

### Cleanup Example

```js
useEffect(() => {
  const timer = setInterval(() => {}, 1000);

  return () => clearInterval(timer);
}, []);
```

### Important Note

Avoid using `async` directly inside `useEffect`.

Correct pattern:

```js
useEffect(() => {
  const loadData = async () => {};
  loadData();
}, []);
```

---

## 🔹 useRef

### Purpose

* Access DOM elements directly
* Store mutable values without causing re-renders

### Syntax

```js
const ref = useRef(initialValue);
```

### DOM Access Example

```js
const inputRef = useRef();

<input ref={inputRef} />
<button onClick={() => inputRef.current.focus()} />
```

### Persistent Value Example

```js
const counter = useRef(0);
counter.current++;
```

### Difference Between useState and useRef

| useState           | useRef                    |
| ------------------ | ------------------------- |
| Triggers re-render | No re-render              |
| For UI updates     | For hidden/mutable values |

---

## 🔹 useContext

### Purpose

Used to avoid **prop drilling** by sharing data globally.

### Steps

#### Create Context

```js
const ThemeContext = createContext();
```

#### Provide Context

```js
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>
```

#### Consume Context

```js
const theme = useContext(ThemeContext);
```

### Common Use Cases

* Theme management
* Authentication state
* Language preferences

⚠️ Overuse may cause unnecessary re-renders.

---

## 🔹 useReducer

### Purpose

Used for **complex state logic** where state transitions need to be predictable.

### Syntax

```js
const [state, dispatch] = useReducer(reducer, initialState);
```

### Example

```js
function reducer(state, action) {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;
    case "DECREMENT":
      return state - 1;
    default:
      return state;
  }
}

const [count, dispatch] = useReducer(reducer, 0);
```

### When to Use

* Multiple related state values
* Complex update logic
* State transitions matter

---

## 🔹 Custom Hooks

### Purpose

Used to **reuse logic**, not UI components.

### Rules

* Custom hooks must start with `use`
* Can call other hooks inside

### Example

```js
function useCounter() {
  const [count, setCount] = useState(0);
  return {
    count,
    increment: () => setCount(count + 1)
  };
}
```

Usage:

```js
const { count, increment } = useCounter();
```

### Common Use Cases

* Data fetching
* Authentication logic
* Form handling

---

## 🧠 Mental Model for Hooks

* `useState` → What changes
* `useEffect` → What reacts to change
* `useRef` → What persists without reacting
* `useContext` → What is shared globally
* `useReducer` → How state evolves
* Custom Hooks → How logic is reused

---