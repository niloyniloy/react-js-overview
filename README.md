# React JS Overview

A personal learning reference for React JS fundamentals. Each topic has its own markdown file with explanations and code examples.

---

## Topics Covered

| File | Topic |
|---|---|
| [Installations.md](./Installations.md) | How to set up a React project using Vite |
| [Components.md](./Components.md) | Creating and using components, passing props |
| [EventHandlers.md](./EventHandlers.md) | Handling events and inline arrow functions |
| [ConditionalRendering.md](./ConditionalRendering.md) | Ternary, &&, null, multiple conditions |
| [RenderingLists.md](./RenderingLists.md) | Rendering arrays, filtering before render |
| [Using States - useState.md](./Using%20States%20-%20useState.md) | useState hook, updating state, object state |
| [Using Effects - useEffect.md](./Using%20Effects%20-%20useEffect.md) | useEffect hook, dependencies, cleanup |

---

## Quick Summary

### Installation
Set up React with Vite using `npm create vite@latest`, then `npm install` and `npm run dev`.

### Components
Reusable UI building blocks. Accept data via props and return JSX.

### Event Handlers
Attach functions to events like `onClick`. Use function references or inline arrow functions.

### Conditional Rendering
Show different UI based on conditions using ternary `? :`, `&&`, or `null`.

### Rendering Lists
Use `.map()` to render arrays. Always provide a `key` prop. Use `.filter()` to narrow data before rendering.

### useState
Lets a component remember and update data. Triggers a re-render when state changes.

### useEffect
Runs side effects after render — such as fetching data, setting up subscriptions, or updating the document title. Controlled by a dependency array.

---

## Project Structure

```
react-js-overview/
├── your-folder-name/        ← Vite React project
│   ├── src/
│   │   ├── components/
│   │   │   └── BasicComponents.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
├── Installations.md
├── Components.md
├── EventHandlers.md
├── ConditionalRendering.md
├── RenderingLists.md
├── Using States - useState.md
└── Using Effects - useEffect.md
```
