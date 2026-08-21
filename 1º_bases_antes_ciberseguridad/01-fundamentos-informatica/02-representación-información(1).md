# 2. Representación de la información

Los ordenadores trabajan internamente con información representada mediante **bits**.

Todo tipo de información digital —texto, imágenes, audio, vídeo, programas, instrucciones o datos— debe representarse finalmente mediante valores que el sistema pueda almacenar y procesar.

En el nivel más básico, estos valores pueden representarse mediante:

```text
0
1
```

Estos dos valores forman la base del sistema binario.

---

## 2.1. Bit

Un **bit** (*binary digit*) es la unidad básica de información digital.

Un bit solamente puede tener dos valores:

```text
0
1
```

Por tanto, un bit puede representar:

```text
2 valores diferentes
```

Si combinamos varios bits, aumenta la cantidad de valores que podemos representar.

```text
1 bit  → 2 valores
2 bits → 4 valores
3 bits → 8 valores
4 bits → 16 valores
```

La cantidad de combinaciones se calcula mediante:

```text
2ⁿ
```

donde `n` es el número de bits.

Por ejemplo:

```text
8 bits

2⁸ = 256 combinaciones
```

---

## 2.2. Byte

Un **byte** está formado por **8 bits**.

```text
1 byte = 8 bits
```

Como cada bit puede tener dos valores, un byte puede representar:

```text
2⁸ = 256 combinaciones
```

Estas combinaciones van desde:

```text
00000000
```

hasta:

```text
11111111
```

Si interpretamos esas combinaciones como un número entero sin signo, obtenemos:

```text
00000000 = 0
11111111 = 255
```

Por tanto:

```text
1 byte → 256 valores posibles
```

o, cuando se utiliza para representar un entero sin signo:

```text
0–255
```

Es importante distinguir entre cantidad de combinaciones y rango numérico.

---

## 2.3. Más bits, más combinaciones

La capacidad de representación aumenta exponencialmente con el número de bits.

| Bits | Combinaciones |
|---:|---:|
| 1 | 2 |
| 2 | 4 |
| 3 | 8 |
| 4 | 16 |
| 8 | 256 |
| 16 | 65.536 |
| 32 | 4.294.967.296 |
| 64 | 18.446.744.073.709.551.616 |

La fórmula general es:

```text
Número de combinaciones = 2ⁿ
```

Esto será importante posteriormente para comprender:

- tamaños de datos;
- direcciones;
- registros;
- espacios de memoria;
- claves criptográficas;
- rangos de valores;
- arquitecturas de 32 y 64 bits.

---

## 2.4. Bit frente a byte

Es muy importante no confundir estas dos unidades.

### Bit

Se representa normalmente mediante:

```text
b
```

### Byte

Se representa normalmente mediante:

```text
B
```

Por tanto:

```text
1 B = 8 b
```

La diferencia entre `b` y `B` es importante especialmente cuando trabajamos con redes y almacenamiento.

Por ejemplo:

```text
100 Mb/s
```

significa:

```text
100 megabits por segundo
```

mientras que:

```text
100 MB
```

significa:

```text
100 megabytes
```

No representan la misma cantidad.

---

## 2.5. Unidades de información

Las unidades más habituales son:

- bit (`b`)
- byte (`B`)
- kilobyte
- megabyte
- gigabyte
- terabyte
- petabyte

Sin embargo, existen dos sistemas de medida diferentes.

---

## 2.6. Unidades decimales

Las unidades decimales utilizan potencias de 1000.

```text
1 kB = 1.000 bytes
1 MB = 1.000.000 bytes
1 GB = 1.000.000.000 bytes
1 TB = 1.000.000.000.000 bytes
```

Estas unidades son habituales en las capacidades comerciales indicadas por los fabricantes de almacenamiento.

---

## 2.7. Unidades binarias

En informática también se utilizan unidades basadas en potencias de 1024.

Sus nombres técnicos son:

```text
1 KiB = 1.024 bytes
1 MiB = 1.024 KiB
1 GiB = 1.024 MiB
1 TiB = 1.024 GiB
```

Por tanto:

```text
1 KiB = 1.024 bytes
```

mientras que:

```text
1 kB = 1.000 bytes
```

No son exactamente lo mismo.

La diferencia entre ambas convenciones explica parte de la diferencia que podemos observar entre la capacidad anunciada de un dispositivo y la capacidad que muestra un sistema operativo.

---

## 2.8. Representación binaria

El sistema binario utiliza únicamente dos símbolos:

```text
0
1
```

Cada posición representa una potencia de 2.

```text
2³  2²  2¹  2⁰
 8   4   2   1
```

Por ejemplo:

```text
1010₂
```

se calcula como:

```text
1×8 + 0×4 + 1×2 + 0×1

= 8 + 2

= 10
```

Por tanto:

```text
1010₂ = 10₁₀
```

---

## 2.9. Sistema hexadecimal

Trabajar directamente con largas secuencias de bits resulta poco cómodo para las personas.

Por eso en informática se utiliza frecuentemente el **sistema hexadecimal**.

El hexadecimal utiliza 16 símbolos:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Los valores de las letras son:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

La gran ventaja del hexadecimal es su relación directa con el binario.

---

## 2.10. Relación entre hexadecimal y binario

Un dígito hexadecimal representa exactamente cuatro bits.

```text
Hexadecimal  Binario
0            0000
1            0001
2            0010
3            0011
4            0100
5            0101
6            0110
7            0111
8            1000
9            1001
A            1010
B            1011
C            1100
D            1101
E            1110
F            1111
```

Por tanto:

```text
1 dígito hexadecimal = 4 bits
2 dígitos hexadecimales = 8 bits = 1 byte
```

Por ejemplo:

```text
11111111₂ = FF₁₆ = 255₁₀
```

---

## 2.11. La misma información puede tener diferentes representaciones

Un mismo valor puede representarse utilizando diferentes sistemas.

Por ejemplo:

```text
Decimal:     65
Binario:     01000001
Hexadecimal: 41
```

Son tres formas diferentes de representar el mismo valor.

Esta relación será importante cuando estudiemos la representación de texto.

Por ejemplo:

```text
0x41 = 65 = 01000001₂
```

y en ASCII:

```text
0x41 = A
```

---

## 2.12. ¿Por qué es importante el hexadecimal?

El hexadecimal aparece constantemente en informática y especialmente en ciberseguridad.

Puede encontrarse en:

- direcciones de memoria;
- volcados de memoria (*memory dumps*);
- código máquina;
- bytes;
- shellcode;
- hashes;
- direcciones MAC;
- análisis de archivos;
- firmas de archivos;
- reverse engineering;
- análisis de malware.

Por ejemplo:

```text
48 8B 05 12 34 56 78
```

puede representar bytes de código máquina.

No es necesario saber todavía qué instrucciones representan esos bytes. Lo importante en esta etapa es reconocer que estamos viendo valores expresados en hexadecimal que representan datos binarios.

---

## 2.13. Objetivos de aprendizaje

Al terminar este tema deberías poder:

- explicar qué es un bit;
- explicar qué es un byte;
- calcular cuántas combinaciones representan `n` bits;
- diferenciar bit y byte;
- diferenciar unidades decimales y binarias;
- convertir valores básicos entre decimal y binario;
- reconocer valores hexadecimales;
- convertir hexadecimal básico a binario;
- convertir binario básico a hexadecimal;
- explicar por qué hexadecimal se utiliza en informática;
- reconocer que un mismo valor puede tener diferentes representaciones.

---

## 2.14. Idea fundamental

> **Los ordenadores procesan información digital, pero nosotros podemos representar esa misma información mediante diferentes sistemas de numeración.**

Comprender esta idea será fundamental para los siguientes temas de informática y, posteriormente, para memoria, redes, sistemas operativos, análisis de archivos, criptografía y ciberseguridad.
