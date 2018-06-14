# Pathfinding

+ Buscar caminos
+ Principalmente se aplica en desarrollo de video juegos.
+ Existen muchos tipos de problemas de pathfinding. No hay una solucion generica.
+ Factores por considerar:
	- Es el destinio estatico?
	- Hay obstaculos?
	- Hay distintos tipos de terreno?
	
## Pathfinding Basico

+ Es el proceso de mover un personaje desde su posicion inicial hasta el destino.
+ La solucion consiste en igualar el x y y del origen con el destino
`Insertar grafica 1`
+ La solucion basica produce un movimiento poco natural.
+ Para mejorar la animacion se puede usar un algoritmo de linea-vista.
`Insertar grafica 2`
+ Un algoritmo de linea-vista aplicable es el algoritmo de **Bresenhan**
+El pathfinding basico __no__se puede aplicar si hay obstaculos entre el origen y el destino.
`Insertar grafica 3`

## Movimiento Aleatorio

+ Puede ser un metodo simple y efectivo de evitar obstaculos.
+ Funciona bien si hay pocos obstaculos.
+ Basicamente consiste en buscar un camino directo mediante linea-vista. Si no hay, se mueve en una posicion aleatoria y se intenta de nuevo.

## Obstacle Training

+ Efectivo para buscar caminos alrededor de obstaculos grandes.
+ El personaje sigue una linea vista hasta encontrar el obstaculo. Cuando choca con el obstaculo, entra en un estado de training
+ En el estado de training, sigue el borde del obstaculo para rodearlo.
`Insertar grafica 4`
+ Al hacer training, se debe evitar caer en un ciclo. Se puede calcular de dos formas:
	- Calcular una linea que cruza el obstaculo. El tracing se detiene hasta llegar a la linea
	`Insertar grafica 4`
	- Calcular linea de vista con cada paso. Si en el paso actual hay camino direcot, se detiene el tracing.
	`Insertar grafica 5`

## Breadcrumb Pathfinding

+ El personaje controlado por el jugador deja un rastro que puede eguir los NPC.
+ En este caso, no hya que realizar muchos calculos puesto que el camino es conocido.

## Wall tracing

+ No calcula un cmanio de inicio al final. ES mas una teorica de exploracion que de pathfinding.
+ Efectiva en juegos tipo laberinto.
+ Se utliza un enfoque de mano izquierda.
+ El NPC siempre se mueve tontiguo a la pared izquierda.

## Waypoint Navigation

+ para reducir el consumo de CPU, se pueda precalcular caminos entre las secciones del mapa.
`Insertar grafica 6`


