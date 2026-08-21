# Roadmap de Ciberseguridad — Ruta Red Team

> **Objetivo principal:** construir una base informática sólida y progresar hasta ser capaz de comprender, evaluar y explotar sistemas de forma controlada, documentando los hallazgos profesionalmente.
>
> **Orientación:** Red Team / Pentesting, manteniendo abiertas las vías hacia Web Security, Active Directory Security, Cloud Security, Reverse Engineering, Malware Analysis y otras especializaciones.
>
> **Principio fundamental:** primero comprender cómo funciona la tecnología; después aprender cómo puede fallar; finalmente aprender a utilizar herramientas para identificar y explotar esas debilidades.

---

# 0. Cómo utilizar este roadmap

El roadmap no debe interpretarse como una lista de tecnologías que hay que memorizar.

Cada bloque debe estudiarse siguiendo este ciclo:

1. **Concepto** — entender qué es y para qué sirve.
2. **Funcionamiento** — comprender qué ocurre internamente.
3. **Uso legítimo** — utilizar la tecnología normalmente.
4. **Seguridad** — identificar errores, configuraciones débiles y superficies de ataque.
5. **Práctica** — reproducir escenarios en un laboratorio controlado.
6. **Automatización** — utilizar scripts cuando tenga sentido.
7. **Documentación** — explicar qué se ha hecho y por qué.
8. **Consolidación** — demostrar que se puede resolver un problema nuevo sin seguir un tutorial paso a paso.

### Regla de progreso

No se considera completado un bloque por haber leído sobre él.

Un conocimiento se considera **operativo** cuando puedes:

- explicarlo con tus propias palabras;
- utilizarlo desde la línea de comandos;
- identificar errores o comportamientos anómalos;
- resolver problemas básicos sin copiar una solución;
- reproducirlo en un laboratorio;
- relacionarlo con otros conocimientos del roadmap.

---

# FASE I — FUNDAMENTOS INFORMÁTICOS

## Nivel 1 — Representación de la información

### Contenidos

- Bits y bytes
- Sistema binario
- Sistema hexadecimal
- Conversión entre decimal, binario y hexadecimal
- ASCII
- Unicode
- Representación de números
- Representación de texto
- Endianness
- Tamaños de datos
- Unidades de almacenamiento

### Objetivo

Comprender cómo se representa la información internamente y poder interpretar valores binarios y hexadecimales.

### Debes ser capaz de

- convertir entre decimal, binario y hexadecimal;
- interpretar bytes y palabras;
- reconocer representaciones ASCII/Unicode;
- entender qué significa little-endian y big-endian.

---

# Nivel 2 — Hardware y arquitectura de computadores

### Contenidos

- CPU
- ALU
- Registros
- RAM
- Caché
- SSD/HDD
- Bus
- Entrada/salida
- Firmware
- BIOS/UEFI
- Procesos
- Hilos
- Kernel
- Espacio de usuario
- Espacio de kernel
- Stack
- Heap
- Memoria virtual
- Arquitectura x86/x64
- Arquitectura ARM

### Objetivo

Entender qué ocurre físicamente y a nivel de sistema cuando se ejecuta un programa.

### Debes ser capaz de

- diferenciar proceso e hilo;
- explicar stack y heap;
- explicar usuario frente a kernel;
- entender cómo CPU, memoria y almacenamiento interactúan;
- relacionar estos conceptos con vulnerabilidades posteriores.

---

# Nivel 3 — Sistemas operativos

## Conceptos comunes

- Kernel
- Procesos
- Hilos
- Memoria
- Syscalls
- Sistema de archivos
- Permisos
- Usuarios
- Servicios
- Logs
- IPC
- Variables de entorno
- Gestión de recursos

## Linux

- Estructura del sistema de archivos
- `/etc`
- `/home`
- `/var`
- `/tmp`
- `/proc`
- `/dev`
- `/sys`
- Terminal
- Shell
- Bash
- Usuarios y grupos
- Permisos
- `sudo`
- Procesos
- Señales
- Servicios
- `systemd`
- Logs
- `cron`
- SSH
- Pipes
- Redirecciones
- Variables de entorno
- Gestión de paquetes

## Windows

- Usuarios y grupos
- NTFS
- ACL
- Procesos
- Servicios
- Registro
- DLL
- UAC
- Eventos
- PowerShell
- CMD
- Variables de entorno
- Program Files
- AppData
- System32

### Objetivo

Trabajar con soltura en Linux y Windows y comprender ambos sistemas desde la perspectiva de administración y seguridad.

### Debes ser capaz de

- administrar usuarios y permisos;
- localizar procesos y servicios;
- analizar logs;
- utilizar Bash y PowerShell;
- conectarte mediante SSH;
- investigar qué está ocurriendo en un sistema sin depender de una interfaz gráfica.

---

# FASE II — PROGRAMACIÓN Y AUTOMATIZACIÓN

# Nivel 4 — Python

### Fundamentos

- Variables
- Tipos de datos
- Operadores
- Condicionales
- Bucles
- Funciones
- Scope
- Strings
- Listas
- Tuplas
- Diccionarios
- Sets

### Programación práctica

- Ficheros
- JSON
- CSV
- Excepciones
- Módulos
- Paquetes
- `pip`
- Entornos virtuales
- Argumentos de línea de comandos
- `argparse`
- Regex
- List comprehensions
- Iteradores
- Generadores
- POO
- Testing
- Logging

### Automatización

- Procesamiento de logs
- Automatización de tareas
- Peticiones HTTP
- APIs REST
- Sockets
- Parsing
- Automatización de reconocimiento
- Generación de informes

### Objetivo

Utilizar Python como herramienta de automatización y análisis, no necesariamente convertirse en desarrollador profesional.

### Proyecto de salida

Construir varias herramientas pequeñas, por ejemplo:

- analizador de logs;
- enumerador de hosts;
- parser de resultados;
- cliente HTTP;
- automatizador de tareas;
- herramienta de análisis de texto;
- script que consuma una API.

---

# Nivel 5 — Git y GitHub

### Contenidos

- Repositorios
- Commits
- Branches
- Merge
- Clone
- Push / Pull
- `.gitignore`
- README
- Tags
- Historial
- Resolución de conflictos

### Objetivo

Gestionar correctamente el código y construir un repositorio técnico que documente el aprendizaje.

### Proyecto de salida

Crear un repositorio de laboratorio con:

- scripts;
- documentación;
- notas técnicas;
- write-ups;
- pequeños proyectos;
- metodología reproducible.

---

# Nivel 6 — C y fundamentos de bajo nivel

### Contenidos

- Tipos
- Arrays
- Strings
- Punteros
- Structs
- Memoria
- `malloc`
- `free`
- Stack
- Heap
- Compilación
- Linking
- Binarios
- Syscalls

### Posteriormente

- Registros
- Assembly básico
- Stack frames
- Calling conventions
- ELF
- PE
- Little-endian
- Depuración

### Objetivo

Comprender qué ocurre a bajo nivel cuando un programa manipula memoria.

### Importante

C no necesita dominarse antes de comenzar con Redes, Linux o Pentesting.

Su función principal dentro de esta ruta es proporcionar una base para:

- vulnerabilidades de memoria;
- explotación;
- reverse engineering;
- malware analysis;
- exploit development.

---

# FASE III — REDES

# Nivel 7 — Redes y TCP/IP

### Fundamentos

- Modelo OSI
- TCP/IP
- Ethernet
- MAC
- ARP
- IPv4
- IPv6
- Subnetting
- CIDR

### Protocolos

- TCP
- UDP
- ICMP
- DNS
- DHCP
- HTTP
- HTTPS
- TLS
- SSH
- FTP
- SMB

### Infraestructura

- Routing
- NAT
- VLAN
- Firewall
- Proxy
- VPN
- Switching

### Conceptos avanzados

- Three-way handshake
- Estados TCP
- Puertos
- Sockets
- DNS resolution
- ARP resolution
- Routing tables
- Segmentación
- MTU

### Objetivo

Comprender una comunicación de extremo a extremo.

### Debes ser capaz de responder

> ¿Qué ocurre exactamente desde que escribo una URL hasta que recibo la respuesta del servidor?

Si no puedes explicar ese proceso, todavía falta base de redes.

---

# Nivel 8 — Análisis de tráfico

### Herramientas

- Wireshark
- `tcpdump`
- Netcat

### Contenidos

- Captura de tráfico
- Filtros
- TCP streams
- DNS
- HTTP
- TLS
- ARP
- Anomalías
- Análisis de conexiones

### Proyecto de salida

Analizar una captura de tráfico y reconstruir:

- quién se comunica con quién;
- qué protocolos utiliza;
- qué conexiones se establecen;
- qué información puede observarse;
- qué comportamiento resulta anómalo.

---

# FASE IV — WEB Y APLICACIONES

# Nivel 9 — Web

### Fundamentos

- HTML
- JavaScript básico
- HTTP
- Requests
- Responses
- Headers
- Cookies
- Sessions
- Methods
- Status codes
- URL
- Query parameters
- Forms

### Backend

- REST
- JSON
- APIs
- SQL
- Bases de datos
- Autenticación
- Autorización

### Identidad

- Sessions
- Tokens
- OAuth2
- JWT
- Cookies
- CORS
- CSRF

### Conceptos de seguridad

- Input validation
- Injection
- XSS
- SQL Injection
- Broken Access Control
- Authentication flaws
- Session flaws
- File upload
- SSRF
- Path traversal
- Command injection

### Objetivo

Comprender cómo funciona una aplicación web antes de intentar atacarla.

---

# Nivel 10 — Web Security y Burp Suite

### Burp Suite

- Proxy
- Repeater
- Intruder
- Decoder
- Comparer
- HTTP history
- Scope

### Metodología

1. Identificación de superficie
2. Enumeración
3. Análisis de requests
4. Identificación de entradas
5. Manipulación
6. Validación de hipótesis
7. Explotación controlada
8. Evidencia
9. Reporting

### Proyecto de salida

Realizar una evaluación completa de una aplicación vulnerable de laboratorio y producir un informe profesional.

---

# FASE V — IDENTIDAD Y ENTORNOS EMPRESARIALES

# Nivel 11 — Active Directory

### Fundamentos

- Domain Controller
- Dominios
- Forests
- Trees
- Usuarios
- Grupos
- OU
- GPO
- LDAP
- DNS

### Autenticación

- Kerberos
- NTLM
- Tickets
- SPN
- Delegación

### Servicios

- SMB
- RPC
- LDAP
- DNS

### Seguridad

- ACL
- Privilegios
- Delegación
- Trusts
- Service Accounts
- Misconfigurations

### Herramientas

- BloodHound
- Impacket
- PowerView
- CrackMapExec / NetExec

### Objetivo

Comprender cómo se organiza y autentica una infraestructura Windows empresarial y cómo puede producirse un compromiso progresivo.

---

# Nivel 12 — Pentesting de infraestructura

### Metodología

1. Scope
2. Reconocimiento
3. Enumeración
4. Scanning
5. Identificación de servicios
6. Análisis de vulnerabilidades
7. Explotación
8. Post-explotación
9. Escalada de privilegios
10. Movimiento lateral
11. Obtención de objetivos
12. Limpieza
13. Reporting

### Herramientas principales

- Nmap
- Netcat
- Gobuster
- ffuf
- Metasploit
- Impacket
- BloodHound
- Hashcat
- John the Ripper

### Principio

> **La herramienta no sustituye al razonamiento.**

El objetivo no es aprender comandos de memoria, sino comprender qué pregunta responde cada herramienta.

---

# FASE VI — FUNDAMENTOS DE SEGURIDAD

# Nivel 13 — Fundamentos de ciberseguridad

### Conceptos

- Confidencialidad
- Integridad
- Disponibilidad
- Autenticación
- Autorización
- Accounting
- Non-repudiation
- Defensa en profundidad
- Zero Trust
- Least privilege

### Gestión del riesgo

- Activo
- Amenaza
- Vulnerabilidad
- Riesgo
- Impacto
- Probabilidad
- Control
- Mitigación

### Vulnerabilidades

- CVE
- CVSS
- CWE
- Exploit
- Payload
- PoC
- Superficie de ataque
- Vector de ataque

### Marcos

- NIST
- MITRE ATT&CK
- OWASP

### Objetivo

Utilizar lenguaje y modelos profesionales de ciberseguridad.

---

# FASE VII — OPERACIÓN RED TEAM

# Nivel 14 — Reconocimiento y OSINT

### Contenidos

- Reconocimiento pasivo
- Reconocimiento activo
- OSINT
- DNS enumeration
- Subdomains
- WHOIS
- Certificate transparency
- Metadata
- Technology fingerprinting
- Asset discovery

### Herramientas

- Nmap
- DNS utilities
- Search engines
- Recon frameworks

### Objetivo

Construir una imagen de la superficie de ataque antes de interactuar con ella.

---

# Nivel 15 — Explotación y post-explotación

### Explotación

- Identificación de vulnerabilidades
- Exploit selection
- Payloads
- Shells
- Reverse shells
- Bind shells

### Post-explotación

- Enumeración local
- Credenciales
- Tokens
- Procesos
- Servicios
- Configuración
- Privilegios
- Persistencia

### Escalada de privilegios

#### Linux

- SUID/SGID
- sudo
- Capabilities
- Cron
- Servicios
- PATH
- Kernel vulnerabilities

#### Windows

- Services
- Scheduled Tasks
- Registry
- Token privileges
- DLL hijacking
- Weak permissions
- Unquoted service paths

---

# Nivel 16 — Movimiento lateral y Active Directory Security

### Contenidos

- Credential reuse
- Pass-the-Hash
- Pass-the-Ticket
- Kerberoasting
- AS-REP Roasting
- SMB
- WinRM
- Remote services
- Delegation abuse
- ACL abuse

### Objetivo

Comprender cómo un atacante puede pasar de un sistema comprometido a otros sistemas dentro de una infraestructura.

---

# Nivel 17 — Reporting profesional

### Contenidos

- Executive Summary
- Scope
- Methodology
- Findings
- Evidence
- Impact
- Risk
- Reproduction
- Remediation
- Technical appendix

### Cada vulnerabilidad debe responder

1. ¿Qué ocurre?
2. ¿Por qué ocurre?
3. ¿Cómo se reproduce?
4. ¿Qué impacto tiene?
5. ¿Qué evidencia lo demuestra?
6. ¿Cómo se corrige?

### Objetivo

Convertir conocimiento técnico en un resultado profesional que otra persona pueda entender y utilizar.

---

# FASE VIII — ESPECIALIZACIÓN TÉCNICA

Estas áreas no deben adelantarse al núcleo de Red Team.

## Nivel 18 — Reverse Engineering

- Assembly
- Debuggers
- Ghidra
- ELF
- PE
- Imports/exports
- Calling conventions
- Static analysis
- Dynamic analysis
- Control flow
- Strings
- Functions

---

## Nivel 19 — Exploit Development

- Memory corruption
- Buffer overflow
- Stack overflow
- Heap
- NX
- ASLR
- PIE
- Canary
- ROP
- Shellcode
- Exploit chains

---

## Nivel 20 — Malware Analysis

- Static analysis
- Dynamic analysis
- Sandboxing
- Indicators
- Persistence
- C2
- Obfuscation
- Packing
- Behavioral analysis

---

## Nivel 21 — Cloud Security

### AWS

- IAM
- EC2
- S3
- VPC
- Security Groups
- Roles
- Policies

### Azure

- Entra ID
- IAM
- App registrations
- Managed identities
- Azure resources
- Conditional Access

### Objetivo

Comprender cómo cambia la superficie de ataque cuando la infraestructura pasa de servidores tradicionales a cloud.

---

## Nivel 22 — Docker y Kubernetes

### Docker

- Images
- Containers
- Registries
- Volumes
- Networks
- Dockerfile

### Kubernetes

- Pods
- Services
- Deployments
- Secrets
- RBAC
- Network policies

### Prioridad

Conocimiento complementario para Red Team y Cloud Security.

---

# FASE IX — OTRAS ESPECIALIZACIONES

Una vez consolidado el núcleo, se puede elegir una especialización principal:

### Red Team / Pentesting
Ruta principal.

### Web Security
Especialización en aplicaciones y APIs.

### Active Directory Security
Especialización en entornos corporativos Windows.

### Cloud Security
AWS, Azure, IAM y entornos híbridos.

### Reverse Engineering
Análisis profundo de binarios.

### Malware Analysis
Análisis de software malicioso.

### Exploit Development
Desarrollo de exploits y explotación avanzada.

### Blue Team / SOC
Detección, monitorización y respuesta.

### Purple Team
Integración entre ataque y defensa.

### Security Engineering
Diseño y construcción de controles de seguridad.

### Mobile Security
Android e iOS.

### AI Security
Seguridad de sistemas y aplicaciones basados en IA.

### IoT / Hardware Security
Dispositivos, firmware y hardware.

### OT / ICS Security
Entornos industriales y sistemas de control.

---

# FASE X — LABORATORIO Y PORTFOLIO

El laboratorio debe evolucionar junto al conocimiento.

## Etapa inicial

- Linux virtualizado
- Windows virtualizado
- Git
- Python
- Bash
- PowerShell

## Etapa de redes

- Varias máquinas virtuales
- Red aislada
- Wireshark
- Nmap
- Servicios vulnerables

## Etapa Web

- Aplicaciones vulnerables
- Burp Suite
- Bases de datos
- APIs

## Etapa Active Directory

- Domain Controller
- Windows clients
- Usuarios
- Grupos
- GPO
- Máquinas Linux integradas

## Etapa avanzada

- Red Team lab
- Segmentación
- Logging
- SIEM
- EDR
- Máquinas vulnerables
- Escenarios de ataque completos

---

# PROYECTOS DE CONTROL

El progreso debe demostrarse mediante proyectos, no solamente mediante teoría.

## Proyecto 1 — Automatización Python

Crear una herramienta útil para analizar o automatizar una tarea técnica.

## Proyecto 2 — Linux

Administrar una máquina Linux únicamente mediante terminal y documentar el proceso.

## Proyecto 3 — Redes

Analizar una captura y explicar el tráfico observado.

## Proyecto 4 — Reconocimiento

Realizar reconocimiento y enumeración de un laboratorio.

## Proyecto 5 — Web

Evaluar una aplicación vulnerable mediante Burp Suite.

## Proyecto 6 — Active Directory

Comprometer un laboratorio AD desde el reconocimiento hasta el objetivo final.

## Proyecto 7 — Pentest completo

Realizar un pentest controlado:

> Reconocimiento → Enumeración → Explotación → Post-explotación → Escalada → Movimiento lateral → Reporting

## Proyecto 8 — Portfolio

Publicar documentación técnica, scripts, write-ups y proyectos en GitHub.

---

# CRITERIO GENERAL DE DOMINIO

No avanzar únicamente porque se haya terminado el temario.

Para cada bloque:

- **0 — Desconocido:** no conozco el concepto.
- **1 — Reconocimiento:** sé qué es.
- **2 — Comprensión:** puedo explicarlo.
- **3 — Operativo:** puedo utilizarlo.
- **4 — Análisis:** puedo investigar problemas con él.
- **5 — Seguridad:** puedo identificar y explotar debilidades en laboratorio.

El objetivo del núcleo de Red Team es alcanzar al menos:

- Fundamentos → **3**
- Linux → **4**
- Redes → **4**
- Windows → **4**
- Python → **3–4**
- Web → **4**
- Active Directory → **4**
- Pentesting → **4**
- Herramientas → **3–4**

La especialización avanzada puede comenzar cuando el núcleo sea suficientemente sólido.