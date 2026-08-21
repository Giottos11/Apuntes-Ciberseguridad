# 4. Representación de texto

Los ordenadores no almacenan directamente conceptos como:

```text
Hola
A
á
€
```

Para un ordenador, esos caracteres deben convertirse en **datos numéricos** que puedan almacenarse y procesarse.

Este proceso se conoce como **codificación de caracteres**.

---

## 4.1. Caracteres y valores numéricos

Un carácter puede asociarse a un valor numérico.

Por ejemplo, en ASCII:

```text
A → 65
B → 66
C → 67
```

Estos valores pueden expresarse en diferentes sistemas de numeración.

Por ejemplo:

```text
A
↓
65 decimal
↓
0x41 hexadecimal
↓
01000001 binario
```

Por tanto, un carácter puede relacionarse con:

```text
carácter
   ↓
valor
   ↓
representación binaria
   ↓
bytes
```

---

## 4.2. ASCII

**ASCII** (*American Standard Code for Information Interchange*) es una codificación de caracteres ampliamente utilizada históricamente en informática.

ASCII original utiliza **7 bits** y permite representar:

```text
2⁷ = 128 valores
```

Estos valores incluyen:

- letras mayúsculas;
- letras minúsculas;
- números;
- signos de puntuación;
- caracteres de control.

Por ejemplo:

```text
A → 65
B → 66
C → 67

a → 97
b → 98
c → 99
```

---

## 4.3. ASCII y hexadecimal

Los valores ASCII pueden representarse también en hexadecimal.

Por ejemplo:

```text
A → 65 decimal → 0x41
a → 97 decimal → 0x61
```

Por tanto:

```text
A = 0x41
a = 0x61
```

Esto resulta especialmente útil en análisis de datos y bajo nivel.

Por ejemplo, si encontramos:

```text
48 6F 6C 61
```

podemos interpretar cada byte como un valor hexadecimal:

```text
48 → H
6F → o
6C → l
61 → a
```

Por tanto:

```text
48 6F 6C 61
```

representa:

```text
Hola
```

Este tipo de conversión aparece frecuentemente en:

- análisis de archivos;
- análisis de memoria;
- redes;
- debugging;
- reverse engineering;
- malware analysis.

---

## 4.4. Limitaciones de ASCII

ASCII resulta suficiente para representar el alfabeto inglés y determinados símbolos, pero tiene una limitación importante.

Solo dispone de:

```text
128 valores
```

Por tanto, no puede representar por sí solo todos los caracteres utilizados en los diferentes idiomas del mundo.

Por ejemplo:

```text
á
ñ
ç
€
中
Ж
ع
```

requieren un sistema de representación más amplio.

---

## 4.5. Unicode

**Unicode** es un estándar diseñado para representar caracteres de prácticamente todos los sistemas de escritura utilizados en los sistemas informáticos modernos.

Unicode asigna a cada carácter un identificador denominado **code point**.

Por ejemplo:

```text
A → U+0041
a → U+0061
€ → U+20AC
```

La notación:

```text
U+....
```

indica normalmente un valor Unicode expresado en hexadecimal.

Por ejemplo:

```text
U+0041
```

corresponde al carácter:

```text
A
```

---

## 4.6. Unicode no es lo mismo que UTF-8

Esta diferencia es fundamental.

**Unicode** define los caracteres y sus **code points**.

Una **codificación** determina cómo esos caracteres se representan mediante bytes.

Entre las codificaciones Unicode más conocidas encontramos:

- UTF-8
- UTF-16
- UTF-32

Por tanto:

```text
Unicode
   ↓
define caracteres / code points

UTF-8
UTF-16
UTF-32
   ↓
formas de codificar esos caracteres
```

No debemos considerar UTF-8 y Unicode como exactamente lo mismo.

---

## 4.7. UTF-8

**UTF-8** es una codificación de Unicode basada en unidades de 8 bits, es decir, bytes.

Una de sus principales características es que utiliza un número variable de bytes para representar los caracteres.

Los caracteres ASCII ocupan:

```text
1 byte
```

Otros caracteres Unicode pueden ocupar:

```text
2 bytes
3 bytes
4 bytes
```

Esto permite representar una enorme cantidad de caracteres manteniendo compatibilidad con ASCII.

---

## 4.8. Compatibilidad de UTF-8 con ASCII

Los primeros 128 valores Unicode corresponden a los caracteres ASCII.

Por ello, los caracteres ASCII tienen la misma representación en UTF-8.

Por ejemplo:

```text
A
```

tiene:

```text
ASCII decimal: 65
ASCII hexadecimal: 0x41
UTF-8: 0x41
```

---

## 4.9. Ejemplo con caracteres no ASCII

Consideremos:

```text
á
```

Este carácter no puede representarse mediante ASCII estándar.

Sin embargo, puede representarse mediante Unicode y codificarse utilizando UTF-8.

Por tanto:

```text
Carácter
   ↓
Code point Unicode
   ↓
Codificación UTF-8
   ↓
Bytes
```

Este modelo mental será importante posteriormente para comprender archivos y comunicaciones de red.

---

## 4.10. UTF-16 y UTF-32

Además de UTF-8 existen otras codificaciones Unicode.

### UTF-8

- utiliza unidades de 8 bits;
- utiliza entre 1 y 4 bytes para un carácter;
- es extremadamente común en Internet;
- mantiene compatibilidad directa con ASCII.

### UTF-16

Utiliza unidades de 16 bits y puede necesitar una o dos unidades para determinados caracteres.

### UTF-32

Utiliza unidades de 32 bits.

Su representación es conceptualmente sencilla, pero utiliza más espacio que UTF-8 para muchos textos.

---

## 4.11. ¿Por qué importa esto en informática?

La representación de texto aparece prácticamente en todos los sistemas informáticos.

Por ejemplo:

- archivos de texto;
- código fuente;
- archivos JSON;
- páginas web;
- cabeceras HTTP;
- bases de datos;
- logs;
- terminales;
- correos electrónicos;
- nombres de archivos;
- protocolos de red.

Cuando una aplicación recibe texto, necesita interpretarlo utilizando una codificación determinada.

Si la codificación utilizada para escribir los datos y la utilizada para leerlos no coinciden, pueden aparecer errores de interpretación.

---

## 4.12. Texto y bytes

Desde el punto de vista de un ordenador, un archivo de texto termina almacenándose como una secuencia de bytes.

Podemos representar el proceso de forma simplificada:

```text
Texto
  ↓
Caracteres
  ↓
Unicode / code points
  ↓
Codificación
  ↓
Bytes
  ↓
Almacenamiento o transmisión
```

Cuando el sistema recupera la información ocurre el proceso contrario:

```text
Bytes
  ↓
Decodificación
  ↓
Code points
  ↓
Caracteres
  ↓
Texto
```

La diferencia entre **codificar** y **decodificar** será importante posteriormente en programación, redes y análisis de archivos.

---

## 4.13. Ejemplo conceptual

Supongamos el texto:

```text
ABC
```

Podemos representarlo mediante ASCII:

```text
A → 65
B → 66
C → 67
```

En hexadecimal:

```text
A → 41
B → 42
C → 43
```

Y como bytes:

```text
41 42 43
```

Por tanto:

```text
Texto:
ABC

Valores decimales:
65 66 67

Valores hexadecimales:
41 42 43

Bytes:
41 42 43
```

---

## 4.14. Importancia para ciberseguridad

Comprender la representación de texto resulta especialmente útil en:

- análisis de logs;
- análisis de tráfico de red;
- HTTP;
- APIs;
- archivos;
- malware analysis;
- reverse engineering;
- análisis hexadecimal;
- debugging;
- explotación de vulnerabilidades;
- análisis de entradas controladas por el usuario.

Por ejemplo, durante el análisis de una aplicación podemos encontrar:

```text
41 64 6D 69 6E
```

Si reconocemos hexadecimal y ASCII:

```text
41 → A
64 → d
6D → m
69 → i
6E → n
```

Resultado:

```text
Admin
```

---

## 4.15. Conceptos que debemos diferenciar

### Carácter

La unidad conceptual de texto que queremos representar.

Ejemplo:

```text
A
```

### Code point

El identificador asignado al carácter dentro de Unicode.

Ejemplo:

```text
A → U+0041
```

### Codificación

La forma en que ese carácter se convierte en bytes.

Ejemplo:

```text
A → UTF-8 → 41
```

### Byte

La unidad de datos que finalmente puede almacenarse o transmitirse.

---

## 4.16. Objetivos de aprendizaje

Al terminar este tema deberías poder:

- explicar por qué los ordenadores necesitan codificar texto;
- explicar qué es ASCII;
- saber que ASCII utiliza originalmente 7 bits;
- reconocer valores ASCII básicos;
- convertir caracteres ASCII sencillos a hexadecimal;
- explicar qué es Unicode;
- explicar qué es un code point;
- diferenciar Unicode de UTF-8;
- explicar qué es UTF-8;
- conocer las diferencias generales entre UTF-8, UTF-16 y UTF-32;
- entender la relación entre caracteres, code points, codificación y bytes;
- reconocer texto ASCII representado en hexadecimal.

---

## 4.17. Idea fundamental

> **El ordenador no almacena directamente el significado de un texto; almacena datos que, mediante una determinada codificación, pueden interpretarse como caracteres.**

Por tanto:

```text
Carácter
   ↓
Unicode / code point
   ↓
Codificación
   ↓
Bytes
```

Comprender esta cadena será fundamental para estudiar posteriormente archivos, memoria, redes, programación, protocolos y análisis de datos.
