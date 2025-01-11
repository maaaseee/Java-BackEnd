Un **Stream** es una secuencia de elementos que soporta operaciones funcionales y declarativas para procesar datos. Los Streams no almacenan datos, sino que procesan datos de una fuente (como una colección, un array, o un archivo).

### **Principales características**

1. **Declarativo**: Permite expresar el "qué" en lugar del "cómo".
2. **Lazily Evaluated**: Las operaciones intermedias (como `filter`) no se ejecutan hasta que se invoca una operación terminal (como `collect`).
3. **Inmutable**: Los Streams no modifican la fuente de datos original.
4. **Paralelismo**: Puedes usar Streams para procesamiento paralelo con facilidad (`parallelStream()`).

### **Tipos de Operaciones en Streams**

1. **Operaciones intermedias**:
    - Devuelven un nuevo Stream.
    - Se ejecutan de forma "perezosa" (lazy).
    - Ejemplos: `filter`, `map`, `sorted`, `distinct`, `limit`.
2. **Operaciones terminales**:
    - Devuelven un resultado (colección, primitivo, o void).
    - Ejemplos: `collect`, `forEach`, `reduce`, `count`.

### **Creación de Streams**

Los **Streams** se pueden crear desde diversas fuentes:

- **Desde colecciones:**
	``` Java
	List<String> names = List.of("Alice", "Bob", "Charlie"); 
	Stream<String> stream = names.stream();
	```
- **Desde un array:**
	``` Java
	int[] numbers = {1, 2, 3}; 
	IntStream intStream = Arrays.stream(numbers);
	```
- **Desde valores literales:**
	``` Java
	Stream<String> stream = Stream.of("A", "B", "C");
	```

### **Operaciones Comunes en Streams**

1. `filter`: Filtra elementos basados en una condición.
``` Java
List<String> names = List.of("Alice", "Bob", "Charlie"); 
List<String> filtered = names.stream() 
			.filter(name -> name.startsWith("A")) 
			.collect(Collectors.toList()); 
System.out.println(filtered); // Result: [Alice]
```
2. `map`: Transforma cada elemento.
``` Java
List<String> names = List.of("Alice", "Bob"); 
List<Integer> lengths = names.stream() 
			.map(String::length) 
			.collect(Collectors.toList()); 
System.out.println(lengths); // Result: [5, 3]
```
3. `sorted`: Ordena elementos.
``` Java
List<Integer> numbers = List.of(5, 3, 1, 4, 2); 
List<Integer> sorted = numbers.stream() 
			.sorted() 
			.collect(Collectors.toList()); 
System.out.println(sorted); // Result: [1, 2, 3, 4, 5]
```
4. `reduce`: Reduce el stream a un único valor.
``` Java
List<Integer> numbers = List.of(1, 2, 3, 4); 
int sum = numbers.stream() 
	.reduce(0, Integer::sum); 
System.out.println(sum); // Result: 10
```
5. `collect`: Recoge el resultado en una colección o formato deseado.
``` Java
List<String> names = List.of("Alice", "Bob", "Charlie"); 
String joined = names.stream() 
		.collect(Collectors.joining(", ")); 
System.out.println(joined); // Result: "Alice, Bob, Charlie"
```

### **Ejemplo Completo**

#### Problema:
Dada una lista de números, encuentra los cuadrados de los números pares, ordénalos en orden descendente, y recógelos en una lista.

``` Java
List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6); 
List<Integer> result = numbers.stream() 
			.filter(n -> n % 2 == 0) // Filtrar números pares 
			.map(n -> n * n) // Obtener el cuadrado 
			.sorted(Comparator.reverseOrder()) // Ordenar en orden descendente 
			.collect(Collectors.toList()); // Recoger en una lista 
			
System.out.println(result); // Result: [36, 16, 4]
```
### **Ejercicios para Practicar**

1. Dada una lista de nombres, encontrar los que tienen más de 4 letras, para luego convertirlos a mayúscula. **[[Java Core/Java 8+/2. Stream/Ejemplo 1]]**
2. Calcular la suma de los cubos de todos los números impares en una lista. **[[Java Core/Java 8+/2. Stream/Ejemplo 2]]**
3. De una lista de nombres, agrupar los que comienzan con la misma letra usando `Collectors.groupingBy`. **[[Java Core/Java 8+/2. Stream/Ejemplo 3]]**
4. Dada una lista de números, encontrar el segundo número más grande. Si no hay suficiente información, devolver un valor predeterminado (-1). **[[Java Core/Java 8+/2. Stream/Ejemplo 4]]**
5. Dado un archivo de texto, encontrar la palabra más larga. **[[Ejemplo 5]]**
6. Dada una lista de productos con categorías, agrupar los productos por categoría y contar cuántos hay en cada una. [[Ejemplo 6]]

En caso de necesitar buscar algún método específico, acá está la [documentación de Java](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html).

Si buscas mas ejercicios, [esta página tiene algunos sobre Streams](https://www.w3resource.com/java-exercises/stream/index.php).