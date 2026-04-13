
---

# 🔹 React Interview Concepts (Q51–Q55)

## 51. 🔄 **Do Hooks replace render props and HOCs?**
- **Hooks** (like `useState`, `useEffect`, `useContext`) provide a simpler way to reuse logic.
- They don’t *completely* replace **Render Props** or **Higher-Order Components (HOCs)**, but they make them less necessary.
- Hooks solve the problem of **wrapper hell** (too many nested components).

**Example:**
```jsx
// With HOC
function withLogger(Component) {
  return function Wrapped(props) {
    console.log(props);
    return <Component {...props} />;
  };
}

// With Hook
function useLogger(value) {
  useEffect(() => console.log(value), [value]);
}
```

📌 **Symbol Note**: 🔄 Hooks = modern, cleaner alternative to HOCs/render props.

---

## 52. 🔀 **Switching Component**
- A **switching component** renders one component out of many based on a condition.
- Often used in **routing** or **tab systems**.

**Example:**
```jsx
function Switch({ page }) {
  switch (page) {
    case "home": return <Home />;
    case "about": return <About />;
    default: return <NotFound />;
  }
}
```

📌 **Symbol Note**: 🔀 Switching = conditional component chooser.

---

## 53. 🧩 **React Mixins**
- **Mixins** were used in older React (pre-ES6 classes) to share reusable logic across components.
- Example: `PureRenderMixin` for performance.
- ❌ **Deprecated** in favor of **HOCs** and **Hooks**.

**Example (old style):**
```jsx
var MyMixin = {
  componentDidMount() { console.log("Mounted!"); }
};

var MyComponent = React.createClass({
  mixins: [MyMixin],
  render() { return <div>Hello</div>; }
});
```

📌 **Symbol Note**: 🧩 Mixins = legacy pattern, replaced by Hooks/HOCs.

---

## 54. 🖱️ **Pointer Events in React**
React supports **pointer events** (unified input for mouse, touch, pen):
- `onPointerDown`
- `onPointerMove`
- `onPointerUp`
- `onPointerCancel`
- `onGotPointerCapture`
- `onLostPointerCapture`
- `onPointerEnter`
- `onPointerLeave`
- `onPointerOver`
- `onPointerOut`

**Example:**
```jsx
<div onPointerDown={() => console.log("Pointer down!")}>
  Click or Touch Me
</div>
```

📌 **Symbol Note**: 🖱️ Pointer events = cross-device input handling.

---

## 55. 🔠 **Why Component Names Start with Capital Letter**
- React treats **lowercase tags** as HTML elements (`<div>`, `<span>`).
- **Capitalized names** are treated as **custom components**.
- If you use lowercase, React will assume it’s a DOM tag and fail to render your component.

**Example:**
```jsx
function Welcome() {
  return <h1>Hello</h1>;
}

// ✅ Correct
<Welcome />

// ❌ Wrong (React thinks it's <welcome> HTML tag)
<welcome />
```

📌 **Symbol Note**: 🔠 Capital letter = tells React it’s a component.

---

# 🧾 Quick Cheat-Sheet Recap
- 🔄 **Hooks vs HOCs/Render Props** → Hooks simplify reuse, reduce wrapper hell.
- 🔀 **Switching Component** → Chooses which component to render.
- 🧩 **Mixins** → Legacy, replaced by Hooks/HOCs.
- 🖱️ **Pointer Events** → Unified input events (mouse, touch, pen).
- 🔠 **Capital Names** → Distinguish components from HTML tags.

---

# 🔹 React Interview Concepts (Q56–Q60)

## 56. 🏷️ **Custom DOM Attributes in React v16**
- ✅ Yes, React v16+ supports **custom DOM attributes**.
- Before v16, unknown attributes were stripped out.
- Now, React passes them directly to the DOM.

**Example:**
```jsx
<div data-user="Kuldeep" custom-attr="123">Hello</div>
```
📌 **Symbol Note**: 🏷️ Useful for `data-*` attributes or integration with non-React libraries.

---

## 57. 🔁 **Looping Inside JSX**
- You can’t use traditional loops (`for`) directly inside JSX.
- Instead, use **array methods** like `.map()`.

**Example:**
```jsx
const items = ["A", "B", "C"];
<ul>
  {items.map((item, index) => <li key={index}>{item}</li>)}
</ul>
```

📌 **Symbol Note**: 🔁 `.map()` is the standard way to loop in JSX.

---

## 58. 📝 **Accessing Props Within Attribute Quotes**
- Use **curly braces `{}`** inside JSX attributes to inject props.

**Example:**
```jsx
function User({ name }) {
  return <input placeholder={`Hello, ${name}`} />;
}
```

📌 **Symbol Note**: 📝 Curly braces allow dynamic values inside attributes.

---

## 59. 📐 **React PropType Array with Shape**
- `PropTypes.arrayOf(PropTypes.shape({...}))` validates arrays of objects with specific structure.

**Example:**
```jsx
import PropTypes from "prop-types";

MyComponent.propTypes = {
  users: PropTypes.arrayOf(
    PropTypes.shape({
      id: PropTypes.number.isRequired,
      name: PropTypes.string.isRequired
    })
  )
};
```

📌 **Symbol Note**: 📐 Ensures array elements follow a defined object schema.

---

## 60. 🎭 **Conditionally Applying Class Attributes**
- Use **ternary operator** or libraries like `classnames`.

**Example:**
```jsx
<div className={isActive ? "active" : "inactive"}>Status</div>
```

**With `classnames`:**
```jsx
import classNames from "classnames";

<div className={classNames("btn", { "btn-active": isActive })}>Click</div>
```

📌 **Symbol Note**: 🎭 Conditional classes = dynamic styling based on state.

---

# 🧾 Quick Cheat-Sheet Recap
- 🏷️ **Custom Attributes** → Supported in React v16+.
- 🔁 **Looping** → Use `.map()` inside JSX.
- 📝 **Props in Attributes** → Curly braces `{}` for dynamic values.
- 📐 **PropType Array Shape** → Validate structured arrays of objects.
- 🎭 **Conditional Classes** → Ternary or `classnames` library.

---
