# Fundamentos de informática

## Objetivo

Construir una comprensión sólida de **cómo funciona un ordenador internamente** antes de estudiar ciberseguridad.

No se trata de convertirse en ingeniero de hardware, sino de entender qué ocurre cuando un programa se ejecuta, cómo se representa la información, cómo se utiliza la memoria, cómo interactúan los componentes y qué papel desempeña el sistema operativo.

Estos conocimientos serán especialmente importantes posteriormente para comprender:

- Vulnerabilidades de memoria.
- Procesos e hilos.
- Escalada de privilegios.
- Sistemas operativos.
- Malware.
- Reverse engineering.
- Exploit development.
- Seguridad de aplicaciones.
- Funcionamiento de herramientas de ciberseguridad.

---

## 1. Representación de la información

Los ordenadores trabajan internamente con información representada mediante **bits**.

### 1.1. Bit

Un **bit** es la unidad mínima de información y puede tener dos valores:

```text
0
1
```

### 1.2. Byte

Un **byte** está formado por **8 bits**.

```text
1 byte = 8 bits
```

Con 8 bits pueden representarse:

```text
2⁸ = 256 valores diferentes
```

Por ejemplo, desde `00000000` hasta `11111111`.

### 1.3. Unidades de información

- bit (`b`)
- byte (`B`)
- kilobyte (KB)
- megabyte (MB)
- gigabyte (GB)
- terabyte (TB)

También hay diferentes convenciones para calcular estas unidades, por lo que un GB comercial no siempre coincide exactamente con una potencia de 1024.

---

## 2. Sistemas de numeración

### Decimal

Es el sistema que utilizamos habitualmente y utiliza diez símbolos:

```text
0 1 2 3 4 5 6 7 8 9
```

### Binario

Es el sistema fundamental de los ordenadores.

Utiliza únicamente:

```text
0 y 1
```

Ejemplo:

```text
1010₂ = 10₁₀
```

Es importante saber realizar conversiones básicas entre decimal y binario.

### Hexadecimal

Utiliza 16 símbolos:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Ejemplo:

```text
10₁₀ = A₁₆
```

El hexadecimal es especialmente importante en ciberseguridad porque aparece constantemente en:

- Direcciones de memoria.
- Dumps de memoria.
- Hashes.
- Bytes.
- Código máquina.
- Shellcode.
- Análisis de archivos.
- Reverse engineering.

### Relación entre binario y hexadecimal

Cada dígito hexadecimal representa exactamente **4 bits**.

```text
0000 = 0
0001 = 1
...
1010 = A
...
1111 = F
```

Por eso el hexadecimal permite representar grandes cantidades de información binaria de forma mucho más compacta.

---

## 3. Representación de texto

Los ordenadores necesitan transformar caracteres como:

```text
A
B
á
€
```

en números que puedan almacenar y procesar.

### ASCII

**ASCII** es un sistema de codificación de caracteres que asigna valores numéricos a determinados caracteres.

Por ejemplo:

```text
A → 65
a → 97
```

ASCII es importante porque aparece en programación, redes, archivos y análisis de datos.

### Unicode

**Unicode** permite representar una cantidad mucho mayor de caracteres y sistemas de escritura.

Incluye caracteres de diferentes idiomas y símbolos.

Relacionado con Unicode aparecen diferentes formas de codificación, como:

- UTF-8
- UTF-16
- UTF-32

**UTF-8** es especialmente importante porque es extremadamente común en sistemas actuales y en Internet.

---

# 4. Hardware

El hardware está formado por los componentes físicos del ordenador.

Para ciberseguridad interesa comprender **qué hace cada componente y cómo interactúa con el resto**.

---

## 4.1. CPU

La **CPU (Central Processing Unit)** es el componente encargado de ejecutar instrucciones.

De forma simplificada:

```text
Programa
   ↓
Instrucciones
   ↓
CPU
   ↓
Resultado
```

La CPU trabaja con:

- Instrucciones.
- Registros.
- Datos.
- Direcciones de memoria.

Conceptos relacionados:

- Núcleos.
- Frecuencia.
- Registros.
- Caché.
- Instrucciones.
- Arquitectura de CPU.

---

## 4.2. Registros

Los **registros** son pequeñas áreas de almacenamiento extremadamente rápidas situadas dentro de la CPU.

Se utilizan para almacenar temporalmente:

- Datos.
- Direcciones.
- Resultados.
- Información necesaria para ejecutar instrucciones.

Serán especialmente importantes cuando posteriormente se estudie **ensamblador y arquitectura de computadores**.

---

## 4.3. RAM

La **RAM (Random Access Memory)** es la memoria principal utilizada por los programas mientras están ejecutándose.

Por ejemplo:

```text
Programa almacenado en SSD
          ↓
       RAM
          ↓
        CPU
```

La RAM es mucho más rápida que el almacenamiento permanente, pero normalmente es **volátil**: cuando el equipo pierde alimentación, su contenido desaparece.

---

## 4.4. Caché

La CPU dispone de diferentes niveles de memoria caché, normalmente denominados:

```text
L1
L2
L3
```

Su objetivo es reducir el tiempo necesario para acceder a datos e instrucciones utilizados frecuentemente.

De forma simplificada:

```text
CPU
 ↓
Caché
 ↓
RAM
 ↓
SSD/HDD
```

Cuanto más cerca está la memoria de la CPU, normalmente menor es su capacidad y mayor es su velocidad.

---

## 4.5. SSD y HDD

Son dispositivos de almacenamiento persistente.

A diferencia de la RAM:

```text
Apagar ordenador
       ↓
Los datos siguen almacenados
```

### HDD

Utiliza componentes mecánicos y platos magnéticos.

### SSD

Utiliza memoria flash y no contiene las partes mecánicas de un HDD tradicional.

En ciberseguridad es importante comprender la diferencia entre:

- almacenamiento;
- memoria RAM;
- memoria virtual.

---

## 4.6. Placa base

La placa base conecta los diferentes componentes del ordenador.

En ella encontramos, entre otros elementos:

- CPU.
- RAM.
- Ranuras de expansión.
- Conectores de almacenamiento.
- Controladores.
- Interfaces de comunicación.

---

## 4.7. Buses

Los **buses** permiten transportar información entre diferentes componentes.

De forma conceptual pueden transportar:

- Datos.
- Direcciones.
- Señales de control.

No es necesario profundizar inicialmente en la electrónica de los buses, pero sí entender que los componentes necesitan mecanismos para comunicarse entre sí.

---

## 4.8. Entrada y salida (I/O)

**I/O (Input/Output)** hace referencia a las operaciones de entrada y salida de información.

Ejemplos:

```text
Teclado → ordenador
Ratón → ordenador
SSD → ordenador
Ordenador → pantalla
Ordenador → red
```

El sistema operativo y los controladores permiten gestionar gran parte de estas operaciones.

---

# 5. Programas e instrucciones

Un programa es, simplificando, un conjunto de instrucciones que indican al ordenador qué debe hacer.

Por ejemplo:

```python
numero = 10
resultado = numero + 5
```

Python permite escribir esto de forma sencilla porque proporciona un alto nivel de abstracción.

Por debajo existen múltiples procesos de transformación y ejecución que finalmente terminan en instrucciones que puede ejecutar el procesador.

Esto será especialmente importante cuando posteriormente se estudien:

- Compiladores.
- Código máquina.
- C.
- Ensamblador.
- Reverse engineering.

---

# 6. Programa, proceso e hilo

Estos conceptos suelen confundirse.

### Programa

Un **programa** es el conjunto de instrucciones y datos almacenados que permiten realizar una determinada tarea.

Por ejemplo:

```text
chrome.exe
python.exe
notepad.exe
```

### Proceso

Un **proceso** es una instancia de un programa que está siendo ejecutada por el sistema operativo.

Un proceso tiene recursos asociados, como:

- Memoria.
- Identidad.
- Permisos.
- Archivos abiertos.
- Handles.
- Hilos.

### Hilo

Un **hilo (thread)** es una unidad de ejecución dentro de un proceso.

Un proceso puede tener:

```text
Proceso
├── Hilo 1
├── Hilo 2
└── Hilo 3
```

Comprender procesos e hilos será fundamental posteriormente para estudiar:

- Malware.
- Inyección de procesos.
- Escalada de privilegios.
- Análisis de procesos.
- Seguridad de sistemas.

---

# 7. Sistema operativo

El **sistema operativo** actúa como intermediario entre las aplicaciones y el hardware.

Ejemplos:

- Windows.
- Linux.
- macOS.
- Android.

De forma simplificada:

```text
Aplicaciones
      ↓
Sistema operativo
      ↓
Hardware
```

El sistema operativo gestiona recursos como:

- CPU.
- Memoria.
- Procesos.
- Archivos.
- Dispositivos.
- Usuarios.
- Permisos.
- Redes.

Por eso conocer los sistemas operativos es fundamental en ciberseguridad.

---

# 8. Kernel

El **kernel** es el núcleo del sistema operativo.

Es una de las partes con mayor nivel de privilegio del sistema y se encarga de gestionar recursos fundamentales.

Entre sus responsabilidades están:

- Gestión de procesos.
- Gestión de memoria.
- Comunicación con hardware.
- Sistema de archivos.
- Control de permisos.
- Interfaces con dispositivos.
- Syscalls.

De forma simplificada:

```text
Aplicación
     ↓
  Syscall
     ↓
  Kernel
     ↓
 Hardware
```

Este concepto será especialmente importante al estudiar **Linux, Windows internals y escalada de privilegios**.

---

# 9. Memoria

Comprender la memoria es uno de los puntos más importantes de esta base.

---

## 9.1. Direcciones de memoria

La memoria puede entenderse conceptualmente como una enorme colección de posiciones identificables mediante direcciones.

```text
Dirección       Contenido

0x0010          ...
0x0011          ...
0x0012          ...
0x0013          ...
```

Las direcciones suelen representarse en hexadecimal.

---

## 9.2. Stack

El **stack (pila)** es una zona de memoria utilizada, entre otras cosas, para gestionar información asociada a las llamadas a funciones.

Puede contener información como:

- Variables locales.
- Parámetros.
- Direcciones de retorno.
- Información relacionada con las llamadas.

Conceptualmente:

```text
Función A
   ↓
Función B
   ↓
Función C
```

Cada llamada puede crear un **stack frame**.

El stack será fundamental para comprender posteriormente determinadas vulnerabilidades, como los **stack-based buffer overflows**.

---

## 9.3. Heap

El **heap** es una región de memoria utilizada para asignaciones dinámicas.

En lenguajes como C puede utilizarse mediante:

```c
malloc()
free()
```

El heap también es importante para comprender vulnerabilidades relacionadas con la gestión dinámica de memoria.

---

## 9.4. Memoria virtual

Los sistemas operativos modernos utilizan **memoria virtual**.

Esto permite que cada proceso trabaje con su propio espacio de direcciones virtuales, proporcionando aislamiento entre procesos.

Conceptualmente:

```text
Proceso A → espacio de memoria virtual A
Proceso B → espacio de memoria virtual B
```

Esto es fundamental para la seguridad porque evita, en condiciones normales, que un proceso pueda acceder directamente a toda la memoria de otro proceso.

---

# 10. Sistema de archivos

El sistema operativo necesita organizar los datos almacenados.

### Archivos

Un archivo contiene información almacenada de forma persistente.

Puede contener:

- Texto.
- Imágenes.
- Programas.
- Configuraciones.
- Bases de datos.
- Logs.

### Directorios

Los directorios permiten organizar archivos.

```text
/
├── home
│   └── usuario
├── etc
├── var
└── tmp
```

La estructura exacta depende del sistema operativo.

---

## 10.1. Rutas

Una ruta identifica la ubicación de un archivo o directorio.

Ejemplo en Linux:

```text
/home/usuario/documento.txt
```

Ejemplo en Windows:

```text
C:\Users\Usuario\documento.txt
```

Hay que distinguir entre:

- rutas absolutas;
- rutas relativas.

---

## 10.2. Metadatos

Los archivos no contienen únicamente su contenido.

El sistema también puede almacenar información como:

- Tamaño.
- Fechas.
- Propietario.
- Permisos.
- Tipo.
- Ubicación.
- Otros atributos.

Estos datos son importantes en análisis forense y respuesta a incidentes.

---

# 11. Permisos y usuarios

Los sistemas operativos necesitan controlar **quién puede hacer qué**.

Conceptos fundamentales:

- Usuario.
- Grupo.
- Propietario.
- Permisos.
- Privilegios.
- Administrador/root.

Por ejemplo, en Linux aparecen habitualmente permisos como:

```text
r = read
w = write
x = execute
```

Y pueden aplicarse a:

```text
usuario
grupo
otros
```

En Windows existe un modelo diferente basado principalmente en **ACLs (Access Control Lists)** y otros mecanismos de seguridad.

Comprender permisos es fundamental para posteriormente estudiar:

- Escalada de privilegios.
- Control de acceso.
- Seguridad de archivos.
- Active Directory.
- Linux privilege escalation.

---

# 12. Arquitectura básica del ordenador

A nivel conceptual podemos representar un ordenador así:

```text
                 ┌───────────────┐
                 │      CPU      │
                 │  Registros    │
                 │    Caché      │
                 └───────┬───────┘
                         │
                 ┌───────▼───────┐
                 │      RAM      │
                 └───────┬───────┘
                         │
              ┌──────────┴──────────┐
              │                     │
       ┌──────▼──────┐       ┌──────▼──────┐
       │ SSD / HDD   │       │ Dispositivos │
       │             │       │    I/O       │
       └─────────────┘       └──────────────┘
```

El **sistema operativo** gestiona gran parte de estas interacciones y proporciona servicios que permiten a las aplicaciones utilizar los recursos del ordenador.

---

# 13. Conceptos que conviene relacionar

No basta con estudiar cada concepto aisladamente. Lo importante es entender sus relaciones.

Por ejemplo:

```text
Programa
   ↓
Proceso
   ↓
Memoria virtual
   ├── Stack
   ├── Heap
   └── Código / datos
   ↓
CPU
   ↓
Instrucciones
```

Y:

```text
Aplicación
    ↓
Sistema operativo
    ↓
Kernel
    ↓
Drivers / hardware
    ↓
CPU / RAM / SSD / dispositivos
```

Esto proporciona una visión mucho más útil para ciberseguridad que memorizar definiciones independientes.

---

# 14. Relación con la ciberseguridad

| Concepto | Aparece posteriormente en |
|---|---|
| Binario / hexadecimal | Análisis de datos, memoria, reversing |
| CPU | Arquitectura, malware, reversing |
| Registros | Ensamblador, exploit development |
| Procesos | Malware, EDR, escalada de privilegios |
| Hilos | Malware, procesos, análisis |
| Kernel | Rootkits, drivers, escalada |
| Stack | Buffer overflow, exploit development |
| Heap | Heap exploitation |
| Memoria virtual | Aislamiento y explotación |
| Archivos | Malware, forense, permisos |
| Permisos | Escalada de privilegios |
| Usuarios | Autenticación y control de acceso |
| Sistema operativo | Prácticamente toda la ciberseguridad |
| I/O | Drivers, dispositivos y sistemas |
| Unicode/ASCII | Web, protocolos, parsing y explotación |
| Procesos + memoria | Malware y análisis dinámico |

---

# Meta

Al terminar este bloque deberías ser capaz de explicar, **sin entrar todavía en detalles de bajo nivel**, qué ocurre aproximadamente cuando ejecutas un programa:

```text
1. El programa está almacenado en el SSD/HDD.
              ↓
2. El sistema operativo lo carga en memoria.
              ↓
3. Se crea un proceso.
              ↓
4. El proceso recibe un espacio de memoria virtual.
              ↓
5. Se crean y utilizan estructuras como stack y heap.
              ↓
6. Sus instrucciones y datos son procesados por la CPU.
              ↓
7. El programa solicita recursos al sistema operativo.
              ↓
8. El kernel gestiona esas solicitudes y el acceso al hardware.
              ↓
9. El programa puede utilizar archivos, red, dispositivos, etc.
```

**La meta real no es memorizar esta secuencia**, sino conseguir que conceptos como **CPU, RAM, proceso, hilo, kernel, memoria virtual, stack, heap, archivos y permisos** formen un único modelo mental.

Cuando ese modelo esté claro, conceptos posteriores de **Linux, Windows, redes, malware, escalada de privilegios, reverse engineering y Red Team** serán mucho más fáciles de entender.
