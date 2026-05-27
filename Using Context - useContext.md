# Using Context - useContext

`useContext` is a React Hook that lets you share data across components without passing props manually at every level.

Instead of passing data from parent to child to grandchild through props, you put the data in a context and any component can read it directly.

---

## Syntax

```jsx
const value = useContext(MyContext);
```

---

## Three Steps to Use Context

1. **Create** the context using `createContext`
2. **Wrap** your components with the context Provider and pass the value
3. **Read** the value inside any child component using `useContext`

---

## Basic Example — Sharing a Username

**Step 1 — Create the context**

```jsx
import { createContext } from "react";

const UserContext = createContext();

export default UserContext;
```

---

**Step 2 — Wrap components with the Provider**

```jsx
import { useState } from "react";
import UserContext from "./UserContext";
import Profile from "./Profile";

function App() {
	const [username] = useState("John");

	return (
		<UserContext.Provider value={username}>
			<Profile />
		</UserContext.Provider>
	);
}

export default App;
```

Here:
- `UserContext.Provider` wraps the components that need access to the value.
- `value={username}` passes the data into the context.

---

**Step 3 — Read the value in a child component**

```jsx
import { useContext } from "react";
import UserContext from "./UserContext";

function Profile() {
	const username = useContext(UserContext);

	return <h2>Logged in as: {username}</h2>;
}

export default Profile;
```

Here:
- `useContext(UserContext)` reads the value directly from the context.
- No props were passed from `App` to `Profile`.

---

## Without Context vs With Context

**Without context** — you pass props through every level:

```jsx
<App username="John">
	<Profile username="John">
		<Avatar username="John" />
	</Profile>
</App>
```

**With context** — any component reads the value directly:

```jsx
const username = useContext(UserContext);
```

---

## Important Notes

- Use `useContext` when multiple components at different levels need the same data.
- The component must be inside the `Provider` to read the context value.
- If the value in the Provider changes, all components using that context will re-render.
- Do not call `useContext` inside loops, conditions, or nested functions — always call it at the top level of your component.
