Alright Kuldeep, let’s tackle questions 21–25 with **symbols, tables, and examples** so they’re easy to revise and interview-ready.  

---

# ⚛️ React Concepts (21–25)

## 2️⃣1️⃣ What are Controlled Components?
- 🎛️ A **controlled component** is a form element (like input, textarea, select) whose value is **controlled by React state**.  
- React becomes the “single source of truth.”  
- Example:  
  ```jsx
  function Form() {
    const [name, setName] = React.useState("");
    return (
      <input 
        value={name} 
        onChange={(e) => setName(e.target.value)} 
      />
    );
  }
  ```

---

## 2️⃣2️⃣ What are Uncontrolled Components?
- 🎚️ An **uncontrolled component** manages its own state internally via the DOM.  
- React does not control the value; instead, you use `ref` to access it.  
- Example:  
  ```jsx
  function Form() {
    const inputRef = React.useRef();
    function handleSubmit() {
      alert(inputRef.current.value);
    }
    return <input type="text" ref={inputRef} />;
  }
  ```

---

## 2️⃣3️⃣ Difference Between `createElement` and `cloneElement`

| Aspect | ⚛️ `React.createElement` | 🧬 `React.cloneElement` |
|--------|--------------------------|-------------------------|
| Purpose | Creates a new React element. | Clones an existing element. |
| Usage | `React.createElement('div', null, 'Hello')` | `React.cloneElement(element, { newProp: 'value' })` |
| Props | Pass props during creation. | Modify or add props to an existing element. |
| Example | `const el = <div>Hello</div>` | `const newEl = React.cloneElement(el, { className: 'highlight' })` |

---

## 2️⃣4️⃣ What is Lifting State Up in React?
- 📤 **Lifting state up** means moving state from child components to a **common parent** so multiple children can share and synchronize data.  
- Example:  
  ```jsx
  function Parent() {
    const [value, setValue] = React.useState("");
    return (
      <>
        <ChildInput value={value} onChange={setValue} />
        <ChildDisplay value={value} />
      </>
    );
  }
  ```
- ✅ Ensures consistency across components.

---

## 2️⃣5️⃣ What are Higher-Order Components (HOCs)?
- 🧩 A **Higher-Order Component** is a function that takes a component and returns a new component with added functionality.  
- Used for **code reuse, logic abstraction, and cross-cutting concerns**.  
- Example:  
  ```jsx
  function withLogger(WrappedComponent) {
    return function(props) {
      console.log("Props:", props);
      return <WrappedComponent {...props} />;
    };
  }

  const EnhancedComponent = withLogger(MyComponent);
  ```
- ✅ Commonly used for authentication, logging, or theming.

---

✨ **Quick Recap for You**:  
- Controlled = React manages value.  
- Uncontrolled = DOM manages value.  
- `createElement` = new element; `cloneElement` = copy + modify.  
- Lifting state up = share state via parent.  
- HOCs = functions that enhance components.  

---
Alright Kuldeep, let’s break down questions 26–30 with **symbols, tables, and examples** so they’re sharp and easy to revise.  

---

# ⚛️ React Concepts (26–30)

## 2️⃣6️⃣ What is the `children` Prop?
- 👶 The **`children` prop** is a special prop in React that allows you to pass nested elements/components into another component.  
- It makes components more flexible and reusable.  
- Example:  
  ```jsx
  function Card(props) {
    return <div className="card">{props.children}</div>;
  }

  <Card>
    <h2>Title</h2>
    <p>Content inside Card</p>
  </Card>
  ```
- ✅ Here, `<h2>` and `<p>` are passed as `children`.

---

## 2️⃣7️⃣ How do you write comments in React?
- 📝 Comments inside JSX use curly braces with `/* ... */`.  
- Example:  
  ```jsx
  function App() {
    return (
      <div>
        {/* This is a comment */}
        <h1>Hello Kuldeep</h1>
      </div>
    );
  }
  ```
- Outside JSX, you can use normal JavaScript comments (`//` or `/* ... */`).

---

## 2️⃣8️⃣ What is Reconciliation?
- 🔄 **Reconciliation** is the process React uses to update the DOM efficiently.  
- Steps:  
  1. React builds a new virtual DOM when state/props change.  
  2. It compares the new virtual DOM with the old one (**diffing algorithm**).  
  3. Only the changed parts are updated in the real DOM.  
- ✅ This makes updates fast and avoids unnecessary re-renders.

---

## 2️⃣9️⃣ Does the `lazy` Function Support Named Exports?
- ❌ No, `React.lazy()` only supports **default exports**.  
- If you want to use a named export, you must re-export it as default.  
- Example:  
  ```jsx
  // MyComponent.js
  export function MyComponent() { ... }

  // Wrong
  const LazyComp = React.lazy(() => import('./MyComponent')); // ❌

  // Correct
  export default MyComponent;
  const LazyComp = React.lazy(() => import('./MyComponent')); // ✅
  ```

---

## 3️⃣0️⃣ Why Does React Use `className` Instead of `class`?
- 🏷️ In JavaScript, `class` is a reserved keyword (used for defining classes).  
- ⚛️ To avoid conflicts, React uses `className` to apply CSS classes.  
- Example:  
  ```jsx
  <div className="container">Hello</div>
  ```
- ✅ This ensures compatibility with JavaScript syntax.

---

✨ **Quick Recap for You**:  
- `children` prop = nested content inside components.  
- Comments in JSX = `{/* ... */}`.  
- Reconciliation = diffing + efficient DOM updates.  
- `lazy()` = only default exports.  
- `className` = avoids conflict with JS `class` keyword.  

---


