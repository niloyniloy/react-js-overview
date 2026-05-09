# Rendering Lists

Rendering lists here 

## Rendering A List Only If Data Exists

When working with arrays, check the length before rendering.

```jsx
function ProductList({ products }) {

	return (
		<>
			<h2>Products</h2>

			{products.length > 0 ? (
				<ul>
					{products.map((product) => (
						<li key={product.id}>{product.name}</li>
					))}
				</ul>
			) : (
				<p>No products found.</p>
			)}
		</>
	);
}

export default ProductList;
```


## Appyling filter before Rendering lists 



```jsx
function BasicComponents({data}) {

	const products = [
		{ id: 1, name: "Laptop", price: 1200, category: "Electronics" },
		{ id: 2, name: "Phone", price: 800, category: "Electronics" },
		{ id: 3, name: "Shirt", price: 40, category: "Fashion" },
		{ id: 4, name: "Shoes", price: 100, category: "Fashion" },
		{ id: 5, name: "Watch", price: 250, category: null }
	];

	const filteredProducts = products.filter( product => product.price > 100  )

	return (
		<>

			{filteredProducts.map((eachProduct) => (
				<> {eachProduct.name} {eachProduct.price}</>
			))}
			
		</>
	);
}

export default BasicComponents;
```