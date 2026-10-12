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
| descuento |       18      |     6      |
| total     |     123.42    |   137.94   |

- Línea del error y explicación: (escrito sin querer corregido en la actividad 2, en la tabla anterior) Linea 24 y 27. Porque al igualarlo con =, estamos calculando un valor, pero ese valor ya no se va a dar en el proximo cálculo. Tendríamos que poner de forma que se guarde ese valor, para después sumarle el resultado de la otra operación.
- Corrección: descuento += base * 0.10; y descuento += base * 0.05;
- Mi propia prueba (producto, precio, cantidad, socio → total): producto: anillos, precio: 88, cantidad: 15, socio: s -> total = 1357,62 euros.
Captura del depurador: capturas/reto3.png

## Reto 4 · Reutilización
- Métodos creados y para qué sirve cada uno:
    - calcularDescuento(double base, boolean socio): calcula cuánto dinero se descuenta. Da un 10 % si la compra pasa de 100 € y un 5 % más si el cliente es socio.
    - aplicarIVA(double importe): coge un precio sin IVA y devuelve ese precio con el 21 % de IVA sumado.
    - pedirDecimal(Scanner sc, String mensaje): escribe una pregunta en pantalla y devuelve el número decimal que escribe el usuario. Así no hay que repetir print + nextDouble.
- ¿Qué ventaja tiene frente al código anterior?
    - Antes todo el cálculo estaba mezclado dentro de main. Ahora cada tarea tiene su propio método con un nombre claro, y el código se lee mucho mejor.
    - Si hay que usar el descuento o el IVA otra vez, solo se llama al método en vez de copiar y pegar el código.
    - Si cambia una regla (por ejemplo, el porcentaje del descuento), se cambia en un solo sitio.
    - Es más fácil encontrar errores, porque se puede revisar cada método por separado.
    - Comprobación: con precio 60, cantidad 2 y socio s sigue dando 123,42 €, así que el resultado no ha cambiado.

## Reto 5 · ¿Qué lenguaje elegirías?
- - Caso A (web de la tienda):
    Usaria un lenguaje interpretado como JavaScript que es el que ejecuta el navegador del cliente.
- Tipo de proyecto: es una pagina web y todos los navegadores ya traen un interprete de JavaScript asi que el cliente no tiene que instalar nada.
- Portabilidad: el mismo codigo funciona en Windows Mac o movil porque lo ejecuta el navegador y no la CPU directamente.
- Coste de desarrollo: es rapido de escribir y de probar y para una calculadora sencilla no hace falta nada más complicado.
- Rendimiento: no es critico porque un presupuesto son cuatro cuentas y se calculan al instante. No es un caso de tiempo real.

- Caso B (propuesta en ensamblador):
  No lo haria: el ensamblador no vale para todos los ordenadores porque depende de cada CPU. Usaria un lenguaje de alto nivel como Java o uno compilado.
  - Portabilidad: un programa en ensamblador hecho para un procesador no funciona en otro y habria que reescribirlo. Java funciona en cualquier equipo con la maquina virtual de Java.
  - Coste de desarrollo: programar en ensamblador es lento y dificil y hay mas posibilidades de cometer errores. Ademas es complicado de mantener y reescribir toda la calculadora costaria mucho tiempo.
  - Rendimiento: la calculadora hace operaciones muy sencillas y la mejora de velocidad no se notaria. El ensamblador solo compensa para ajustes puntuales en casos muy concretos y no para reescribir un programa entero.