# 10. Memoria

Comprender la memoria es uno de los puntos más importantes de esta base.

---

## 10.1. Direcciones de memoria

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

## 10.2. Stack

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

## 10.3. Heap

El **heap** es una región de memoria utilizada para asignaciones dinámicas.

En lenguajes como C puede utilizarse mediante:

```c
malloc()
free()
```

El heap también es importante para comprender vulnerabilidades relacionadas con la gestión dinámica de memoria.

---

## 10.4. Memoria virtual

Los sistemas operativos modernos utilizan **memoria virtual**.

Esto permite que cada proceso trabaje con su propio espacio de direcciones virtuales, proporcionando aislamiento entre procesos.

Conceptualmente:

```text
Proceso A → espacio de memoria virtual A
Proceso B → espacio de memoria virtual B
```

Esto es fundamental para la seguridad porque evita, en condiciones normales, que un proceso pueda acceder directamente a toda la memoria de otro proceso.

---

