# Components

## Basic Example 

Here is an Example of using components 

```bash
function BasicComponents() {

	return (
		<>
			Sample compoents
		</>
	);
}

export default BasicComponents;
```

Then use that BasicComponents in inside any components 

```bash
import BasicComponents from "./components/BasicComponents";

function App() {

	return (
		<>
			<BasicComponents />
		</>
	);
}

export default App;
```


## Passing data into components 

```bash
function BasicComponents({ data }) {

	return (
		<>
			Sample {data}
		</>
	);
}

export default BasicComponents;
```

Then sending data to components 
```bash
import BasicComponents from "./components/BasicComponents";

function App() {

	return (
		<>
			<BasicComponents data="components" />
		</>
	);
}

export default App;
```