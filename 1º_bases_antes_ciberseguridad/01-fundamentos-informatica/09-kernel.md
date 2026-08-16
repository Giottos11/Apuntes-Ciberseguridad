# 9. Kernel

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

