Dada una lista de nombres, encontrar los que tienen más de 4 letras, para luego convertirlos a mayúscula.

``` Java
List<String> names = List.of("Alice", "Bob", "Charlie", "Fede", "Sofía", "David", "Fran");
List<String> filteredNames = names.stream()
			.filter(n -> n.length() > 4) // Filtramos todos los nombres que tengan menos de 4 caracteres
			.map(n -> n.toUpperCase()) // A esos nombres, los pasamos a mayúsculas
			.collect(Collectors.toList()); // Recogemos en una lista

System.out.println(filteredNames); // Result: ["ALICE", "CHARLIE", "SOFÍA", "DAVID"]
```
