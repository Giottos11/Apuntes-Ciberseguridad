# 3. Sistemas de numeración

Un **sistema de numeración** es un método utilizado para representar cantidades mediante un conjunto determinado de símbolos y unas reglas de posición.

En informática trabajaremos principalmente con tres sistemas:

- decimal;
- binario;
- hexadecimal.

Comprender estos tres sistemas es fundamental porque una misma información puede aparecer representada de diferentes formas dependiendo del contexto.

---

## 3.1. Sistema decimal

El sistema decimal es el sistema de numeración que utilizamos habitualmente las personas.

Es un sistema de **base 10** y utiliza diez símbolos:

```text
0 1 2 3 4 5 6 7 8 9
```

La posición de cada cifra determina su valor.

Por ejemplo:

```text
583
```

puede descomponerse como:

```text
5 × 10²
8 × 10¹
3 × 10⁰
```

Por tanto:

```text
583 = 500 + 80 + 3
```

---

## 3.2. Base de un sistema de numeración

La **base** indica cuántos símbolos diferentes utiliza un sistema antes de pasar a una nueva posición.

Por ejemplo:

### Decimal

Base 10:

```text
0–9
```

### Binario

Base 2:

```text
0–1
```

### Hexadecimal

Base 16:

```text
0–9 + A–F
```

La posición de cada símbolo representa una potencia de la base.

---

## 3.3. Sistema binario

El sistema binario es un sistema de **base 2**.

Utiliza únicamente dos símbolos:

```text
0
1
```

Esto resulta especialmente adecuado para los sistemas digitales porque permite representar dos estados diferenciables.

Por ejemplo:

```text
0 → estado 0
1 → estado 1
```

Una secuencia binaria puede representar un número.

Por ejemplo:

```text
1010₂
```

---

## 3.4. Valor posicional en binario

Cada posición representa una potencia de 2.

```text
2³  2²  2¹  2⁰
 8   4   2   1
```

Para convertir:

```text
1010₂
```

a decimal:

```text
1×2³ + 0×2² + 1×2¹ + 0×2⁰
```

Por tanto:

```text
8 + 0 + 2 + 0 = 10
```

Resultado:

```text
1010₂ = 10₁₀
```

---

## 3.5. Ejemplo de conversión binario → decimal

Convertimos:

```text
1101₂
```

Aplicamos los valores posicionales:

```text
1×8
1×4
0×2
1×1
```

Resultado:

```text
8 + 4 + 0 + 1 = 13
```

Por tanto:

```text
1101₂ = 13₁₀
```

---

## 3.6. Conversión decimal → binario

Para convertir un número decimal a binario podemos utilizar divisiones sucesivas entre 2.

Por ejemplo, para convertir:

```text
13₁₀
```

dividimos sucesivamente:

```text
13 ÷ 2 = 6   resto 1
 6 ÷ 2 = 3   resto 0
 3 ÷ 2 = 1   resto 1
 1 ÷ 2 = 0   resto 1
```

Leyendo los restos de abajo hacia arriba:

```text
1101
```

Por tanto:

```text
13₁₀ = 1101₂
```

---

## 3.7. Sistema hexadecimal

El sistema hexadecimal es un sistema de **base 16**.

Utiliza dieciséis símbolos:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Las letras representan:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

Por ejemplo:

```text
10₁₀ = A₁₆
15₁₀ = F₁₆
16₁₀ = 10₁₆
```

---

## 3.8. Valor posicional en hexadecimal

Cada posición representa una potencia de 16.

Por ejemplo:

```text
2F₁₆
```

se calcula como:

```text
2 × 16¹ + F × 16⁰
```

Como:

```text
F = 15
```

tenemos:

```text
2 × 16 + 15 × 1

= 32 + 15

= 47
```

Por tanto:

```text
2F₁₆ = 47₁₀
```

---

## 3.9. Relación entre binario y hexadecimal

La relación entre ambos sistemas es especialmente importante.

Un dígito hexadecimal representa exactamente cuatro bits.

```text
0000 = 0
0001 = 1
0010 = 2
0011 = 3
0100 = 4
0101 = 5
0110 = 6
0111 = 7
1000 = 8
1001 = 9
1010 = A
1011 = B
1100 = C
1101 = D
1110 = E
1111 = F
```

Esto permite convertir binario a hexadecimal directamente agrupando los bits de cuatro en cuatro.

---

## 3.10. Ejemplo binario → hexadecimal

Tenemos:

```text
11111111₂
```

Agrupamos de cuatro en cuatro:

```text
1111 1111
```

Cada grupo corresponde a:

```text
1111 = F
1111 = F
```

Por tanto:

```text
11111111₂ = FF₁₆
```

---

## 3.11. Ejemplo hexadecimal → binario

Tenemos:

```text
A7₁₆
```

Convertimos cada dígito:

```text
A = 1010
7 = 0111
```

Por tanto:

```text
A7₁₆ = 10100111₂
```

---

## 3.12. Relación entre decimal, binario y hexadecimal

Podemos representar un mismo valor utilizando los tres sistemas.

Por ejemplo:

```text
Decimal:     255
Binario:     11111111
Hexadecimal: FF
```

Otro ejemplo:

```text
Decimal:     65
Binario:     01000001
Hexadecimal: 41
```

Es importante reconocer que:

```text
65₁₀
```

y:

```text
0x41
```

representan el mismo valor.

---

## 3.13. Prefijos y notación

En programación y herramientas técnicas podemos encontrar diferentes formas de indicar la base.

Por ejemplo:

```text
10
```

normalmente representa decimal.

En muchos lenguajes:

```text
0b1010
```

indica binario.

Y:

```text
0xA
```

indica hexadecimal.

Por tanto:

```text
10₁₀ = 0b1010 = 0xA
```

Los tres representan el mismo valor.

---

## 3.14. ¿Por qué es tan importante el hexadecimal en ciberseguridad?

El hexadecimal permite representar datos binarios de forma mucho más compacta.

Por ejemplo:

```text
11111111 10101010 00001111 11001100
```

puede representarse como:

```text
FF AA 0F CC
```

Esto facilita el trabajo con datos de bajo nivel.

El hexadecimal aparece frecuentemente en:

- direcciones de memoria;
- dumps de memoria;
- bytes;
- código máquina;
- shellcode;
- hashes;
- análisis de archivos;
- firmas de archivos;
- direcciones MAC;
- reverse engineering;
- análisis de malware.

---

## 3.15. Objetivos de aprendizaje

Al finalizar este tema deberías poder:

- explicar qué significa la base de un sistema de numeración;
- identificar las bases 10, 2 y 16;
- convertir binario a decimal;
- convertir decimal a binario;
- convertir hexadecimal a decimal;
- convertir decimal a hexadecimal;
- convertir binario a hexadecimal;
- convertir hexadecimal a binario;
- reconocer la notación `0x`;
- explicar por qué hexadecimal es tan utilizado en informática.

---

## 3.16. Idea fundamental

> **Binario es la representación fundamental de los sistemas digitales; hexadecimal es una forma compacta y práctica de representar esos mismos valores para las personas.**

Dominar estas conversiones será necesario antes de avanzar hacia memoria, código máquina, análisis de archivos, redes y otras áreas de ciberseguridad.
