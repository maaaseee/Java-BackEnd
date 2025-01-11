Dada una lista de productos con categorías, agrupar los productos por categoría y contar cuántos hay en cada una.

Creamos una clase Producto:
```Java
class Product { 
	private String name; 
	private String category; 
	
	public Product(String name, String category) { 
		this.name = name; 
		this.category = category; 
	} 

	public String getName() { return name; }
	public String getCategory() { return category; }
}
```

Y volvemos al main:
```Java
List<Product> products = List.of( 
	new Product("Notebook", "Electrónico"), 
	new Product("Celular", "Electrónico"), 
	new Product("Remera", "Ropa"), 
	new Product("Pantalone", "Ropa"), 
	new Product("Medias", "Ropa") 
); 
        
Map<String, Long> productCountByCategory = products.stream() 
	.collect(Collectors.groupingBy(product -> product.getCategory(), Collectors.counting())); 

System.out.println(productCountByCategory); // Result: {Electrónico=2, Ropa=3}
```