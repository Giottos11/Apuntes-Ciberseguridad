# 1. Fundamentos de informática

## 1.1. Introducción

Antes de comenzar a estudiar ciberseguridad es necesario construir una base sólida de **informática**.

El objetivo de este apartado no es convertirse en ingeniero de hardware, sino comprender qué ocurre dentro de un sistema informático cuando ejecutamos un programa, almacenamos información o realizamos una determinada operación.

La ciberseguridad se apoya constantemente en conceptos propios de la informática. Cuando analizamos una vulnerabilidad, investigamos un proceso, estudiamos un malware o intentamos comprender por qué una aplicación puede ser explotada, necesitamos saber qué está ocurriendo por debajo de la interfaz que vemos.

Por este motivo, antes de estudiar técnicas ofensivas o defensivas es necesario comprender progresivamente:

- cómo se representa la información;
- cómo se almacenan los datos;
- cómo funciona el procesador;
- cómo se ejecutan las instrucciones;
- cómo se organiza la memoria;
- cómo se comunican los componentes;
- cómo se ejecutan los programas;
- qué es un proceso y qué es un hilo;
- qué función desempeña el sistema operativo;
- cómo se comunican el software y el hardware;
- qué son las llamadas al sistema (*syscalls*);
- cómo se gestionan los recursos de un ordenador.

---

## 1.2. ¿Por qué estudiar informática antes de ciberseguridad?

La ciberseguridad no es una disciplina aislada.

Una vulnerabilidad de software puede estar relacionada con:

- la forma en que se gestiona la memoria;
- los permisos de un sistema operativo;
- la comunicación entre procesos;
- la validación de datos;
- la comunicación de red;
- la autenticación;
- la arquitectura de una aplicación;
- la interacción entre software y hardware.

Por ejemplo, para comprender posteriormente un **buffer overflow** será necesario entender memoria, direcciones, bytes, stack, instrucciones y procesos.

Para comprender una **escalada de privilegios** será necesario conocer usuarios, permisos, procesos y separación entre diferentes niveles de privilegio.

Para comprender **malware** será necesario saber cómo se ejecutan los programas, cómo interactúan con el sistema operativo y cómo utilizan los recursos del sistema.

Para comprender **reverse engineering** será necesario conocer binarios, instrucciones, memoria, registros y representación hexadecimal.

Por tanto, los fundamentos informáticos no son conocimientos independientes de la ciberseguridad. Constituyen una parte de su base técnica.

---

## 1.3. De la información al hardware

Un ordenador necesita representar información de alguna manera que sus componentes electrónicos puedan procesar.

En el nivel más básico, la información digital puede representarse mediante **bits**, cuyos valores son:

```text
0
1
```

A partir de estos bits se construyen representaciones más complejas:

```text
bits
  ↓
bytes
  ↓
números
  ↓
texto
  ↓
datos
  ↓
programas e instrucciones
```

Estos datos son posteriormente almacenados, transportados y procesados por los diferentes componentes del sistema.

Por eso conceptos aparentemente sencillos como **binario, hexadecimal y bytes** terminan siendo importantes cuando posteriormente trabajamos con:

- memoria;
- archivos;
- redes;
- código máquina;
- ejecutables;
- hashes;
- direcciones;
- protocolos;
- malware.

---

## 1.4. Del software al hardware

Cuando ejecutamos un programa parece que simplemente hacemos clic sobre un icono y el programa comienza a funcionar.

Internamente ocurre un proceso mucho más complejo.

De forma simplificada:

```text
Programa
   ↓
Instrucciones
   ↓
Sistema operativo
   ↓
Procesador / memoria / almacenamiento
   ↓
Hardware
```

El programa está formado por datos e instrucciones que deben ser interpretados y ejecutados por el sistema.

La **CPU** ejecuta instrucciones.

La **memoria RAM** mantiene temporalmente los datos y programas que están siendo utilizados.

El **almacenamiento** conserva información de forma persistente.

El **sistema operativo** coordina estos recursos y proporciona servicios que permiten a las aplicaciones utilizarlos.

Más adelante estudiaremos cada uno de estos componentes por separado.

---

## 1.5. Conceptos que se estudiarán en esta sección

### Representación de la información

- Bit
- Byte
- Unidades de información
- Binario
- Decimal
- Hexadecimal
- ASCII
- Unicode
- UTF-8

### Arquitectura del ordenador

- CPU
- Registros
- ALU
- Memoria
- Caché
- RAM
- Almacenamiento
- Buses
- Entrada/salida

### Ejecución de programas

- Instrucciones
- Procesos
- Hilos
- Stack
- Heap
- Memoria virtual
- Espacio de usuario
- Espacio de kernel

### Sistema operativo

- Kernel
- Procesos
- Servicios
- Sistema de archivos
- Permisos
- Syscalls
- Gestión de memoria
- Gestión de recursos

Estos conceptos se irán introduciendo de forma progresiva.

---

## 1.6. Relación con la ciberseguridad

Comprender informática permite posteriormente comprender mejor problemas de seguridad como:

- vulnerabilidades de memoria;
- buffer overflows;
- ejecución de código;
- escalada de privilegios;
- inyección;
- malware;
- procesos maliciosos;
- manipulación de archivos;
- análisis de binarios;
- reverse engineering;
- exploit development;
- seguridad de aplicaciones;
- seguridad de sistemas operativos.

También permite comprender mejor las herramientas utilizadas en ciberseguridad.

Una herramienta como `Wireshark`, `Nmap`, `Ghidra`, `Burp Suite` o `GDB` resulta mucho más fácil de comprender cuando se conocen los conceptos que existen detrás de ella.

---

## 1.7. Objetivo de esta sección

Al finalizar los fundamentos de informática deberías ser capaz de responder, al menos a nivel conceptual:

- ¿Cómo representa un ordenador la información?
- ¿Qué diferencia existe entre un bit y un byte?
- ¿Por qué se utiliza hexadecimal?
- ¿Cómo se representa un carácter?
- ¿Qué diferencia existe entre ASCII y Unicode?
- ¿Qué es UTF-8?
- ¿Qué ocurre cuando se ejecuta un programa?
- ¿Qué función tiene la CPU?
- ¿Qué función tiene la memoria?
- ¿Qué es un proceso?
- ¿Qué es un hilo?
- ¿Qué es el kernel?
- ¿Qué es una syscall?
- ¿Cómo interactúa una aplicación con el sistema operativo?

No es necesario conocer todavía todos estos conceptos en profundidad. La finalidad de esta primera sección es construir progresivamente el modelo mental necesario para comprenderlos.

---

## 1.8. Idea fundamental

> **Antes de aprender cómo atacar un sistema, hay que entender cómo funciona el sistema.**

La ciberseguridad consiste, en gran medida, en comprender cómo debería funcionar una tecnología, identificar qué ocurre cuando ese funcionamiento se rompe o se utiliza de una forma no prevista y determinar qué consecuencias puede tener.

Por eso los fundamentos informáticos constituyen el punto de partida de todo el roadmap.
