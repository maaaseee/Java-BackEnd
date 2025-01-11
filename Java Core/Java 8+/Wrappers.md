Las clases Wrapper en Java son una forma de convertir tipos de datos primitivos (`int`, `double`, `char`, etc.) en objetos. Estas clases son útiles cuando necesitas trabajar con primitivos en contextos que requieren objetos, como en colecciones (`List`, `Map`, etc.).

| **Tipo Primitivo** | Clase Wrapper | Ejemplo práctico                                                              |
| ------------------ | ------------- | ----------------------------------------------------------------------------- |
| `byte`             | `Byte`        | Almacenar el nivel de batería (0 a 100) en una app móvil.                     |
| `short`            | `Short`       | Representar la cantidad de páginas en un libro.                               |
| `int`              | `Integer`     | Contar el número de usuarios activos en una plataforma.                       |
| `long`             | `Long`        | Almacenar el número de transacciones de un banco en un día.                   |
| `float`            | `Float`       | Calcular la calificación promedio de un estudiante con dos decimales.         |
| `double`           | `Double`      | Almacenar el precio de un producto con centavos.                              |
| `char`             | `Character`   | Validar si un carácter ingresado es una letra, número o símbolo especial.     |
| `boolean`          | `Boolean`     | Verificar si un usuario está habilitado para acceder a una sección de la app. |
### **Tipos de Operaciones en Streams**
```Java
// Autoboxing: convertir un primitivo a su wrapper
Integer edad = 25;

// Unboxing: convertir un wrapper a su primitivo
int edadPrimitivo = edad;

// Métodos útiles
String numeroComoTexto = Integer.toString(edad); // "25"
int valorParseado = Integer.parseInt("42"); // 42
Integer numero = Integer.valueOf("123"); // 123
```

### **Comparación con primitivos y Optional**

- **Primitivos:** Más eficientes en términos de memoria y velocidad. Úsalos siempre que no necesites trabajar con colecciones o valores nulos.
- **Wrappers:** Útiles en colecciones (`List<Integer>` en lugar de `int[]`) y cuando debes manejar valores nulos.
- **Optional:** Se utiliza para representar valores que pueden estar ausentes (mejor alternativa para evitar `null`).

### **Casos de uso eficiente**
- Uso en colecciones:
```Java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4);
int suma = numeros.stream().mapToInt(Integer::intValue).sum(); 
// Sumar todos los valores
```
- Manejo de valores nulos:
```Java
Integer valor = null;
int resultado = (valor != null) ? valor : 0; // Manejo seguro del valor
```