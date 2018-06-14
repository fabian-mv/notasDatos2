# File Systems
+ A partir de ahora, se abstraen los discos como una secuencia lineal de bloques que sopoprtan dos operaciones:
    - Leer bloque K
    - Escribir bloque K
    - `Diagram 1`
    - Un archivo es una unidad logica creada por procesos
    - Un disco puede contener miles de archivos independientes entre si
    - La infromacion en los archivos es persistente: no se ve afectada por la creacion / terminacion de procesos.
    - El sistema de archivos es la parte del OS en cargada de administrar archivos.
    - Hay muchos tipos de sistemas de archivos:
        - Ext2, Ext3
        - NTFS
        - FAT, FAT32
        - CDFS
    - Los programadores usan un API para interactuar con el sistema de archivos.
    - Requerimientos:
        - Persistente
        - Velocidad
        - Compartir
        - Proteccion

## Estrucutra de archivos
+ Hay tres estructruas comunes
    - Secuencia de Bytes: el OS no conoce o se interesa por el contenido del archivo solo de bytes.
    - Unix y Windows utiliza este enfoque
    - Provee maxima flexibilidad. El OS no ayuda ni obstaculiza. 

## Registro de tamagno fijo
+ Un archivo es una secuencia de registros con una estrucutra interna
+ La operacion READ retorna un registro completo y la operacion WRITE escribe un registro completo
+ Utilizado en mainframes/ midranges.
