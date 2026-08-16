# 15. Relación con la ciberseguridad

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
