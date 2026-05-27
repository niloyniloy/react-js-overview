# Using Ref - useRef

`useRef` is a React Hook that lets you reference a value or a DOM element directly without causing a re-render.

Unlike `useState`, updating a ref does **not** trigger a re-render of the component.

---

## Syntax

```jsx
const ref = useRef(initialValue);
```

- `ref.current` holds the current value.
- You can read or update `ref.current` at any time.
- Changing `ref.current` does **not** cause the component to re-render.

---

## Two Main Use Cases

| Use Case | Description |
|---|---|
| Referencing a DOM element | Access and interact with an HTML element directly |
| Storing a mutable value | Keep a value between renders without triggering re-render |

---

## Basic Example — Focusing an Input

```jsx
import { useRef } from "react";

function InputFocus() {
	const inputRef = useRef(null);

	function handleFocus() {
		inputRef.current.focus();
	}

	return (
		<>
			<input ref={inputRef} type="text" placeholder="Type here..." />
			<button onClick={handleFocus}>Focus Input</button>
		</>
	);
}

export default InputFocus;
```

Here:
- `useRef(null)` creates a ref with an initial value of `null`.
- `ref={inputRef}` attaches the ref to the input element.
- `inputRef.current` gives direct access to the input DOM element.
- Clicking the button calls `.focus()` on the input without any re-render.

---

## Example — Storing a Mutable Value

```jsx
import { useState, useRef } from "react";

function RenderCount() {
	const [count, setCount] = useState(0);
	const renderCount = useRef(0);

	renderCount.current = renderCount.current + 1;

	return (
		<>
			<h2>Count: {count}</h2>
			<p>Component rendered: {renderCount.current} times</p>
			<button onClick={() => setCount(count + 1)}>Increase</button>
		</>
	);
}

export default RenderCount;
```

Here:
- `renderCount` tracks how many times the component has rendered.
- Updating `renderCount.current` does not cause an extra re-render.
- This is useful for tracking values that should persist between renders but should not trigger UI updates.

---

## Example — Storing Previous State Value

```jsx
import { useState, useEffect, useRef } from "react";

function PreviousValue() {
	const [count, setCount] = useState(0);
	const prevCount = useRef(0);

	useEffect(() => {
		prevCount.current = count;
	}, [count]);

	return (
		<>
			<h2>Current: {count}</h2>
			<h2>Previous: {prevCount.current}</h2>
			<button onClick={() => setCount(count + 1)}>Increase</button>
		</>
	);
}

export default PreviousValue;
```

Here:
- `prevCount.current` stores the previous value of `count`.
- The `useEffect` updates the ref after every render, saving the last value.
- The ref update does not cause an extra re-render.

---

## useRef vs useState

| | `useRef` | `useState` |
|---|---|---|
| Causes re-render | No | Yes |
| Persists between renders | Yes | Yes |
| Access value | `ref.current` | directly via variable |
| Use for DOM access | Yes | No |

---

## Important Notes

- `useRef` does not cause a re-render when its value changes.
- Always use `ref.current` to read or update the value.
- Use `useRef` for DOM access, timers, previous values, or any value that should not trigger a re-render.
- Do not call `useRef` inside loops, conditions, or nested functions — always call it at the top level of your component.
