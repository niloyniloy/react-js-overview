# Using States - useState

`useState` is a React Hook that lets a component remember data.

When the state value changes, React renders the component again with the new value.

## Basic Example

```jsx
import { useState } from "react";

function Counter() {
	const [count, setCount] = useState(0);

	function handleIncrease() {
		setCount(count + 1);
	}

	return (
		<>
			<h2>Count: {count}</h2>
			<button onClick={handleIncrease}>Increase</button>
		</>
	);
}

export default Counter;
```

Here:

- `count` is the current state value.
- `setCount` is the function used to update the state.
- `useState(0)` means the starting value of `count` is `0`.
- When the button is clicked, `setCount(count + 1)` updates the value and React shows the new count.

## Shorter Inline Example

```jsx
import { useState } from "react";

function Counter() {
	const [count, setCount] = useState(0);

	return (
		<>
			<p>{count}</p>
			<button onClick={() => setCount(count + 1)}>Increase</button>
		</>
	);
}

export default Counter;
```


## Extending useState & updating specific state 

```jsx
import { useState } from "react";

function Counter() {
	const [states, setStates] = useState({
		count: 0,
		status: "Loading ..."
	});

	const handleIncrease = () => {
		setStates({
			...states,
			count: states.count + 1
		});
	};

	return (
		<>
			<p>{states.count}</p>

			<button onClick={handleIncrease}>
				Increase
			</button>
		</>
	);
}

export default Counter;
```
