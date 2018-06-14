# Programacion Dinamica

+ Es un metodo para optimizar problemas al separalos en problemas mas sencillos. (similar a "divide y conquista")
+ Una vez que los problemas mas simples se han resuelto, se combinan para obtenerr la solucion global.
+ Invnetado en 1957 por Richard Bellman.

## Caracteristicas
+ La solucion se puede obtner mediante resolver sub-problmas
+ La subproblemas se traslapan

```
	por ejemplo, fibonacci
	
	Fib(n)
	{
		0						if		n = 0	;
		1						if		n = 1	;
		Fib(n-1) + Fib(n-2) 	if		n > 1	;
	}
```

```
	int fib(n)
	{
		int partial [n+1];
		partial[0] = 0;
		partial[1] = 1;
		
		for (int i =2; i < n+1; i++)
		{
			partial[i] = partial [i-1] + partial[i-2];
		}
		
		return partial[n];
	}
```
+ Es importante almacenar las solucioens de los subproblemas en tablas (arrays, hashmaps) las llamadas isguientes revisan la tabla para envitar re trabajo


# Algoritmos Geneticos
+ En los 60's los cientificos de computacion estudian la evolucion biologica con el finde utilizar principios de esta para optimizar problemas de ingenieria
+ Desarrollado en 1970 por Henry Holland
+ Se basa en conceptos como:
	- Seleccion Natural
	- Herencia Genetica
	- Mutaciones
+ Se pueden ver como busquedas aleatorias para optimizar probleams
	- Utlizan informacion historica para dirigir las busquedas.
	- A la hora de aplicarlos, se debe definirj:
		* Representacion genetica del dominio del problema
		* Funcion de fitness para evaluar el dominio.
		
## Proceso General
+ 1. Se genera una poblacion inicial aleatoria
+ 2. Se aplica fitness para seleccionar individuos
+ 3. Se combinan los individuos seleccionados
+ 4. Se descartan individuos con bajo fitness

+ Se genera una nueva generacion a partir de 3 y 4 y vuelve al paso 1

+ El proceso temrina cuando:
	- Umbral de genracion
	- Tiempo
	- No hay cambios geneticos


