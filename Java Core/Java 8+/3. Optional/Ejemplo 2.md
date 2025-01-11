Dado un `Optional<String>` que contiene un número en formato texto, realiza las siguientes acciones:
- Si el valor está presente, conviértelo a un entero.
- Si el entero es par, devuelve el número multiplicado por 2.
- Si no hay valor o no es un número válido, lanza una excepción personalizada.

Creamos el método para verificar nuestro número: 
```Java
public static Integer checkInteger(Optional<String> optional) {
	Integer toReturn = optional
			.map(Integer::parseInt)
			.filter(n -> n % 2 == 0)
			.map(n -> n * 2)
			.orElseThrow(() -> new IllegalArgumentException("Número inválido o no presente"));
	
	return toReturn;
}
```

Y probamos en el main:
```Java
Optional<String> optional = Optional.ofNullable("6");
try {
	System.out.println(checkInteger(optional));
} catch (IllegalArgumentException ex) {
	System.err.println(ex.getMessage());
} // Result: 12
```