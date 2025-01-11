Escribe un método que reciba un `Optional<String>` y devuelva:
- El valor en mayúsculas si está presente.
- La cadena `"VACÍO"` si no hay valor.

Primero creamos el método:
```Java
public static void checkString(Optional<String> optional) {
	optional.ifPresentOrElse(
		val -> System.out.println(val.toUpperCase()),
		() -> System.out.println("VACÍO")
	);
}
```

Y después lo probamos:
```Java
Optional<String> optional = Optional.of("fideos");
// Result: "FIDEOS"

optional = Optional.empty();
// Result: "VACÍO"

Optional.ofNullable(null);
// Result: "VACÍO"
```