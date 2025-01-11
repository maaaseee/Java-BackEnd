Dada una lista de números, encontrar el segundo número más grande. Si no hay suficiente información, devolver un valor predeterminado (-1).
``` Java
List<Integer> numbers = List.of(3, 5, 7, 5, 9, 2, 8); 
int secondLargest = numbers.stream() 
	.distinct() // Eliminar duplicados 
	.sorted(Comparator.reverseOrder()) // Ordenar en orden descendente 
	.skip(1) // Ignorar el más grande 
	.findFirst() // Tomar el segundo más grande 
	.orElse(-1); // Valor predeterminado 

System.out.println(secondLargest); // Result: 8
```