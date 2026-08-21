# Matriz de prioridad tecnológica — Ruta Red Team

Las puntuaciones representan la **utilidad aproximada dentro de una ruta orientada a Red Team/Pentesting**.

No representan:

- dificultad;
- prestigio;
- importancia absoluta dentro de informática;
- necesidad de dominar completamente la tecnología.

Una tecnología con **10/10** merece prioridad y práctica recurrente. Una de **4/10** puede ser útil, pero no debe consumir tiempo que corresponda al núcleo de la ruta.

---

# 1. Prioridad crítica — 10/10

| Conocimiento | Prioridad | Motivo |
|---|---:|---|
| Linux | 10/10 | Plataforma fundamental para pentesting y administración |
| Redes / TCP-IP | 10/10 | Base para comprender prácticamente cualquier ataque de infraestructura |
| Windows | 10/10 | Principal plataforma empresarial |
| Sistemas operativos | 10/10 | Base para comprender procesos, memoria, permisos y privilegios |

---

# 2. Prioridad muy alta — 9/10

| Conocimiento | Prioridad | Motivo |
|---|---:|---|
| Python | 9/10 | Automatización, tooling, parsing y APIs |
| Active Directory | 9/10 | Fundamental en pentesting corporativo |
| HTTP/HTTPS | 9/10 | Base de Web Security y APIs |
| Bash | 9/10 | Automatización y operación Linux |
| PowerShell | 9/10 | Administración y operaciones sobre Windows |
| DNS | 9/10 | Fundamental para redes, Web, AD y reconocimiento |
| SQL / bases de datos | 9/10 | Fundamental para Web Security |

---

# 3. Prioridad alta — 8/10

| Conocimiento | Prioridad |
|---|---:|
| Metodología de Pentesting | 8/10 |
| APIs REST / JSON | 8/10 |
| Nmap | 8/10 |
| Burp Suite | 8/10 |
| BloodHound | 8/10 |
| SSH | 8/10 |
| OSINT | 8/10 |
| Azure / Entra ID | 8/10 |
| Impacket | 8/10 |
| Netcat | 8/10 |
| Gobuster / ffuf | 8/10 |

---

# 4. Prioridad media-alta — 7/10

| Conocimiento | Prioridad |
|---|---:|
| C | 7/10 |
| Git / GitHub | 7/10 |
| Regex | 7/10 |
| POO | 7/10 |
| JavaScript | 7/10 |
| OAuth2 | 7/10 |
| JWT | 7/10 |
| Wireshark | 7/10 |
| AWS | 7/10 |
| Cloud | 7/10 |
| Reverse Engineering | 7/10 |
| Hashcat | 7/10 |
| John the Ripper | 7/10 |

---

# 5. Prioridad media — 6/10

| Conocimiento | Prioridad |
|---|---:|
| Criptografía | 6/10 |
| Docker | 6/10 |
| Entornos virtuales / pip | 6/10 |
| Testing | 6/10 |
| HTML | 6/10 |
| Virtualización | 6/10 |
| Wi-Fi | 6/10 |
| Malware Analysis | 6/10 |
| Exploit Development | 6/10 |
| NIST / frameworks | 6/10 |
| Metasploit | 6/10 |

> Que una herramienta tenga una prioridad inferior no significa que sea poco útil. Significa que aprender a utilizarla no debe adelantarse al conocimiento conceptual que permite comprenderla.

---

# 6. Prioridad secundaria — 5/10

| Conocimiento | Prioridad |
|---|---:|
| Kubernetes | 5/10 |
| CI/CD | 5/10 |
| OT/ICS | 5/10 |
| Ensamblador | 5/10 |
| WebSockets | 5/10 |
| PE / ELF avanzado | 5/10 |

Estas tecnologías adquieren mucha más importancia cuando se elige una especialización concreta.

---

# 7. Prioridad baja dentro de la ruta Red Team — 4/10

| Conocimiento | Prioridad |
|---|---:|
| YAML | 4/10 |
| Android | 4/10 |
| IoT | 4/10 |

Son conocimientos útiles, pero no justifican retrasar Linux, Redes, Windows, Web o Active Directory.

---

# 8. Prioridad baja — 3/10

| Conocimiento | Prioridad |
|---|---:|
| CSS | 3/10 |
| iOS/macOS | 3/10 |

Deben estudiarse principalmente si posteriormente se elige una especialización que los requiera.

---

# 9. Orden recomendado de aprendizaje

La prioridad no debe interpretarse como una simple clasificación. El orden importa.

## Bloque A — Base

1. Sistemas operativos
2. Linux
3. Redes
4. Windows
5. Python

## Bloque B — Herramientas de trabajo

6. Bash
7. PowerShell
8. Git/GitHub
9. SSH
10. Regex

## Bloque C — Web

11. HTTP/HTTPS
12. HTML
13. JavaScript básico
14. SQL
15. APIs REST
16. JSON
17. Autenticación
18. OAuth2
19. JWT
20. Burp Suite

## Bloque D — Infraestructura empresarial

21. Active Directory
22. DNS
23. Kerberos
24. LDAP
25. SMB
26. PowerShell
27. BloodHound
28. Impacket

## Bloque E — Pentesting

29. Reconocimiento
30. Enumeración
31. Nmap
32. Vulnerability analysis
33. Explotación
34. Post-explotación
35. Escalada de privilegios
36. Movimiento lateral
37. Reporting

## Bloque F — Bajo nivel

38. C
39. Memoria
40. Assembly
41. Reverse Engineering
42. Exploit Development

## Bloque G — Cloud

43. Cloud fundamentals
44. IAM
45. AWS
46. Azure
47. Entra ID
48. Docker
49. Kubernetes

## Bloque H — Especialización

50. Elegir una especialización principal.

---

# 10. Distribución aproximada del esfuerzo

Para una ruta principalmente Red Team:

| Área | Peso recomendado |
|---|---:|
| Linux / Sistemas | 15% |
| Redes | 15% |
| Windows / Active Directory | 20% |
| Python / Automatización | 10% |
| Web / APIs | 15% |
| Pentesting / Metodología | 15% |
| Bajo nivel | 5% |
| Cloud | 5% |

Estos porcentajes no representan horas exactas. Sirven para evitar dedicar demasiado tiempo a tecnologías secundarias mientras todavía existen carencias en el núcleo.

---

# 11. Núcleo que nunca debería saltarse

Si hubiera que reducir todo el roadmap a los conocimientos que forman el verdadero **Core Red Team**, serían:

1. Linux
2. Redes TCP/IP
3. Windows
4. Sistemas operativos
5. Python
6. Bash
7. PowerShell
8. DNS
9. HTTP/HTTPS
10. SQL
11. Active Directory
12. Autenticación
13. Enumeración
14. Metodología de Pentesting
15. Nmap
16. Burp Suite
17. BloodHound
18. Impacket
19. Escalada de privilegios
20. Movimiento lateral
21. Reporting

Este núcleo debe estar consolidado antes de invertir cantidades importantes de tiempo en especializaciones avanzadas.

---

# 12. Regla para decidir si estudiar una tecnología

Antes de añadir una nueva tecnología al plan, responder:

### 1. ¿Es necesaria para comprender otra materia?

Si sí → alta prioridad.

### 2. ¿Aparece frecuentemente durante pentesting?

Si sí → alta prioridad.

### 3. ¿Es específica de una especialización?

Si sí → posponer hasta elegir especialización.

### 4. ¿Es principalmente una herramienta?

Aprender primero el concepto que la herramienta automatiza.

### 5. ¿Puedo practicarla en laboratorio?

Si no, buscar primero una aplicación práctica controlada.

---

# 13. Regla principal del roadmap

> **No perseguir herramientas. Perseguir comprensión.**

Por ejemplo:

**Nmap** no debe estudiarse como una colección de comandos.

Primero:

> Redes → TCP/IP → puertos → servicios → enumeración

Después:

> Nmap → automatización de esas tareas.

El mismo principio se aplica a:

- Burp Suite → HTTP/Web;
- BloodHound → Active Directory;
- Wireshark → Redes;
- Impacket → protocolos y autenticación Windows;
- Metasploit → explotación;
- Ghidra → binarios y Assembly;
- Hashcat → hashes y autenticación.

---

# 14. Criterio de madurez

Una persona está progresando correctamente cuando deja de pensar:

> "¿Qué herramienta utilizo?"

y empieza a pensar:

> "¿Qué información necesito obtener para formular la siguiente hipótesis?"

Ese cambio marca la transición entre **aprender herramientas** y **aprender seguridad ofensiva**.