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

