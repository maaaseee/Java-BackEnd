De una lista de nombres, agrupar los que comienzan con la misma letra usando `Collectors.groupingBy`

``` Java
List<String> names = List.of("Alice", "Bob", "Charlie", "Anna", "Brian", "Catherine"); 
Map<Character, List<String>> groupedByInitial = names.stream()
		.collect(Collectors.groupingBy(name -> name.charAt(0))); // Agrupar por la primera letra

System.out.println(groupedByInitial);
/* {A=[Alice, Anna], 
	B=[Bob, Brian], 
	C=[Charlie, Catherine]}
*/
```

###  **¿Cómo funciona `Collectors.groupingBy()`?**
El método **`Collectors.groupingBy`** crea un **Map** donde:
- La **clave** se genera usando una función de clasificación (Classifier Function).
- El **valor** asociado a cada clave es una colección (o un valor agregado, dependiendo de los parámetros).

### **Sobrecargas del Método `groupingBy`**
Hay tres formas principales de usarlo:
##### 1. **`groupingBy(Classifier Function)`**
- Agrupa elementos según la clave generada por la función de clasificación.
- Los valores son listas (por defecto).
##### 2. **`groupingBy(Classifier Function, Downstream Collector)`**
- Agrupa elementos según la clave, pero puedes aplicar una operación sobre los valores de cada grupo (como contar o sumar).
##### 3. **`groupingBy(Classifier Function, Map Factory, Downstream Collector)`**
- Lo mismo que la anterior, pero permite especificar qué tipo de `Map` utilizar (por ejemplo, un `TreeMap` para ordenar).