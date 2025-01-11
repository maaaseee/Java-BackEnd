Calcular la suma de los cubos de todos los números impares en una lista.
``` Java
List<Integer> nums = List.of(1, 2, 3, 4, 5, 6);
        int sumOfCubes = nums.stream()
            .filter(n -> n % 2 != 0)   // Filtramos los números impares
            .map(n -> n ** 3)      // A cada número, lo potenciamos al cubo
            .reduce(0, Integer::sum); // Sumamos cada uno de los resultados
	    
		/*
		1: 1^3 = 1
		3: 3^3 = 27
		5: 5^3 = 125
		125 + 27 + 1 = 153
		*/
        System.out.println(sumOfCubes); // Result: 153
```