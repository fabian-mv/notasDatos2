# Apuntes para Datos 2

---

---

## Administracion de Memoria
+ El sistema operativo:
	- Es Software
	- Es una capa de software que se ejecuta directamente en el hardware de la computadora
	- La funcion principal es:
		* Proveer un API para los desarrolladores de software
		* Administrar los recursos de la maquina.
	- Administra:
		* Procesador
		* Memoria
		* Archivos / Disco
		* I / O
		
`Insertar Diagrama 1`

+ Conforme los S.O han evolucionado, han habido distintos esquemas para la administracion de memoria
	- Los esquemas cambian principalmente para cumplir con nuevos requerimientos. Por ejemplo la **multiprogramacion**.

`Insertar Diagrama 2`

---

## Esquemas

+ No separacion de la memoria fisica
+ Bajo este esquema no hay transparencia
+ Se utiliza en los mainframes (60s), microcomputadores (70s) y PC's antes de los 80s.
+ Cuando el S.O recibe un comando, se copia el programa entero a memoria. Cuando termina y se ejecuta otro comando, se copia el nuevo programa, sobre-escribiendo el primero.
+ Trae un nuevo problema.

`Insertar Diagrama 3`

+ Se soluciona mediante "static relocation"
	- Modificar las referencias a memoria cuando el programa se carga.
+ Espacios de direcciones:
	- Es un conjunto de direcciones que un proces puede usar para direccionar memoria.
	- Cada proceso tiene su espacio de direciones (rang)
	- Para implementar esto se usa **dinamic relocation**.
+ El CPU tiene dos registros especiales: Base y Limite.
+ El registro base contiene la direccion en la que se cargo en programa.
+ El registro limite contiene el tamano del programa.
+ Cada vez que se ejecuta una instruccion que contiene una referencia a memoria, se le suma el registro base y se verifica que **NO** se pasa del limite.
+ El problema es el **overhead** de hacer el calculo.

---

## Espacios de Direcciones
+ Swapping
	- Si tengo un programa de 1 GB, otro de 512 MB y otro de 256 MB, pero solo tengo 1 GB de RAM. Como se puede ejecutar mas de uno a la vez?
	- Swapping es una tecnica que trae un programa entero a memoria, lo ejecuta por un tiempo y luego lo descarga a disco.
	
`Insertar Diagrama 4`

---

## Memoria Virtual
+ El tamano de los programas crece mas rapido que la memoria disponible.
+ Como ejecuto un programa mas grande que el total de memoria?
+ Cada programa se divide en paginas de tamano fijo.
+ Cada pagina es un rango de direcciones "Virtuales"
+ Cuando el programa refencia una direccion, hardware especial hace le mapeo a la direccion real
+ Si se referencia mas paginas que no esta cargada, el OS la trae a memoria 

`Insertar Diagrama 5`

`Insertar Diagrama 6`

`Insertar Diagrama 7`

---

## Espacios de Direcciones
+ A nivel de proces
	- Proceso: un programa en ejecucion
	- Los procesos utilizan una abstraccion de la memoria
	- La estrucutra puede varias segun la plataforma, pero tradicionalmente es:

`Insetar Diagrama 8`
		
---

## Pila (Stack)

+ Es una seccion del memory layout se comporta LIFO.
+ Se compone de un conjunto de **Stack Frames**. Cada Frame es una llamada a una funcion.
+ Cuando una funcion se llama, se agrega un nuevo frame.
+ Cuando la funcion termina, se elmina el frame.
+ Cada stack frame contiene:
	- Almacenamineto para todas la variables automaticas de la funcion.
	- Numero de linea de la funcion que llama
	- Parametros de la funcion llamada.
	
```
	int main (void)
	{
		printf("Hola");
		foo();
		print("Adios");
		return 0;
	}
	
	void foo()
	{
		int a =3;
		char c = ‘c’;
		int* ptr = NULL;
		foo2(a);
	}
	
	void foo2(int p)
	{
		int b = p;
	}
	
```
	`Insertar Diagrama 9`
	

	
+ La pila administra la memoria automaticamente. Es **transparente** para el programador.
+ Cuando un frame se elmiina, la memoria asociada se libera.
+ Hay un limite bien concido en el tamano de las variables.

---

## Heap

+ Seccion del memory layout.
+ **NO** es administrado automaticamente => **mayor cuidado**
+ El programador interactua con el Heap mediante un API que permite
	-Asignar memoria
	-Liberar memoria
	-Redimensionar memoria
	-Punteros
+ Se puede evitar el uso del Heap.
+ Sin Heap:
	- El lenguaje es restrictivo
	- No hay estructuras de datos "interesantes"
	

```
	#con Stack
	int main()
	{
		int age = 30;
		double salary = 100.00;
		double array [2] = {1.2 , 1.3}
		array [0] = 0;
	}
	
	#con Heap
	int main()
	{
		int*age = malloc(sizeof(int));
		*age = 30;
		double salary = malloc(sizeof(double));
		*salary = 100.00;
		double* array = malloc(sizeof(double)*3);
		array[0] = 1.2;
	}
```

---

## Punteros
+ Ciertas cosas unicamente se pueden hacer atraves de punteros
	- Estructuras de datos
	- Variables de gran tamano
+ Cuando una variable se declara, memoria se le asigna.
	`Insertar Diagrama 10`
+ La variable es un "label", un alias de la direccion de memoria
+ Utilizando este alias, se puede leer o escribir el valor en memoria.
+ Un puntero es una variable cuyo valor es una direccion de memoria
+ Almacena una **referencia** a otro valor. Guarda la direccion de memoria de un valor en memoria.
+ Un puntero existe en memoria. Por ejemplo:
```
int counter = 666;
int* counterPtr = &counter;
```
`Insertar Diagrama 11`

+ En C, un puntero es un tipo de datos especial:
```
int*
double*
char*
struct*
void*
```
+ Los punteros, sin importar el tipo, ocupa la misma memoria:
	- xbytes, donde x tiene un rango de valores que permite direccionar toda la memoria
	- En una OS de 32 bits, la direcciones son de 32 bits:
	
	`Insetar Diagrama 12`

+ Un puntero normalmente se usa para referenciar memoria del Heap, pero tambien puede manipular memoria en el stack:
```
// Este NO sirve

int main ()
{
	int* b = foo();
	*b = 5;				//2. Haciendo que esto retorne null y se caiga.
}

int* foo()
{
	int a = 100;
	return &a;
}						//1. aqui va terminar int a
```

```
// Este SI sirve

int main ()
{
	int* b = foo();
	*b = 5;
}

int* foo()
{
	int* a = malloc(sizeof(int));
	*a = 100;
	return a;	
}
```

+ El valor por defecto de un puntero se conoce como **BAD VALUE**. Es una direccion aleatoria.

+ Desreferenciar un putnero sin inicializar cause un runtime error
	- **Siempre inicialice los punteros!**
+ Null es un valor especial que equivale a 0.
	- Desreferenciar un puntero nulo causa un runtime error.
	
---

## El operador "&"
+ Obtiene la direccion de meoria de la variable a la que se le aplique el operador.
+ Es un operador _unario_.
```
&var != if (a&b({}
     != a&b -> bitwise
```

---

## El operador "*"
+ Es un operador _unario_
+ Va a la izquierda de una variable pointer.
+ Recupera el valor apuntando por el puntero.

```
int main ()
{
	int dato = 55;
	int* dPtr = &dato;
	
	printf (data);	// 55
	printf (dPtr);	// Direccion de Memoria
	printf (*dPtr);	// 55
}
```

## Sharing
+ Tener mas de un puntero al mismo dato
`Instertar Diagrama 12`
+ CounterPtr y CounterPtr2 permiten manipular la memoria de counter.

---

## Deep Copy
+ Utilizar punteros para copiar datos
`Insertar Diagrama 13`
+ Requiere cierto trabajo.
```
int value = 5;
int* pointer = &value;
int* pointer2 = malloc (sizeof(int));
*pointer2 = *pointer;
```
+ PAra estructuras/ variables mas cmplejas se puede requerir trabajo adicional y el uso de memcpy, strcpy u otros.

## Shallow Copy
+ Utilizar punteros para copiar la referencia
`Insertar Diagrama 14`

---

## Arreglos y Aritmetica de Punteros
+ Declarar un arreglo con una expresion como
` int vec[5]; ` es solicitar memoria contigua

`Insertar Diagrama 15`
+ La variable vec == 0x01
+ Navegar en el arreglo es aritmetica de punteros
```
int* vec = malloc(sizeof(int)*3);
vec[0] = 1;
vec[1] = 2;
*(vec + 0) = 1;
*(vec + 1) = 2;
```