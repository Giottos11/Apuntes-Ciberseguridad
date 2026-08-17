## 2. Representación de la información

Los ordenadores trabajan internamente con información representada mediante **bits**. Todo tipo de información digital —texto, imágenes, audio, vídeo, programas o instrucciones— termina siendo codificada como una secuencia de 0 y 1.

El sistema binario permite que los componentes electrónicos del ordenador representen de forma sencilla dos estados diferentes, como ausencia/presencia de señal eléctrica, apagado/encendido o falso/verdadero.

Comprender cómo se representa la información es fundamental para estudiar posteriormente conceptos como memoria, almacenamiento, codificación, sistema hexadecimal, direcciones de memoria, redes y análisis de datos.

### 2.1. Bit

Un **bit** (binary digit) es la unidad mínima de información que puede manejar un sistema digital. Solo puede tener dos valores posibles:

```text
0
1
```
Estos dos valores pueden utilizarse para representar dos estados diferentes. Por ejemplo:

```text
0 → apagado
1 → encendido
```

Un único bit tiene 2 valores posibles. Al combinar varios bits, aumenta exponencialmente la cantidad de información que pueden representar.

### 2.2. Byte

Un **byte** está formado por **8 bits**.

```text
1 byte = 8 bits
```
Al disponer de 8 bits, cada uno con dos estados posibles, podemos representar:

```text
2⁸ = 256 valores diferentes
```
Por tanto, un byte puede representar 256 combinaciones distintas, desde:

Por ejemplo, desde `00000000` hasta `11111111`.

En representación decimal:
```text
00000000 = 0
00000001 = 1
00000010 = 2
...
11111111 = 255
```

Por tanto, un byte permite representar valores comprendidos entre **0 y 255** cuando se utiliza para almacenar un número entero sin signo.

El byte es una unidad fundamental en informática porque se utiliza habitualmente para representar **datos, caracteres y valores numéricos**.

### 2.3. Unidades de información

Las principales unidades utilizadas para expresar cantidades de información son:

- bit (`b`)
- byte (`B`)
- kilobyte (KB)
- megabyte (MB)
- gigabyte (GB)
- terabyte (TB)
- petabyte (PB)

Es importante distinguir entre bits y bytes:

```text
1 B = 8 b
```

También hay diferentes convenciones para calcular estas unidades, por lo que un GB comercial no siempre coincide exactamente con una potencia de 1024.

### 2.4. Unidades decimales y binarias

Existen diferentes convenciones para expresar las cantidades de información.

En el sistema decimal, utilizado habitualmente por los fabricantes de dispositivos de almacenamiento:

```text
1 KB = 1.000 bytes
1 MB = 1.000.000 bytes
1 GB = 1.000.000.000 bytes
1 TB = 1.000.000.000.000 bytes
```

En el sistema binario, las unidades se calculan utilizando potencias de 1024:

```text
1 KiB = 1.024 bytes
1 MiB = 1.024 KiB
1 GiB = 1.024 MiB
1 TiB = 1.024 GiB
```

Las unidades binarias se identifican técnicamente mediante los prefijos KiB, MiB, GiB y TiB, mientras que KB, MB, GB y TB corresponden estrictamente a las unidades decimales.

Por este motivo, la capacidad indicada por el fabricante de un disco o SSD puede no coincidir exactamente con la capacidad que muestra el sistema operativo.

### 2.5. Sistema binario y sistema hexadecimal

Aunque los ordenadores trabajan internamente con bits, representar grandes cantidades de 0 y 1 resulta poco práctico para las personas. Por ello, en informática se utiliza con mucha frecuencia el sistema hexadecimal, especialmente en programación de bajo nivel, administración de sistemas y ciberseguridad.

El sistema hexadecimal utiliza 16 símbolos:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Cada dígito hexadecimal representa exactamente 4 bits:

```text
0000 = 0
0001 = 1
0010 = 2
...
1111 = F
```

Por tanto:

```text
1 dígito hexadecimal = 4 bits
2 dígitos hexadecimales = 8 bits = 1 byte
```

Por ejemplo:

```text
Binario:     11111111
Hexadecimal: FF
Decimal:     255
```

El sistema hexadecimal será especialmente importante posteriormente para trabajar con direcciones de memoria, valores binarios, volcados de memoria, código máquina, hashes, direcciones MAC, permisos y análisis de malware.
---

[Volver al indice](/1º_bases_antes_ciberseguridad/2ºreadme.md)