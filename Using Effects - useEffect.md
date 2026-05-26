# Using Effects - useEffect

`useEffect` is a React Hook that lets you run side effects in a component.

Side effects are things like fetching data, updating the document title, setting up a timer, or subscribing to something.

It runs **after** the component renders.

---

## Syntax

```jsx
useEffect(() => {
	// your side effect code here

	return () => {
		// optional cleanup
	};
}, [dependencies]);
```

- The **first argument** is a function containing your side effect.
- The **second argument** is the dependency array that controls when the effect runs.

---

## Dependency Array Rules

| Dependency Array | When the effect runs |
|---|---|
| Not provided | After every render |
| `[]` empty array | Only once, after the first render |
| `[value]` with values | After first render and whenever `value` changes |

---

## Basic Example — Run Once on Mount

```jsx
import { useEffect } from "react";

function Welcome() {

	useEffect(() => {
		console.log("Component mounted");
	}, []);

	return <h2>Welcome!</h2>;
}

export default Welcome;
```

Here:
- The empty `[]` means this effect runs only once when the component first appears on the screen.

---

## Example — Run When a Value Changes

```jsx
import { useState, useEffect } from "react";

function Counter() {
	const [count, setCount] = useState(0);

	useEffect(() => {
		document.title = `Count: ${count}`;
	}, [count]);

	return (
		<>
			<h2>Count: {count}</h2>
			<button onClick={() => setCount(count + 1)}>Increase</button>
		</>
	);
}

export default Counter;
```

Here:
- Every time `count` changes, the effect runs and updates the browser tab title.
- `[count]` in the dependency array tells React to re-run the effect when `count` changes.

---

## Example — Fetching Data

```jsx
import { useState, useEffect } from "react";

function UserList() {
	const [users, setUsers] = useState([]);

	useEffect(() => {
		fetch("https://jsonplaceholder.typicode.com/users")
			.then((response) => response.json())
			.then((data) => setUsers(data));
	}, []);

	return (
		<ul>
			{users.map((user) => (
				<li key={user.id}>{user.name}</li>
			))}
		</ul>
	);
}

export default UserList;
```

Here:
- The fetch runs once when the component mounts.
- The result is stored in `users` state and rendered as a list.

---

## Example — Cleanup Function

```jsx
import { useState, useEffect } from "react";

function Timer() {
	const [seconds, setSeconds] = useState(0);

	useEffect(() => {
		const interval = setInterval(() => {
			setSeconds((prev) => prev + 1);
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	}, []);

	return <h2>Seconds: {seconds}</h2>;
}

export default Timer;
```

Here:
- `setInterval` starts a timer when the component mounts.
- The cleanup function `clearInterval(interval)` runs when the component unmounts, stopping the timer and preventing memory leaks.

---

## Important Notes

- Always add variables used inside `useEffect` to the dependency array.
- Use an empty `[]` when you only want the effect to run once on mount.
- Return a cleanup function when you set up subscriptions, timers, or event listeners.
- Do not call `useEffect` inside loops, conditions, or nested functions — always call it at the top level of your component.
