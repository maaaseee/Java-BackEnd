Introducido en **Java 8**, **`Optional<T>`** es un contenedor que puede o no contener un valor. Su objetivo principal es **representar valores nulos de forma segura** y obligar al programador a manejar explícitamente los casos en los que el valor puede estar ausente.

### **Creación de Optional**

1. Crear un `Optional` con un valor no nulo (Si se recibe un `null`, se lanza una `NullPointerException`).
```Java
Optional<String> optional = Optional.of("Hola Mundo");
```
2. **Crear un `Optional` que puede ser nulo**
```Java
Optional<String> optional = Optional.ofNullable(null);
```
3. **Crear un `Optional` vacío**
```Java
Optional<String> emptyOptional = Optional.empty();
```

### **Uso de Optional**

- ####  **Comprobar si el valor está presente**
Puedes verificar si un valor está presente con **`isPresent`** o, de forma inversa, **`isEmpty`**.
1. isPresent():
```Java
Optional<String> optional = Optional.ofNullable(null);

if (optional.isPresent()) {
	System.out.println("Valor presente: " + optional.get());
} else {
	System.out.println("No hay valor presente.");
}
```
1. isEmpty():
```Java
Optional<String> optional = Optional.ofNullable(null);

if (optional.isEmpty()) {
	System.out.println("No hay valor presente.");
} else {
	System.out.println("Valor presente: " + optional.get());
}
```
También podríamos invertir los booleanos, por ejemplo, `!(isEmpty())` o `!(isPresent())`.

### **Transformar el valor de un Optional**

Con `Optional`, podemos:
- Aplicar una operación con `map`: 
```Java
// Transforma el valor dentro del `Optional` si está presente.
Optional<String> optional = Optional.of("Hola");
Optional<Integer> length = optional.map(String::length);
System.out.println(length.get()); // 4
```
- Encadenar operaciones con `flatMap`
```Java
// Similar a `map`, pero para funciones que ya retornan un `Optional`.
Optional<String> optional = Optional.of("Hola");
Optional<String> upperCase = optional.flatMap(val -> Optional.of(val.toUpperCase()));
System.out.println(upperCase.get()); // HOLA
```

### **Ejecutar acciones**

- #### **Si el valor está presente: `ifPresent`**
```Java
// Ejecuta un `Consumer` si el valor está presente.
Optional<String> optional = Optional.of("Hola");
optional.ifPresent(System.out::println); // Hola
```
- #### **Combinar con `ifPresentOrElse`**
```Java
// Ejecuta una acción si el valor está presente, y otra si está vacío.
Optional<String> optional = Optional.ofNullable(null);
optional.ifPresentOrElse(
    System.out::println,
    () -> System.out.println("No hay valor")
); // No hay valor
```

### **Ejemplo Completo**

Dado un repositorio de usuarios, encuentra un usuario por ID, obtiene su correo y lo imprime en mayúsculas si existe. Si no, muestra un mensaje.

1. Creamos la clase para el repositorio de usuarios:
```Java
class UserRepository { 
	public Optional<String> findUserById(int id) { 
		return id == 1 ? Optional.of("usuario@gmail.com") : Optional.empty(); 
	} 
}
```
2. En el main, ejecutamos el siguiente bloque de código:
```Java
UserRepository repository = new UserRepository();

String result = repository.findUserById(1) 
	.map(String::toUpperCase) // Transformar correo a mayúsculas 
	.orElse("Usuario no encontrado"); 

System.out.println(result); // USUARIO@GMAIL.COM 

String notFound = repository.findUserById(2) 
	.map(String::toUpperCase) 
	.orElse("Usuario no encontrado"); 

System.out.println(notFound); // Usuario no encontrado
```

### **Ejercicios para Practicar**
1. Escribe un método que reciba un `Optional<String>` y devuelva:
	- El valor en mayúsculas si está presente.
	- La cadena `"VACÍO"` si no hay valor.
```Java
Optional<String> optional = Optional.of("java");
output: "JAVA"

Optional<String> optional = Optional.empty();
output: "VACÍO"
```

**[[Java Core/Java 8+/3. Optional/Ejemplo 1|Ejemplo 1]]**

2. Dado un `Optional<String>` que contiene un número en formato texto, realiza las siguientes acciones:
	- Si el valor está presente, conviértelo a un entero.
	- Si el entero es par, devuelve el número multiplicado por 2.
	- Si no hay valor o no es un número válido, lanza una excepción personalizada.
```Java
Optional<String> optional = Optional.ofNullable("16");
try {
	System.out.println(checkInteger(optional));
} catch (IllegalArgumentException ex) {
	System.err.println(ex.getMessage());
} // Result: 32

Optional<String> optional = Optional.ofNullable("13");
try {
	System.out.println(checkInteger(optional));
} catch (IllegalArgumentException ex) {
	System.err.println(ex.getMessage());
} // Result: "Número inválido o no presente"
```

**[[Java Core/Java 8+/3. Optional/Ejemplo 2|Ejemplo 2]]**

3. Dado un `Optional<Optional<String>>`, escribe un método que:
	- Devuelva el valor interno, si existe.
	- Si el valor interno no existe, devuelva `"Sin datos"`.
```Java
Optional<Optional<String>> optional = Optional.ofNullable(Optional.ofNullable(null));

System.out.println(checkNestedOptional(optional)); 
// Result: "Sin datos"

Optional<Optional<String>> optional = Optional.ofNullable(Optional.ofNullable("Cadenita"));

System.out.println(checkNestedOptional(optional)); 
// Result: "Cadenita"
```

**[[Java Core/Java 8+/3. Optional/Ejemplo 3|Ejemplo 3]]**

4. Supongamos que tienes una configuración para el idioma de la aplicación. El programa recibe un String, con el cual se indica la configuración.
	- Si empieza con "es", devolverá "español".
	- Caso contrario, se devuelve la configuración por defecto, en este caso "inglés".

```Java
String region = "es_AR"; // La región del usuario 
String language = findLanguageConfig() 
		.orElseGet(() -> region.startsWith("es") ? "español" : "inglés"); 
		
System.out.println(language); // Resultado: español
```

**[[Java Core/Java 8+/3. Optional/Ejemplo 4|Ejemplo 4]]**