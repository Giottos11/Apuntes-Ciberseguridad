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

