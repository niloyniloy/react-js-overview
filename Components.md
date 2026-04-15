# Components

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

