# Analisis de Algoritmos

+ Un algortimo es un conjunto finito de instrucciones precisas para realizar una computacion
+ Caracteristicas:
    - Entrada
    - Instrucciones Precisas
    - Exactos y correctos
    - Numero finito de instrucciones
+ Un algoritmo se pruede representar como:
    - Pseudocodigo
    - Lenguaje natural
    - Diagrama de flujo
    - Lenguaje formal
        ```
        factoria: Natural -> Natural
            para todo i en los Naturales
                factorial(0) = 1
                factorial(1+1) = (i+1)*factorial(i)
        ```
+ Analisis de algoritmos es el metodo para estimar el consumo de recursos de un algoritmo
+ Nociones iniciales datan de 1860 con el trabajo de Babbage
+ Allan Turing establece las bases del analisis de algoritmos que aun se utilizan.

+ Para que analizar algoritmos?
    - Determinar que tan bein se ajusta un algoritmo para una u otra aplicacion
    - Comparar algoritmos
    - Predecir desempegno
    - Entender y mejorar un algoritmo.
    
## Que factores afectan el tiepo de ejecuccion de un algoritmo?
+ CPU, Memoria, Disco (hardware)
+ Compilador
+ Lenaje de programacion
+ Sistema operativo
+ El programador

## Como medir el tiempo que consume un algoritmo?
+ Empiricamente:
    - "Benchmarks". Timestamp al inicio, timestamp al final, calcular la diferencia.
+ Mediante Simulaciones:
    - Empiricamente con datos selecionados para probar ciertos casos.
+ Formalmente mediante un modelo matemacio:
    - "Complejidad computacional".

## Complejidad Computacional
+ Rama de la ciencia de computacion que se interesa en clasificar problemas segun su complejidad:
    - complejidad temporal:
        - Busca determinar una funcion del tamagno de la entrada, que permita predecir el desmpegno de un algoritmo.
        - Se enfoca en operaciones dominantes o elementales
            - Instucciones que siempre toman el mismo tiempo
                - `+ , - , / , % , ^ , << , >> , == , != , & , | , return , asignaciones , [i] , ...`
            - Se consideran independientes de los ciclos que requieran para ejecutarse
    - complejidad espacial
    
```
var M = A[0]            //  ------> 2T          \
                        //                          f(n) = 2NT+3T \
for (var i=0; i<M; i++) //  ------> T + NT + NT /                      k(n) = 2NT + 4NT + 3T
{                       //                                        /         = 6NT + 3T
    if (A[i] >= M)      //  ------> 2T  \                        /
    {                   //                  g(n) = 4T           /
        M = A[i];       //  ------> 2T  /
    }
}
```

## Analisis Asintotico:
+ Enforcarse como crece la funcion segun la **N**. Entender como se comporta el algoritmo en las peores condiciones:
    - Puedo ignorar los terminos de la funcion que son irrelevantes para el crecimiento.
+ Por Ejemplo:
    
    2n<sup>3</sup> + 3n<sup>2</sup> + log<sub>10</sub>(n)
    
    |   |   |   |   |
    |---|---|---|---|
    | n = 1   | 2 | 3 | 0 |
    | n = 10  | 2*10<sup>3</sup> | 3*10<sup>3</sup> | 1 |
    | n = 100 | 2*10<sup>6</sup> | 3*10<sup>3</sup> | 2 |
    
    El termino que crece mas rapido es 2*n<sup>3</sup>. Se puede descartar el 2 y enfocarse en n<sup>3</sup>
    - f(n) = n<sup>3</sup>
+ Si no hay loops = f(n) = 1
+ Un solo loop = f(n) = n
+ Loop sin anidar. El mas lento determina la funcion.
+ loop anidad (n<sup>2</sup>,n<sup>3</sup>,n<sup>4</sup>,...)

```
constante
logaritmica (log(n))
lineal (n)
lineal logaritmica (n*log(n))

cuadratica (n<sup>2</sup>)
cubica (n<sup>3</sup>)

exponencial (x<sup>n</sup>)
factorial (n!)
```
    
    
    
    