# Reactjs_16-features-now

Here’s a **Topmate session description** focused on **React 16 Features** — ideal for those learning or preparing for interviews.

Here’s a complete list of **React 16 features**, introduced between versions 16.0 to 16.13:

---

## ✅ **Full List of React 16 Features**

### 🔁 **1. Fiber Architecture (16.0)**

* Complete rewrite of the core engine
* Enables async rendering, prioritization, and better scheduling

### 💥 **2. Error Boundaries (16.0)**

* Use `componentDidCatch` and `getDerivedStateFromError` to catch and handle errors in render lifecycle

### 🌐 **3. Portals (16.0)**

* `ReactDOM.createPortal()` renders elements outside the root DOM tree (e.g., for modals)

### 🧩 **4. Fragments (16.2)**

* Return multiple elements without extra DOM nodes (`<>...</>`)

### 🧱 **5. Return Arrays and Strings from `render()` (16.0)**

* No need to wrap siblings in a `<div>`

### 🔄 **6. New Context API (Stable in 16.3)**

* `React.createContext()` – cleaner state sharing without prop drilling

### ⚙️ **7. getDerivedStateFromProps Lifecycle (16.3)**

* Static method to derive state updates from props

### 🚫 **8. getSnapshotBeforeUpdate Lifecycle (16.3)**

* Capture scroll position or DOM state before the update happens

### 🔄 **9. `componentDidCatch()` (16.0)**

* Used in Error Boundaries to log and handle errors

### 📦 **10. Support for Custom DOM Attributes (16.0)**

* You can pass non-standard props (e.g., `data-id`, `custom-attr`) to DOM elements without React filtering them

### 🧪 **11. React.StrictMode (16.3)**

* Helps detect unsafe lifecycles, legacy API usage, and side effects

### 🛑 **12. Deprecation of Legacy Lifecycle Methods (16.3–16.9)**

* `componentWillMount`, `componentWillReceiveProps`, and `componentWillUpdate` were marked as UNSAFE\_

### 🔥 **13. Concurrent Mode (Experimental in 16.9+)**

* Opt-in feature for interruptible rendering (later fully released in React 18)

### 🧼 **14. Lifecycle Method Cleanup (16.3+)**

* Encouragement to migrate to safer lifecycles (`getDerivedStateFromProps`, `getSnapshotBeforeUpdate`)

### 🧪 **15. Hook Introduction in React DOM (16.8)**

* `useState`, `useEffect`, `useContext`, etc. introduced (though not a class feature)




### ✅ **Short Description**

**React 16 Features Explained**
Understand key React 16 features like Error Boundaries, Portals, Fragments, Context API, and async rendering with real-world code examples.

---

### 📘 **Long Description**

**⚛️ React 16 Deep Dive – 1:1 Learning Session**

React 16 introduced powerful features that laid the foundation for modern React development. In this session, I’ll guide you through each one with live code and practical use cases.

### 🔍 Key Topics:

* **Error Boundaries** – gracefully catch UI crashes
* **Portals** – render modals/tooltips outside root DOM
* **Fragments** – avoid extra DOM wrappers
* **Context API (New)** – manage state without prop drilling
* **Async Rendering & Fiber Architecture** – how React reconciles faster
* **componentDidCatch** lifecycle
* **New core architecture (Fiber)** – the engine behind concurrent UI

💡 Ideal for:

* React developers upgrading from older versions
* Interview prep (React internals)
* Building production-ready apps with React 16+

Great! Let’s do a **deep dive into all React 16 features** with clear explanations and examples. React 16 was a foundational release introducing **Fiber**, **error handling**, **portals**, **fragments**, and more.

---

## ⚛️ 1. **Fiber Architecture (Core Rewrite)**

**What it is:** React 16 was completely rewritten with **Fiber**, a new reconciliation engine to improve performance and allow async rendering.

### 🔍 Key Benefits:

* Incremental rendering
* Better error handling
* Priority-based updates (scheduling)

### 🧠 Example:

With Fiber, React can pause work and resume later, improving responsiveness for large UI trees.

```jsx
// React will break this down into async units of work
<MyBigList data={hugeDataset} />
```

You don't write anything new—**Fiber just changes how React handles updates internally**.

---

## 💥 2. **Error Boundaries**

**What it is:** Before React 16, UI errors would break the entire component tree. Now, you can **catch JavaScript errors in components and show fallback UIs**.

### 🔧 Usage:

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.log(error, info);
  }

  render() {
    return this.state.hasError ? <h1>Something went wrong.</h1> : this.props.children;
  }
}
```

### ✅ Wrap usage:

```jsx
<ErrorBoundary>
  <ProblematicComponent />
</ErrorBoundary>
```

---

## 🌌 3. **Portals**

**What it is:** Lets you render children into a **DOM node outside the parent hierarchy** — perfect for modals, tooltips.

### 🔧 Usage:

```jsx
ReactDOM.createPortal(child, container)
```

### ✅ Example:

```jsx
const Modal = () => {
  return ReactDOM.createPortal(
    <div className="modal">I'm a modal!</div>,
    document.getElementById('modal-root') // outside of main app root
  );
};
```

---

## 🧩 4. **Fragments**

**What it is:** Lets you group children **without adding extra DOM nodes**.

### ✅ Instead of:

```jsx
<div>
  <h1>Hello</h1>
  <p>World</p>
</div>
```

### Use:

```jsx
<React.Fragment>
  <h1>Hello</h1>
  <p>World</p>
</React.Fragment>

// Or shorthand
<>
  <h1>Hello</h1>
  <p>World</p>
</>
```

---

## 🔄 5. **Improved Server-Side Rendering (SSR)**

React 16 brought a complete rework of SSR with `renderToNodeStream`, allowing **streaming of HTML content** for faster TTFB (time to first byte).

### 🧠 Benefit:

Faster page loads for large SSR apps.

---

## 🌐 6. **New Context API (Stable in 16.3)**

**What it is:** A better way to share state without prop drilling.

### 🔧 Setup:

```jsx
const ThemeContext = React.createContext('light');

// Provide
<ThemeContext.Provider value="dark">
  <Toolbar />
</ThemeContext.Provider>

// Consume
const ThemedButton = () => {
  const theme = useContext(ThemeContext);
  return <button className={theme}>Click me</button>;
};
```

Much cleaner than `contextTypes` used in React 15.

---

## 🎯 7. **Support for Returning Arrays/Strings in render()**

In React 16, `render()` no longer requires a single parent node.

### ✅ Example:

```jsx
render() {
  return ['Item 1', 'Item 2'];
}
```

---

## 📉 8. **Reduced Bundle Size**

React 16 reduced the core size and removed legacy features, making apps faster.

---

## 🧪 9. **componentDidCatch Lifecycle**

Specific to error boundaries, it captures error info in class components.

```jsx
componentDidCatch(error, info) {
  logErrorToMyService(error, info);
}
```

---

## 🚨 10. **Custom DOM Attributes**

React 16 allows you to pass **non-standard attributes** without warnings.

```jsx
<div data-id="123" custom-attr="yes" />
```

---

## Summary Table

| Feature               | Purpose                 | Real-World Use                     |
| --------------------- | ----------------------- | ---------------------------------- |
| **Fiber**             | Core rendering engine   | Async rendering, better scheduling |
| **Error Boundaries**  | Catch UI crashes        | Wrap risky components              |
| **Portals**           | Render outside root     | Modals, overlays                   |
| **Fragments**         | Group without extra DOM | Clean markup                       |
| **Context API**       | Share state across tree | Theme, Auth, Language              |
| **Render Arrays**     | Multiple children       | Lists, no wrappers                 |
| **SSR Improvements**  | Faster server render    | Streaming HTML                     |
| **Custom Attributes** | Flexibility             | 3rd-party libs                     |
| **componentDidCatch** | Handle crashes          | Logging, fallback UI               |

Here’s a complete list of **React 16 features**, introduced between versions 16.0 to 16.13:

---

Here's a **deep dive into React Fiber Architecture**, its goals, how it works internally, and why it was a game-changer for React starting from **v16**:

---

## 🔁 **React Fiber Architecture (Introduced in React 16)**

### 🧠 **What is Fiber?**

React Fiber is the **reimplementation of the React core algorithm**—responsible for **reconciliation**, **rendering**, and **scheduling**.

It replaced the old "stack-based" algorithm with a **linked list-based structure** that supports **incremental rendering**.

---

## 🎯 Goals of Fiber

1. **Incremental rendering** — break rendering work into small units.
2. **Prioritization** — high-priority updates (e.g., user input) interrupt low-priority ones.
3. **Concurrency** — pause and resume rendering work.
4. **Better error handling** — introduced `componentDidCatch`.
5. **Backwards compatibility** — kept the public API the same.

---

## ⚙️ Fiber as a Data Structure

Each element in the virtual DOM tree becomes a **Fiber Node**, forming a **linked list**:

```ts
type FiberNode = {
  type: string | FunctionComponent;
  child: FiberNode;
  sibling: FiberNode;
  return: FiberNode;
  alternate: FiberNode; // previous fiber
  effectTag: string;
  stateNode: DOMElement | Component;
};
```

### 🔁 Instead of recursive depth-first traversal (old), Fiber uses:

* A **linked list of fibers** (one per component/DOM element)
* Enables **pause-resume** and **priority-based updates**

---

## 🔄 Example: Prioritized Updates

```jsx
<button onClick={() => setCount(count + 1)}>Click</button>
<BigSlowComponent />
```

With Fiber, React can **pause rendering** `BigSlowComponent` if a button click needs immediate feedback — and **continue rendering later** without restarting.

---

## 🧬 Fiber Phases

1. **Render Phase (Reconciliation):**

   * Build a new fiber tree
   * Compare with previous fiber tree (diffing)
   * Mark changes (effects)

2. **Commit Phase:**

   * Apply DOM changes
   * Run lifecycle methods like `componentDidMount`

---

## 🧪 Real Benefits of Fiber

| Feature                         | Benefit                              |
| ------------------------------- | ------------------------------------ |
| Interruptible rendering         | Improves responsiveness              |
| Time slicing (future)           | Scheduling work across frames        |
| Better error handling           | `componentDidCatch()` support        |
| Concurrent rendering foundation | Enables React 18 features            |
| Animation priority              | Schedule animation frames separately |

---

## 🎨 Visual: Fiber Node Tree

```
App
├── Header
├── Main
│   ├── Sidebar
│   └── Content
└── Footer
```

In Fiber:

* Each node is a `Fiber` with links to:

  * `.child` → first child
  * `.sibling` → next sibling
  * `.return` → parent

This structure allows React to **traverse and pause/resume** easily.

---

## 🧩 Summary

React Fiber:

* Rewrote React internals in React 16
* Introduced fine-grained control over rendering
* Enables key future features (concurrent rendering, Suspense, etc.)

📘 **Still hidden from the developer** — but **powerful under the hood**

Absolutely! Let’s walk through **practical examples** that show the impact of **React Fiber** and how its core ideas (async rendering, prioritization, etc.) play out — even if **you don’t directly interact with Fiber**.

---

## ⚙️ Example 1: **Simulating a Slow Component**

Before Fiber, slow rendering would block the entire UI.

### 🧪 Without Prioritization (Old React ≤15)

```jsx
const BigList = () => {
  let items = [];
  for (let i = 0; i < 10000; i++) {
    items.push(<div key={i}>Item #{i}</div>);
  }
  return <div>{items}</div>;
};

function App() {
  const [clicked, setClicked] = useState(false);
  return (
    <div>
      <button onClick={() => setClicked(true)}>Click Me</button>
      <BigList />
    </div>
  );
}
```

> ❌ Clicking the button becomes unresponsive until the `BigList` fully renders.

---

### ✅ With React Fiber (v16+)

React internally **splits rendering work** and prioritizes the click over `BigList`. So even if `BigList` is huge, the button click is responsive.

```jsx
// Same code as above, but React Fiber will now prioritize the button update
```

✅ **Result:** You can interact with the UI **while the list renders**, especially in **React 18** with **Concurrent Mode**.

---

## 🌀 Example 2: **Suspense for Lazy Loading (Built on Fiber)**

Fiber enabled suspending parts of the tree during async operations.

```jsx
import React, { Suspense, lazy } from "react";

const LazyProfile = lazy(() => import('./Profile'));

function App() {
  return (
    <Suspense fallback={<div>Loading profile...</div>}>
      <LazyProfile />
    </Suspense>
  );
}
```

✅ **Fiber’s power:** Allows rendering of fallback (`<div>Loading…`) **while `Profile` is still loading**, and resumes rendering later.

---

## 🔁 Example 3: **Error Boundaries in Action (Enabled by Fiber)**

Fiber introduced `componentDidCatch`:

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error(error, info);
  }

  render() {
    return this.state.hasError ? <h2>Crash! Recovered.</h2> : this.props.children;
  }
}

function BuggyComponent() {
  throw new Error('Boom!');
}

function App() {
  return (
    <ErrorBoundary>
      <BuggyComponent />
    </ErrorBoundary>
  );
}
```

✅ **React Fiber lets the app continue rendering other components** even if one crashes.

---

## 🧠 Recap of Concepts Used in Examples

| Concept                 | Enabled By Fiber | Example                      |
| ----------------------- | ---------------- | ---------------------------- |
| Async Rendering         | ✅                | BigList doesn’t block button |
| Interruptible Work      | ✅                | UI stays responsive          |
| Suspense / Lazy Loading | ✅                | Lazy `Profile` example       |
| Error Recovery          | ✅                | Error Boundary example       |
| Fine-Grained Scheduling | ✅                | Prioritize user input        |

Here's a complete deep dive into **Error Boundaries in React 16**, including **what they are, when to use them, how to implement them, and examples**:

---

## 💥 **Error Boundaries (React 16.0)**

### 🔍 What are Error Boundaries?

**Error Boundaries** are React components that catch **JavaScript errors** anywhere in their child component tree, **log those errors**, and **display a fallback UI** instead of crashing the whole app.

> Without them, any rendering error breaks the entire React tree.

---

## 🚨 Why Were They Introduced?

Prior to React 16, if any component threw an error during render, the **entire app crashed**. React 16's **Fiber architecture** introduced better error recovery.

---

## ⚙️ How They Work

Error Boundaries catch errors during:

* Rendering
* Lifecycle methods
* Constructors of the child components

They **do NOT** catch:

* Event handlers (you must use try-catch manually there)
* Async code (like `setTimeout`)
* Server-side rendering
* Errors outside the React tree

---

## 🧱 Implementing an Error Boundary

You create a class component with two special lifecycle methods:

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    // Update state so next render shows fallback
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // Log error to a monitoring service
    console.error("Error caught by boundary:", error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h2>Oops! Something went wrong.</h2>;
    }

    return this.props.children;
  }
}
```

---

## 🧪 Example Usage

```jsx
function BuggyComponent() {
  throw new Error('💥 Crashed!');
}

function App() {
  return (
    <div>
      <h1>My App</h1>
      <ErrorBoundary>
        <BuggyComponent />
      </ErrorBoundary>
    </div>
  );
}
```

✅ The error is isolated. Only the part inside `ErrorBoundary` fails — the rest of the app keeps working.

---

## 🧠 Best Practices

| Tip                        | Description                                                    |
| -------------------------- | -------------------------------------------------------------- |
| Create multiple boundaries | Wrap specific sections, not the whole app                      |
| Show fallback UI           | Provide helpful recovery info to users                         |
| Log errors                 | Integrate with tools like Sentry or LogRocket                  |
| Don’t use hooks            | Only class components can be error boundaries (as of React 18) |

---

## 🔮 Future Note

React is exploring ways to support **error boundaries with hooks** in future versions (experimental APIs).

Here’s a complete deep dive into **Portals in React 16.0**, including **definition, use cases, example code, and how it works under the hood**:

---

## 🌐 **Portals (Introduced in React 16.0)**

### 🔍 What are Portals?

**Portals** let you render a React component's output **into a different part of the DOM tree** than its parent — typically **outside the main app root**.

> Useful for modals, tooltips, dropdowns, and overlays that shouldn't be constrained by parent styles like `overflow: hidden`.

---

## 🧠 Why Use Portals?

Without portals, rendering a modal inside a deeply nested component can cause issues with:

* Z-index stacking
* CSS overflow/clipping
* Positioning logic

Portals solve this by rendering **outside the component hierarchy**.

---

## 🧱 Basic Usage

### ✅ HTML structure (index.html):

```html
<div id="root"></div>
<div id="modal-root"></div>
```

### ✅ React code:

```jsx
import ReactDOM from 'react-dom';

function Modal({ children }) {
  return ReactDOM.createPortal(
    <div className="modal">{children}</div>,
    document.getElementById('modal-root')
  );
}

function App() {
  return (
    <div>
      <h1>My App</h1>
      <Modal>
        <p>This is rendered outside the #root!</p>
      </Modal>
    </div>
  );
}
```

---

## ⚙️ How It Works Internally

ReactDOM’s `createPortal(child, container)`:

* `child` → JSX to render
* `container` → DOM node to render into (e.g., `#modal-root`)

React maintains event bubbling — meaning **clicks, keypresses inside the Portal still bubble to React’s root tree**.

---

## 🎯 Real-World Use Cases

| Use Case            | Benefit                                  |
| ------------------- | ---------------------------------------- |
| Modals              | Not clipped by parent `overflow: hidden` |
| Tooltips            | Easily position on top of any element    |
| Dropdowns           | Escape parent stacking context           |
| Toast notifications | Attach to global notification root       |

---

## 🔐 Best Practices

* Ensure portal DOM containers (e.g., `#modal-root`) are always present in your HTML.
* Handle **focus trapping** and **ARIA roles** for accessibility in modals.

---

## 📌 Summary

| Feature    | Value                                     |
| ---------- | ----------------------------------------- |
| What?      | Render elements outside the root DOM node |
| How?       | `ReactDOM.createPortal(child, container)` |
| Works with | All React children (components, elements) |
| Benefits   | UI layering, Z-index fixes, better UX     |


Absolutely! Here's a full **React Portals (16.0)** deep dive **with a working example**:

---

## 🌐 **React Portals (Introduced in React 16.0)**

### 🔍 What is a Portal?

A **portal** allows you to render a component into a **different part of the DOM tree** outside your React app’s root — perfect for modals, tooltips, and overlays.

---

## 📦 Real Example: Modal using Portal

### 🗂 **HTML Setup (public/index.html)**

```html
<body>
  <div id="root"></div>
  <div id="modal-root"></div> <!-- separate DOM target for portal -->
</body>
```

---

### ⚛️ **React Code (App.jsx)**

```jsx
import ReactDOM from "react-dom";
import React, { useState } from "react";

// Modal component using Portal
function Modal({ children, onClose }) {
  return ReactDOM.createPortal(
    <div style={modalStyle}>
      <div style={modalContentStyle}>
        {children}
        <button onClick={onClose}>Close</button>
      </div>
    </div>,
    document.getElementById("modal-root")
  );
}

// Main App
function App() {
  const [show, setShow] = useState(false);

  return (
    <div>
      <h1>React Portal Demo</h1>
      <button onClick={() => setShow(true)}>Open Modal</button>

      {show && (
        <Modal onClose={() => setShow(false)}>
          <p>This is inside a portal!</p>
        </Modal>
      )}
    </div>
  );
}

// Some basic styling
const modalStyle = {
  position: "fixed",
  top: 0, left: 0, right: 0, bottom: 0,
  background: "rgba(0,0,0,0.6)",
  display: "flex",
  alignItems: "center",
  justifyContent: "center"
};

const modalContentStyle = {
  background: "#fff",
  padding: "2rem",
  borderRadius: "8px",
  minWidth: "300px"
};

export default App;
```

---

### ✅ What This Does:

* Clicking "Open Modal" shows a modal rendered **outside** the `#root` in `#modal-root`.
* Despite being outside, events like `onClick` still **bubble up through React** normally.
* Solves z-index and overflow issues.

---

## 📌 Summary

| Feature       | Value                                |
| ------------- | ------------------------------------ |
| API           | `ReactDOM.createPortal()`            |
| Use Case      | Modals, tooltips, dropdowns, toasts  |
| Benefits      | DOM flexibility + React event system |
| React Version | 16.0+                                |


Here’s a complete deep dive into **“Return Arrays and Strings from `render()`”** — a feature introduced in **React 16.0**, with clear explanation and practical examples:

---

## 🧱 **Return Arrays and Strings from `render()` (React 16.0)**

### 🔍 What Changed?

Before React 16, the `render()` method **had to return a single root element** (e.g., a `<div>`). React 16 removed this restriction.

You can now return:

* **Multiple elements** (as an array)
* **Plain strings**

✅ **No need to wrap everything in extra `<div>`s**.

---

## 🎯 Why It Matters

This improves:

* **Cleaner markup** (no unnecessary DOM nesting)
* **More flexibility** for rendering list-like structures

---

## 🔧 Example 1: Returning an Array of Elements

```jsx
function List() {
  return [
    <li key="1">Item One</li>,
    <li key="2">Item Two</li>,
    <li key="3">Item Three</li>
  ];
}

function App() {
  return (
    <ul>
      <List />
    </ul>
  );
}
```

✅ **Result:** No wrapper `<div>` — direct siblings returned as an array.

> 📝 **Keys are mandatory** when returning arrays to help React with reconciliation.

---

## 🔧 Example 2: Returning a String from `render()`

```jsx
function Welcome() {
  return "Hello, React 16!";
}

function App() {
  return (
    <div>
      <Welcome />
    </div>
  );
}
```

✅ **Result:** Renders plain text `"Hello, React 16!"` directly into the DOM.

---

## 🔁 Comparison Before vs After React 16

| Before React 16                           | After React 16                          |
| ----------------------------------------- | --------------------------------------- |
| `render()` must return one root element   | Can return multiple elements or strings |
| Required extra wrapper like `<div>`       | Cleaner JSX, no extra DOM               |
| Throws error for multiple top-level nodes | Works natively without issues           |

---

## 🧠 Use Cases

* Rendering **table rows** without wrapper `<tr>`
* Creating **inline lists** or text segments
* Avoiding **unnecessary divs** in the DOM tree

Great! Let’s now deep dive into **Fragments (React 16.2)** — what they are, why they matter, and how to use them effectively.

---

## 🧩 **Fragments (Introduced in React 16.2)**

### 🔍 What Are Fragments?

**Fragments** let you group multiple JSX elements **without adding an extra node** to the DOM — unlike wrapping everything in a `<div>`.

> ✅ Cleaner markup, better layout control, and no unnecessary nesting.

---

## 🧱 Why Use Fragments?

Before React 16.2:

```jsx
return (
  <div>
    <h1>Title</h1>
    <p>Description</p>
  </div>
);
```

👎 Adds an extra `<div>` to the DOM unnecessarily.

With **Fragments**:

```jsx
return (
  <>
    <h1>Title</h1>
    <p>Description</p>
  </>
);
```

👍 No extra DOM node!

---

## 🔧 Example 1: Using Short Syntax (`<>...</>`)

```jsx
function Info() {
  return (
    <>
      <h2>User Info</h2>
      <p>React version: 16.2+</p>
    </>
  );
}
```

### ✅ Resulting DOM:

```html
<h2>User Info</h2>
<p>React version: 16.2+</p>
```

---

## 🔧 Example 2: Named Fragment with `key` (React.Fragment)

Use `React.Fragment` when you need to assign a `key` (e.g., inside `.map()`):

```jsx
const items = ['One', 'Two', 'Three'];

function List() {
  return items.map((item, i) => (
    <React.Fragment key={i}>
      <dt>{item}</dt>
      <dd>Description of {item}</dd>
    </React.Fragment>
  ));
}
```

---

## 🧠 When to Use Fragments

| Use Case                   | Benefit                      |
| -------------------------- | ---------------------------- |
| Grouping children          | Without adding extra nodes   |
| Table rows (`<tr>`)        | Valid HTML structure         |
| Avoiding CSS/layout issues | Prevent unnecessary wrappers |
| List rendering with `key`  | Use `React.Fragment`         |

---

## ✅ Summary

| Feature   | Fragments                             |
| --------- | ------------------------------------- |
| Syntax    | `<></>` or `<React.Fragment>`         |
| Version   | React 16.2+                           |
| Key prop? | Only with `<React.Fragment>`          |
| Purpose   | Group children without extra DOM node |


Here’s a complete working **React Context API (React 16.3+)** project demonstrating theme switching using the **new Context API** — includes all files you need.

---

### 🗂️ Folder Structure

```
my-app/
├── public/
│   └── index.html
├── src/
│   ├── App.js
│   ├── ThemeContext.js
│   ├── Toolbar.js
│   └── ThemedButton.js
└── index.js
```

---

### 📄 `public/index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>React Context Demo</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

---

### 📄 `src/index.js`

```js
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

---

### 📄 `src/ThemeContext.js`

```js
import React from "react";

const ThemeContext = React.createContext("light"); // default value

export default ThemeContext;
```

---

### 📄 `src/App.js`

```js
import React, { useState } from "react";
import ThemeContext from "./ThemeContext";
import Toolbar from "./Toolbar";

function App() {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () =>
    setTheme((prev) => (prev === "light" ? "dark" : "light"));

  return (
    <ThemeContext.Provider value={theme}>
      <div className={`app ${theme}`}>
        <h1>React 16 Context API Demo</h1>
        <button onClick={toggleTheme}>Toggle Theme</button>
        <Toolbar />
      </div>
    </ThemeContext.Provider>
  );
}

export default App;
```

---

### 📄 `src/Toolbar.js`

```js
import React from "react";
import ThemedButton from "./ThemedButton";

function Toolbar() {
  return (
    <div>
      <h2>Toolbar Section</h2>
      <ThemedButton />
    </div>
  );
}

export default Toolbar;
```

---

### 📄 `src/ThemedButton.js`

```js
import React, { useContext } from "react";
import ThemeContext from "./ThemeContext";

function ThemedButton() {
  const theme = useContext(ThemeContext);

  const style = {
    backgroundColor: theme === "dark" ? "#333" : "#eee",
    color: theme === "dark" ? "#fff" : "#000",
    padding: "10px 20px",
    border: "none",
    borderRadius: "5px"
  };

  return <button style={style}>Styled by {theme} theme</button>;
}

export default ThemedButton;
```

---

### ✅ Result

* Toggle between light and dark themes.
* `ThemedButton` reads theme **from context** — no props needed.


Perfect! Here's an **advanced React Context API example** using the following:

✅ Multiple Contexts
✅ Theme switching + Authentication handling
✅ Custom `useTheme()` and `useAuth()` hooks
✅ Real-world layout with Navbar + Protected Content

---

### 🗂️ Folder Structure

```
advanced-context-app/
├── public/
│   └── index.html
├── src/
│   ├── index.js
│   ├── App.js
│   ├── context/
│   │   ├── ThemeContext.js
│   │   └── AuthContext.js
│   ├── hooks/
│   │   ├── useTheme.js
│   │   └── useAuth.js
│   ├── components/
│   │   ├── Navbar.js
│   │   └── Dashboard.js
└── styles.css
```

---

## 📄 `public/index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>React Advanced Context</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

---

## 📄 `src/index.js`

```js
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import "./styles.css";

ReactDOM.render(<App />, document.getElementById("root"));
```

---

## 📄 `src/App.js`

```js
import React from "react";
import { ThemeProvider } from "./context/ThemeContext";
import { AuthProvider } from "./context/AuthContext";
import Navbar from "./components/Navbar";
import Dashboard from "./components/Dashboard";

function App() {
  return (
    <ThemeProvider>
      <AuthProvider>
        <Navbar />
        <Dashboard />
      </AuthProvider>
    </ThemeProvider>
  );
}

export default App;
```

---

## 📄 `src/context/ThemeContext.js`

```js
import React, { createContext, useState } from "react";

export const ThemeContext = createContext();

export const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () =>
    setTheme((prev) => (prev === "light" ? "dark" : "light"));

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      <div className={theme}>{children}</div>
    </ThemeContext.Provider>
  );
};
```

---

## 📄 `src/context/AuthContext.js`

```js
import React, { createContext, useState } from "react";

export const AuthContext = createContext();

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);

  const login = (username) => setUser({ name: username });
  const logout = () => setUser(null);

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};
```

---

## 📄 `src/hooks/useTheme.js`

```js
import { useContext } from "react";
import { ThemeContext } from "../context/ThemeContext";

export default function useTheme() {
  return useContext(ThemeContext);
}
```

---

## 📄 `src/hooks/useAuth.js`

```js
import { useContext } from "react";
import { AuthContext } from "../context/AuthContext";

export default function useAuth() {
  return useContext(AuthContext);
}
```

---

## 📄 `src/components/Navbar.js`

```js
import React from "react";
import useTheme from "../hooks/useTheme";
import useAuth from "../hooks/useAuth";

function Navbar() {
  const { theme, toggleTheme } = useTheme();
  const { user, login, logout } = useAuth();

  return (
    <nav className="navbar">
      <span>🌐 React Advanced Context</span>
      <div>
        <button onClick={toggleTheme}>
          Switch to {theme === "light" ? "dark" : "light"} mode
        </button>
        {user ? (
          <>
            <span>👤 {user.name}</span>
            <button onClick={logout}>Logout</button>
          </>
        ) : (
          <button onClick={() => login("Hari")}>Login</button>
        )}
      </div>
    </nav>
  );
}

export default Navbar;
```

---

## 📄 `src/components/Dashboard.js`

```js
import React from "react";
import useAuth from "../hooks/useAuth";

function Dashboard() {
  const { user } = useAuth();

  return (
    <div className="dashboard">
      {user ? (
        <h2>Welcome, {user.name}! 🎉 You’re authenticated.</h2>
      ) : (
        <h2>Please login to access the dashboard 🔐</h2>
      )}
    </div>
  );
}

export default Dashboard;
```

---

## 📄 `src/styles.css`

```css
body {
  margin: 0;
  font-family: sans-serif;
}

.light {
  background: #f9f9f9;
  color: #111;
}

.dark {
  background: #111;
  color: #f9f9f9;
}

.navbar {
  display: flex;
  justify-content: space-between;
  background: #444;
  color: white;
  padding: 1rem;
}

.dashboard {
  padding: 2rem;
}

button {
  margin-left: 1rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
}
```

---

## ✅ Features in Action

* 🔄 Theme toggle with context (`ThemeContext`)
* 👤 Auth login/logout with context (`AuthContext`)
* 🧠 Custom `useTheme()` and `useAuth()` hooks
* 🎯 Conditional rendering in Dashboard

Here are the **top React Context API interview questions** with **concise, correct answers**, ideal for React 16.3+:

---

### ✅ 1. **What is the Context API in React?**

**Answer:**
Context API is a way to pass data through the component tree without manually passing props at every level. It enables global state sharing.

---

### ✅ 2. **When should you use Context in React?**

**Answer:**
Use Context for **global data** like authenticated user, theme, locale, or app config — data needed by many components at different levels.

---

### ✅ 3. **What are the main components of the Context API?**

**Answer:**

1. `React.createContext()` – creates the context
2. `<Context.Provider>` – supplies the data
3. `useContext(Context)` – accesses the data (or `<Context.Consumer>` in class components)

---

### ✅ 4. **Can you update context data?**

**Answer:**
Yes. You can pass state and updater functions (like `useState`) through the Provider and modify them in child components.

---

### ✅ 5. **How is Context different from Redux?**

**Answer:**

| Context API                      | Redux                                   |
| -------------------------------- | --------------------------------------- |
| Built-in                         | External library                        |
| For small to medium global state | Great for large apps with complex state |
| Simple setup                     | More boilerplate                        |
| No middleware support            | Supports middleware like thunk/saga     |

---

### ✅ 6. **How do you use multiple contexts?**

**Answer:**

Wrap Providers:

```jsx
<AuthProvider>
  <ThemeProvider>
    <App />
  </ThemeProvider>
</AuthProvider>
```

Access them individually via `useContext()` in child components.

---

### ✅ 7. **What are some common pitfalls with Context API?**

**Answer:**

* Overusing context can lead to unnecessary re-renders.
* Large context objects break component separation.
* Updating deep-nested values can get complex.

---

### ✅ 8. **How do you avoid performance issues with Context?**

**Answer:**

* Split large contexts into smaller ones (AuthContext, ThemeContext, etc.)
* Use memoization or selectors.
* Avoid passing unnecessary props via context.

---

### ✅ 9. **Does using Context API cause re-renders?**

**Answer:**
Yes. **Any change in the `value` prop of `<Provider>` re-renders all consumers**. Optimize with `React.memo` and context splitting.

---

### ✅ 10. **Can you use Context in class components?**

**Answer:**
Yes, with `Context.Consumer` or `this.context` if the context is assigned via `static contextType`.

```jsx
static contextType = ThemeContext;
```

Here’s a complete **deep dive into the New Context API** introduced in **React 16.3**, including what changed, why it matters, how to use it, real examples, and interview essentials.

---

## 🌐 **New Context API (React 16.3)**

### 🔍 What Is It?

The **new Context API** provides a cleaner, more reliable way to **share global state** (like themes, authentication, or language) **without prop drilling**.

> 🔄 Replaces the old `contextTypes`, `childContextTypes` API — which was unstable and discouraged.

---

## 🎯 Key Features

| Feature                 | Description                        |
| ----------------------- | ---------------------------------- |
| `React.createContext()` | Create a new context               |
| `<Context.Provider>`    | Supply context value               |
| `<Context.Consumer>`    | Read context (class components)    |
| `useContext(Context)`   | Read context (function components) |

---

## ✅ Simple Real-World Example

### 1️⃣ Create a Context

```jsx
import React from 'react';
const ThemeContext = React.createContext("light");
export default ThemeContext;
```

---

### 2️⃣ Provide Context Value

```jsx
import ThemeContext from './ThemeContext';

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```

---

### 3️⃣ Consume Context with `useContext()`

```jsx
import React, { useContext } from 'react';
import ThemeContext from './ThemeContext';

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button className={theme}>I’m styled by {theme} theme</button>;
}
```

✅ **No props drilling needed** from `App → Toolbar → ThemedButton`.

---

## 🧠 Class Component Alternative

```jsx
class ThemedButton extends React.Component {
  static contextType = ThemeContext;
  render() {
    return <button className={this.context}>Class theme: {this.context}</button>;
  }
}
```

---

## 🚀 Advanced Use Cases

| Use Case        | Description                              |
| --------------- | ---------------------------------------- |
| AuthContext     | Manage login/logout, user state globally |
| ThemeContext    | Toggle between light and dark themes     |
| LocaleContext   | Internationalization support             |
| SettingsContext | Manage app-wide preferences              |

---

## ⚠️ Common Pitfalls

* 🧨 **Re-render on every value change**: Every consumer re-renders if context value updates.
* 📦 **Avoid giant contexts**: Use **multiple small contexts** instead of one large global context.

---

## ✅ Interview Essentials

**Q:** Why was the new Context API introduced?
**A:** To replace the unstable legacy context system and provide a better way to manage global state without extra libraries.

**Q:** What triggers re-renders in context consumers?
**A:** Any change to the `value` prop of `<Provider>`.

**Q:** Is context a replacement for Redux?
**A:** For simple to medium state — yes. For complex state with middleware and time travel, Redux is still useful.

Here’s a complete deep dive into **`getDerivedStateFromProps`**, introduced in **React 16.3**:

---

## 🔄 **getDerivedStateFromProps (React 16.3)**

### 🔍 What is it?

`getDerivedStateFromProps` is a **static lifecycle method** that runs **before every render** (both initial and update).
It's used to **update state based on changes in props**.

```js
static getDerivedStateFromProps(props, state) {
  // return an object to update state, or null to do nothing
}
```

---

## ⚠️ Why Was It Introduced?

To **replace the unsafe** and deprecated `componentWillReceiveProps`, which had timing issues in async rendering (Fiber).

---

## 🔧 Syntax and Parameters

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      derivedValue: props.initialValue
    };
  }

  static getDerivedStateFromProps(nextProps, prevState) {
    if (nextProps.initialValue !== prevState.derivedValue) {
      return { derivedValue: nextProps.initialValue };
    }
    return null; // no state update
  }

  render() {
    return <div>Value: {this.state.derivedValue}</div>;
  }
}
```

---

## 📌 Key Points

| Aspect             | Description                           |
| ------------------ | ------------------------------------- |
| Static method      | No `this` access                      |
| Runs before render | Both on mount and update              |
| Use case           | Sync state with props (rarely needed) |
| Returns            | New state object or `null`            |

---

## ❌ When **Not** to Use It

* Avoid syncing props to state unless **absolutely required**.
* Prefer **controlled components** or lifting state up.

---

## ✅ Real Use Case: Resetting Form on Prop Change

```jsx
class Form extends React.Component {
  state = { input: '' };

  static getDerivedStateFromProps(nextProps, prevState) {
    if (nextProps.resetKey !== prevState.resetKey) {
      return {
        input: '',
        resetKey: nextProps.resetKey
      };
    }
    return null;
  }

  render() {
    return <input value={this.state.input} onChange={(e) => this.setState({ input: e.target.value })} />;
  }
}
```

---

## ⚠️ Warning

> Overusing this method is a sign of bad component design. Try using **props directly** or **lifting state up** instead.

Here’s a complete deep dive into **`componentDidCatch()`**, introduced in **React 16.0**, with explanation, examples, and best practices:

---

## 💥 **componentDidCatch() (React 16.0)**

### 🔍 What is it?

`componentDidCatch()` is a **lifecycle method used in Error Boundaries**. It allows class components to **catch JavaScript errors** in their child components and handle them gracefully.

---

## 📘 Syntax

```jsx
componentDidCatch(error, errorInfo)
```

* `error`: the error that was thrown
* `errorInfo`: an object with a `componentStack` string showing where the error occurred

---

## 🧱 Full Example: Error Boundary with `componentDidCatch`

```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.error("Caught by Error Boundary:", error, errorInfo);
    // You could also log to a service like Sentry here
  }

  render() {
    if (this.state.hasError) {
      return <h2>Oops! Something went wrong.</h2>;
    }
    return this.props.children;
  }
}
```

✅ **Usage:**

```jsx
<ErrorBoundary>
  <ComponentThatMightCrash />
</ErrorBoundary>
```

---

## 🚫 What It *Catches*

* Errors during **rendering**
* Errors in **lifecycle methods**
* Errors in **constructor** of child components

---

## ❌ What It *Doesn’t Catch*

| Doesn't Catch                        | Reason                          |
| ------------------------------------ | ------------------------------- |
| Errors in event handlers             | Use try/catch manually          |
| Async errors (`setTimeout`, `fetch`) | Not in the render tree          |
| Errors outside React tree            | Not part of component lifecycle |

---

## 📌 Best Practices

* Always **log the error** (`console.error`, Sentry, etc.)
* Show a **fallback UI**
* Use **multiple Error Boundaries** for isolated sections
* Use `getDerivedStateFromError` to update UI, not `componentDidCatch`

---

## ✅ Summary

| Feature              | Details                           |
| -------------------- | --------------------------------- |
| Introduced in        | React 16.0                        |
| Class component only | ✅ Yes                             |
| Used with            | Error Boundaries                  |
| Paired with          | `getDerivedStateFromError()`      |
| Replaces             | Total app crash on error (pre-16) |

Here’s a complete explanation of the **Support for Custom DOM Attributes** introduced in **React 16.0**, with clear examples:

---

## 🏷️ **Support for Custom DOM Attributes (React 16.0)**

### 🔍 What Changed?

Before React 16.0:

* React **filtered out unknown DOM attributes**.
* Custom attributes like `data-test-id` or `aria-*` **didn't render** unless explicitly allowed.

Starting in **React 16.0**, **any valid HTML attribute or custom attribute** is passed directly to the DOM.

---

## ✅ What This Enables

You can now safely use:

* **Custom attributes**: `custom-attr`, `x-meta`, etc.
* **Testing attributes**: `data-testid`, `data-id`
* **ARIA attributes**: `aria-label`, `aria-hidden`, etc.

---

## 📄 Example

```jsx
function CustomComponent() {
  return (
    <div
      data-id="user-123"
      custom-attr="my-value"
      aria-label="User info"
    >
      Hello!
    </div>
  );
}
```

### ✅ Resulting HTML:

```html
<div data-id="user-123" custom-attr="my-value" aria-label="User info">Hello!</div>
```

---

## 📌 Use Cases

| Use Case        | Example                       |
| --------------- | ----------------------------- |
| Testing         | `data-testid="submit-button"` |
| Accessibility   | `aria-label="Close menu"`     |
| Custom behavior | `custom-attr="xyz"`           |
| Integrate libs  | `<div x-meta="value" />`      |

---

## ⚠️ Notes

* React still warns for **invalid attribute names** (like camelCase: `customAttr` won't work).
* You should still follow **HTML standards** for browser compatibility.

Here's a deep dive into React 16.3+ features: **StrictMode**, **legacy lifecycle deprecation**, **Concurrent Mode (experimental)**, and **lifecycle cleanup** — with clear explanations and examples:

---

## 🧪 **11. React.StrictMode (16.3)**

### 🔍 What is it?

`<React.StrictMode>` is a tool to help you **identify unsafe lifecycle methods**, **unexpected side effects**, and **deprecated APIs** in development.

### ✅ Usage:

```jsx
import React from 'react';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

### 🔎 What it does:

* Double-invokes `componentDidMount`, `useEffect`, etc. (in dev only)
* Warns about:

  * `UNSAFE_` lifecycle methods
  * Deprecated string refs
  * Side effects during render

> 💡 It doesn’t render anything in the DOM — only affects development.

---

## 🛑 **12. Deprecation of Legacy Lifecycle Methods (React 16.3–16.9)**

### ❌ Deprecated methods:

| Old Method                    | Replacement                          |
| ----------------------------- | ------------------------------------ |
| `componentWillMount()`        | `UNSAFE_componentWillMount()`        |
| `componentWillReceiveProps()` | `UNSAFE_componentWillReceiveProps()` |
| `componentWillUpdate()`       | `UNSAFE_componentWillUpdate()`       |

> 🧼 These methods were problematic with async rendering and were marked UNSAFE\_ to discourage use.

---

## 🔄 Use Safer Alternatives

| Instead of…                   | Use…                                                  |
| ----------------------------- | ----------------------------------------------------- |
| `componentWillReceiveProps()` | `getDerivedStateFromProps()`                          |
| `componentWillMount()`        | `constructor` or `useEffect()`                        |
| `componentWillUpdate()`       | `getSnapshotBeforeUpdate()` or `componentDidUpdate()` |

---

## 🔥 **13. Concurrent Mode (Experimental in 16.9+)**

### 🔍 What is it?

Concurrent Mode is an **opt-in experimental feature** that lets React interrupt rendering to make UIs more responsive.

**Not enabled by default in React 16** — laid the groundwork for React 18’s features like:

* **Concurrent rendering**
* **Suspense for data fetching**
* **Time-slicing**

✅ Enabled via:

```jsx
import { createRoot } from 'react-dom/client';

const root = createRoot(document.getElementById('root'));
root.render(<App />);
```

> 📢 Fully stable in **React 18**.

---

## 🧼 **14. Lifecycle Cleanup (React 16.3+)**

### 🔧 What Changed?

React 16.3+ encouraged developers to:

* Migrate away from legacy lifecycle methods
* Use **static-safe** and **async-compatible** alternatives:

  * `getDerivedStateFromProps()`
  * `getSnapshotBeforeUpdate()`
  * `componentDidCatch()`

### 💡 Why?

To prepare apps for **async rendering**, **concurrent updates**, and **modern hooks-based architecture**.

---

## ✅ Summary

| Feature                     | Purpose                                |
| --------------------------- | -------------------------------------- |
| `StrictMode`                | Highlight unsafe code and side effects |
| `UNSAFE_` lifecycle methods | Mark legacy APIs for deprecation       |
| Concurrent Mode (exp.)      | Enable async/reactive rendering        |
| Lifecycle cleanup           | Encourage modern best practices        |


Here’s a complete and up-to-date list of **all major React Hooks**, grouped by category, including built-in hooks from React 16.8+ and later versions (like 18 & 19):

---

## ✅ 1. **Basic Hooks** (React 16.8)

| Hook         | Purpose                                  |
| ------------ | ---------------------------------------- |
| `useState`   | Add local state to functional components |
| `useEffect`  | Side effects (data fetch, subscriptions) |
| `useContext` | Access context values                    |

---

## 🔁 2. **Additional Built-in Hooks** (React 16.8)

| Hook                  | Purpose                                           |
| --------------------- | ------------------------------------------------- |
| `useReducer`          | Alternative to `useState` for complex state logic |
| `useCallback`         | Memoize functions                                 |
| `useMemo`             | Memoize computed values                           |
| `useRef`              | Access DOM refs or persist values across renders  |
| `useImperativeHandle` | Customize instance value exposed to parent        |
| `useLayoutEffect`     | Like `useEffect`, but fires before paint          |
| `useDebugValue`       | Show custom label in React DevTools               |

---

## 🧪 3. **Hooks Introduced in React 18**

| Hook                   | Purpose                                          |
| ---------------------- | ------------------------------------------------ |
| `useTransition`        | Manage non-urgent updates (concurrent rendering) |
| `useDeferredValue`     | Defer re-rendering of non-critical subtrees      |
| `useId`                | Generate unique IDs for SSR/CSR matching         |
| `useSyncExternalStore` | Subscribe to external stores (e.g., Redux)       |
| `useInsertionEffect`   | Inject styles before layout/render               |

---

## 🧪 4. **Hooks Introduced in React 19 (canary)**

| Hook            | Purpose                                               |
| --------------- | ----------------------------------------------------- |
| `use`           | Suspense-first data fetching (await inside component) |
| `useFormStatus` | Status of a form submission (in Server Actions)       |
| `useFormState`  | Manage form state across Server Actions               |
| `useOptimistic` | Optimistic UI updates with rollback support           |

---

## ✨ 5. **Custom Hooks** (User-defined)

React lets you create **your own hooks** for reusing logic across components:

```js
function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);
  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);
    window.addEventListener("resize", handleResize);
    return () => window.removeEventListener("resize", handleResize);
  }, []);
  return width;
}
```

---

## ✅ Summary Table

| Category   | Hooks                                                                |
| ---------- | -------------------------------------------------------------------- |
| Basic      | `useState`, `useEffect`, `useContext`                                |
| Additional | `useReducer`, `useCallback`, `useMemo`, `useRef`, etc.               |
| React 18   | `useTransition`, `useDeferredValue`, `useId`, `useSyncExternalStore` |
| React 19   | `use`, `useFormStatus`, `useOptimistic`, `useFormState`              |
| Custom     | User-defined: `useFetch`, `useLocalStorage`, etc.                    |

Here’s a complete, interview-ready deep dive into **`useState`**, React’s most fundamental Hook:

---

## 🔧 `useState` – Add State to Functional Components

### ✅ What is it?

`useState` lets you **declare and manage local state** in a functional component — a feature that was previously only possible in class components.

---

## 🧪 Syntax

```js
const [state, setState] = useState(initialValue);
```

| Term           | Meaning                      |
| -------------- | ---------------------------- |
| `state`        | Current state value          |
| `setState`     | Function to update the state |
| `initialValue` | The initial state (any type) |

---

## 📘 Basic Example

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // initial state = 0

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment ➕</button>
    </div>
  );
}
```

---

## 🧠 Things to Remember

### 1️⃣ You can store any type:

```js
useState('hello')       // string
useState([])            // array
useState({ name: 'A' }) // object
```

---

### 2️⃣ State updates are async:

```js
setCount(count + 1);
setCount(count + 1); // both use the same 'count'
```

💡 Use the callback form to safely update state based on previous value:

```js
setCount(prev => prev + 1);
```

---

### 3️⃣ Re-render on update:

Every time `setState` is called, the component **re-renders** with the new state.

---

## 🔄 Example: Toggle Button

```jsx
function Toggle() {
  const [isOn, setIsOn] = useState(false);
  return (
    <button onClick={() => setIsOn(prev => !prev)}>
      {isOn ? "ON" : "OFF"}
    </button>
  );
}
```

---

## ✅ Summary

| Feature       | Details                            |
| ------------- | ---------------------------------- |
| React version | 16.8+                              |
| Purpose       | Add state to functional components |
| Returns       | `[state, setState]`                |
| Replaces      | `this.state`, `this.setState()`    |

Let’s now dive into **`useEffect`**, the most important React hook for managing **side effects** in functional components.

---

## ⚙️ `useEffect` – Run Side Effects in Functional Components

### ✅ What is it?

`useEffect` lets you perform **side effects** in your component, like:

* Fetching data
* Setting up subscriptions
* Manually manipulating the DOM
* Timers / intervals

> It replaces lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

---

## 📘 Syntax

```js
useEffect(() => {
  // side-effect logic here

  return () => {
    // cleanup logic (optional)
  };
}, [dependencies]);
```

| Part             | Purpose                               |
| ---------------- | ------------------------------------- |
| Effect function  | Runs after render                     |
| Cleanup function | Runs on unmount or before next effect |
| Dependency array | Controls when the effect runs         |

---

## 🔧 Example 1: Run on Mount (like `componentDidMount`)

```js
useEffect(() => {
  console.log("Component mounted");
}, []); // empty deps = run only once
```

---

## 🔁 Example 2: Run on State Change

```js
const [count, setCount] = useState(0);

useEffect(() => {
  console.log("Count changed to:", count);
}, [count]); // run when `count` changes
```

---

## 🧹 Example 3: Cleanup (like `componentWillUnmount`)

```js
useEffect(() => {
  const timer = setInterval(() => console.log("Tick"), 1000);

  return () => {
    clearInterval(timer); // cleanup
  };
}, []);
```

---

## ✅ Summary

| Feature           | Details                              |
| ----------------- | ------------------------------------ |
| React version     | 16.8+                                |
| Use for           | Side effects, data fetching, cleanup |
| Runs after render | ✅                                    |
| Cleanup function  | Optional return inside `useEffect`   |


Here are combined and practical examples of **`useState`** and **`useEffect`** together — from basic to real-world use cases:

---

## ✅ 1. **Basic Counter (State + Effect)**

```jsx
import React, { useState, useEffect } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Count updated:", count);
  }, [count]); // runs after count changes

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(prev => prev + 1)}>➕ Increment</button>
    </div>
  );
}
```

---

## 🌐 2. **Fetch API Data on Mount**

```jsx
import React, { useState, useEffect } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []); // run once on mount

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

---

## 🧹 3. **Timer with Cleanup**

```jsx
import React, { useState, useEffect } from "react";

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds(prev => prev + 1), 1000);
    return () => clearInterval(interval); // cleanup
  }, []);

  return <h2>⏱️ Timer: {seconds}s</h2>;
}
```

---

## 💡 4. **Online/Offline Status Detector**

```jsx
import React, { useState, useEffect } from "react";

function NetworkStatus() {
  const [isOnline, setIsOnline] = useState(navigator.onLine);

  useEffect(() => {
    const handleOnline = () => setIsOnline(true);
    const handleOffline = () => setIsOnline(false);

    window.addEventListener("online", handleOnline);
    window.addEventListener("offline", handleOffline);

    return () => {
      window.removeEventListener("online", handleOnline);
      window.removeEventListener("offline", handleOffline);
    };
  }, []);

  return <div>Status: {isOnline ? "✅ Online" : "❌ Offline"}</div>;
}
```

Here are the **Next.js + TypeScript versions** of the previous `useState` + `useEffect` examples:

---

## ✅ 1. **Counter Component (Next.js + TypeScript)**

```tsx
// components/Counter.tsx
import { useState, useEffect } from "react";

export default function Counter() {
  const [count, setCount] = useState<number>(0);

  useEffect(() => {
    console.log("Count is now:", count);
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount((prev) => prev + 1)}>Increment ➕</button>
    </div>
  );
}
```

---

## 🌐 2. **Fetch Users (API call with TypeScript)**

```tsx
// components/Users.tsx
import { useState, useEffect } from "react";

type User = {
  id: number;
  name: string;
};

export default function Users() {
  const [users, setUsers] = useState<User[]>([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => res.json())
      .then((data: User[]) => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

---

## ⏱️ 3. **Timer with Cleanup (TypeScript)**

```tsx
// components/Timer.tsx
import { useState, useEffect } from "react";

export default function Timer() {
  const [seconds, setSeconds] = useState<number>(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds((s) => s + 1), 1000);
    return () => clearInterval(interval);
  }, []);

  return <h2>⏱️ {seconds} seconds elapsed</h2>;
}
```

---

## 📡 4. **Online/Offline Status**

```tsx
// components/NetworkStatus.tsx
import { useState, useEffect } from "react";

export default function NetworkStatus() {
  const [isOnline, setIsOnline] = useState<boolean>(typeof window !== "undefined" ? navigator.onLine : true);

  useEffect(() => {
    const goOnline = () => setIsOnline(true);
    const goOffline = () => setIsOnline(false);

    window.addEventListener("online", goOnline);
    window.addEventListener("offline", goOffline);

    return () => {
      window.removeEventListener("online", goOnline);
      window.removeEventListener("offline", goOffline);
    };
  }, []);

  return <p>Status: {isOnline ? "🟢 Online" : "🔴 Offline"}</p>;
}
```
Here’s a **detailed guide to `useContext`** in React with a complete example using **Next.js + TypeScript (w5h: What, Why, When, Where, How)**:

---

## 🧠 `useContext` – Share State Across Components (No Prop Drilling)

---

### 🟡 **What is `useContext`?**

`useContext` is a React hook that lets **any child component** access data from a shared `Context` object — without manually passing props down the component tree.

---

### 💡 **Why use it?**

* Avoid **prop drilling**
* Share **global state** (e.g., auth, theme, language)
* Works in **functional components** only (use `.contextType` in classes)

---

### ⏰ **When should I use it?**

* You need **global** or **shared** data across deeply nested components
* Ideal for **auth tokens**, **UI themes**, **locale/language**, or **user info**

---

### 🗺️ **Where is it used?**

Anywhere inside a **Context Provider tree**:

```tsx
<AuthContext.Provider value={user}> // <--- You must be inside this
  <Dashboard />
</AuthContext.Provider>
```

---

### ⚙️ **How to use `useContext`**

#### 🔨 1. Create Context

```tsx
// context/ThemeContext.tsx
import { createContext } from "react";

export const ThemeContext = createContext<string>("light");
```

---

#### 🔧 2. Provide Context Value

```tsx
// pages/_app.tsx
import { ThemeContext } from "@/context/ThemeContext";
import type { AppProps } from "next/app";

export default function App({ Component, pageProps }: AppProps) {
  return (
    <ThemeContext.Provider value="dark">
      <Component {...pageProps} />
    </ThemeContext.Provider>
  );
}
```

---

#### 📥 3. Consume with `useContext`

```tsx
// components/ThemedButton.tsx
import { useContext } from "react";
import { ThemeContext } from "@/context/ThemeContext";

export default function ThemedButton() {
  const theme = useContext(ThemeContext);

  return (
    <button className={`btn ${theme}`}>
      Theme in use: {theme}
    </button>
  );
}
```

---

### ✅ Full Working Flow (Next.js + TypeScript)

```
📁 context/
  └── ThemeContext.tsx

📁 components/
  └── ThemedButton.tsx

📁 pages/
  ├── _app.tsx
  └── index.tsx
```

```tsx
// pages/index.tsx
import ThemedButton from "@/components/ThemedButton";

export default function Home() {
  return (
    <div>
      <h1>Home Page</h1>
      <ThemedButton />
    </div>
  );
}
```

---

## 🧠 Bonus Tip: Context + Custom Hook Pattern

```tsx
// context/UserContext.tsx
export const UserContext = createContext<User | null>(null);

export const useUser = () => useContext(UserContext);
```

---

### ⚠️ Caveats

* Changing `value` in `<Provider>` will **trigger all consumers to re-render**
* Not ideal for **high-frequency updates** (e.g., mouse position)
* Best to split into **small contexts** (e.g., AuthContext, ThemeContext separately)

Here is a complete working **Next.js + TypeScript project** using `useContext` to toggle a **light/dark theme**, including all necessary files and structure:

---

## 🧾 1. **File: `context/ThemeContext.tsx`**

```tsx
// context/ThemeContext.tsx
import { createContext, useState, useContext, ReactNode } from "react";

type Theme = "light" | "dark";

interface ThemeContextType {
  theme: Theme;
  toggleTheme: () => void;
}

const ThemeContext = createContext<ThemeContextType | undefined>(undefined);

export const ThemeProvider = ({ children }: { children: ReactNode }) => {
  const [theme, setTheme] = useState<Theme>("light");

  const toggleTheme = () => setTheme((prev) => (prev === "light" ? "dark" : "light"));

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      <div className={theme === "dark" ? "dark" : "light"}>{children}</div>
    </ThemeContext.Provider>
  );
};

export const useTheme = () => {
  const context = useContext(ThemeContext);
  if (!context) throw new Error("useTheme must be used within ThemeProvider");
  return context;
};
```

---

## 📄 2. **File: `components/ThemedButton.tsx`**

```tsx
// components/ThemedButton.tsx
import { useTheme } from "@/context/ThemeContext";

export default function ThemedButton() {
  const { theme, toggleTheme } = useTheme();

  return (
    <button
      onClick={toggleTheme}
      style={{
        padding: "12px 20px",
        backgroundColor: theme === "dark" ? "#222" : "#eee",
        color: theme === "dark" ? "#fff" : "#000",
        border: "none",
        cursor: "pointer",
        marginTop: "20px"
      }}
    >
      Toggle Theme (Current: {theme})
    </button>
  );
}
```

---

## 🔧 3. **File: `pages/_app.tsx`**

```tsx
// pages/_app.tsx
import type { AppProps } from "next/app";
import { ThemeProvider } from "@/context/ThemeContext";

export default function App({ Component, pageProps }: AppProps) {
  return (
    <ThemeProvider>
      <Component {...pageProps} />
    </ThemeProvider>
  );
}
```

---

## 🏠 4. **File: `pages/index.tsx`**

```tsx
// pages/index.tsx
import ThemedButton from "@/components/ThemedButton";

export default function Home() {
  return (
    <main style={{ padding: "40px", fontFamily: "sans-serif" }}>
      <h1>🌗 Welcome to Theme Toggle App</h1>
      <ThemedButton />
    </main>
  );
}
```

---

## 📁 Project Structure

```
/context
  └── ThemeContext.tsx
/components
  └── ThemedButton.tsx
/pages
  ├── _app.tsx
  └── index.tsx
```

Here’s a complete breakdown of the **`useCallback`** hook with W5H (What, Why, When, Where, How) and **working examples** (React + TypeScript):

---

## 🔁 `useCallback` Hook – W5H Breakdown

---

### ✅ **What** is `useCallback`?

`useCallback` is a React Hook that **memoizes a function** — it returns a cached version of the callback that only changes if its dependencies change.

```tsx
const memoizedFn = useCallback(() => {
  // logic
}, [dependencies]);
```

---

### 💡 **Why** use it?

In React, functions are re-created on every render. This can cause:

* Unnecessary **re-renders** of child components
* Breaking **reference equality checks**
* Performance issues in large components

---

### ⏰ **When** to use it?

Use `useCallback` **only** when:

* You pass a function to a **child component** that is memoized with `React.memo`
* You're seeing **performance bottlenecks** or **unwanted re-renders**

---

### 🗺️ **Where** is it used?

* Inside **functional components**
* Common with:

  * `React.memo`
  * `useEffect`
  * `useMemo`
  * Performance optimizations

---

### ⚙️ **How** to use it?

```tsx
const handleClick = useCallback(() => {
  setCount((prev) => prev + 1);
}, []);
```

---

## 🧪 Example 1: Preventing Unnecessary Re-renders

### 🧱 Setup

```tsx
// components/Child.tsx
import React from "react";

type Props = {
  onClick: () => void;
};

const Child = React.memo(({ onClick }: Props) => {
  console.log("🔄 Child Rendered");
  return <button onClick={onClick}>Click Me</button>;
});

export default Child;
```

```tsx
// pages/index.tsx
import { useState, useCallback } from "react";
import Child from "@/components/Child";

export default function Home() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Button clicked");
  }, []);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount((c) => c + 1)}>Increment Count</button>
      <Child onClick={handleClick} />
    </div>
  );
}
```

✅ **Without `useCallback`**: `Child` re-renders every time parent renders
✅ **With `useCallback`**: `Child` only re-renders when `handleClick` changes

---

## ✅ Summary Table

| Aspect   | Detail                                    |
| -------- | ----------------------------------------- |
| Purpose  | Memoize functions to prevent re-renders   |
| Syntax   | `useCallback(fn, [deps])`                 |
| Return   | Cached function reference                 |
| Use With | `React.memo`, heavy lists, handlers       |
| Good For | Optimization in child component rendering |

Let’s now combine **`useCallback`** and **`useMemo`** in one optimized example with a heavy calculation and a memoized click handler to demonstrate **real-world performance optimization**.

---

## 🧠 Combined Example: `useMemo` + `useCallback` (TypeScript)

---

### 📁 File: `components/HeavyChild.tsx`

```tsx
import React from "react";

type Props = {
  onClick: () => void;
  result: number;
};

const HeavyChild = React.memo(({ onClick, result }: Props) => {
  console.log("🔁 Child rendered");
  return (
    <div>
      <p>Heavy Calculation Result: {result}</p>
      <button onClick={onClick}>Click Me</button>
    </div>
  );
});

export default HeavyChild;
```

---

### 📄 File: `pages/index.tsx`

```tsx
import { useState, useMemo, useCallback } from "react";
import HeavyChild from "@/components/HeavyChild";

// Simulate a heavy computation
function slowFunction(num: number): number {
  console.log("🧮 Running heavy computation...");
  for (let i = 0; i < 1e8; i++) {} // delay loop
  return num * 2;
}

export default function Home() {
  const [count, setCount] = useState(0);
  const [other, setOther] = useState(0);

  // Memoize heavy calculation
  const double = useMemo(() => slowFunction(count), [count]);

  // Memoize handler to prevent re-renders
  const handleClick = useCallback(() => {
    alert("Clicked!");
  }, []);

  return (
    <main style={{ padding: "2rem" }}>
      <h1>useMemo + useCallback Optimization</h1>
      <button onClick={() => setCount((c) => c + 1)}>➕ Count: {count}</button>
      <button onClick={() => setOther((o) => o + 1)}>🔁 Other: {other}</button>

      <HeavyChild result={double} onClick={handleClick} />
    </main>
  );
}
```

---

### ✅ Optimizations Explained:

| Technique     | Benefit                                            |
| ------------- | -------------------------------------------------- |
| `useMemo`     | Avoid recalculating slow function unnecessarily    |
| `useCallback` | Prevent re-creating the function on every render   |
| `React.memo`  | Skip re-render of `HeavyChild` unless props change |

Here’s a full W5H breakdown of **`useMemo`** with deep explanation, real-world uses, and a working React + TypeScript example:

---

## 🧠 `useMemo` – W5H Breakdown (What, Why, When, Where, How)

---

### ✅ **What** is `useMemo`?

`useMemo` is a React Hook that **memoizes (caches)** the result of a computation and **recomputes only when dependencies change**.

```ts
const memoizedValue = useMemo(() => expensiveFunction(), [deps]);
```

---

### 💡 **Why** use `useMemo`?

React re-renders everything by default. `useMemo` avoids:

* Running **expensive calculations** on every render
* Breaking **referential equality** in props
* Performance bottlenecks in **large apps**

---

### ⏰ **When** to use it?

Use `useMemo` when:

* You have **heavy computation**
* You want to **prevent unnecessary renders** of child components
* You want to **memoize object/array literals**

---

### 🗺️ **Where** is it used?

* Inside **functional components**
* With **React.memo** or comparison-based re-render prevention
* With **array/object props** passed to children

---

### ⚙️ **How** to use it?

```tsx
const result = useMemo(() => slowFunction(count), [count]);
```

It will **only re-run slowFunction when `count` changes**.

---

## 🔧 React + TypeScript Example

### 🧮 Simulate Expensive Function

```tsx
// utils/slowFn.ts
export function heavyComputation(n: number): number {
  console.log("💥 Heavy function running...");
  let total = 0;
  for (let i = 0; i < 1e8; i++) {
    total += i % n;
  }
  return total;
}
```

---

### 📄 `pages/index.tsx`

```tsx
import { useState, useMemo } from "react";
import { heavyComputation } from "@/utils/slowFn";

export default function UseMemoDemo() {
  const [count, setCount] = useState(5);
  const [other, setOther] = useState(0);

  // ✅ Memoize heavy computation
  const computedValue = useMemo(() => heavyComputation(count), [count]);

  return (
    <main style={{ padding: "2rem", fontFamily: "sans-serif" }}>
      <h2>🔁 useMemo Example</h2>
      <p>Count: {count}</p>
      <p>Computed: {computedValue}</p>
      <button onClick={() => setCount((c) => c + 1)}>➕ Count</button>
      <button onClick={() => setOther((o) => o + 1)}>🔁 Other: {other}</button>
    </main>
  );
}
```

---

### 🔍 Observation

* `heavyComputation()` **only runs** when `count` changes
* Clicking “Other” will **not trigger recomputation**
* Prevents wasteful cycles and makes the UI fast

---

## ✅ Summary Table

| Hook       | `useMemo`                         |
| ---------- | --------------------------------- |
| Use Case   | Cache result of a function        |
| Returns    | Memoized value                    |
| Input      | Callback + dependency array       |
| React Ver. | 16.8+                             |
| Common Use | Expensive calc, memoizing objects |

Here’s a real-world **React + TypeScript** example using `useMemo` with `React.memo` to **optimize a filtered search list**, like a product or user filter – commonly seen in dashboards, admin panels, and e-commerce UIs.

---

## ✅ Goal: Filter List with `useMemo` to Optimize Performance

---

### 👇 Problem Without `useMemo`

* Each keypress **filters the list** again.
* Even if the input hasn’t changed, **filtering logic re-executes** on every render.
* 👎 Not scalable for 1000s of items.

---

### ✅ Solution Using `useMemo`

* Only re-run filtering **when data or query changes**.
* Avoid re-renders using `React.memo`.

---

## 🧱 Component Structure

```
/components
  └── UserList.tsx
/pages
  └── index.tsx
```

---

### 📄 `components/UserList.tsx`

```tsx
import React from "react";

type Props = {
  users: string[];
};

const UserList = React.memo(({ users }: Props) => {
  console.log("👥 UserList re-rendered");
  return (
    <ul>
      {users.map((u) => (
        <li key={u}>{u}</li>
      ))}
    </ul>
  );
});

export default UserList;
```

---

### 📄 `pages/index.tsx`

```tsx
import { useMemo, useState } from "react";
import UserList from "@/components/UserList";

const USERS = [
  "Alice",
  "Bob",
  "Charlie",
  "David",
  "Eve",
  "Frank",
  "Grace",
  "Heidi",
  "Ivan",
  "Judy",
];

export default function Home() {
  const [query, setQuery] = useState("");

  const filteredUsers = useMemo(() => {
    console.log("🔍 Filtering users...");
    return USERS.filter((name) => name.toLowerCase().includes(query.toLowerCase()));
  }, [query]);

  return (
    <main style={{ padding: "2rem" }}>
      <h1>👤 Filter Users</h1>
      <input
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Search user..."
        style={{ padding: "8px", marginBottom: "12px" }}
      />
      <UserList users={filteredUsers} />
    </main>
  );
}
```

---

## ✅ Optimization Recap

| Feature      | Purpose                                   |
| ------------ | ----------------------------------------- |
| `useMemo`    | Cache filtered list by input query        |
| `React.memo` | Prevent `UserList` from re-rendering      |
| Result       | Efficient filtering even with 1000+ items |


Here’s a full W5H breakdown of **`React.memo`**, one of the key performance optimization tools in React, with examples and use cases:

---

## 🧠 `React.memo` – W5H Breakdown (What, Why, When, Where, How)

---

### ✅ **What** is `React.memo`?

`React.memo` is a **higher-order component (HOC)** that **memoizes a functional component**, preventing unnecessary re-renders if its **props don’t change**.

```tsx
const MemoizedComponent = React.memo(MyComponent);
```

---

### 💡 **Why** use `React.memo`?

React re-renders child components even if their props haven’t changed (because functions/objects/arrays are re-created).

✅ `React.memo`:

* Skips re-rendering when **props are shallow equal**
* Improves performance in large trees or heavy components
* Ideal with `useCallback`, `useMemo`

---

### ⏰ **When** to use it?

Use `React.memo` when:

* The component re-renders often with **unchanged props**
* Component is **pure** (depends only on props)
* Props are **primitive values** or memoized

---

### 🗺️ **Where** is it used?

Wrap **functional components**, especially:

* Leaf components
* Components with heavy render logic
* Components that accept **handlers or data** as props

---

### ⚙️ **How** to use it?

```tsx
const MyButton = React.memo(({ label }: { label: string }) => {
  console.log("Button rendered");
  return <button>{label}</button>;
});
```

You can also provide a custom `propsAreEqual(prev, next)` comparison:

```tsx
React.memo(Component, (prevProps, nextProps) => {
  return prevProps.value === nextProps.value;
});
```

---

## 🧪 Working Example: With and Without `React.memo`

```tsx
// components/Counter.tsx
const Counter = ({ value }: { value: number }) => {
  console.log("🧮 Counter rendered");
  return <div>Value: {value}</div>;
};

export default React.memo(Counter);
```

```tsx
// pages/index.tsx
import { useState } from "react";
import Counter from "@/components/Counter";

export default function Home() {
  const [count, setCount] = useState(0);
  const [other, setOther] = useState(0);

  return (
    <div>
      <h1>React.memo Demo</h1>
      <button onClick={() => setCount((c) => c + 1)}>Increment Count</button>
      <button onClick={() => setOther((o) => o + 1)}>Update Other</button>
      <Counter value={count} />
    </div>
  );
}
```

✅ Clicking “Update Other” won’t re-render `Counter`, thanks to `React.memo`.

---

## ✅ Summary Table

| Feature     | Description                              |
| ----------- | ---------------------------------------- |
| Purpose     | Skip re-renders if props haven't changed |
| Type        | HOC (Higher Order Component)             |
| Usage       | `React.memo(Component)`                  |
| Common Pair | `useCallback`, `useMemo`                 |
| Caveat      | Shallow prop comparison only             |

Let’s build a **reusable and optimized component setup** using `React.memo` + `useCallback` + `useMemo` in a real-world **React + TypeScript dashboard UI**.

---

## ✅ Goal: Optimized Dashboard Card Component

We’ll create:

* `StatCard`: A reusable card showing metrics
* `React.memo` to avoid unnecessary re-renders
* `useCallback` for actions (e.g., refresh)
* `useMemo` to calculate derived props (e.g., % change)

---

### 🧱 Project Structure

```
/components
  ├── StatCard.tsx
/pages
  └── index.tsx
```

---

## 📄 `components/StatCard.tsx`

```tsx
import React from "react";

type Props = {
  label: string;
  value: number;
  onRefresh: () => void;
};

const StatCard = React.memo(({ label, value, onRefresh }: Props) => {
  console.log(`🎯 Rendering card: ${label}`);

  return (
    <div style={{
      padding: "20px",
      margin: "10px",
      border: "1px solid #ddd",
      borderRadius: "8px",
      width: "200px"
    }}>
      <h3>{label}</h3>
      <p style={{ fontSize: "1.5rem", fontWeight: "bold" }}>{value}</p>
      <button onClick={onRefresh}>🔄 Refresh</button>
    </div>
  );
});

export default StatCard;
```

---

## 📄 `pages/index.tsx`

```tsx
import { useState, useCallback, useMemo } from "react";
import StatCard from "@/components/StatCard";

export default function Dashboard() {
  const [sales, setSales] = useState(1200);
  const [visits, setVisits] = useState(4500);
  const [refreshCount, setRefreshCount] = useState(0);

  // Memoized derived value
  const conversionRate = useMemo(() => ((sales / visits) * 100).toFixed(2), [sales, visits]);

  // Memoized handlers
  const refreshSales = useCallback(() => {
    setSales((s) => s + Math.floor(Math.random() * 200));
    setRefreshCount((c) => c + 1);
  }, []);

  const refreshVisits = useCallback(() => {
    setVisits((v) => v + Math.floor(Math.random() * 500));
    setRefreshCount((c) => c + 1);
  }, []);

  return (
    <div style={{ padding: "2rem" }}>
      <h1>📊 Dashboard</h1>
      <p>Total refreshes: {refreshCount}</p>
      <div style={{ display: "flex", gap: "1rem" }}>
        <StatCard label="Sales" value={sales} onRefresh={refreshSales} />
        <StatCard label="Visits" value={visits} onRefresh={refreshVisits} />
        <StatCard label="Conversion %" value={parseFloat(conversionRate)} onRefresh={() => {}} />
      </div>
    </div>
  );
}
```

---

### ✅ Optimization Recap

| Hook          | Used For                                         |
| ------------- | ------------------------------------------------ |
| `React.memo`  | Avoid re-rendering `StatCard` if props unchanged |
| `useCallback` | Prevents function recreation for `onRefresh`     |
| `useMemo`     | Avoid recomputing derived conversion rate        |

Here’s a complete W5H breakdown of **`useReducer`** with deep explanation and a full **React + TypeScript working example**.

---

## 🧠 `useReducer` – W5H Breakdown

---

### ✅ **What** is `useReducer`?

`useReducer` is a React hook that manages **complex state logic** using a **reducer function**, similar to Redux.

```tsx
const [state, dispatch] = useReducer(reducerFn, initialState);
```

---

### 💡 **Why** use it?

* Handles **multiple related state updates**
* Organizes logic in one place (reducer)
* Better than `useState` for **complex state transitions**

---

### ⏰ **When** to use it?

* You have **multi-step state updates**
* States depend on **previous states**
* You want **Redux-like behavior** without Redux

---

### 🗺️ **Where** is it used?

* Inside React **function components**
* Often with **context** for global state
* Replaces `useState` for **predictable state transitions**

---

### ⚙️ **How** to use it?

```tsx
type State = { count: number };
type Action = { type: "increment" | "decrement" };

function reducer(state: State, action: Action): State {
  switch (action.type) {
    case "increment": return { count: state.count + 1 };
    case "decrement": return { count: state.count - 1 };
    default: return state;
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });
```

---

## ✅ Real-World Example: Counter with `useReducer` (TypeScript)

```tsx
import { useReducer } from "react";

// 1. Define types
type State = { count: number };
type Action = { type: "increment" } | { type: "decrement" } | { type: "reset" };

// 2. Reducer function
function counterReducer(state: State, action: Action): State {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return { count: 0 };
    default:
      return state;
  }
}

export default function Counter() {
  const [state, dispatch] = useReducer(counterReducer, { count: 0 });

  return (
    <div style={{ padding: "2rem", textAlign: "center" }}>
      <h2>🧮 Count: {state.count}</h2>
      <button onClick={() => dispatch({ type: "increment" })}>➕</button>
      <button onClick={() => dispatch({ type: "decrement" })}>➖</button>
      <button onClick={() => dispatch({ type: "reset" })}>🔁</button>
    </div>
  );
}
```

---

## ✅ Summary Table

| Feature      | Description                           |
| ------------ | ------------------------------------- |
| `useReducer` | Manages state transitions via reducer |
| Best For     | Complex logic, multiple updates       |
| API          | `[state, dispatch] = useReducer(...)` |
| Inspired By  | Redux                                 |


Here’s a complete **W5H breakdown** of `useRef` in React with deep explanation and a working **React + TypeScript** example.

---

## 🧠 `useRef` – W5H Breakdown

---

### ✅ **What** is `useRef`?

`useRef` is a React Hook that returns a **mutable reference object** which persists across renders without causing re-renders.

```tsx
const ref = useRef(initialValue);
```

---

### 💡 **Why** use it?

* To access and manipulate **DOM elements**
* To store **mutable values** (e.g., timers, counters) **without triggering re-renders**
* Alternative to class-based instance variables

---

### ⏰ **When** to use it?

* When you need to **persist a value without re-rendering**
* To **focus**, **scroll**, or interact with DOM nodes
* Store **previous values**, **timeouts**, or **intervals**

---

### 🗺️ **Where** is it used?

* Inside functional components
* Anywhere you need to **track DOM** or **mutable state**

---

### ⚙️ **How** to use it?

```tsx
const inputRef = useRef<HTMLInputElement>(null);

useEffect(() => {
  inputRef.current?.focus();
}, []);
```

---

## ✅ Example 1: Focus an input on mount

```tsx
import { useRef, useEffect } from "react";

export default function FocusInput() {
  const inputRef = useRef<HTMLInputElement>(null);

  useEffect(() => {
    inputRef.current?.focus();
  }, []);

  return (
    <div style={{ padding: "2rem" }}>
      <h2>🔎 Focus Input on Mount</h2>
      <input ref={inputRef} placeholder="Type here..." />
    </div>
  );
}
```

---

## ✅ Example 2: Keep previous value

```tsx
import { useEffect, useRef, useState } from "react";

export default function PrevValue() {
  const [count, setCount] = useState(0);
  const prevCount = useRef<number | null>(null);

  useEffect(() => {
    prevCount.current = count;
  }, [count]);

  return (
    <div style={{ padding: "2rem" }}>
      <h2>🕓 Current: {count}</h2>
      <h3>Previous: {prevCount.current}</h3>
      <button onClick={() => setCount((c) => c + 1)}>Increment</button>
    </div>
  );
}
```

---

## ✅ Summary Table

| Feature    | Description                                    |
| ---------- | ---------------------------------------------- |
| `useRef()` | Stores mutable value or DOM reference          |
| Triggers   | ❌ Doesn’t cause re-render                      |
| Common Use | DOM access, timers, storing prev value, flags  |
| Initial    | `useRef(null)` for DOM, or a value for storage |

Let’s build a **custom video player controller** using `useRef` in **React + TypeScript**, demonstrating:

✅ DOM manipulation
✅ `play()`, `pause()` control
✅ Time tracking using `requestAnimationFrame`
✅ Seek bar and play/pause buttons

---

## 🎥 Custom Video Player (React + TypeScript)

### 📁 File Structure

```
/components
  └── VideoPlayer.tsx
/pages
  └── index.tsx
/public
  └── sample.mp4 (any short video)
```

---

### 📄 `components/VideoPlayer.tsx`

```tsx
import { useRef, useState, useEffect } from "react";

export default function VideoPlayer() {
  const videoRef = useRef<HTMLVideoElement>(null);
  const [playing, setPlaying] = useState(false);
  const [progress, setProgress] = useState(0);

  const togglePlay = () => {
    const video = videoRef.current;
    if (!video) return;

    if (video.paused) {
      video.play();
      setPlaying(true);
    } else {
      video.pause();
      setPlaying(false);
    }
  };

  const handleTimeUpdate = () => {
    const video = videoRef.current;
    if (video) {
      const percent = (video.currentTime / video.duration) * 100;
      setProgress(percent);
    }
  };

  const seek = (e: React.ChangeEvent<HTMLInputElement>) => {
    const video = videoRef.current;
    if (video) {
      const newTime = (+e.target.value / 100) * video.duration;
      video.currentTime = newTime;
    }
  };

  return (
    <div style={{ padding: "2rem" }}>
      <video
        ref={videoRef}
        src="/sample.mp4"
        width="600"
        onTimeUpdate={handleTimeUpdate}
        style={{ borderRadius: "8px", marginBottom: "1rem" }}
        controls={false}
      />
      <div>
        <button onClick={togglePlay} style={{ marginRight: "1rem" }}>
          {playing ? "⏸ Pause" : "▶️ Play"}
        </button>
        <input
          type="range"
          value={progress}
          onChange={seek}
          style={{ width: "300px" }}
        />
      </div>
    </div>
  );
}
```

---

### 📄 `pages/index.tsx`

```tsx
import VideoPlayer from "@/components/VideoPlayer";

export default function Home() {
  return (
    <main style={{ fontFamily: "sans-serif" }}>
      <h1 style={{ padding: "2rem" }}>🎬 Custom Video Player</h1>
      <VideoPlayer />
    </main>
  );
}
```

---

### ✅ What This Demonstrates

| `useRef` Use Case    | How it's used                         |
| -------------------- | ------------------------------------- |
| DOM Access           | `videoRef.current.play()` / `pause()` |
| Read state on demand | Get `currentTime`, `duration`         |
| Avoiding re-renders  | `videoRef` doesn’t trigger rerender   |

Here’s a complete **W5H breakdown** of `useLayoutEffect` in React with a deep explanation and **React + TypeScript** working example:

---

## 🧠 `useLayoutEffect` – W5H Breakdown

---

### ✅ **What** is `useLayoutEffect`?

`useLayoutEffect` is a React hook just like `useEffect`, but it **fires synchronously after all DOM mutations**, **before the browser paints** the screen.

```tsx
useLayoutEffect(() => {
  // Read or change layout
}, []);
```

---

### 💡 **Why** use it?

Use `useLayoutEffect` when you:

* Need to **measure DOM size or position**
* Need to **mutate DOM styles** before browser paint
* Avoid flickering or layout shift

---

### ⏰ **When** to use it?

* **Before paint**: update layout, scroll, style, or measure elements
* When changes must be **visible instantly**
* For **tooltips, modals, transitions**, etc.

---

### 🗺️ **Where** is it used?

* Inside **functional components**
* Replaces old `componentDidMount`/`componentDidUpdate` if layout is involved

---

### ⚙️ **How** to use it?

```tsx
useLayoutEffect(() => {
  const width = boxRef.current?.offsetWidth;
  console.log("Measured width:", width);
}, []);
```

---

## ✅ Real Example: Measure a box width and avoid flicker

```tsx
import { useLayoutEffect, useRef, useState } from "react";

export default function BoxMeasure() {
  const boxRef = useRef<HTMLDivElement>(null);
  const [width, setWidth] = useState(0);

  useLayoutEffect(() => {
    if (boxRef.current) {
      setWidth(boxRef.current.offsetWidth);
    }
  }, []);

  return (
    <div style={{ padding: "2rem" }}>
      <h2>📏 Box width: {width}px</h2>
      <div
        ref={boxRef}
        style={{
          width: "70%",
          height: "100px",
          backgroundColor: "#f0f0f0",
          border: "1px solid #ccc",
        }}
      >
        Resize the window to see layout effect
      </div>
    </div>
  );
}
```

---

### 🧠 `useLayoutEffect` vs `useEffect`

| Hook              | Fires               | Use for                      |
| ----------------- | ------------------- | ---------------------------- |
| `useEffect`       | After paint (async) | Side effects, API calls      |
| `useLayoutEffect` | Before paint (sync) | Layout read/write (DOM size) |

---

## ✅ Summary Table

| Feature          | Description                                     |
| ---------------- | ----------------------------------------------- |
| Type             | Synchronous effect                              |
| When It Runs     | After DOM changes, **before paint**             |
| Common Use Cases | Measuring elements, scrolling, avoiding flicker |
| Warning          | Can block paint → avoid for async side effects  |

Let’s build a **real-world React + TypeScript example** using `useLayoutEffect` to implement a **sticky header that changes size and style when scrolling** — no flicker, no layout shift. This is a perfect `useLayoutEffect` use case!

---

## 🎯 Goal: Sticky Header with Scroll-Based Resize (no flicker)

* Header shrinks on scroll
* Layout changes smoothly before browser paint
* DOM measurements trigger re-style logic synchronously

---

## 📁 `StickyHeader.tsx`

```tsx
import { useLayoutEffect, useRef, useState } from "react";

export default function StickyHeader() {
  const headerRef = useRef<HTMLDivElement>(null);
  const [isScrolled, setIsScrolled] = useState(false);

  useLayoutEffect(() => {
    const handleScroll = () => {
      const top = window.scrollY;
      setIsScrolled(top > 60); // Trigger style update
    };

    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  return (
    <div
      ref={headerRef}
      style={{
        position: "sticky",
        top: 0,
        backgroundColor: "#ffffff",
        boxShadow: isScrolled ? "0 2px 10px rgba(0,0,0,0.1)" : "none",
        padding: isScrolled ? "10px 20px" : "30px 20px",
        fontSize: isScrolled ? "1rem" : "1.5rem",
        transition: "all 0.2s ease-in-out",
        zIndex: 1000,
      }}
    >
      Sticky Header ✨
    </div>
  );
}
```

---

## 📄 `pages/index.tsx`

```tsx
import StickyHeader from "@/components/StickyHeader";

export default function Home() {
  return (
    <div>
      <StickyHeader />
      <main style={{ padding: "2rem", lineHeight: "2rem" }}>
        {Array.from({ length: 100 }, (_, i) => (
          <p key={i}>Scroll down to see the sticky header effect</p>
        ))}
      </main>
    </div>
  );
}
```

---

### ✅ Why `useLayoutEffect`?

| Reason                      | Benefit                              |
| --------------------------- | ------------------------------------ |
| Synchronous scroll listener | Updates `setIsScrolled` before paint |
| No flicker/layout jump      | Layout is ready when paint happens   |
| Measurable header changes   | No `resizeObserver` needed here      |

Here’s a clear **W5H breakdown** of both `useDebugValue` and `useDeferredValue` in React (with TypeScript examples):

---

## 🧠 `useDebugValue` – W5H Breakdown

---

### ✅ **What** is `useDebugValue`?

`useDebugValue` is a **developer tool hook** that lets you **label and display custom values** in React DevTools when debugging custom hooks.

```tsx
useDebugValue(value);
```

---

### 💡 **Why** use it?

* Improve debugging of **custom hooks**
* Show meaningful data in **React DevTools**
* No effect in production

---

### ⏰ **When** to use it?

* Inside **custom hooks** only
* When debugging or building a hook library

---

### 🧱 Example: Custom Auth Hook

```tsx
import { useState, useEffect, useDebugValue } from "react";

function useAuth() {
  const [user, setUser] = useState<string | null>(null);

  useEffect(() => {
    setTimeout(() => setUser("Hari"), 1000); // Simulate login
  }, []);

  useDebugValue(user ? "Logged In" : "Logged Out");

  return user;
}
```

✅ In React DevTools, you’ll see:

```
🪪 useAuth: "Logged In"
```

---

## ✅ Summary: `useDebugValue`

| Feature       | Purpose                      |
| ------------- | ---------------------------- |
| Dev-only Hook | Shows debug info in DevTools |
| Used in       | Custom hooks only            |
| Cost          | No runtime effect            |

---

---

## 🕓 `useDeferredValue` – W5H Breakdown

---

### ✅ **What** is `useDeferredValue`?

`useDeferredValue` allows you to **defer an update** to a less urgent value. It helps prevent slow renders on high-priority updates (like input typing).

```tsx
const deferredValue = useDeferredValue(value);
```

---

### 💡 **Why** use it?

* Improve UI **responsiveness**
* Prioritize updates (keep typing fast)
* Prevent blocking renders

---

### ⏰ **When** to use it?

* When filtering large lists from **fast-changing input**
* Deferring non-urgent updates like **search**, **charts**, etc.

---

### 🧱 Real Example: Search Input with `useDeferredValue`

```tsx
import { useState, useDeferredValue } from "react";

const list = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);

export default function DeferredSearch() {
  const [query, setQuery] = useState("");
  const deferredQuery = useDeferredValue(query);

  const filtered = list.filter((item) => item.toLowerCase().includes(deferredQuery.toLowerCase()));

  return (
    <div style={{ padding: "2rem" }}>
      <input
        placeholder="Search..."
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        style={{ padding: "8px", width: "300px" }}
      />
      <p>Matching: {filtered.length}</p>
      <ul>{filtered.slice(0, 20).map((item) => <li key={item}>{item}</li>)}</ul>
    </div>
  );
}
```

---

## ✅ Summary: `useDeferredValue`

| Feature   | Description                         |
| --------- | ----------------------------------- |
| Hook type | Defers rendering of non-urgent data |
| Good for  | Large filtered lists, autocomplete  |
| Based on  | React 18 concurrent features        |
| Improves  | Responsiveness of fast interactions |

Let’s combine **`useTransition` + `useDeferredValue`** to build a blazing-fast **React search experience** — great for filtering large lists, dashboard queries, autocomplete, or charts.

---

## 🚀 Goal: Responsive Search with `useTransition` + `useDeferredValue`

* `useTransition`: Keeps input responsive (marks filtering as low-priority)
* `useDeferredValue`: Prevents re-rendering while user is typing
* ✅ Real-world: 10,000+ items, responsive UX

---

## 🔧 React + TypeScript Setup

```tsx
import { useState, useDeferredValue, useTransition } from "react";

const data = Array.from({ length: 10000 }, (_, i) => `🔍 Result #${i + 1}`);

export default function SmartSearch() {
  const [query, setQuery] = useState("");
  const deferredQuery = useDeferredValue(query);

  const [isPending, startTransition] = useTransition();

  const handleInput = (e: React.ChangeEvent<HTMLInputElement>) => {
    const value = e.target.value;
    startTransition(() => {
      setQuery(value);
    });
  };

  const filtered = data.filter((item) =>
    item.toLowerCase().includes(deferredQuery.toLowerCase())
  );

  return (
    <div style={{ padding: "2rem", fontFamily: "sans-serif" }}>
      <h1>🔎 Fast Search (10,000 items)</h1>
      <input
        type="text"
        onChange={handleInput}
        placeholder="Type to filter..."
        style={{ padding: "8px", width: "300px" }}
      />
      {isPending && <p>⏳ Loading...</p>}
      <p>Matches: {filtered.length}</p>
      <ul style={{ maxHeight: "300px", overflowY: "auto" }}>
        {filtered.slice(0, 20).map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

## ✅ Why This Combo?

| Hook               | Purpose                                    |
| ------------------ | ------------------------------------------ |
| `useTransition`    | Prioritize input, delay non-urgent renders |
| `useDeferredValue` | Keeps render smooth during large updates   |

---

## 📈 When to Use This Pattern

* Search bars with large datasets
* Data-heavy dashboards or reports
* UI animations + state updates (avoid jank)
* Debounced text filters, async queries, charts

Here's a complete **W5H breakdown** of both `useImperativeHandle` and `useInsertionEffect` with **React + TypeScript** examples:

---

## 🛠️ `useImperativeHandle` – W5H Breakdown

---

### ✅ **What** is `useImperativeHandle`?

It’s a React hook that **customizes the ref** exposed to parent components using `forwardRef`.

```tsx
useImperativeHandle(ref, () => ({ methods or values }));
```

---

### 💡 **Why** use it?

* To **expose controlled functions** (like `.focus()`, `.scrollToTop()`)
* Avoid exposing full internal DOM/component state
* Used in component libraries (e.g., modals, inputs, carousels)

---

### ⏰ **When** to use it?

* When parent needs to **trigger child actions via ref**
* For building **imperative APIs** inside function components

---

### ⚙️ Example: Expose a `focus()` method from child

```tsx
import { forwardRef, useImperativeHandle, useRef } from "react";

type InputHandle = {
  focus: () => void;
};

const FancyInput = forwardRef<InputHandle>((_, ref) => {
  const inputRef = useRef<HTMLInputElement>(null);

  useImperativeHandle(ref, () => ({
    focus: () => inputRef.current?.focus(),
  }));

  return <input ref={inputRef} placeholder="Type here..." />;
});

export default FancyInput;
```

```tsx
// Parent.tsx
import { useRef } from "react";
import FancyInput from "./FancyInput";

export default function Parent() {
  const inputRef = useRef<{ focus: () => void }>(null);

  return (
    <div>
      <FancyInput ref={inputRef} />
      <button onClick={() => inputRef.current?.focus()}>Focus Input</button>
    </div>
  );
}
```

---

## 🧵 `useInsertionEffect` – W5H Breakdown

---

### ✅ **What** is `useInsertionEffect`?

`useInsertionEffect` is a **low-level React hook** used to **inject styles before browser paints** (very early in commit phase).

```tsx
useInsertionEffect(() => {
  // Inject styles before layout effect
}, []);
```

---

### 💡 **Why** use it?

* For **CSS-in-JS libraries** (like Emotion, styled-components)
* Ensures styles are injected **before any layout reads**
* Prevents flickers/layout shift

---

### ⏰ **When** to use it?

* Only for libraries or custom renderers managing **dynamic CSS**
* **Avoid using it for general logic or data**

---

### ⚙️ Example: Inject a dynamic style

```tsx
import { useInsertionEffect } from "react";

export default function StyledBox() {
  useInsertionEffect(() => {
    const style = document.createElement("style");
    style.innerHTML = `
      .dynamic-style {
        color: white;
        background: teal;
        padding: 1rem;
        font-weight: bold;
      }
    `;
    document.head.appendChild(style);
    return () => {
      document.head.removeChild(style);
    };
  }, []);

  return <div className="dynamic-style">Inserted Style with useInsertionEffect</div>;
}
```

---

## ⚠️ Comparison Summary

| Hook                  | Use Case                          | Danger Zone                       |
| --------------------- | --------------------------------- | --------------------------------- |
| `useImperativeHandle` | Expose methods to parent via ref  | Don’t misuse to break abstraction |
| `useInsertionEffect`  | Inject styles before layout phase | Don’t use for async/data logic    |

Here’s a full **W5H breakdown** of `useOptimistic` — introduced in **React 18.2+ / React 19** for managing **optimistic UI updates** — with deep explanation and real examples.

---

## ⚡ `useOptimistic` – W5H Breakdown

---

### ✅ **What** is `useOptimistic`?

`useOptimistic` is a **React 19 hook** that helps you **optimistically update UI state** before a server mutation (like API call) completes.

```tsx
const [optimisticState, addOptimistic] = useOptimistic(state, updateFn);
```

It lets you **temporarily assume success**, improving UX by updating UI instantly.

---

### 💡 **Why** use it?

* Avoids waiting for server response before updating UI
* Prevents flicker/latency for user actions (e.g. like, add-to-cart)
* Keeps logic clean, native to React — **no state duplication or hacks**

---

### ⏰ **When** to use it?

* On slow server interactions
* For **form submissions**, **chat messages**, **likes**, **task toggles**, etc.
* Inside **Server Actions** in React Server Components (RSC)

---

### 🧠 **How** does it work?

* Takes your real state and an updater
* Lets you **immediately simulate** a new UI state
* Then **replaces it** with server-confirmed state after mutation completes

---

## ✅ Real Example: Optimistic Todo Toggle

```tsx
"use client";
import { useOptimistic, useState } from "react";

type Todo = { id: number; title: string; done: boolean };

export default function OptimisticTodo() {
  const [todos, setTodos] = useState<Todo[]>([
    { id: 1, title: "Learn React", done: false },
    { id: 2, title: "Build App", done: false },
  ]);

  const [optimisticTodos, addOptimistic] = useOptimistic(
    todos,
    (prev, updatedTodo: Todo) =>
      prev.map((t) => (t.id === updatedTodo.id ? updatedTodo : t))
  );

  const toggleTodo = async (todo: Todo) => {
    // Optimistic update
    addOptimistic({ ...todo, done: !todo.done });

    // Simulate API delay
    await new Promise((res) => setTimeout(res, 1000));

    // Then apply real update
    setTodos((prev) =>
      prev.map((t) => (t.id === todo.id ? { ...t, done: !t.done } : t))
    );
  };

  return (
    <div style={{ padding: "2rem" }}>
      <h2>✅ Optimistic Todos</h2>
      <ul>
        {optimisticTodos.map((todo) => (
          <li key={todo.id}>
            <label>
              <input
                type="checkbox"
                checked={todo.done}
                onChange={() => toggleTodo(todo)}
              />
              {todo.title}
            </label>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## ✅ Summary Table

| Feature           | Description                        |
| ----------------- | ---------------------------------- |
| `useOptimistic()` | For optimistic UI updates          |
| Best for          | Mutations: toggles, likes, forms   |
| Part of           | React 19 / App Router              |
| Replaces          | Manual UI duplication + rollback   |
| Works with        | Server Actions & Client Components |

---

Would you like to:

* Combine it with **form actions** and `useFormState`?
* See a **chat app message sending** example?
* Compare to `useTransition` or Redux optimistic logic?

Let's take `useOptimistic` further and build a **real-world optimistic chat message sender** using **React 19 + Server Actions + useOptimistic + useFormState**.

---

## 💬 Scenario: Optimistic Chat App

* Users send a message
* UI updates **instantly** (optimistically) before server saves it
* Message is later confirmed (or rolled back if needed)

---

### 📁 File Structure (App Router)

```
/app
  /chat
    page.tsx         ← Chat UI
    actions.ts       ← Server Action to send message
/components
  ChatInput.tsx
```

---

## ✅ Step 1: `app/chat/actions.ts` (Server Action)

```tsx
"use server";

let messages: { id: number; text: string }[] = [];

export async function sendMessage(prevState: any, formData: FormData) {
  const text = formData.get("text") as string;
  await new Promise((res) => setTimeout(res, 1000)); // simulate delay

  const message = { id: Date.now(), text };
  messages.push(message);
  return { success: true, messages };
}
```

---

## ✅ Step 2: `app/chat/page.tsx`

```tsx
"use client";

import { useOptimistic, useState } from "react";
import { sendMessage } from "./actions";
import ChatInput from "@/components/ChatInput";

export default function ChatPage() {
  const [messages, setMessages] = useState<{ id: number; text: string }[]>([]);

  const [optimisticMessages, addOptimistic] = useOptimistic(
    messages,
    (prev, newMsg: { id: number; text: string }) => [...prev, newMsg]
  );

  return (
    <div style={{ padding: "2rem" }}>
      <h2>💬 Chat</h2>
      <ul>
        {optimisticMessages.map((msg) => (
          <li key={msg.id}>{msg.text}</li>
        ))}
      </ul>
      <ChatInput
        onSend={async (text) => {
          const newMessage = { id: Date.now(), text };
          addOptimistic(newMessage);
          const res = await sendMessage({}, new FormData([[["text", text]]]));
          setMessages(res.messages); // update with real state
        }}
      />
    </div>
  );
}
```

---

## ✅ Step 3: `components/ChatInput.tsx`

```tsx
"use client";
import { useState } from "react";

export default function ChatInput({ onSend }: { onSend: (text: string) => void }) {
  const [text, setText] = useState("");

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    onSend(text);
    setText("");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={text}
        onChange={(e) => setText(e.target.value)}
        placeholder="Type a message"
        style={{ padding: "0.5rem", width: "70%" }}
      />
      <button type="submit" style={{ marginLeft: "1rem" }}>
        Send
      </button>
    </form>
  );
}
```

---

## ✅ Summary: Optimistic + Form State

| Concept           | Hook Used         | Purpose                       |
| ----------------- | ----------------- | ----------------------------- |
| Instant UI update | `useOptimistic`   | Simulate UI changes early     |
| Server mutation   | `sendMessage`     | Store actual data             |
| Form trigger      | `onSend` callback | Integrate into form component |

Great! Let's **extend the chat app with `useFormState`** to manage the form's **server-side validation**, **submission state**, and integrate it smoothly with `useOptimistic` for **instant UI feedback**.

---

## 🧠 Why `useFormState` + `useOptimistic`?

| Feature         | Benefit                                              |
| --------------- | ---------------------------------------------------- |
| `useFormState`  | Tracks server validation, errors, and status         |
| `useOptimistic` | Shows the message in UI **immediately** on send      |
| Combined        | Smooth user experience + backend validation fallback |

---

## ✅ Final Setup Overview

We'll:

1. Use `useFormState()` to bind server action to form
2. Display server errors (e.g., empty message)
3. Optimistically add messages with `useOptimistic`

---

## 🔧 Step-by-Step Integration

---

### ✅ 1. `app/chat/actions.ts` (updated)

```tsx
"use server";

let messages: { id: number; text: string }[] = [];

export async function sendMessage(prevState: any, formData: FormData) {
  const text = (formData.get("text") as string)?.trim();

  if (!text) {
    return { error: "Message can't be empty", messages };
  }

  await new Promise((res) => setTimeout(res, 800)); // simulate delay

  const message = { id: Date.now(), text };
  messages.push(message);

  return { success: true, messages };
}
```

---

### ✅ 2. `app/chat/page.tsx`

```tsx
"use client";

import { useOptimistic, useState } from "react";
import { useFormState } from "react-dom";
import { sendMessage } from "./actions";
import ChatInput from "@/components/ChatInput";

export default function ChatPage() {
  const [messages, setMessages] = useState<{ id: number; text: string }[]>([]);

  const [formState, formAction] = useFormState(sendMessage, { error: "", messages: [] });

  const [optimisticMessages, addOptimistic] = useOptimistic(
    messages,
    (prev, newMsg: { id: number; text: string }) => [...prev, newMsg]
  );

  return (
    <div style={{ padding: "2rem" }}>
      <h2>💬 Optimistic Chat</h2>

      <ul>
        {optimisticMessages.map((msg) => (
          <li key={msg.id}>{msg.text}</li>
        ))}
      </ul>

      <ChatInput
        formAction={async (formData) => {
          const text = formData.get("text") as string;
          const newMessage = { id: Date.now(), text };
          addOptimistic(newMessage);
          const result = await sendMessage({}, formData);
          setMessages(result.messages); // sync real state
        }}
        serverAction={formAction}
        formState={formState}
      />
    </div>
  );
}
```

---

### ✅ 3. `components/ChatInput.tsx`

```tsx
"use client";
import { useRef } from "react";

export default function ChatInput({
  serverAction,
  formAction,
  formState,
}: {
  serverAction: (formData: FormData) => void;
  formAction: (formData: FormData) => void;
  formState: { error?: string };
}) {
  const formRef = useRef<HTMLFormElement>(null);

  const handleSubmit = async (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    const formData = new FormData(formRef.current!);
    await formAction(formData); // optimistic
    serverAction(formData); // real update
    formRef.current?.reset(); // reset input
  };

  return (
    <form ref={formRef} onSubmit={handleSubmit} style={{ marginTop: "1rem" }}>
      <input
        name="text"
        placeholder="Type a message"
        style={{ padding: "0.5rem", width: "70%" }}
      />
      <button type="submit" style={{ marginLeft: "1rem" }}>
        Send
      </button>
      {formState?.error && (
        <p style={{ color: "red", marginTop: "0.5rem" }}>{formState.error}</p>
      )}
    </form>
  );
}
```

---

## ✅ Key Benefits

| Hook            | Role                             |
| --------------- | -------------------------------- |
| `useFormState`  | Validates input, shows errors    |
| `useOptimistic` | UI updates instantly, no flicker |
| `useRef`        | Reset form cleanly               |

Here's a deep **W5H breakdown** of both `useSyncExternalStore` and `useTransition` with real examples in React (TypeScript-ready).

---

## 🔁 `useSyncExternalStore` – W5H

---

### ✅ **What** is it?

`useSyncExternalStore` is a React hook for subscribing to **external, non-React stores** (like Redux, Zustand, localStorage, etc.) **safely with concurrent rendering**.

```tsx
const value = useSyncExternalStore(subscribe, getSnapshot);
```

---

### 💡 **Why** use it?

* Prevent tearing during concurrent rendering
* Use **external stores** (without useState/useEffect hacks)
* Core for state libraries like Redux v8, Zustand, Jotai

---

### ⏰ **When** to use it?

* When state **lives outside React**
* Want to **sync it into React components**

---

### 🧠 How it works?

1. `subscribe`: tells React how to listen for changes
2. `getSnapshot`: returns current value (sync)
3. React re-renders when `subscribe` signals update

---

### ⚙️ Example: Subscribe to `window.location.pathname`

```tsx
function usePathname() {
  return useSyncExternalStore(
    (cb) => {
      window.addEventListener("popstate", cb);
      return () => window.removeEventListener("popstate", cb);
    },
    () => window.location.pathname
  );
}

function PathViewer() {
  const path = usePathname();
  return <p>📍 Current Path: {path}</p>;
}
```

---

## 🧵 `useTransition` – W5H

---

### ✅ **What** is it?

`useTransition` lets you **mark updates as non-urgent**, preventing UI from blocking on slow renders (e.g., large lists or state updates).

```tsx
const [isPending, startTransition] = useTransition();
```

---

### 💡 **Why** use it?

* Keeps input fast while deferring expensive rendering
* Avoids blocking UX for non-critical updates
* Improves responsiveness for filters, search, graphs, etc.

---

### ⏰ **When** to use it?

* When user types → long re-renders (filtering)
* Tab switching, UI transitions, route preloading

---

### ⚙️ Real Example: Filter a large list

```tsx
const list = Array.from({ length: 5000 }, (_, i) => `Item ${i + 1}`);

export default function TransitionExample() {
  const [input, setInput] = useState("");
  const [results, setResults] = useState<string[]>([]);
  const [isPending, startTransition] = useTransition();

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const value = e.target.value;
    setInput(value);

    startTransition(() => {
      const filtered = list.filter((item) =>
        item.toLowerCase().includes(value.toLowerCase())
      );
      setResults(filtered);
    });
  };

  return (
    <div>
      <input value={input} onChange={handleChange} placeholder="Search..." />
      {isPending && <p>⏳ Filtering...</p>}
      <ul>
        {results.slice(0, 20).map((r) => (
          <li key={r}>{r}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

## ✅ Comparison Summary

| Hook                   | Purpose                                  |
| ---------------------- | ---------------------------------------- |
| `useSyncExternalStore` | Subscribe to external (non-React) stores |
| `useTransition`        | Defer non-urgent state updates           |

Let’s take it deeper — we’ll explore:

---

## ✅ `useSyncExternalStore` with a Custom Store

## ✅ Compare `useTransition` vs `useDeferredValue` in a real app

---

### 🔁 1. `useSyncExternalStore` with a Custom Global Store

Let’s build a tiny **custom counter store** (outside React) and sync it using `useSyncExternalStore`.

#### 📦 `store/counter.ts`

```ts
// A basic custom store (non-React)
let count = 0;
let listeners: (() => void)[] = [];

export const counterStore = {
  getSnapshot: () => count,

  increment: () => {
    count++;
    listeners.forEach((fn) => fn());
  },

  subscribe: (callback: () => void) => {
    listeners.push(callback);
    return () => {
      listeners = listeners.filter((l) => l !== callback);
    };
  },
};
```

#### 📘 `useCounter.ts`

```ts
import { useSyncExternalStore } from "react";
import { counterStore } from "./store/counter";

export const useCounter = () =>
  useSyncExternalStore(counterStore.subscribe, counterStore.getSnapshot);
```

#### 📟 `Counter.tsx`

```tsx
import { useCounter } from "@/useCounter";
import { counterStore } from "@/store/counter";

export default function Counter() {
  const count = useCounter();

  return (
    <div>
      <h2>🔢 Count: {count}</h2>
      <button onClick={counterStore.increment}>Increment</button>
    </div>
  );
}
```

✅ This syncs **external state** into React **safely** even during concurrent renders.

---

### 🔄 2. `useTransition` vs `useDeferredValue`

| Use Case            | `useTransition`                              | `useDeferredValue`                           |
| ------------------- | -------------------------------------------- | -------------------------------------------- |
| 🔧 Type             | Hook to schedule state updates               | Hook to delay usage of a value               |
| 📥 Trigger          | Wraps update: `startTransition(() => {...})` | Works on existing state value                |
| 🧠 Mental Model     | “Defer this render work”                     | “Use stale value until update completes”     |
| 🎯 Use in Forms     | Type + filter in real time (non-blocking)    | Delay result rendering during typing         |
| 🧪 With `isPending` | Yes                                          | No built-in state, use `useEffect` if needed |

---

### 🧪 Demo Idea: Search Bar with Both

#### 🔍 `SearchBox.tsx` using both:

```tsx
const [input, setInput] = useState("");
const deferredInput = useDeferredValue(input);
const [isPending, startTransition] = useTransition();

const filtered = useMemo(() => {
  return data.filter((item) =>
    item.toLowerCase().includes(deferredInput.toLowerCase())
  );
}, [deferredInput]);

function handleChange(e: React.ChangeEvent<HTMLInputElement>) {
  const val = e.target.value;
  startTransition(() => setInput(val));
}
```

✅ `useTransition` makes typing smooth
✅ `useDeferredValue` ensures expensive rendering uses **deferred** input

Here’s a deep dive into all the React APIs and experimental features you listed — with **what they do**, **why/when to use them**, and examples where applicable:

---

## ✅ Core React APIs

---

### 1. `React.createContext()`

* **Purpose**: Share data (like theme/auth) deeply without prop drilling.
* ✅ Stable since React 16.3

```tsx
const ThemeContext = createContext("light");
```

---

### 2. `React.memo()`

* **Purpose**: Memoize a component to avoid re-renders if props don’t change.
* ✅ Works like `React.PureComponent`

```tsx
const MyComp = React.memo((props) => <div>{props.value}</div>);
```

---

### 3. `React.lazy()`

* **Purpose**: Code-split components with dynamic `import()`.
* ✅ Combined with `Suspense`.

```tsx
const LazyPage = React.lazy(() => import("./Page"));
```

---

### 4. `React.startTransition()`

* **Purpose**: Defer low-priority UI updates to avoid UI blocking.
* ✅ Use with `useTransition`.

```tsx
startTransition(() => setState(...));
```

---

### 5. `React.use()`

* **Purpose**: Await promises in React components directly (React 19+)
* ✅ For Server Components + Suspense

```tsx
const data = use(fetchData());
```

---

## 🧪 Experimental APIs (React Compiler / Taint Tracking)

---

### 6. `experimental_taintObjectReference(obj, reason)`

* **Purpose**: Tags a JS object so React Compiler avoids optimizations using it.
* 🧪 Used for debugging side-effects or impure objects.

```tsx
experimental_taintObjectReference(userData, "Mutates after render");
```

---

### 7. `experimental_taintUniqueValue(val, reason)`

* **Purpose**: Tags a primitive/unique value for tracking usage inside components.
* Helps React Compiler detect **non-deterministic logic**.

```tsx
const timestamp = Date.now();
experimental_taintUniqueValue(timestamp, "Avoid using in render");
```

---

## 🧠 Internal/Advanced APIs

---

### 8. `act()`

* **Purpose**: Wrap tests so all updates are flushed before assertions.
* ✅ For `@testing-library/react` and unit tests.

```tsx
act(() => {
  fireEvent.click(button);
});
```

---

### 9. `cache()` – React 18+ (Server Functions)

* **Purpose**: Memoizes async server functions in RSC (like `getUser()`).
* ✅ Avoids unnecessary fetches on re-renders.

```tsx
const getData = cache(async () => {
  return await fetch("...");
});
```

---

### 10. `captureOwnerStack()` (Internal)

* **Purpose**: Internal React error-tracing tool.
* 🧪 Not intended for public use.

---

## Summary Table

| API                   | Type         | Usage                     |
| --------------------- | ------------ | ------------------------- |
| `createContext`       | Core         | Global state (theme/auth) |
| `memo`                | Core         | Memoize components        |
| `lazy`                | Core         | Dynamic import/code split |
| `startTransition`     | Core         | Prioritize UI updates     |
| `use()`               | React 19+    | Await inside components   |
| `experimental_taint*` | Experimental | Track impure values       |
| `act()`               | Testing      | Flush updates before test |
| `cache()`             | Server       | Memoize server functions  |
| `captureOwnerStack()` | Internal     | Error tracing             |

Great! Let’s build a **real-world React 19 app** using all of the following together:

---

## 🚀 Real-World App: Blog with Cached Server Fetching, Transitions, and Memoization

---

### 🎯 Goals:

| Feature                    | Tech Used                              |
| -------------------------- | -------------------------------------- |
| SSR + Async fetch          | `React.use()` + `cache()`              |
| UI Responsiveness          | `startTransition` + `useDeferredValue` |
| Performance optimization   | `React.memo()` + `lazy()`              |
| Server fetch deduplication | `cache()`                              |
| Error handling (testable)  | `act()` (in test file)                 |

---

### 🗂️ Folder Structure

```
/app
  /blog
    page.tsx         ← SSR blog page (uses `use` + `cache`)
    client.tsx       ← `useTransition` + filter
/components
  PostList.tsx       ← Memoized list component
  PostCard.tsx       ← Lazy-loaded post preview
/lib
  fetchPosts.ts      ← Server `cache()` function
```

---

### 🧠 1. `lib/fetchPosts.ts` — server + cache

```tsx
import { cache } from "react";

export const fetchPosts = cache(async () => {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts", {
    next: { revalidate: 60 }, // for Next.js 14
  });
  return res.json();
});
```

---

### ⚙️ 2. `app/blog/page.tsx` — SSR + use()

```tsx
import { use } from "react";
import { fetchPosts } from "@/lib/fetchPosts";
import BlogClient from "./client";

export default function BlogPage() {
  const posts = use(fetchPosts()); // React 19 await

  return <BlogClient initialPosts={posts} />;
}
```

---

### 🖥️ 3. `app/blog/client.tsx` — `startTransition` + `useDeferredValue`

```tsx
"use client";

import { useState, useTransition, useDeferredValue } from "react";
import PostList from "@/components/PostList";

export default function BlogClient({ initialPosts }: { initialPosts: any[] }) {
  const [input, setInput] = useState("");
  const [isPending, startTransition] = useTransition();

  const deferredInput = useDeferredValue(input);

  const filteredPosts = initialPosts.filter((post) =>
    post.title.toLowerCase().includes(deferredInput.toLowerCase())
  );

  return (
    <>
      <input
        placeholder="Search posts"
        value={input}
        onChange={(e) =>
          startTransition(() => {
            setInput(e.target.value);
          })
        }
      />
      {isPending && <p>🔄 Filtering...</p>}
      <PostList posts={filteredPosts} />
    </>
  );
}
```

---

### 🧱 4. `components/PostList.tsx` — `React.memo`

```tsx
import PostCard from "./PostCard";

const PostList = React.memo(({ posts }: { posts: any[] }) => {
  return (
    <ul>
      {posts.map((post) => (
        <PostCard key={post.id} post={post} />
      ))}
    </ul>
  );
});

export default PostList;
```

---

### 🧩 5. `components/PostCard.tsx` — `React.lazy`

```tsx
import React from "react";

const PostCard = React.lazy(() => import("./PostCardInner"));

export default function Wrapper(props: any) {
  return (
    <React.Suspense fallback={<p>Loading post…</p>}>
      <PostCard {...props} />
    </React.Suspense>
  );
}
```

---

### 🧪 6. `tests/blog.test.tsx` — with `act()`

```tsx
import { render, screen } from "@testing-library/react";
import { act } from "react-dom/test-utils";
import BlogClient from "../app/blog/client";

test("filters posts", async () => {
  await act(async () => {
    render(<BlogClient initialPosts={[{ title: "React" }, { title: "Vue" }]} />);
  });

  expect(screen.getByText("React")).toBeInTheDocument();
});
```

---

## ✅ Final Result

* 🔁 SSR powered by `use(fetchPosts())`
* 🧠 Fuzzy search using `useDeferredValue`
* 🧵 Smooth UI via `startTransition`
* 📦 Post list optimized with `memo` and `lazy`
* 🧪 Tested safely with `act`











