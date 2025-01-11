4. Supongamos que tienes una configuración para el idioma de la aplicación. El programa recibe un String, con el cual se indica la configuración.
	- Si empieza con "es", devolverá "español".
	- Caso contrario, se devuelve la configuración por defecto, en este caso "inglés".

Creamos el método:
```Java
Optional<String> findLanguageConfig() { 
	return Optional.empty(); // Simula que no hay configuración de idioma 
}
```

Y lo probamos en el main:
```Java
String region = "es_AR"; // La región del usuario 
String language = findLanguageConfig() 
		.orElseGet(() -> region.startsWith("es") ? "español" : "inglés"); 
		
System.out.println(language); // Resultado: español
```

Con `orElseGet()`, el valor predeterminado **solo se genera si el original no está presente**, lo que lo hace más eficiente. A diferencia de `orElse()`, el cual se construye aunque no vaya a ser utilizado.