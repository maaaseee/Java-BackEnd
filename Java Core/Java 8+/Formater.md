El formateo en Java se refiere a la conversión de números o cadenas a representaciones específicas, como agregar decimales, símbolos de moneda o ajustar el formato.
### **Clases útiles:**
1. `DecimalFormat`: Para formatear números con decimales o patrones personalizados.
2. `String.format()`: Para construir cadenas con formatos específicos.
3. `NumberFormat`: Para manejar formatos de moneda.

### **Ejemplo básico con `DecimalFormat`**:
```Java
DecimalFormat formato = new DecimalFormat("#,###.00"); 
double numero = 12345.678; 
System.out.println(formato.format(numero)); 
// "12.345,68" (configuración regional de Argentina)
```

### **Uso práctico**:
- Validación y visualización de datos del usuario:
```Java
String ingreso = "1234,56"; // Cadena ingresada
ingreso = ingreso.replace(",", "."); // Reemplazar coma por punto
double monto = Double.parseDouble(ingreso); // Convertir a double
DecimalFormat formato = new DecimalFormat("#,###.00");
System.out.println("Monto ingresado: " + formato.format(monto)); // Mostrarlo formateado
```
- Mensajes que compartan una estructura definida:
```Java
String nombre = "Federico";
System.out.println(String.format("Hola, %s. Tienes %d mensajes.", nombre, 5)); 
// "Hola, Federico. Tienes 5 mensajes."
```
- Mostrar distintos formatos para el dinero:
```Java
// Formateo para Argentina 
BigDecimal platita = BigDecimal.valueOf(1234568.99);
NumberFormat formatARG = NumberFormat.getNumberInstance(new Locale("es", "AR")); 
formatARG.setMinimumFractionDigits(2); 
formatARG.setMaximumFractionDigits(2); 
String platitaARG = formatARG.format(platita); 
System.out.println("Argentina: " + platitaARG); 

// Formateo para Estados Unidos 
NumberFormat formatUS = NumberFormat.getNumberInstance(Locale.US); 
formatUS.setMinimumFractionDigits(2); 
formatUS.setMaximumFractionDigits(2); 
String platitaUS = formatUS.format(platita); 
System.out.println("Estados Unidos: " + platitaUS);
```