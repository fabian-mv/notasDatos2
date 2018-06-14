# Estructuras de Almacenamiento Externo
+ El almacenamineto normalmente se clasifica en almacenamiento principla (o principal / RAM) y almacenamiento __secudnario o periferico.__

## HDD
+ Hard-Disk Drive
+ Memoria no volatil
+ Almacenar los datos en platos rigidos con superficies magneticos que rotan a altas velocidades (7200 RPMs)
+ Es una unidad sellada
+ Los platos se apilan
+ Hay cabezas posicionadas arriba y abajo de cada plato
+ `Diagrama 1 `
+ Son dispositivos de accceso directo
    - toma el mismo tiempo acceder distintas partes de un arduino

## Platos
+ Cada plato se divide en pistas
+ Las pistas son cilindros concentricos
+ `Diagrama 2`
+ La informacion se almacena enlas pistas

## Sectores
+ `Digarama 3`

## Tipos
+ IDE: Integrated Drive Electronics es el termino que identifica los discos duros tradicionales de lso discos de antagno
    - Incluye la interfaz ATA (Advanced Technology Attachment)
    - SATA(Serial-ATA) reemplaza la interfaz ATA

+ SCSI (Small computer System Interface) es una interfaz de alta velocidad. En la actualidad se usa SAS (Serial attached SCI)

## Data Stripping
+ "Es una tecnica para diviir logicamente datos secuenciales (archivo)"

## Mirroring
+ "Es la replicacion de volumenes en unidaes separadas para asegurar continuidad"