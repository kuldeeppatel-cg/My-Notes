# React Masterclass: Part 1 - Fundamentals

Welcome to the comprehensive React guide. Here, we break down the most essential React concepts, perfectly formatted for your interview preparation and deep understanding.

---

## 1. What is React?

React is a declarative, efficient, and flexible open-source JavaScript library for building user interfaces, primarily for single-page applications.

### Key Aspects:
*   **UI Library (Not a full framework):** React focuses solely on the view layer (the "V" in MVC). It concerns itself with rendering UI components based on data.
*   **Declarative:** You describe *what* you want the UI to look like for a given state, and React handles the *how* (updating the DOM efficiently).
*   **Component-Based:** UIs are broken down into small, isolated, and reusable pieces of code called components.
*   **Maintained By:** Facebook (Meta) and a community of individual developers and companies.

---

## 2. What is the history behind React’s evolution?

React was developed to solve the problem of maintaining cascading updates in complex, dynamic web applications (like Facebook's News Feed).

### Timeline:
*   **2011 (Origins):** Created by **Jordan Walke**, a software engineer at Facebook. It was initially heavily influenced by XHP (an HTML component framework for PHP) and was called "FaxJS". It was first deployed on Facebook's News Feed.
*   **2012:** Acquired by Instagram and deployed on their web application.
*   **May 2013 (Open Source):** React was officially open-sourced at JSConf US.
*   **2015 (React Native):** React Native was announced, allowing developers to build mobile apps using React patterns.
*   **February 2019 (React 16.8):** A massive paradigm shift occurred with the introduction of **Hooks**, allowing developers to use state and lifecycle features without writing class components.
*   **2022 (React 18):** Introduction of Concurrent React features, Server Components, and improved hydration.

---

## 3. What are the major features of React?

React's popularity stems from a few powerful, core features:

### Major Features:
1.  **JSX (JavaScript XML):** A syntax extension that allows you to write HTML-like structures directly inside JavaScript.
2.  **Virtual DOM (Document Object Model):** React creates an in-memory lightweight representation of the real DOM. When data changes, React updates the Virtual DOM, compares it with the previous version (Diffing algorithm), and then efficiently updates only the changed parts in the real DOM (Reconciliation).
3.  **One-way Data Binding / Unidirectional Data Flow:** Data strictly flows from parent to child components. This makes debugging easier and the application more predictable.
4.  **Component-Based Architecture:** Everything in React is a component, leading to reusable, independent pieces of code.
5.  **Declarative UI:** As state changes, React simply updates and renders the right components rather than you manually manipulating DOM elements.

---

## 4. What is JSX?

**JSX** stands for **JavaScript XML**. It is a syntax extension for JavaScript that looks very similar to HTML but works inside JavaScript files.

### Why use JSX?
*   It provides syntactic sugar for `React.createElement()`.
*   It produces React "elements" and makes code much easier to read and write.
*   It prevents injection attacks (XSS) because React DOM escapes any values embedded in JSX before rendering them.

### Example:
```jsx
// Writing this in JSX:
const element = <h1>Hello, {name}!</h1>;

// Is transformed under the hood into this JavaScript:
const element = React.createElement('h1', null, `Hello, ${name}!`);
```

---

## 5. What is the difference between an Element and a Component?

A common area of confusion is the distinction between these two foundational concepts.

### React Element
*   **Definition:** The smallest building block in React. It describes *what* you want to see on the screen.
*   **Nature:** It is a plain JavaScript object returned by `React.createElement()` or JSX. It is immutable (once created, it cannot be changed).
*   **Analogy:** A blueprint or a still frame in a movie.
```jsx
// This is an element
const myElement = <div>Hello World</div>;
```

### React Component
*   **Definition:** A blueprint or a template that can return React Elements.
*   **Nature:** It is a JavaScript function or class that accepts inputs (props) and returns a React element tree.
*   **Analogy:** The factory or machine that reads the blueprint and produces the element.
```jsx
// This is a component returning an element
function Welcome() {
  return <div>Hello World</div>;
}
```

---

## 6. How do you create components in React?

There are two primary ways to create components in React:

### 1. Function Components
These are the modern, standard way of writing React. They are simply JavaScript functions that accept `props` as an argument and return a React element.

```jsx
// Function Component
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Or using Arrow Functions:
const Greeting = ({ name }) => <h1>Hello, {name}</h1>;
```

### 2. Class Components
The older, legacy way of writing components. They require extending `React.Component` and must contain a `render()` method.

```jsx
// Class Component
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

---

## 7. When should you use a Class Component over a Function Component?

### Short Answer:
**Almost never in modern React.** You should default to using Function components and Hooks.

### Detailed Breakdown:
*   **Historically (Before 2019):** If your component needed to manage local `state` or needed to use lifecycle methods (like `componentDidMount`), you *had* to use a Class component. Function components were "stateless" and "dumb".
*   **Modern Era (Post-Hooks):** With the introduction of React Hooks (like `useState`, `useEffect`) in version 16.8, Functional components can now do everything Class components can do, but with less boilerplate and cleaner logic.
*   **The Rare Exceptions:** The only time you *must* use a Class component today is if you need to create an **Error Boundary**. Error boundaries currently require specific lifecycle methods (`componentDidCatch` and `static getDerivedStateFromError`) which do not have a hook equivalent yet.

---

## 8. What are Pure Components?

### Definition
A **Pure Component** is a component that renders the same output for the same state and props. React provides a built-in optimization for this.

### How it works:
Instead of re-rendering every time its parent renders, a Pure Component automatically handles a `shouldComponentUpdate()` check. It performs a **shallow comparison** of previous and next props and state. If they are exactly the same, the component skips the re-render, boosting performance.

### Implementations:
*   **In Class Components:** You extend `React.PureComponent` instead of `React.Component`.
*   **In Function Components:** You wrap your component in `React.memo()`.

```jsx
// Function Component using React.memo
const MyPureComponent = React.memo(function MyComponent(props) {
  /* renders using props */
});
```
*Note: Because it uses a shallow comparison, complex deeply nested objects might cause unexpected behavior if mutated directly.*

---

## 9. What is state in React?

### Definition
**State** is a built-in React object that stores data or information about the component. 

### Characteristics:
*   **Local & Encapsulated:** State is completely private and fully controlled by the component it belongs to.
*   **Mutable:** Unlike props, state *can* and *should* change over time (usually in response to user actions, network responses, etc.).
*   **Triggers Re-Renders:** Whenever a component's state changes, React will automatically re-render that specific component to reflect the new data on the UI.

### Usage Example (Hooks):
```jsx
import React, { useState } from 'react';

function Counter() {
  // 'count' is the state variable, 'setCount' is the function to update it
  const [count, setCount] = useState(0); 

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

---

## 10. What are props in React?

### Definition
**Props** (short for "Properties") are how components communicate with each other. They allow you to pass data from a parent component down to a child component.

### Characteristics:
*   **Unidirectional:** Data via props flows in only one direction: top-down (parent to child).
*   **Read-Only (Immutable):** A child component can NEVER modify its own props. They must be treated as pure data. If data needs to change, the component must use state instead.
*   **Analogy:** Similar to arguments passed to a standard JavaScript function.

### Usage Example:
```jsx
// Parent Component passing props
function App() {
  return <ProfileCard name="Kuldeep" title="Software Engineer" />;
}

// Child Component receiving and consuming props
function ProfileCard(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>{props.title}</p>
    </div>
  );
}
```
