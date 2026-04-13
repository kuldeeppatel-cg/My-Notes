
---

# 🔹 React Interview Concepts (Q81–Q85)

## 81. 🧩 **Components of React Router v6**
React Router v6 introduced a simplified API:
- `<BrowserRouter>` → Wraps the app, enables routing.
- `<Routes>` → Replaces `<Switch>`, renders the first matching route.
- `<Route>` → Defines path-to-component mapping.
- `<Link>` / `<NavLink>` → Navigation links.
- `useNavigate` → Programmatic navigation.
- `useParams` → Access route parameters.
- `useLocation` → Access current location object.

**Example:**
```jsx
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about/:id" element={<About />} />
  </Routes>
</BrowserRouter>
```

📌 **Symbol Note**: 🧩 v6 = `<Routes>` replaces `<Switch>`.

---

## 82. 🔀 **Purpose of `push` and `replace` in History**
- `history.push(path)` → Navigates to a new route, adds entry to history stack.
- `history.replace(path)` → Navigates but **replaces current entry** (no back navigation).

**Example:**
```jsx
history.push("/home");    // Adds new entry
history.replace("/login"); // Replaces current entry
```

📌 **Symbol Note**: 🔀 Push = add, Replace = overwrite.

---

## 83. 🎯 **Programmatic Navigation in React Router v4**
- Use `this.props.history.push()` inside class components.
- Use `useHistory()` hook in functional components.

**Example (v4 functional):**
```jsx
import { useHistory } from "react-router-dom";

function MyComponent() {
  const history = useHistory();
  return <button onClick={() => history.push("/dashboard")}>Go</button>;
}
```

📌 **Symbol Note**: 🎯 `useHistory` = navigate programmatically.

---

## 84. 🔍 **Get Query Parameters in React Router v4**
- React Router v4 doesn’t parse query strings automatically.
- Use `location.search` + `URLSearchParams`.

**Example:**
```jsx
import { useLocation } from "react-router-dom";

function MyComponent() {
  const { search } = useLocation();
  const query = new URLSearchParams(search);
  const id = query.get("id");
  return <p>ID: {id}</p>;
}
```

📌 **Symbol Note**: 🔍 `URLSearchParams` = query parsing.

---

## 85. ⚠️ **"Router may have only one child element" Warning**
- In React Router, `<Router>` must have **exactly one child**.
- If you return multiple elements, wrap them in a single parent (like `<Routes>` or `<div>`).

**Example (Fix):**
```jsx
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
  </Routes>
</BrowserRouter>
```

📌 **Symbol Note**: ⚠️ Always wrap multiple routes/components inside one parent.

---

# 🧾 Quick Cheat-Sheet Recap
- 🧩 **Router v6 Components** → `<Routes>`, `<Route>`, hooks (`useNavigate`, `useParams`).
- 🔀 **Push vs Replace** → Add vs overwrite history.
- 🎯 **Programmatic Navigation (v4)** → `useHistory` or `this.props.history.push`.
- 🔍 **Query Params (v4)** → `URLSearchParams(location.search)`.
- ⚠️ **Router Warning** → Only one child, wrap with `<Routes>`.

---

# 🔹 React Interview Concepts (Q86–Q90)

## 86. 📦 **Passing Params with `history.push` (React Router v4)**
- You can pass **state or params** when navigating with `history.push`.
- Params are passed as an object.

**Example:**
```jsx
// Passing params
history.push({
  pathname: "/profile",
  state: { userId: 123 }
});

// Accessing params
this.props.location.state.userId
```

📌 **Symbol Note**: 📦 Params go inside the `state` object.

---

## 87. 🚧 **Implementing a Default / NotFound Page**
- Use a `<Route>` with no matching path or a wildcard (`*` in v6).
- Place it last inside `<Routes>`.

**Example (v6):**
```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```

📌 **Symbol Note**: 🚧 Wildcard route = catch-all for 404 pages.

---

## 88. 🎯 **Getting History in React Router v4**
- In v4, history is available via:
  - `this.props.history` in class components.
  - `useHistory()` hook in functional components.

**Example:**
```jsx
import { useHistory } from "react-router-dom";

function MyComponent() {
  const history = useHistory();
  return <button onClick={() => history.push("/home")}>Go Home</button>;
}
```

📌 **Symbol Note**: 🎯 `useHistory` = direct access to navigation API.

---

## 89. 🔐 **Automatic Redirect After Login**
- After successful login, use `history.push()` or `<Navigate>` (v6).
- Commonly done inside login handler.

**Example (v6):**
```jsx
import { Navigate } from "react-router-dom";

function Login({ isLoggedIn }) {
  if (isLoggedIn) {
    return <Navigate to="/dashboard" />;
  }
  return <LoginForm />;
}
```

📌 **Symbol Note**: 🔐 Redirect ensures secure flow after authentication.

---

## 90. 🌍 **What is React Intl?**
- **React Intl** is a library for **internationalization (i18n)** in React.
- Provides components and APIs for:
  - Formatting dates, numbers, currencies.
  - Handling translations.
  - Managing locale-specific messages.

**Example:**
```jsx
import { IntlProvider, FormattedMessage } from "react-intl";

<IntlProvider locale="en" messages={{ hello: "Hello, Kuldeep!" }}>
  <FormattedMessage id="hello" />
</IntlProvider>
```

📌 **Symbol Note**: 🌍 React Intl = localization + formatting for global apps.

---

# 🧾 Quick Cheat-Sheet Recap
- 📦 **Params in history.push** → Pass via `state`.
- 🚧 **NotFound Page** → Use wildcard route (`*`).
- 🎯 **Get History (v4)** → `useHistory` or `this.props.history`.
- 🔐 **Redirect After Login** → `Navigate` or `history.push`.
- 🌍 **React Intl** → Internationalization library for translations, dates, numbers.

---

