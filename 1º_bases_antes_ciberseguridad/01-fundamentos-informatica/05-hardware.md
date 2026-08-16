# 5. Hardware

El hardware está formado por los componentes físicos del ordenador.

Para ciberseguridad interesa comprender **qué hace cada componente y cómo interactúa con el resto**.

---

## 5.1. CPU

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

## 5.2. Registros

Los **registros** son pequeñas áreas de almacenamiento extremadamente rápidas situadas dentro de la CPU.

Se utilizan para almacenar temporalmente:

- Datos.
- Direcciones.
- Resultados.
- Información necesaria para ejecutar instrucciones.

Serán especialmente importantes cuando posteriormente se estudie **ensamblador y arquitectura de computadores**.

---

## 5.3. RAM

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

## 5.4. Caché

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

## 5.5. SSD y HDD

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

## 5.6. Placa base

La placa base conecta los diferentes componentes del ordenador.

En ella encontramos, entre otros elementos:

- CPU.
- RAM.
- Ranuras de expansión.
- Conectores de almacenamiento.
- Controladores.
- Interfaces de comunicación.

---

## 5.7. Buses

Los **buses** permiten transportar información entre diferentes componentes.

De forma conceptual pueden transportar:

- Datos.
- Direcciones.
- Señales de control.

No es necesario profundizar inicialmente en la electrónica de los buses, pero sí entender que los componentes necesitan mecanismos para comunicarse entre sí.

---

## 5.8. Entrada y salida (I/O)

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

