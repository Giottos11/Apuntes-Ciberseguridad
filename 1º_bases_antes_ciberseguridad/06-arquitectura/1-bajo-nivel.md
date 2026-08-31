# Bajo nivel y arquitectura

Este bloque debe estudiarse después de adquirir una base sólida de programación, sistemas operativos, Linux y Windows. Su finalidad es cambiar progresivamente la perspectiva: pasar de pensar en un programa como un conjunto de instrucciones escritas en un lenguaje de alto nivel a comprenderlo como una secuencia de operaciones que terminan ejecutándose sobre una CPU, utilizando registros, memoria y mecanismos proporcionados por el sistema operativo.

La programación de alto nivel permite abstraerse de muchos detalles de la máquina. Una variable puede parecer simplemente un nombre asociado a un valor, una función puede parecer una unidad lógica de código y una estructura de datos puede utilizarse sin conocer exactamente cómo se representa en memoria. En bajo nivel estas abstracciones desaparecen progresivamente. El objetivo es comprender qué hay detrás de ellas: cómo se representan los datos, dónde se almacenan, cómo se pasan los argumentos, cómo se crea una pila de ejecución, cómo se reserva memoria dinámica y cómo una llamada a una función termina convirtiéndose en instrucciones que ejecuta el procesador.

Esta perspectiva es especialmente importante en seguridad porque muchas vulnerabilidades que parecen abstractas en un lenguaje de alto nivel tienen una explicación muy concreta cuando se observa la memoria y la ejecución a bajo nivel. Un error en los límites de un array, una referencia incorrecta a memoria o una gestión defectuosa de un buffer puede terminar afectando directamente a la forma en que el procesador interpreta los datos almacenados en memoria.

## Arquitectura

El primer paso consiste en comprender la arquitectura básica de un ordenador y, especialmente, la relación entre **CPU, registros, memoria e instrucciones**. La CPU es el componente encargado de ejecutar las instrucciones de un programa. Para ello mantiene un estado interno compuesto por diferentes registros y utiliza mecanismos que permiten obtener instrucciones y datos desde memoria.

Los **registros** son pequeñas áreas de almacenamiento situadas dentro de la propia CPU y utilizadas para mantener temporalmente valores que intervienen en la ejecución. Algunos registros contienen datos generales, mientras que otros tienen funciones específicas relacionadas con el contador de programa, el estado de la CPU o la gestión de la pila. La nomenclatura y organización concreta dependen de la arquitectura, por lo que será necesario familiarizarse especialmente con arquitecturas como **x86-64**.

Uno de los conceptos fundamentales será el **instruction pointer**, que indica la posición de la siguiente instrucción que debe ejecutarse. Junto a él existen registros utilizados para operaciones aritméticas, almacenamiento temporal, paso de argumentos y gestión de la pila. Comprender estos registros permite empezar a leer código ensamblador y relacionarlo con el comportamiento del programa original.

La **memoria** debe entenderse como un espacio direccionable en el que se almacenan instrucciones y datos. Cada posición de memoria tiene una dirección que permite localizar la información almacenada. Sin embargo, un programa no trabaja simplemente con una gran colección lineal de bytes: existen diferentes regiones y mecanismos de organización, como código, datos, memoria dinámica y stack, además de la memoria virtual proporcionada por el sistema operativo.

También es necesario comprender cómo se representan los datos dentro de la memoria. Un procesador trabaja fundamentalmente con bits y bytes, por lo que conceptos aparentemente sencillos como un entero, una dirección o una cadena de caracteres tienen una representación concreta. En este contexto aparecen **little endian** y **big endian**, que determinan el orden en que los bytes de un valor multibyte se almacenan en memoria.

El concepto de endianess resulta especialmente importante cuando se trabaja con estructuras binarias, formatos de archivos, protocolos de red, debugging y análisis de memoria. El mismo valor numérico puede representarse con los mismos bytes pero en un orden diferente dependiendo de la convención utilizada. Comprender esta diferencia evita muchos errores cuando se examinan datos directamente a nivel hexadecimal.

Las **instrucciones de máquina** son las operaciones que la CPU puede ejecutar directamente. Estas instrucciones permiten mover datos, realizar operaciones aritméticas y lógicas, comparar valores, acceder a memoria, modificar registros y alterar el flujo de ejecución mediante saltos y llamadas. A partir de aquí comienza a desaparecer la separación intuitiva entre "programa" y "máquina": una operación escrita en C termina transformándose en una secuencia concreta de instrucciones que modifican registros y memoria.

También es necesario comprender el concepto de **direccionamiento**. Una instrucción puede trabajar con un valor inmediato, un registro o una dirección de memoria calculada a partir de diferentes componentes. Este mecanismo resulta fundamental para entender punteros, arrays, estructuras y acceso a memoria en ensamblador.

## C

El lenguaje **C** constituye el puente natural entre la programación de alto nivel y la arquitectura de la máquina. Aunque C proporciona abstracciones como funciones, estructuras y tipos de datos, mantiene una relación mucho más directa con memoria y direcciones que lenguajes de alto nivel más abstractos.

Los **punteros** son uno de los conceptos centrales. Un puntero contiene una dirección de memoria y permite acceder indirectamente al objeto almacenado en ella. Comprender los punteros implica comprender simultáneamente variables, direcciones, tipos, aritmética de punteros y acceso indirecto a memoria. Esta base será imprescindible posteriormente para interpretar estructuras de datos, código compilado y vulnerabilidades relacionadas con memoria.

Los **arrays** representan regiones contiguas de memoria cuyos elementos tienen un tamaño determinado por su tipo. Esta relación entre índice, dirección y tamaño del elemento permite entender por qué operaciones aparentemente sencillas en C pueden terminar modificando posiciones de memoria que pertenecen a otros objetos cuando no se controlan correctamente los límites.

Las **strings** en C permiten profundizar todavía más en esta relación. Una cadena no constituye un objeto de alto nivel con longitud incorporada, sino una secuencia de caracteres almacenada en memoria y terminada normalmente mediante un byte nulo. Funciones relacionadas con la manipulación de cadenas muestran de forma clara cómo una abstracción aparentemente sencilla depende de una representación concreta en memoria y de que el programa respete correctamente sus límites.

El modelo de memoria de un proceso puede dividirse conceptualmente en diferentes regiones. Entre ellas se encuentran el **stack**, utilizado principalmente para mantener información asociada a las llamadas a funciones, y el **heap**, utilizado para gestionar memoria dinámica durante la ejecución del programa. Comprender la diferencia entre ambas regiones resulta esencial para interpretar cómo se crean y destruyen objetos y cómo se relacionan las variables locales, los argumentos y las reservas dinámicas.

La memoria dinámica se gestiona mediante mecanismos como `malloc` y `free`. `malloc` solicita al sistema de gestión de memoria una determinada cantidad de espacio, mientras que `free` libera una reserva previamente realizada. El programador debe mantener correctamente la relación entre reservas y liberaciones, ya que una gestión incorrecta puede provocar fugas de memoria, accesos a memoria ya liberada o corrupción de estructuras internas.

Estos problemas son importantes no solamente desde el punto de vista de estabilidad del programa. La **corrupción de memoria** puede modificar datos que controlan el comportamiento de una aplicación y, dependiendo del contexto y de las protecciones existentes, puede llegar a tener consecuencias de seguridad.

Para comprender por qué un programa en C termina ejecutando instrucciones de máquina es necesario estudiar el proceso de **compilación**. El código fuente no pasa directamente de C a CPU de una única manera conceptual. Intervienen diferentes fases, entre ellas el preprocesado, la compilación, la generación de ensamblador, el ensamblado y finalmente el enlazado de los diferentes componentes para producir un ejecutable.

El proceso de compilación también permite introducir conceptos como **objetos, símbolos, bibliotecas estáticas y dinámicas, enlazado y optimización**. Comprender estas fases será especialmente útil posteriormente cuando se analicen binarios, símbolos, ejecutables y código desensamblado.

## Ensamblador

El **ensamblador** proporciona una representación legible de las instrucciones que ejecuta el procesador. No es necesario memorizar inicialmente todas las instrucciones de una arquitectura. El objetivo es aprender a reconocer los patrones fundamentales y relacionarlos con conceptos que ya conocemos de C.

Las instrucciones básicas incluyen operaciones para mover datos, realizar cálculos, comparar valores, modificar registros, acceder a memoria y cambiar el flujo de ejecución. Las instrucciones de salto permiten implementar estructuras como `if`, `while` y `for`, mientras que las instrucciones de llamada y retorno permiten implementar funciones.

El conocimiento de los **registros** permitirá seguir el estado de un programa mientras se ejecuta. Será necesario reconocer los registros generales, el registro utilizado como instruction pointer y los registros relacionados con el stack. De esta forma se podrá observar cómo una operación escrita en C termina modificando directamente el estado de la CPU.

El **stack frame** representa el contexto asociado a una llamada a función. Dentro de él pueden encontrarse variables locales, información relacionada con la llamada y otros datos necesarios para mantener la ejecución. Comprender cómo se crea y destruye un stack frame permite conectar directamente el concepto de función de C con la realidad de la memoria del proceso.

Un aspecto fundamental será estudiar las **calling conventions**, es decir, las convenciones que determinan cómo se realiza una llamada a una función. Estas convenciones establecen cuestiones como dónde se colocan los argumentos, dónde se devuelve el resultado, qué registros deben conservarse y cómo se organiza la pila. Su conocimiento es imprescindible para interpretar correctamente código ensamblador y analizar funciones compiladas.

Las **syscalls** representan el límite entre el espacio de usuario y el kernel. Un programa normal no puede realizar directamente determinadas operaciones privilegiadas, por lo que solicita al sistema operativo servicios mediante llamadas al sistema. Comprender este mecanismo permite seguir el recorrido completo desde una función de alto nivel hasta la instrucción que finalmente solicita al kernel una determinada operación.

En este punto resulta especialmente útil relacionar ensamblador con debugging. Un debugger permite detener la ejecución, examinar registros, observar memoria, recorrer instrucciones y seguir el flujo del programa. Esta capacidad convierte conceptos teóricos como stack, heap, registros y calling conventions en estructuras observables directamente.

## Formatos de ejecutables

Una vez comprendidos C, ensamblador y memoria, es necesario estudiar cómo se almacena un programa compilado en un archivo ejecutable. En sistemas Linux el formato principal que debe conocerse es **ELF (Executable and Linkable Format)**, mientras que en Windows se utiliza la familia de formatos **PE (Portable Executable)**.

ELF describe cómo se organiza un binario y proporciona información necesaria para cargarlo y utilizarlo. Entre sus componentes se encuentran segmentos, secciones, tablas de símbolos y referencias a bibliotecas dinámicas. Comprender esta estructura permite relacionar el archivo almacenado en disco con las diferentes regiones que terminan apareciendo en memoria cuando el programa se ejecuta.

En Windows, el formato **PE** cumple una función equivalente y constituye la base de ejecutables como `.exe` y bibliotecas `.dll`. Su estructura contiene información sobre el código, los datos, las dependencias, las direcciones de entrada y diferentes elementos necesarios para que el cargador de Windows pueda preparar el módulo para su ejecución.

El estudio comparativo de ELF y PE permitirá comprender que un ejecutable no es simplemente "código compilado". Es una estructura binaria que contiene información destinada al cargador, al enlazador, al sistema operativo y, en determinados casos, a herramientas de análisis.

## Especialización avanzada

A partir de esta base comienza la especialización en **seguridad ofensiva, análisis de binarios y exploit development**. En esta etapa el objetivo ya no es solamente comprender cómo funciona un programa correcto, sino estudiar qué ocurre cuando el programa contiene errores relacionados con memoria, validación de datos o flujo de ejecución.

Los **buffer overflows** constituyen uno de los ejemplos clásicos. Se producen cuando un programa escribe más información de la que puede contener un determinado buffer, pudiendo provocar la corrupción de memoria adyacente. Para comprender realmente sus implicaciones es necesario relacionar el error de programación con el layout de memoria, los stack frames, los registros y el flujo de ejecución.

A partir de aquí aparecen técnicas como **ROP (Return-Oriented Programming)**, que permiten construir secuencias de ejecución reutilizando fragmentos de código existentes en memoria. Su estudio requiere comprender previamente instrucciones, direcciones, stack, calling conventions y mecanismos de protección de memoria.

El **shellcode** introduce el concepto de código diseñado para ejecutarse dentro de un contexto concreto, normalmente aprovechando una vulnerabilidad que proporciona algún tipo de control sobre la ejecución. Su estudio debe realizarse entendiendo primero cómo se representa el código máquina, cómo se carga en memoria y qué restricciones impone el entorno de ejecución.

El **exploit development** reúne estos conocimientos para analizar vulnerabilidades y estudiar cómo una condición de fallo puede convertirse en un comportamiento controlado. En esta fase también deberán estudiarse las mitigaciones modernas que dificultan la explotación, como **DEP/NX, ASLR, stack canaries, PIE, RELRO, CFG y CET**. El objetivo no es aprender únicamente técnicas de explotación, sino comprender la relación entre una vulnerabilidad, las condiciones necesarias para explotarla y los mecanismos que existen para impedirlo.

El **reverse engineering** amplía esta perspectiva hacia el análisis de programas sin disponer necesariamente del código fuente. A partir de un binario es posible estudiar sus funciones, llamadas, estructuras de datos, cadenas, dependencias y flujo de ejecución utilizando herramientas de desensamblado y debugging. El objetivo es reconstruir progresivamente la lógica que el desarrollador original implementó, aunque las abstracciones del código fuente hayan desaparecido durante la compilación.

Esta especialización conecta directamente con el análisis de malware, vulnerabilidades de software, ingeniería inversa, investigación de exploits y análisis forense de binarios. Sin embargo, estas disciplinas deben abordarse después de dominar los fundamentos anteriores: intentar aprender explotación sin comprender memoria, registros, ensamblador y sistemas operativos conduce a memorizar técnicas sin comprender realmente por qué funcionan.

## Objetivo

El objetivo de este bloque es comprender **qué ocurre por debajo de los lenguajes de alto nivel** y construir un modelo mental que conecte el código fuente con su ejecución real sobre el procesador.

Al finalizar esta etapa se debe poder seguir conceptualmente el recorrido de un programa desde el código escrito en C, pasando por la compilación y el ejecutable, hasta las instrucciones que ejecuta la CPU, los registros que utiliza y las regiones de memoria que modifica. También se debe comprender cómo una función genera un stack frame, cómo se pasan sus argumentos, cómo se gestiona la memoria dinámica y cómo una syscall permite que el programa solicite servicios al kernel.

Esta base permitirá interpretar vulnerabilidades de memoria desde su causa técnica y no simplemente desde su descripción. Un **buffer overflow**, por ejemplo, dejará de ser únicamente "un error que permite sobrescribir memoria" y podrá analizarse como una interacción entre representación de datos, límites de buffers, layout del proceso, instrucciones, registros, flujo de ejecución y mecanismos de mitigación.

La meta final es desarrollar una visión suficientemente profunda como para poder pasar de **"sé utilizar una herramienta"** a **"entiendo qué está haciendo la herramienta y por qué produce ese resultado"**. Esa diferencia es fundamental en disciplinas como reverse engineering, exploit development, análisis de malware y vulnerability research.
