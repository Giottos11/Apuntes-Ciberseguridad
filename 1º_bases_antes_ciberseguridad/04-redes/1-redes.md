# Redes

Las redes constituyen uno de los pilares fundamentales de la ciberseguridad. Un sistema aislado puede tener vulnerabilidades, pero en cuanto se conecta a una red aparecen nuevas superficies de ataque: otros equipos pueden comunicarse con él, determinados servicios quedan expuestos, las identidades atraviesan diferentes sistemas y la información comienza a circular entre múltiples dispositivos y redes.

Por esta razón, comprender ciberseguridad sin comprender redes resulta prácticamente imposible. Un ataque de autenticación, una conexión a Active Directory, una petición DNS, una sesión HTTPS, una conexión SSH o el acceso a un recurso SMB son, en última instancia, comunicaciones que deben atravesar diferentes capas de una infraestructura de red.

El objetivo de este bloque no es memorizar protocolos y números de puerto de forma aislada. La finalidad es desarrollar un **modelo mental del tráfico de red**, de manera que sea posible explicar qué ocurre cuando una aplicación intenta comunicarse con otra, identificar qué dispositivos y protocolos intervienen y comprender dónde pueden aplicarse controles de seguridad.

## Fundamentos de redes

El modelo **OSI** proporciona una forma conceptual de dividir las funciones de una red en diferentes capas. Aunque las implementaciones reales no siempre encajan perfectamente en esta división, el modelo resulta extremadamente útil para razonar sobre problemas de conectividad y seguridad.

El modelo **TCP/IP** proporciona una visión más cercana a las arquitecturas utilizadas realmente en Internet. Comprender la relación entre ambos modelos permitirá dejar de pensar en los protocolos como elementos independientes y empezar a entenderlos como componentes que trabajan conjuntamente.

En la capa de acceso a la red aparece **Ethernet**, que define buena parte de las comunicaciones dentro de redes locales. En este contexto es necesario comprender las **direcciones MAC**, que identifican interfaces de red dentro del ámbito correspondiente a la capa de enlace. Las direcciones MAC no deben confundirse con las direcciones IP: una identifica una interfaz dentro del contexto de la red local, mientras que la otra participa en el direccionamiento lógico utilizado para comunicar diferentes redes.

Uno de los mecanismos fundamentales de IPv4 es **ARP (Address Resolution Protocol)**. Cuando un dispositivo conoce una dirección IP dentro de su red local pero necesita enviar una trama Ethernet al dispositivo correspondiente, necesita averiguar qué dirección MAC está asociada a esa IP. ARP permite realizar esta asociación.

Comprender ARP resulta especialmente importante desde el punto de vista de seguridad porque permite entender fenómenos como la manipulación de tablas ARP, el comportamiento de los dispositivos dentro de una LAN y determinadas técnicas de interceptación de tráfico.

El siguiente nivel fundamental es **IPv4**. Será necesario comprender direcciones, máscaras de red, prefijos, gateways y redes privadas, así como la diferencia entre una dirección de host y una dirección perteneciente a una red. A partir de aquí aparece uno de los conocimientos esenciales para cualquier profesional de redes: el **subnetting**.

El subnetting permite dividir un espacio de direcciones en diferentes redes y determinar qué hosts pueden comunicarse directamente y qué tráfico debe pasar por un router. No debe aprenderse como una serie de cálculos mecánicos, sino como una herramienta para comprender cómo se estructura realmente una infraestructura.

También debe estudiarse **IPv6**, tanto por sus diferencias respecto a IPv4 como por la importancia que tiene en las redes modernas. IPv6 introduce un espacio de direccionamiento enormemente mayor y modifica algunos mecanismos que en IPv4 funcionan de forma diferente, por lo que no debe tratarse simplemente como "IPv4 con direcciones más largas".

## TCP, UDP e ICMP

Una vez comprendido el direccionamiento IP, es necesario estudiar cómo se transportan realmente los datos entre aplicaciones.

**TCP (Transmission Control Protocol)** proporciona una comunicación orientada a conexión y fiable. Esto implica mecanismos para establecer una conexión, mantener el orden de los datos, detectar pérdidas y controlar el flujo de información. El establecimiento de una conexión TCP mediante el conocido **three-way handshake** es un concepto fundamental porque permite entender qué ocurre antes de que una aplicación pueda comenzar a intercambiar datos.

TCP utiliza **puertos** para identificar servicios y aplicaciones dentro de un host. Sin embargo, el número de puerto por sí mismo no determina qué aplicación existe realmente detrás de él. Un servicio puede utilizar un puerto no estándar y, por tanto, el análisis de redes debe centrarse en el comportamiento real del servicio y no únicamente en una tabla de puertos conocidos.

**UDP (User Datagram Protocol)** proporciona un modelo mucho más sencillo, sin las garantías de entrega y orden de TCP. Esta simplicidad resulta útil para determinados protocolos y aplicaciones que prefieren reducir la sobrecarga o gestionar la fiabilidad en otra capa.

**ICMP (Internet Control Message Protocol)** se utiliza para transportar mensajes relacionados con el funcionamiento de IP, como errores y determinadas operaciones de diagnóstico. Herramientas tan conocidas como `ping` utilizan ICMP para comprobar conectividad, aunque ICMP tiene muchas más funciones que simplemente responder a un ping.

Comprender estos protocolos permitirá interpretar posteriormente capturas de tráfico y distinguir si un problema pertenece al direccionamiento, al transporte o a la propia aplicación.

## DNS

El **DNS (Domain Name System)** proporciona la traducción entre nombres y diferentes tipos de información asociada a ellos, siendo especialmente conocida la resolución de nombres de dominio hacia direcciones IP.

Cuando un usuario introduce un nombre como `google.com`, la aplicación no necesita conocer directamente la dirección IP del servidor. El sistema realiza una consulta DNS para obtener la información necesaria y posteriormente utiliza esa dirección para establecer la comunicación.

El funcionamiento de DNS debe estudiarse como un sistema jerárquico, comprendiendo conceptos como **resolvers, servidores autoritativos, root servers, TLD y registros DNS**. También será necesario conocer los principales tipos de registros, como A, AAAA, CNAME y MX.

DNS tiene una importancia especial en seguridad porque interviene prácticamente antes de cualquier comunicación basada en nombres. Manipular, interceptar o controlar la resolución DNS puede modificar el destino de las comunicaciones o proporcionar información sobre la infraestructura de una organización.

También deben comprenderse conceptos como **caché DNS, TTL, DNSSEC y DNS over HTTPS/TLS**, diferenciando claramente la resolución del nombre de la protección del canal utilizado para realizar la consulta.

## DHCP

El **DHCP (Dynamic Host Configuration Protocol)** permite proporcionar automáticamente a los dispositivos parámetros necesarios para operar dentro de una red, como dirección IP, máscara, gateway y servidores DNS.

Comprender DHCP implica estudiar el proceso mediante el cual un dispositivo que inicialmente no dispone de una configuración IP completa puede solicitar y recibir una configuración de red. Este proceso resulta especialmente interesante porque muestra cómo un equipo obtiene la información necesaria para comenzar a comunicarse.

Desde el punto de vista de seguridad, DHCP también debe analizarse como un servicio que puede convertirse en un punto de confianza dentro de una red. Si un dispositivo recibe una configuración maliciosa o incorrecta, puede terminar utilizando un gateway o servidor DNS controlado por un tercero.

## HTTP, HTTPS y TLS

Los protocolos de aplicación permiten comprender cómo las comunicaciones de red terminan convirtiéndose en operaciones que tienen sentido para el usuario.

**HTTP (Hypertext Transfer Protocol)** es uno de los protocolos fundamentales de Internet y constituye la base de buena parte de la comunicación web. Será necesario comprender peticiones y respuestas, métodos, cabeceras, códigos de estado, cookies, sesiones y otros elementos fundamentales del protocolo.

HTTP por sí solo no proporciona confidencialidad ni autenticidad criptográfica. Cualquier información transmitida puede quedar expuesta a quien tenga capacidad para observar el tráfico.

**HTTPS** combina HTTP con una capa de seguridad proporcionada mediante **TLS**. Esto permite proteger la comunicación frente a observadores y proporcionar mecanismos para autenticar el servidor mediante certificados digitales.

Aquí se conectan directamente los conocimientos adquiridos en el bloque de criptografía con las redes. TLS utiliza criptografía asimétrica, certificados, intercambio de claves y criptografía simétrica para establecer y proteger una comunicación. Por tanto, estudiar HTTPS sin comprender previamente estos conceptos limita considerablemente la comprensión del protocolo.

También será necesario comprender conceptos modernos como **HTTP/2, HTTP/3 y QUIC**, especialmente para entender por qué las aplicaciones web actuales no necesariamente funcionan sobre la combinación clásica de HTTP/1.1 y TCP.

## Routing

Una dirección IP no determina por sí misma cómo llegará un paquete a su destino. Para atravesar diferentes redes es necesario utilizar **routing**.

Los **routers** mantienen información que permite determinar hacia dónde debe enviarse un paquete en función de su dirección de destino. El dispositivo compara esa dirección con sus rutas disponibles y selecciona el siguiente salto correspondiente.

El estudio del routing debe comenzar con rutas estáticas y tablas de enrutamiento antes de introducir protocolos dinámicos. Posteriormente pueden estudiarse conceptos como **OSPF, BGP y routing inter-VLAN**, dependiendo del nivel de especialización que se quiera alcanzar.

Comprender routing es fundamental para interpretar infraestructuras reales. Un paquete puede atravesar múltiples routers antes de llegar al servidor final, y cada salto representa una decisión independiente sobre dónde debe enviarse el tráfico.

## NAT

**NAT (Network Address Translation)** permite modificar determinadas direcciones y puertos mientras el tráfico atraviesa un dispositivo de red. Es especialmente habitual en redes privadas que utilizan direcciones RFC 1918 y necesitan comunicarse con Internet.

El concepto debe estudiarse más allá de la idea simplificada de que "NAT sirve para salir a Internet". Será necesario comprender traducción de direcciones, traducción de puertos, tablas de estado y el comportamiento de las conexiones entrantes y salientes.

También debe evitarse considerar NAT como un mecanismo de seguridad equivalente a un firewall. Aunque determinadas configuraciones de NAT pueden dificultar conexiones entrantes no solicitadas, sus objetivos y propiedades son diferentes de los de un sistema de filtrado de tráfico.

## VLAN

Las **VLAN (Virtual Local Area Networks)** permiten dividir lógicamente una infraestructura de red física en diferentes dominios de broadcast.

Esta separación permite, por ejemplo, mantener diferentes segmentos para usuarios, servidores, administración o dispositivos IoT aunque físicamente compartan infraestructura de switching. Para comprenderlas será necesario estudiar conceptos como **access ports, trunk ports, 802.1Q, tagging e inter-VLAN routing**.

Las VLAN son importantes desde el punto de vista de seguridad porque permiten establecer fronteras de segmentación, pero una VLAN por sí sola no debe considerarse una frontera de seguridad absoluta. La arquitectura completa, los dispositivos de routing y los controles de filtrado determinan realmente qué comunicaciones son posibles entre segmentos.

## Firewalls

Un **firewall** controla el tráfico de red aplicando una política que determina qué comunicaciones están permitidas y cuáles deben bloquearse.

Para comprenderlos será necesario diferenciar entre filtrado basado en direcciones y puertos, inspección con estado (*stateful inspection*) y mecanismos más avanzados que pueden analizar características adicionales del tráfico.

También debe estudiarse la diferencia entre **firewall de red y firewall de host**. Un firewall situado en el perímetro de una red puede controlar el tráfico entre segmentos, mientras que un firewall instalado directamente en un equipo puede aplicar políticas específicas para las comunicaciones de ese sistema.

La seguridad de un firewall depende tanto de su tecnología como de la política configurada. Una infraestructura con un firewall técnicamente avanzado puede seguir estando expuesta si sus reglas permiten demasiado tráfico o están mal diseñadas.

## VPN

Una **VPN (Virtual Private Network)** permite crear una comunicación protegida a través de una infraestructura que no necesariamente es de confianza.

El concepto debe estudiarse distinguiendo diferentes objetivos. Algunas VPN proporcionan acceso remoto a una red corporativa, otras conectan redes completas entre sí y otras protegen comunicaciones entre dispositivos.

Será necesario comprender conceptos como **tunneling, cifrado, autenticación, encapsulación y terminación del túnel**, así como tecnologías representativas como IPsec y WireGuard.

Una VPN no hace que automáticamente todo el tráfico sea seguro. La seguridad depende del protocolo utilizado, la autenticación, la gestión de claves y la configuración del túnel.

## Proxy

Un **proxy** actúa como intermediario entre un cliente y un servidor. En lugar de comunicarse directamente con el destino, el cliente envía la petición al proxy y este realiza la comunicación correspondiente.

Los proxies pueden utilizarse para controlar acceso, registrar actividad, aplicar políticas, realizar filtrado o proporcionar funciones de caché. En determinados entornos también pueden utilizarse para inspeccionar tráfico cifrado mediante mecanismos específicamente configurados para ello.

Será importante distinguir un proxy de un router, NAT o firewall. Aunque puedan coexistir en el mismo dispositivo y algunas funciones se solapen, cada mecanismo responde a un problema diferente.

## Captura y análisis de tráfico

El conocimiento de redes debe terminar trasladándose a la observación directa del tráfico. Herramientas como **Wireshark** permiten capturar paquetes y analizar qué ocurre realmente durante una comunicación.

Una captura de tráfico debe poder interpretarse desde las diferentes capas: Ethernet proporciona información de enlace, ARP permite observar resolución de direcciones, IP muestra origen y destino, TCP permite analizar conexiones y estados, TLS permite observar el establecimiento del canal seguro y HTTP permite analizar las operaciones de aplicación cuando el tráfico es visible.

También será necesario aprender a utilizar herramientas de línea de comandos para diagnosticar conectividad y comportamiento de red. Herramientas como `ping`, `traceroute`, `ip`, `ss`, `dig`, `nslookup` y `curl` permiten observar diferentes partes del proceso sin depender exclusivamente de interfaces gráficas.

El objetivo no es aprender comandos de memoria, sino comprender **qué pregunta responde cada herramienta**. Por ejemplo, `dig` permite investigar DNS, `ss` permite observar sockets y conexiones, mientras que `traceroute` ayuda a estudiar el camino que siguen los paquetes hacia un destino.

## Objetivo práctico

El objetivo práctico de este bloque es poder explicar de principio a fin qué ocurre cuando un usuario escribe:

```text
https://google.com
```

El proceso comienza cuando el navegador necesita resolver el nombre de dominio. El sistema consulta DNS y obtiene una o varias direcciones IP asociadas al servicio. A continuación, el host determina si el destino se encuentra en su propia red o si debe enviar el tráfico a su gateway.

Si el destino está fuera de la red local, el sistema entrega el tráfico al router correspondiente. Para poder construir la trama Ethernet necesaria, puede utilizar ARP para resolver la dirección MAC del siguiente salto. A partir de ahí, el paquete IP atraviesa uno o varios routers hasta alcanzar la infraestructura del servidor.

Una vez establecido el camino, el navegador necesita comunicarse con el servicio correspondiente. Dependiendo del protocolo utilizado, esto puede implicar una conexión TCP o mecanismos basados en QUIC sobre UDP. En el caso clásico de HTTPS sobre TCP, se establece primero la conexión TCP y posteriormente se realiza el handshake de TLS.

Durante el handshake de TLS se negocian parámetros criptográficos, se establece el material de claves y se valida la identidad del servidor mediante certificados. Una vez completado este proceso, los datos de aplicación pueden viajar protegidos mediante cifrado autenticado.

Finalmente aparece **HTTP**, que contiene la petición que el navegador realiza al servidor. El servidor procesa la solicitud, genera una respuesta y esta recorre el camino inverso hasta llegar al cliente, donde el navegador interpreta los datos recibidos y presenta el resultado al usuario.

Conceptualmente:

```text
Aplicación
   ↓
HTTP / HTTPS
   ↓
TLS
   ↓
TCP / QUIC
   ↓
IP
   ↓
Ethernet / Wi-Fi
   ↓
Gateway
   ↓
Routing
   ↓
Internet
   ↓
Servidor
   ↓
Respuesta
```

Lo importante no es memorizar esta secuencia como una receta rígida. En una comunicación real pueden existir DNS, proxies, balanceadores, firewalls, NAT, CDNs, múltiples conexiones y diferentes protocolos intermedios. El objetivo es disponer de un modelo que permita **seguir el tráfico y explicar qué función cumple cada componente**.

## Principio

El principio fundamental de este bloque es que **las redes deben comprenderse como sistemas de comunicación, no como listas de protocolos y puertos**.

Memorizar que DNS utiliza determinados puertos o que HTTPS suele utilizar el 443 tiene una utilidad limitada si no se comprende qué ocurre cuando una aplicación realiza una consulta DNS, cómo se establece una conexión, qué dispositivo decide el siguiente salto, cómo se traduce una dirección, dónde se aplica un firewall o cómo se protege posteriormente el tráfico mediante TLS.

Los puertos deben estudiarse como identificadores utilizados por los protocolos de transporte para asociar tráfico con servicios, pero nunca como una descripción completa de lo que existe detrás de una conexión. Un servicio puede ejecutarse en un puerto no estándar y un puerto conocido puede estar utilizado por una aplicación diferente.

El verdadero objetivo es poder observar una comunicación y responder preguntas como: **¿quién inicia la conexión?, ¿qué dirección tiene cada extremo?, ¿cómo se resuelve el nombre?, ¿qué ruta sigue el tráfico?, ¿qué protocolo de transporte se utiliza?, ¿dónde se aplica NAT?, ¿qué dispositivo filtra la conexión?, ¿cómo se autentica el servidor?, ¿qué parte del tráfico está cifrada y qué información sigue siendo visible?**

Cuando estas preguntas pueden responderse de forma natural, redes deja de ser un bloque independiente y comienza a convertirse en la infraestructura que conecta el resto de conocimientos de ciberseguridad: sistemas operativos, Active Directory, criptografía, aplicaciones web, cloud, análisis de tráfico, pentesting y detección.

La meta final es poder pasar de **"hay una conexión entre dos equipos"** a comprender toda la cadena que hace posible esa conexión y los controles de seguridad que existen en cada punto.
