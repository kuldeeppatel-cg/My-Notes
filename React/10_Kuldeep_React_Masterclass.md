
---

# 🔹 React Intl Concepts (Q91–Q95)

## 91. 🌍 **Main Features of React Intl**
- Provides **internationalization (i18n)** support for React apps.
- Features:
  - 🌐 Locale management (switch languages easily).
  - 📅 Date & time formatting.
  - 💱 Number & currency formatting.
  - 📝 Message translation with placeholders.
  - ♿ Built-in support for pluralization & accessibility.

---

## 92. ✨ **Two Ways of Formatting in React Intl**
1. **Using Components** (declarative):
   - `<FormattedMessage>`, `<FormattedDate>`, `<FormattedNumber>`.
2. **Using API Functions** (imperative):
   - `intl.formatMessage()`, `intl.formatDate()`, `intl.formatNumber()`.

**Example:**
```jsx
// Declarative
<FormattedNumber value={1000} style="currency" currency="USD" />

// Imperative
intl.formatNumber(1000, { style: "currency", currency: "USD" });
```

📌 **Symbol Note**: ✨ Components = JSX, API = JS functions.

---

## 93. 📝 **Using FormattedMessage as a Placeholder**
- You can embed `<FormattedMessage>` inside attributes like `placeholder`.

**Example:**
```jsx
<input 
  placeholder={<FormattedMessage id="enterName" defaultMessage="Enter your name" />} 
/>
```

📌 **Symbol Note**: 📝 Messages can be used inside props like `placeholder`.

---

## 94. 🔍 **Access Current Locale**
- Use `useIntl()` hook or `injectIntl` HOC to access the current locale.

**Example:**
```jsx
import { useIntl } from "react-intl";

function MyComponent() {
  const intl = useIntl();
  return <p>Current locale: {intl.locale}</p>;
}
```

📌 **Symbol Note**: 🔍 `intl.locale` gives active language.

---

## 95. 📅 **Format a Date with React Intl**
- Use `<FormattedDate>` component or `intl.formatDate()`.

**Example:**
```jsx
// Declarative
<FormattedDate value={new Date()} year="numeric" month="long" day="2-digit" />

// Imperative
intl.formatDate(new Date(), { year: "numeric", month: "long", day: "2-digit" });
```

📌 **Symbol Note**: 📅 Format dates declaratively or imperatively.

---

# 🧾 Quick Cheat-Sheet Recap
- 🌍 **Features** → Locale, dates, numbers, messages, pluralization.
- ✨ **Formatting** → Components vs API functions.
- 📝 **FormattedMessage Placeholder** → Use inside attributes.
- 🔍 **Current Locale** → `intl.locale` via `useIntl`.
- 📅 **Date Formatting** → `<FormattedDate>` or `intl.formatDate`.


---

# 🔹 React Testing Concepts (Q96–Q100)

## 96. 🔍 **Shallow Renderer in React Testing**
- The **Shallow Renderer** allows you to render a component **without rendering its child components**.
- Useful for **unit testing** a component in isolation.
- Provided by `react-test-renderer/shallow`.

**Example:**
```jsx
import ShallowRenderer from "react-test-renderer/shallow";
const renderer = new ShallowRenderer();
renderer.render(<MyComponent />);
const result = renderer.getRenderOutput();
```

📌 **Symbol Note**: 🔍 Shallow = test component logic without children.

---

## 97. 🧩 **TestRenderer Package**
- `react-test-renderer` lets you render React components to a **pure JavaScript object**.
- Useful for snapshot testing and verifying component output without a DOM.

**Example:**
```jsx
import TestRenderer from "react-test-renderer";
const testInstance = TestRenderer.create(<MyComponent />);
console.log(testInstance.toJSON());
```

📌 **Symbol Note**: 🧩 TestRenderer = JSON representation of component tree.

---

## 98. 🛠️ **ReactTestUtils Package**
- Provides **utilities** for testing React components.
- Features:
  - Simulate events (`Simulate.click`, `Simulate.change`).
  - Render components into a detached DOM for testing.
- More low-level compared to libraries like Enzyme or Testing Library.

**Example:**
```jsx
import ReactTestUtils from "react-dom/test-utils";
ReactTestUtils.Simulate.click(buttonNode);
```

📌 **Symbol Note**: 🛠️ TestUtils = simulate events + low-level testing.

---

## 99. ⚡ **What is Jest?**
- Jest is a **JavaScript testing framework** developed by Facebook.
- Features:
  - Built-in test runner.
  - Snapshot testing.
  - Mocking capabilities.
  - Works seamlessly with React.

**Example:**
```jsx
test("adds 1 + 2 = 3", () => {
  expect(1 + 2).toBe(3);
});
```

📌 **Symbol Note**: ⚡ Jest = fast, integrated testing framework.

---

## 100. ✅ **Advantages of Jest over Jasmine**
- Jest is built with modern JS apps in mind, especially React.
- Advantages:
  - 🚀 Zero configuration (works out of the box).
  - 📸 Snapshot testing support.
  - 🎭 Built-in mocking.
  - ⚡ Faster test execution with parallel runs.
  - 🔄 Active community + maintained by Meta.

📌 **Symbol Note**: ✅ Jest = modern, snapshot-ready, faster than Jasmine.

---

# 🧾 Quick Cheat-Sheet Recap
- 🔍 **Shallow Renderer** → Isolated component testing.
- 🧩 **TestRenderer** → JSON output for snapshots.
- 🛠️ **TestUtils** → Simulate events, low-level testing.
- ⚡ **Jest** → Modern JS testing framework.
- ✅ **Jest vs Jasmine** → Faster, snapshot support, zero config.

---


