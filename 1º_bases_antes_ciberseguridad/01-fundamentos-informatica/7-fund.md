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

