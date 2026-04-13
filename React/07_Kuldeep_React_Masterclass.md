
---

# 🔹 React Interview Concepts (Q61–Q65)

## 61. 🔧 **Difference between React and ReactDOM**
- **React** → Core library for building UI components.
- **ReactDOM** → Handles rendering those components to the DOM (browser).
- Think of React as the **engine**, and ReactDOM as the **bridge to the browser**.

**Example:**
```jsx
// React: defines components
function App() {
  return <h1>Hello World</h1>;
}

// ReactDOM: renders to DOM
import ReactDOM from "react-dom";
ReactDOM.render(<App />, document.getElementById("root"));
```

📌 **Symbol Note**: 🔧 React = logic, ReactDOM = rendering.

---

## 62. 🔀 **Why ReactDOM is separated from React**
- Separation allows React to be **platform-agnostic**:
  - ReactDOM → Web
  - React Native → Mobile
  - React 360 → VR
- This modular design makes React reusable across environments.

📌 **Symbol Note**: 🔀 Separation = flexibility across platforms.

---

## 63. 🏷️ **Using the React `<label>` Element**
- In React, use `htmlFor` instead of `for` (because `for` is a reserved keyword in JS).
- Links a label to an input field.

**Example:**
```jsx
<label htmlFor="username">Username:</label>
<input id="username" type="text" />
```

📌 **Symbol Note**: 🏷️ `htmlFor` = React-safe attribute for labels.

---

## 64. 🎨 **Combining Multiple Inline Style Objects**
- Use the **spread operator** or `Object.assign`.

**Example:**
```jsx
const baseStyle = { color: "blue", fontSize: "20px" };
const extraStyle = { backgroundColor: "yellow" };

<div style={{ ...baseStyle, ...extraStyle }}>Styled Text</div>
```

📌 **Symbol Note**: 🎨 Spread operator merges style objects.

---

## 65. 📏 **Re-render on Browser Resize**
- Use `useEffect` with `window.addEventListener("resize")`.
- Store dimensions in state, trigger re-render when they change.

**Example:**
```jsx
function WindowSize() {
  const [size, setSize] = React.useState(window.innerWidth);

  React.useEffect(() => {
    const handleResize = () => setSize(window.innerWidth);
    window.addEventListener("resize", handleResize);
    return () => window.removeEventListener("resize", handleResize);
  }, []);

  return <p>Width: {size}px</p>;
}
```

📌 **Symbol Note**: 📏 Resize listener + state = dynamic re-render.

---

# 🧾 Quick Cheat-Sheet Recap
- 🔧 **React vs ReactDOM** → Logic vs Rendering.
- 🔀 **Separation** → Platform flexibility.
- 🏷️ **Label** → Use `htmlFor`.
- 🎨 **Combine Styles** → Spread operator.
- 📏 **Resize Re-render** → `useEffect` + event listener.


---

# 🔹 React Interview Concepts (Q66–Q70)

## 66. 📄 **Pretty-print JSON in React**
- Use `JSON.stringify(data, null, 2)` to format JSON with indentation.
- Render inside `<pre>` for readability.

**Example:**
```jsx
const obj = { name: "Kuldeep", age: 22 };

<pre>{JSON.stringify(obj, null, 2)}</pre>
```

📌 **Symbol Note**: 📄 `null, 2` = indentation for pretty-print.

---

## 67. 🚫 **Why You Can’t Update Props**
- **Props are immutable** → They are read-only values passed from parent to child.
- Updating props breaks **unidirectional data flow**.
- Instead, update **state** in parent and pass new props down.

**Example:**
```jsx
function Child({ name }) {
  // ❌ Wrong: props.name = "NewName";
  return <h1>{name}</h1>;
}
```

📌 **Symbol Note**: 🚫 Props = immutable, State = mutable.

---

## 68. 🎯 **Focus Input on Page Load**
- Use `useRef` + `useEffect` to focus an input when component mounts.

**Example:**
```jsx
function App() {
  const inputRef = React.useRef(null);

  React.useEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} type="text" />;
}
```

📌 **Symbol Note**: 🎯 `useRef` + `focus()` = auto-focus.

---

## 69. 🔍 **Find React Version at Runtime**
- Access `React.version` in the browser console.

**Example:**
```jsx
console.log(React.version); 
// e.g., "18.2.0"
```

📌 **Symbol Note**: 🔍 Quick way to check React version.

---

## 70. 📊 **Add Google Analytics for React Router**
- Use `react-ga` or `gtag.js` with React Router.
- Track page views on route change.

**Example:**
```jsx
import ReactGA from "react-ga";
import { useEffect } from "react";
import { useLocation } from "react-router-dom";

ReactGA.initialize("UA-XXXXXXX-X");

function AnalyticsTracker() {
  const location = useLocation();
  useEffect(() => {
    ReactGA.pageview(location.pathname + location.search);
  }, [location]);
  return null;
}
```

📌 **Symbol Note**: 📊 Hook into `useLocation` to track route changes.

---

# 🧾 Quick Cheat-Sheet Recap
- 📄 **Pretty-print JSON** → `JSON.stringify(obj, null, 2)` inside `<pre>`.
- 🚫 **Props immutable** → Update state, not props.
- 🎯 **Focus input** → `useRef` + `useEffect`.
- 🔍 **React version** → `React.version`.
- 📊 **Google Analytics** → Track route changes with `useLocation`.

---


