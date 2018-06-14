# Diseno de algoritmos

+ Existen distintas tecnicas de diseno de algoritmos
	- Divide y conquista
	- Backtracking
	- Programacion dinamica
	- Algoritmos codiciosos
	- Algoritmos geneticos
	
## Divide y conquista
+ Consiste de:
	- Dividir el problema en subproblemas
	- Conquista los subproblemas
	- Combinar las soluciones de los subproblemas
	
+ Cuando los subproblemas son los usficientemente grandes, estamos en el caso recursivo

+ Cuando el problema es lo suficientemente simple, estamos en el caso base

`Diagrama 1`

+ Son natamente recursivos
+ La recursion es naturalmente paralelizable -> eficiente
+ Algoritmos comunes:
	- Binary Search
	- Merge Sort
	
`Diagrama 2`

## Backtracking
+ Para resolver algunos problemas se necesita probar sistematicamente todas las posiblidades que puedan existir con el contexto del problema.

+ Backtracking utiliza la recurison para probar cada una de las posibilidades. Es una busqueda exhaustiva.
	- Se descompone la tarea en tareas parciales
	- Cada tarea parcial realiza las mismas acciones que la anterior y por tanto, expresa recursivamente.
	- Si la tarea no conduce a una solucion, se prueba con otra tarea basica.
	
### Caracteristicas
+ Exhaustivos: se buscan todas las soluciones o alternativas que conducen a la solucion.
+ Vuelta atras: si una solucion parcial no conduce a la solucion global, se vuelve atras y se prueba con otro camino.

### Esquema General
```
	funcion probar
	inicio
	{
		inicializar cuenta de posibles solucion
		repetir
		{
			tomar siguiente seleccion
			determinar si es valida
			si es
			{
				anotar seleccion
				si problema solucionado
				{
					exito = true
				} si no{
					probar
					si no exito { borrar anotacion}
				}
			}
		}
	} hasta (exito) o no mas posibilidades
```
### Problema de Ejemplo:
+ Problema de las 8 reinas: colocar 8 reinas en un tablero de ajedrez de 8x8 sin que se ataquen

