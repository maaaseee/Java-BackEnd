Dado un archivo de texto, encontrar la palabra más larga.
``` Java
try (Stream<String> lines = new BufferedReader(new FileReader("example.txt")).lines()) {
	String longestWord = lines 
		.flatMap(line -> Arrays.stream(line.split("\\s+"))) // Dividir líneas en palabras 
		.max(Comparator.comparingInt(String::length)) // Buscar la palabra más larga 
		.orElse("No words found"); 
		
	System.out.println("Longest word: " + longestWord); 
}
```
