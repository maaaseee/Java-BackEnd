El paquete `java.time` en Java 8+ incluye varias clases diseñadas para trabajar con fechas y horas.

## **Clases principales**
### 1. `LocalDate`
> Representa una fecha sin tiempo, como "2024-12-28"

##### **Creación**:
- **Fecha actual**: 
```Java
LocalDate fechaHoy = LocalDate.now();
```
- **Fecha específica**:
```Java
LocalDate revDeMayo = LocalDate.of(1810, 5, 25);

// Usando el Enum "Month"
LocalDate diaIndependencia = LocalDate.of(1816, Month.JULY, 9);
```
- **Desde texto**: 
```Java
String fecha = "2024-01-15";

LocalDate fechaFormateada = LocalDate.parse(fecha);
```

##### **Manipulación**:
```Java
LocalDate date = LocalDate.now(); 
date = date.plusDays(10); // Agrega 10 días 
date = date.minusMonths(1); // Resta 1 mes 
date = date.withYear(2025); // Cambia el año
```

##### **Comparación**:
```Java
LocalDate date = LocalDate.now(); // 2024-12-30

boolean isAfter = date.isAfter(LocalDate.of(2024, 1, 1)); // true
boolean isBefore = date.isBefore(LocalDate.of(2023, 12, 31)); // false
```

##### **Día de la semana/mes**:
```Java
DayOfWeek dayOfWeek = date.getDayOfWeek(); // SÁBADO 
int dayOfMonth = date.getDayOfMonth(); // 28 
Month month = date.getMonth(); // DICIEMBRE
```

### 2. `LocalTime`
> Representa una hora sin fecha, como "14:30:15".

##### **Creación**:
- **Hora actual**:
```Java
LocalTime laHora = LocalTime.now();
```
- **Hora específica**: 
```Java
LocalTime laHora = LocalTime.of(23, 39, 45); // "23:39:45"
```

##### **Manipulación**:
```Java
LocalTime time = LocalTime.of(14, 30, 15);
time = time.plusHours(2);  // 16:30:15
time = time.minusMinutes(10); // 16:20:15
time = time.plusSeconds(15); // 16:20:30
```

##### **Comparación**:
```Java
LocalTime time = LocalTime.of(14, 30, 15); 
boolean isBefore = time.isBefore(LocalTime.of(15, 0)); // true
boolean isAfter = time.isAfter(LocalTime.of(13, 0)); // true
```

### 3. `LocalDateTime`
> Combina `LocalDate` y `LocalTime` sin zona horaria.

##### **Creación**:
- **Fecha y hora actuales**: 
```Java
LocalDateTime yaMismo = LocalDateTime.now();
```
- **Fecha y hora específicas**:
```Java
LocalDateTime.of(2022, Month.NOVEMBER, 11, 15, 10, 43); // "2022-11-11T15:10:43"
LocalDateTime.of(2024, Month.SEPTEMBER, 21, 23, 47); // "2024-09-21T23:47"
```

##### **Manipulación**
```Java
LocalDateTime dateTime = LocalDateTime.of(2024, 12, 28, 14, 30);
dateTime = dateTime.plusDays(1).minusHours(2); // "2024-12-29T12:30"
```

##### **Conversión**:
```Java
LocalDateTime dateTime = LocalDateTime.of(2024, 6, 12, 14, 30);
LocalDate date = dateTime.toLocalDate(); // "2024-6-12"
LocalTime time = dateTime.toLocalTime(); // "14:30:00"
```

### 4. **`ZonedDateTime`**
> Representa una fecha y hora con una zona horaria, como "2024-12-28T14:30+01:00[Europe/Paris]".

##### **Creación**:
- **Zona actual**: 
```Java
ZonedDateTime yaMismo = ZonedDateTime.now();
```
- **Zona específica**:
```Java
ZonedDateTime zonedDateTime = ZonedDateTime.of(
    LocalDateTime.now(),
    ZoneId.of("America/New_York")
); // "2024-12-31T00:26:26.799199700-05:00[America/New_York]"
```
##### **Operaciones**:
**Conversión entre zonas**:
```Java
ZonedDateTime newZone = zonedDateTime.withZoneSameInstant(ZoneId.of("Asia/Tokyo"));
```

### **Otras clases**

##### `Duration`
> Representa una cantidad de tiempo (en horas, minutos, segundos, nanosegundos).

- **Duración específica**:
```Java
Duration.ofHours(2); // "PT2H"
```
- **Diferencia entre tiempos**:
```Java
Duration duration = Duration.between(LocalTime.of(10, 0), LocalTime.of(12, 0)); 
// "PT2H"
```

##### `Period`
> Representa una cantidad de tiempo en años, meses o días.

- **Período específico**:
```Java
Period.ofYears(1) // "P1Y"
```
- **Diferencia entre fechas**:
```Java
Period period = Period.between(LocalDate.of(2020, 1, 1), LocalDate.of(2024, 12, 28));
```

##### `DateTimeFormatter`
> Formatea y parsea fechas/horas.

- **Formateo**:
```Java
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd-MM-yyyy"); 
String formattedDate = LocalDate.now().format(formatter); // "28-12-2024"
```
- **Parsing**:
```Java
LocalDate date = LocalDate.parse("28-12-2024", formatter); // "2024-12-28"
```

## **Operaciones Avanzadas**

##### 1. Verificar si una fecha es un día específico: 
```Java
boolean isWeekend = date.getDayOfWeek() == DayOfWeek.SATURDAY || date.getDayOfWeek() == DayOfWeek.SUNDAY;
```

##### 2. Generar una lista de fechas entre dos rangos: 
```Java
LocalDate start = LocalDate.of(2024, 1, 1);
LocalDate end = LocalDate.of(2024, 12, 31);

while (!start.isAfter(end)) {
    System.out.println(start);
    start = start.plusDays(1);
}
```

##### 3. Obtener las zonas disponibles: 
```Java
ZoneId.getAvailableZoneIds().forEach(System.out::println);
```