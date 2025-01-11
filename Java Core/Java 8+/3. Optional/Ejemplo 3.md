Dado un `Optional<Optional<String>>`, escribe un método que:
- Devuelva el valor interno, si existe.
- Si el valor interno no existe, devuelva `"Sin datos"`.

Creamos el método:
```Java
public static String checkNestedOptional(Optional<Optional<String>> optional) {
	return optional
			.flatMap(val -> val)
			.orElse("Sin datos");
}
```

Y lo probamos en el main:
```Java
Optional<Optional<String>> optional = Optional.ofNullable(Optional.ofNullable(null));

System.out.println(checkNestedOptional(optional));
```