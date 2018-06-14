## A* Pathfinding

+ Es el algoritmo mas utilizado en la industria de video juegos, debia a que:
	- Garantiza encontrar la mejor ruta entre dos puntos siempre y cuando exista alguna ruta.
	- Es relativamente eficiente.

+ Utilice A* siempre, a menos que el escenario se pueda resolver de forma mas sencilla, por ejemplo, linea vista.

## Definicion de area de busqueda

+ El area de juego se debe representar de forma tla que facilite la aplicacion de A*
+ El area se representa como un grafo de puntos interconectados. Cada punto es una posicion que puede tomar el jugador o un NPC
+ El algoritmo necesita conocer como se conecta los puntos

`Inster diagrama 1`

+ Un mundo represntado por mosaicos se ajusta optimamente para A*

## Pseudo-codigo de A*

```
add starting node to open list


while open list not empty

do

	current = node from open list with lowest cost

	if current == goal then
		exit
		
	else
		move current to closed list
		get all adjacent of current
		for each adjecent
		do
			if not an open list AND not on close list AND walkable
				move to open and calculate cost
		end do
end do
```

+ Para cada nodo se lleva un link al nodo padre para poder trazar el camino al final

## Scoring

+ Permite calcular el mejor camino desde el inicio hasta el final
+ Se calcula:

```
Costo desde el nodo inicail + Heuristica*

// Cuanto cuesta llegar desde el nodo inicail al nodo i?
// Cuanto cuesta llegar desde el nodo i hasta el destino?
// Se hace aproximado puesto que no se sabe el costo real de un camino desconocido
```

f = g + h

`Insertar diagrama 2`

g = pasos desde origen hasta i
h = i hasta destino

`Insertar diagrama 3`


