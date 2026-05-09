# Conditional Rendering

Conditional rendering means showing different text, values, or JSX based on a condition.

In React functional components, we usually write conditional rendering inside the `return` block using JavaScript expressions inside `{}`.

## Basic Example Using Ternary Operator

Use the ternary operator when you want to show one value if the condition is true, and another value if the condition is false.


```jsx
function UserStatus({ isLoggedIn }) {

	return (
		<>
			{isLoggedIn ? "Welcome back" : "Please login"}
		</>
	);
}

export default UserStatus;
```

Then use that component and send a boolean value.

```jsx
import UserStatus from "./components/UserStatus";

function App() {

	return (
		<>
			<UserStatus isLoggedIn={true} />
		</>
	);
}

export default App;
```

## Rendering JSX Conditionally

We can also render JSX elements conditionally.

```jsx
function Dashboard({ isLoggedIn }) {

	return (
		<>
			{isLoggedIn ? (
				<h2>Dashboard Page</h2>
			) : (
				<h2>Login Page</h2>
			)}
		</>
	);
}

export default Dashboard;
```

## Render Something Only When Condition Is True

Use `&&` when you only want to render something if the condition is true.

If `hasNotification` is `true`, the paragraph will show.

If `hasNotification` is `false`, nothing will show in that place.

```jsx
function Notification({ hasNotification }) {

	return (
		<>
			<h2>Profile</h2>

			{hasNotification && <p>You have a new notification.</p>}
		</>
	);
}

export default Notification;
```


## Render Nothing Using Null

Sometimes we want to render nothing for the false condition. In that case, we can use `null`.

```jsx
function AdminButton({ isAdmin }) {

	return (
		<>
			{isAdmin ? <button>Delete User</button> : null}
		</>
	);
}

export default AdminButton;
```

## Multiple Conditions

For multiple conditions, we can use more than one ternary operator.

```jsx
function UserRole({ role }) {

	return (
		<>
			{role === "admin" ? (
				<h2>Admin Panel</h2>
			) : role === "user" ? (
				<h2>User Dashboard</h2>
			) : (
				<h2>Guest Page</h2>
			)}
		</>
	);
}

export default UserRole;
```

## Important Notes

- Use `{}` inside JSX to write JavaScript expressions.
- Use `condition ? valueIfTrue : valueIfFalse` when you need two possible outputs.
- Use `condition && value` when you only need to show something if the condition is true.
- Use `null` when you want React to render nothing.
- Do not write a normal `if` statement directly inside JSX.

