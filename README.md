# Tarea 3 · La factura bajo el microscopio
Pareja: (Yingyi Li Pan) y (Angel Carneros) · GitHub: (yingyii7), (angelcarneros)

## Reto 1 · Compilar desde la terminal
- Comando usado y resultado (captura: capturas/reto1.png)
- ¿Qué es Factura.java? 
Es el archivo de código fuente escrito en lenguaje Java. Contiene las instrucciones legibles por los humanos.
- ¿Y Factura.class? 
Es el archivo compilado que contiene el bytecode. Es un código intermedio, que es independiente de la plataforma y se genera a partir de traducir el código fuente para que se pueda interpretar de manera eficiente.
- ¿Quién ejecuta el .class?
Lo ejecuta la JVM, Java virtual Machine (Maquina Virtual de Java). Que es la encargada de leer el bytecode del archivo .class y traducirlo a código máquina del sistema operativo.
- ¿Por qué no se ha generado Factura.class la primera vez?
No se ha generado porque el compilador ha encontrado errores de sintaxis en el código, después de corregir los errores ya se generará. 

## Reto 2 · Errores de compilación
| Nº | Línea |        Mensaje de javac                     | Tipo(léxico/sintaxis/semántica) |             Corrección                  |
|----|-------|---------------------------------------------|---------------------------------|-----------------------------------------|
| 1  |   15  | double precio# = sc.nextDouble();           |            léxica               |double precio = sc.nextDoubl();          |
| 2  |   17  | int cantidad = sc.next()                    |           sintáctico            |int cantidad = sc.nextInt();             |
| 3  |   29  |int total = (base - descuento)*(1 + IVA);    |           semántico             |double total =(base-descuento)*(1 + IVA);|
| 4  |   36  |      (no se ha cerrado el scanner)          |           compilación           |sc.close();                              |
| 5  |   24  |      descuento = base * 0.10;               |           lógico                |descuento += base * 0.10;                |
| 6  |   27  |      descuento = base * 0.05;               |           lógico                |descuento += base * 0.05;                |
Captura del programa funcionando: capturas/reto2.png

## Reto 3 · Depuración del error lógico
| Variable  | Valor esperado| Valor real |
|-----------|---------------|------------|
| descuento |               |            |
| total     |               |            |

- Línea del error y explicación:
- Corrección:
- Mi propia prueba (producto, precio, cantidad, socio → total):
Captura del depurador: capturas/reto3.png

## Reto 4 · Reutilización
- Métodos creados y para qué sirve cada uno:
- ¿Qué ventaja tiene frente al código anterior?

## Reto 5 · ¿Qué lenguaje elegirías?
- Caso A (web de la tienda):
- Caso B (propuesta en ensamblador):