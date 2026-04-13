
---

# 🔹 React Interview Concepts (Q41–Q45)

## 41. ⚙️ **ReactDOMServer**
- **Definition**: A module in React that allows you to render components to static HTML on the server.
- **Use Case**: Useful for **Server-Side Rendering (SSR)**, SEO optimization, and sending pre-rendered HTML to clients.
- **Key Methods**:
  - `renderToString()` → Converts React components into an HTML string.
  - `renderToStaticMarkup()` → Similar, but without extra React attributes (like `data-reactroot`).

**Example:**
```jsx
import ReactDOMServer from 'react-dom/server';
import App from './App';

const html = ReactDOMServer.renderToString(<App />);
console.log(html); 
// Outputs: <div id="root"><h1>Hello World</h1></div>
```

---

## 42. 📝 **Using innerHTML in React**
- In React, you **don’t directly use `innerHTML`** because it can cause **XSS (security risks)**.
- Instead, React provides `dangerouslySetInnerHTML`.

**Syntax:**
```jsx
<div dangerouslySetInnerHTML={{ __html: "<h1>Injected HTML</h1>" }} />
```

⚠️ **Symbol Note**: ⚠️ Always sanitize user input before using `dangerouslySetInnerHTML`.

---

## 43. 🎨 **Applying Styles in React**
- **Inline Styles**: Use `style` prop with a JS object.
- **CSS Classes**: Use `className` instead of `class`.
- **CSS Modules / Styled Components**: For scoped or dynamic styling.

**Examples:**
```jsx
// Inline style
<div style={{ color: "blue", fontSize: "20px" }}>Hello</div>

// CSS class
<div className="myClass">Hello</div>
```

🔑 **Symbol Note**: 🎨 Inline styles = quick fixes, `className` = reusable styles.

---

## 44. 🎯 **Events in React**
- React events are **synthetic events** (wrapped around native events for cross-browser compatibility).
- Naming convention: **camelCase** (e.g., `onClick`, `onChange`).
- Functions are passed instead of strings.

**Example:**
```jsx
<button onClick={() => alert("Clicked!")}>Click Me</button>
```

🔄 **Difference vs. DOM**:
- DOM: `<button onclick="handleClick()">`
- React: `<button onClick={handleClick}>`

---

## 45. 🔑 **Impact of Using Indexes as Keys**
- Keys help React identify which items changed in a list.
- Using **indexes as keys** can cause:
  - ❌ Wrong component re-rendering
  - ❌ Performance issues
  - ❌ Bugs when list order changes

**Example:**
```jsx
// Bad practice
{items.map((item, index) => <li key={index}>{item}</li>)}

// Good practice
{items.map(item => <li key={item.id}>{item.name}</li>)}
```

📌 **Symbol Note**: ✅ Use **unique IDs** as keys, not indexes.

---

# 🧾 Quick Cheat-Sheet Recap
- ⚙️ **ReactDOMServer** → SSR with `renderToString()`.
- 📝 **innerHTML** → Use `dangerouslySetInnerHTML`.
- 🎨 **Styles** → Inline `{}`, `className`, or CSS modules.
- 🎯 **Events** → Synthetic, camelCase, pass functions.
- 🔑 **Keys** → Avoid indexes, use unique IDs.

---


---

# 🔹 React Interview Concepts (Q46–Q50)

## 46. 🔀 **Conditional Rendering in React**
- React lets you render components based on conditions (like `if`, `ternary`, or logical operators).
- **Approaches**:
  - `if/else`
  - Ternary `? :`
  - Logical `&&`

**Example:**
```jsx
function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <h1>Welcome Back!</h1> : <h1>Please Sign In</h1>}
    </div>
  );
}
```

📌 **Symbol Note**: 🔀 Use ternary for inline conditions, `&&` for short-circuit rendering.

---

## 47. ⚠️ **Spreading Props on DOM Elements**
- Using `{...props}` on DOM elements can unintentionally pass **invalid attributes**.
- This may cause:
  - ❌ Warnings in console
  - ❌ Security risks (e.g., passing user data)
  - ❌ Performance issues

**Example:**
```jsx
// Risky
<input {...props} />

// Safer
<input type="text" value={props.value} onChange={props.onChange} />
```

⚠️ **Symbol Note**: Be careful — only spread props when you’re sure they are valid HTML attributes.

---

## 48. 🧠 **Memoizing a Component**
- Memoization prevents **unnecessary re-renders**.
- Use `React.memo` for functional components.
- Use `useMemo` or `useCallback` for values/functions inside components.

**Example:**
```jsx
const MyComponent = React.memo(({ name }) => {
  console.log("Rendered!");
  return <div>{name}</div>;
});
```

🔑 **Symbol Note**: 🧠 Memoization = performance boost by caching results.

---

## 49. 🌐 **Implementing Server-Side Rendering (SSR)**
- SSR = Rendering React components on the server and sending HTML to the client.
- Steps:
  1. Use `ReactDOMServer.renderToString()`.
  2. Send HTML from server (Node.js/Express).
  3. Hydrate on client with `ReactDOM.hydrate()`.

**Example (Express SSR):**
```jsx
import express from "express";
import ReactDOMServer from "react-dom/server";
import App from "./App";

const app = express();

app.get("/", (req, res) => {
  const html = ReactDOMServer.renderToString(<App />);
  res.send(`<!DOCTYPE html><div id="root">${html}</div>`);
});

app.listen(3000);
```

📌 **Symbol Note**: 🌐 SSR improves SEO + initial load performance.

---

## 50. 🚀 **Enable Production Mode in React**
- React runs in **development mode** by default (with warnings).
- To enable **production mode**:
  - Use `npm run build` → creates optimized bundle.
  - Deploy the build folder with a server (e.g., `serve`).
  - Production mode removes warnings and optimizes performance.

**Example:**
```bash
npm run build
serve -s build
```

🚀 **Symbol Note**: Production mode = optimized, faster, smaller bundle.

---

# 🧾 Quick Cheat-Sheet Recap
- 🔀 **Conditional Rendering** → `if`, `? :`, `&&`.
- ⚠️ **Spreading Props** → Avoid invalid attributes.
- 🧠 **Memoization** → `React.memo`, `useMemo`, `useCallback`.
- 🌐 **SSR** → `renderToString()` + `hydrate()`.
- 🚀 **Production Mode** → `npm run build`.

---



