

---

# 🔹 React Interview Concepts (Q71–Q75)

## 71. 🏷️ **Vendor Prefixes in Inline Styles**
- React automatically handles most vendor prefixes (e.g., `Webkit`, `Moz`, `ms`).
- You can apply them directly in the style object using camelCase.

**Example:**
```jsx
<div style={{ WebkitTransition: "all 0.3s ease", msTransform: "rotate(20deg)" }}>
  Prefixed Style
</div>
```

📌 **Symbol Note**: 🏷️ Prefixes must be camelCased (`WebkitTransform`, not `-webkit-transform`).

---

## 72. 📦 **Import and Export Components (ES6)**
- **Default Export** → Import without braces.
- **Named Export** → Import with braces.

**Example:**
```jsx
// Export
export default MyComponent;
export const Helper = () => <div>Helper</div>;

// Import
import MyComponent from "./MyComponent";
import { Helper } from "./MyComponent";
```

📌 **Symbol Note**: 📦 Default = one per file, Named = multiple exports.

---

## 73. 🔠 **Exceptions to Component Naming**
- Normally, components must start with **Capital Letters**.
- **Exceptions**:
  - When using `React.createElement()` directly, you can pass lowercase strings for HTML tags.
  - Custom components must be capitalized, but you can alias them.

**Example:**
```jsx
const myButton = () => <button>Click</button>;

// ❌ Wrong
<myButton />

// ✅ Correct
<MyButton />
```

📌 **Symbol Note**: 🔠 Capitalization distinguishes components from HTML tags.

---

## 74. ⚡ **Async/Await in Plain React**
- Yes, you can use `async/await` in React (inside functions, event handlers, or `useEffect`).
- Commonly used for **data fetching**.

**Example:**
```jsx
function App() {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    async function fetchData() {
      const res = await fetch("/api/data");
      const json = await res.json();
      setData(json);
    }
    fetchData();
  }, []);

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

📌 **Symbol Note**: ⚡ Async/await = cleaner async code in React.

---

## 75. 📂 **Common Folder Structures in React**
- There’s no strict rule, but common patterns include:

**Structure Example:**
```
src/
 ├── components/     # Reusable UI components
 ├── pages/          # Page-level components
 ├── hooks/          # Custom hooks
 ├── context/        # Context providers
 ├── assets/         # Images, fonts, styles
 ├── utils/          # Helper functions
 ├── App.js
 └── index.js
```

📌 **Symbol Note**: 📂 Organize by **feature** or **type** for scalability.

---

# 🧾 Quick Cheat-Sheet Recap
- 🏷️ **Vendor Prefixes** → CamelCase in style objects.
- 📦 **Import/Export** → Default vs Named.
- 🔠 **Naming Exceptions** → Components must be capitalized.
- ⚡ **Async/Await** → Works in React for async tasks.
- 📂 **Folder Structures** → Organize by feature/type for clarity.

---

# 🔹 React Interview Concepts (Q76–Q80)

## 76. 🎞️ **Popular Packages for Animation**
- **Framer Motion** → Modern, declarative animations for React.
- **React Spring** → Physics-based animations (smooth, natural).
- **GSAP (GreenSock)** → Powerful, timeline-based animations.
- **React Transition Group** → Simple enter/exit animations for components.

**Example (Framer Motion):**
```jsx
import { motion } from "framer-motion";

<motion.div animate={{ x: 100 }} transition={{ duration: 1 }}>
  Slide Right
</motion.div>
```

📌 **Symbol Note**: 🎞️ Framer Motion = most popular for React.

---

## 77. 🎨 **Benefits of Style Modules**
- Scoped CSS → No global conflicts.
- Auto-generated unique class names.
- Easier maintenance in large projects.
- Works seamlessly with bundlers like Webpack.

**Example:**
```jsx
// Button.module.css
.btn { color: white; background: blue; }

// Button.js
import styles from "./Button.module.css";
<button className={styles.btn}>Click</button>
```

📌 **Symbol Note**: 🎨 Style modules = scoped, conflict-free CSS.

---

## 78. ✅ **Popular React-Specific Linters**
- **ESLint** with React plugins:
  - `eslint-plugin-react`
  - `eslint-plugin-react-hooks`
  - `eslint-plugin-jsx-a11y` (accessibility)
- Helps enforce best practices, catch bugs, and maintain consistency.

📌 **Symbol Note**: ✅ ESLint + plugins = standard React linting setup.

---

## 79. 🛣️ **What is React Router?**
- A **routing library** for React that enables navigation between views/components.
- Provides `<BrowserRouter>`, `<Route>`, `<Link>`, `<Switch>` (or `<Routes>` in v6).
- Handles client-side routing without full page reloads.

**Example:**
```jsx
import { BrowserRouter, Route, Routes, Link } from "react-router-dom";

<BrowserRouter>
  <nav>
    <Link to="/home">Home</Link>
    <Link to="/about">About</Link>
  </nav>
  <Routes>
    <Route path="/home" element={<Home />} />
    <Route path="/about" element={<About />} />
  </Routes>
</BrowserRouter>
```

📌 **Symbol Note**: 🛣️ React Router = SPA navigation.

---

## 80. 🔀 **React Router vs History Library**
- **React Router**:
  - High-level abstraction for routing in React apps.
  - Provides components (`<Route>`, `<Link>`, `<Routes>`).
  - Manages UI + navigation together.
- **History Library**:
  - Low-level library for managing session history (push, replace, goBack).
  - React Router internally uses `history`.

**Comparison Table:**

| Feature            | React Router 🛣️ | History Library 📜 |
|--------------------|-----------------|-------------------|
| Purpose            | UI routing      | Manage browser history |
| Abstraction Level  | High            | Low |
| Usage              | `<Route>`, `<Link>` | `history.push("/path")` |
| Integration        | React-specific  | Generic JS apps |

📌 **Symbol Note**: 🔀 Router = UI + navigation, History = raw navigation API.

---

# 🧾 Quick Cheat-Sheet Recap
- 🎞️ **Animation Packages** → Framer Motion, React Spring, GSAP, Transition Group.
- 🎨 **Style Modules** → Scoped, conflict-free CSS.
- ✅ **Linters** → ESLint + React plugins.
- 🛣️ **React Router** → SPA navigation library.
- 🔀 **Router vs History** → Router = abstraction, History = low-level API.

---
