# Handing events 


## Passing a function reference as event handlers 

You defined the handleClick function and then passed it as a prop to <button>.  handleClick is an event handler. Event handler functions:

```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}

```


## Using an inline arrow function

You defined the handleClick function and then passed it as a prop to <button>.  handleClick is an event handler. Event handler functions:

```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={() => handleClick()}>
      Click me
    </button>
  );
}

```