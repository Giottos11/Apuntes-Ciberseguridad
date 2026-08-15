# Recursos de Ciberseguridad.

## 1. Glosario

1. **Navegación anónima**: cuando realizamos una navegación por Internet utilizando distintos mecanismos para dificultar o impedir que se pueda identificar al usuario, su ubicación o las acciones que realiza. Algunos mecanismos utilizados son VPN, redes como Tor, proxies o sistemas de anonimización.

2. **Hacktivista**: persona o grupo que utiliza técnicas de hacking como forma de protesta o activismo, normalmente con objetivos políticos, sociales o ideológicos.

3. **Script Kiddie**: persona que utiliza herramientas, scripts o exploits desarrollados por otras personas sin disponer necesariamente de conocimientos técnicos suficientes para comprender su funcionamiento o desarrollar sus propias herramientas.

4. **Sniffer**: herramienta de hardware o software que permite capturar y analizar el tráfico que circula por una red. Puede utilizarse para tareas legítimas de administración, diagnóstico y auditoría de redes, así como para analizar comunicaciones.

5. **Hash**: valor de longitud normalmente fija obtenido al aplicar una función hash a unos datos de entrada, como una contraseña, un texto o un fichero. Un buen algoritmo hash hace que sea computacionalmente muy difícil obtener los datos originales a partir del hash. También se utiliza para comprobar la integridad de archivos.

6. **Malware**: término utilizado para referirse a cualquier software diseñado con una finalidad maliciosa, como robar información, dañar sistemas, espiar al usuario, obtener acceso no autorizado o interrumpir servicios.

7. **Ingeniería social**: conjunto de técnicas que buscan manipular o engañar a una persona para conseguir información, acceso a sistemas o que realice una determinada acción. Aprovecha principalmente factores humanos y no vulnerabilidades técnicas.

8. **Intrusión física**: prueba de seguridad en la que se intenta acceder físicamente a instalaciones, equipos o zonas restringidas para comprobar la eficacia de las medidas de seguridad física. Por ejemplo, intentar acceder a una sala técnica o conectar un dispositivo a un equipo.

9. **Defensa en profundidad**: estrategia de seguridad que consiste en utilizar varias capas de protección independientes. Si una capa falla, otras pueden impedir o limitar el ataque. Puede incluir seguridad física, controles de acceso, firewalls, segmentación de red, antivirus, cifrado, monitorización, copias de seguridad, etc.

10. **Defensa en amplitud**: enfoque de seguridad que busca proteger el conjunto de elementos que forman parte de un sistema, teniendo en cuenta diferentes áreas como personas, procesos, aplicaciones, redes, sistemas, datos y dispositivos. Su objetivo es identificar, controlar y reducir los riesgos de seguridad de manera global.

11. **Vulnerabilidad**: debilidad o fallo en un sistema, aplicación, dispositivo, configuración o proceso que puede ser aprovechado para comprometer la confidencialidad, integridad o disponibilidad de un recurso.

12. **Exploit**: código, programa, técnica o conjunto de instrucciones que aprovecha una vulnerabilidad concreta para conseguir un determinado efecto, como ejecutar código, obtener acceso, elevar privilegios o provocar una denegación de servicio.

13. **0-day (zero-day)**: vulnerabilidad desconocida por el fabricante o para la que todavía no existe una corrección disponible. Un **0-day exploit** es un exploit que aprovecha este tipo de vulnerabilidad.

14. **Payload**: conjunto de instrucciones o acción que se ejecuta como consecuencia de la explotación de una vulnerabilidad. El exploit se encarga de aprovechar la vulnerabilidad y el payload define qué se pretende ejecutar o conseguir posteriormente.

15. **Backdoor**: mecanismo que permite acceder a un sistema evitando los mecanismos normales de autenticación o control de acceso. Puede haber sido instalado deliberadamente o creado como consecuencia de un ataque.

16. **Spoofing**: técnica mediante la cual un atacante suplanta la identidad o características de otro dispositivo, usuario, servicio o recurso. Algunos ejemplos son el **IP spoofing**, **ARP spoofing**, **DNS spoofing** o **email spoofing**.

17. **Man-in-the-Middle (MitM)**: ataque en el que un atacante consigue situarse entre dos partes que se están comunicando para interceptar, modificar o analizar la información intercambiada sin que las víctimas sean necesariamente conscientes de ello.

18. **Ataque de fuerza bruta**: técnica que consiste en probar sistemáticamente diferentes combinaciones hasta encontrar una credencial válida o conseguir descifrar un dato protegido. Puede utilizar diccionarios, combinaciones generadas automáticamente o ataques híbridos.

19. **Cracking**: conjunto de técnicas destinadas a romper o superar mecanismos de protección, como contraseñas, hashes o cifrados, con el objetivo de obtener acceso a la información protegida. En el caso de contraseñas almacenadas mediante hash, se pueden utilizar ataques de diccionario, fuerza bruta o tablas precalculadas.

20. **DoS (Denial of Service)**: ataque de denegación de servicio cuyo objetivo es impedir o dificultar que un sistema, aplicación o servicio pueda ser utilizado normalmente por sus usuarios legítimos.

21. **DDoS (Distributed Denial of Service)**: ataque de denegación de servicio distribuido en el que múltiples dispositivos participan simultáneamente en el ataque contra un objetivo. Los dispositivos utilizados pueden formar parte de una botnet.

22. **Phishing**: técnica de ingeniería social que utiliza comunicaciones fraudulentas para intentar engañar a una persona y conseguir información sensible, como contraseñas, datos bancarios o códigos de autenticación. Aunque tradicionalmente se asociaba al correo electrónico, también puede realizarse mediante otros medios.

23. **Vishing**: modalidad de phishing realizada mediante llamadas telefónicas o comunicaciones de voz. El atacante se hace pasar por una persona u organización legítima para obtener información o conseguir que la víctima realice una acción.

24. **Bot**: dispositivo o sistema informático que puede ejecutar automáticamente determinadas acciones siguiendo las instrucciones recibidas de un atacante o de un sistema de control. En ciberseguridad, un dispositivo comprometido puede convertirse en un bot.

25. **Botnet**: conjunto de dispositivos comprometidos que están bajo el control de un atacante y pueden recibir instrucciones de forma centralizada o distribuida. Las botnets pueden utilizarse, entre otras cosas, para realizar ataques DDoS, distribuir malware o enviar spam.

26. **Rootkit**: conjunto de herramientas o software diseñado para mantener un acceso privilegiado a un sistema y, normalmente, ocultar la presencia del atacante, procesos, archivos, conexiones u otras modificaciones realizadas en el sistema.

27. **Ransomware**: tipo de malware diseñado para impedir el acceso a los datos o sistemas de una víctima, normalmente mediante cifrado, con el objetivo de exigir un rescate a cambio de recuperar el acceso. Algunas variantes también amenazan con publicar los datos robados.

28. **CryptoLocker**: familia de ransomware que se hizo especialmente conocida por cifrar archivos de los equipos infectados y exigir un pago para intentar recuperar el acceso a ellos. El término también se utiliza a veces de forma genérica para referirse a ransomware, aunque técnicamente CryptoLocker fue una familia concreta.

29. **Spyware**: tipo de malware diseñado para recopilar información sobre la actividad de un usuario o sistema sin su consentimiento. Puede registrar información como hábitos de navegación, aplicaciones utilizadas, credenciales o datos personales.

30. **Troyano**: malware que se presenta o distribuye aparentando ser un programa, archivo o aplicación legítima. Una vez ejecutado, puede realizar acciones maliciosas como permitir acceso remoto, robar información o descargar otros tipos de malware.

31. **Virus**: tipo de malware que se inserta o se adjunta a otros archivos o programas y que necesita algún tipo de acción o ejecución para propagarse. Puede modificar archivos, propagarse a otros sistemas y realizar diferentes acciones maliciosas.

32. **Gusano (worm)**: malware capaz de propagarse automáticamente entre sistemas, normalmente aprovechando vulnerabilidades o servicios de red, sin necesitar necesariamente que el usuario ejecute manualmente un archivo infectado.

33. **Seguridad integral**: enfoque de seguridad que considera conjuntamente diferentes dimensiones de protección, incluyendo la **seguridad física, digital y humana**. Busca proteger los activos desde una perspectiva global y coordinada.

34. **Test de intrusión de caja negra**: prueba de penetración en la que el auditor dispone de poca o ninguna información previa sobre el sistema objetivo. El objetivo es simular, en la medida de lo posible, las condiciones de un atacante externo.

35. **Test de intrusión de caja negra Post Autenticación**: modalidad de prueba en la que el auditor parte de unas credenciales válidas proporcionadas para la prueba, pero no dispone de información adicional significativa sobre la infraestructura interna. Permite evaluar qué podría conseguir un usuario legítimo una vez autenticado.

36. **Test de intrusión de caja gris**: prueba de penetración en la que el auditor dispone de información parcial sobre el sistema objetivo. Permite realizar una evaluación más profunda que una prueba de caja negra y, al mismo tiempo, simular a un atacante que ya posee cierto conocimiento o acceso.

37. **Test de intrusión de caja blanca**: prueba de penetración en la que el auditor dispone de información amplia o completa sobre el sistema objetivo, como arquitectura, código fuente, credenciales, configuración o documentación. Permite realizar una evaluación exhaustiva de la seguridad.

38. **Protocolo**: conjunto de reglas, normas y convenciones que determinan cómo deben comunicarse dos o más sistemas. Define aspectos como el formato de los mensajes, el orden de comunicación, la identificación de los participantes y cómo se gestionan determinados errores. Ejemplos son HTTP, HTTPS, TCP, UDP, DNS y SSH.

39. **Autenticación**: proceso mediante el cual un sistema verifica la identidad de un usuario, dispositivo o servicio. Puede realizarse mediante contraseñas, certificados, tokens, datos biométricos o múltiples factores.

40. **Autorización**: proceso mediante el cual un sistema determina qué recursos o acciones puede utilizar o realizar una identidad que ya ha sido autenticada.

41. **Control de acceso**: conjunto de mecanismos y políticas utilizados para determinar quién puede acceder a determinados recursos y qué operaciones puede realizar sobre ellos.

42. **Escalada de privilegios**: técnica mediante la cual un usuario o atacante consigue permisos superiores a los que tenía inicialmente. Puede ser **vertical**, cuando se obtienen privilegios mayores, como administrador o root, u **horizontal**, cuando se accede a recursos pertenecientes a otro usuario con privilegios similares.

43. **Enumeración**: proceso de obtener información detallada sobre un sistema, servicio, red o aplicación después de haber realizado una fase inicial de reconocimiento o escaneo.

44. **Reconocimiento**: fase de una auditoría de seguridad o ataque en la que se recopila información sobre el objetivo. Puede incluir dominios, direcciones IP, tecnologías utilizadas, servicios, empleados, infraestructura y otros datos relevantes.

45. **Escaneo de puertos**: técnica utilizada para identificar qué puertos de un dispositivo están abiertos, cerrados o filtrados. Permite conocer qué servicios pueden estar disponibles en un sistema.

46. **Puerto de red**: identificador numérico utilizado por los protocolos de transporte, como TCP y UDP, para diferenciar diferentes servicios o procesos dentro de un dispositivo. Los puertos están numerados del **0 al 65535**.

47. **Firewall**: sistema de seguridad que controla y filtra el tráfico de red basándose en determinadas reglas. Puede permitir, bloquear o registrar comunicaciones dependiendo de factores como dirección IP, puerto, protocolo o aplicación.

48. **VPN (Virtual Private Network)**: tecnología que crea un canal de comunicación protegido entre un dispositivo y una red o servidor remoto. Normalmente utiliza cifrado para proteger el tráfico frente a terceros durante su transporte.

49. **Cifrado**: proceso mediante el cual unos datos legibles, denominados texto plano, se transforman mediante un algoritmo y una clave en información que no puede interpretarse directamente, denominada texto cifrado.

50. **Descifrado**: proceso inverso al cifrado mediante el cual se utiliza la clave correspondiente para recuperar la información original a partir de los datos cifrados.

51. **Cifrado simétrico**: sistema criptográfico en el que se utiliza la misma clave, o claves relacionadas, para cifrar y descifrar la información. Es eficiente para grandes cantidades de datos, pero requiere proteger adecuadamente la clave compartida.

52. **Cifrado asimétrico**: sistema criptográfico que utiliza un par de claves relacionadas: una clave pública y una clave privada. La clave pública puede compartirse, mientras que la privada debe mantenerse protegida.

53. **Clave pública**: clave perteneciente a un sistema de criptografía asimétrica que puede hacerse pública. Dependiendo del algoritmo, puede utilizarse para cifrar información destinada al propietario de la clave privada o para verificar firmas digitales.

54. **Clave privada**: clave secreta de un sistema de criptografía asimétrica que debe mantenerse protegida. Puede utilizarse para descifrar información o generar firmas digitales.

55. **Certificado digital**: documento electrónico que vincula una identidad con una clave pública y que está firmado por una autoridad de certificación o entidad de confianza.

56. **Firma digital**: mecanismo criptográfico que permite comprobar la autenticidad e integridad de un documento o mensaje y vincularlo con el firmante.

57. **Autenticación multifactor (MFA)**: mecanismo de autenticación que requiere dos o más factores diferentes para verificar la identidad de un usuario. Los factores pueden basarse en algo que se sabe, algo que se tiene o algo que se es.

58. **Dirección IP**: identificador lógico utilizado para identificar un dispositivo o interfaz dentro de una red que utiliza el protocolo IP. Puede ser IPv4 o IPv6.

59. **Dirección MAC**: identificador asociado normalmente a una interfaz de red y utilizado en comunicaciones de la capa de enlace. En redes Ethernet tiene habitualmente 48 bits y se representa mediante seis pares hexadecimales.

60. **DNS (Domain Name System)**: sistema que permite traducir nombres de dominio, como `ejemplo.com`, a direcciones IP y realizar otras funciones relacionadas con la resolución de nombres.

61. **HTTP**: protocolo utilizado para la transferencia de información entre clientes y servidores web.

62. **HTTPS**: versión de HTTP que utiliza TLS para proteger la comunicación mediante mecanismos de cifrado, autenticación e integridad.

63. **TLS (Transport Layer Security)**: protocolo criptográfico diseñado para proporcionar comunicaciones seguras a través de redes. Se utiliza, entre otros casos, para proteger conexiones HTTPS.

64. **Dirección IP privada**: dirección IP utilizada dentro de redes privadas y que normalmente no es enrutable directamente a través de Internet. En IPv4 existen rangos privados definidos específicamente para este propósito.

65. **Dirección IP pública**: dirección IP utilizada para identificar una interfaz o dispositivo en Internet y que puede ser enrutable públicamente.

66. **NAT (Network Address Translation)**: mecanismo que permite traducir direcciones IP, normalmente entre direcciones privadas y públicas. Es habitual en routers domésticos para permitir que varios dispositivos de una red privada compartan una dirección IP pública.

67. **Zero Trust**: modelo de seguridad basado en el principio de que ningún usuario, dispositivo o conexión debe considerarse confiable automáticamente. Cada acceso debe verificarse y autorizarse según el contexto y las políticas de seguridad.

68. **CIA (Confidencialidad, Integridad y Disponibilidad)**: modelo fundamental de la seguridad de la información. La **confidencialidad** busca impedir accesos no autorizados, la **integridad** garantiza que la información no sea modificada indebidamente y la **disponibilidad** garantiza que los recursos estén accesibles cuando sean necesarios.

69. **Riesgo**: posibilidad de que una amenaza aproveche una vulnerabilidad y provoque un impacto negativo sobre un activo. Habitualmente se analiza teniendo en cuenta la probabilidad de ocurrencia y el impacto.

70. **Amenaza**: cualquier circunstancia, evento, actor o acción que tenga el potencial de provocar un daño o comprometer la seguridad de un sistema o activo.

71. **Activo**: recurso que tiene valor para una organización o persona y que debe ser protegido. Puede ser información, hardware, software, servicios, instalaciones o incluso personas.

72. **Parche de seguridad**: actualización destinada a corregir vulnerabilidades, errores o problemas de seguridad en un sistema, aplicación o dispositivo.

73. **Pentesting**: abreviatura de *penetration testing*. Es una prueba de seguridad autorizada en la que se intenta identificar y, dentro del alcance acordado, explotar vulnerabilidades para determinar el nivel de seguridad real de un sistema.

74. **Red Team**: equipo que simula las acciones y técnicas de un atacante real con el objetivo de evaluar la capacidad de una organización para prevenir, detectar y responder ante ataques.

75. **Blue Team**: equipo responsable de defender los sistemas y redes de una organización, detectar amenazas, analizar incidentes y aplicar medidas para prevenir o mitigar ataques.

76. **Purple Team**: enfoque que combina las capacidades del Red Team y el Blue Team para mejorar la colaboración entre ataque y defensa y comprobar la eficacia de las medidas de detección y respuesta.

77. **SOC (Security Operations Center)**: centro de operaciones de seguridad encargado de monitorizar sistemas y redes, detectar eventos de seguridad, investigar alertas y responder ante incidentes de seguridad.

78. **SIEM (Security Information and Event Management)**: plataforma que recopila, centraliza y correlaciona registros y eventos procedentes de diferentes sistemas para facilitar la detección, investigación y respuesta ante incidentes de seguridad.

79. **IOC (Indicator of Compromise)**: indicador que puede proporcionar evidencias de que un sistema ha podido verse comprometido, como una dirección IP maliciosa, un hash de archivo sospechoso, un dominio o un comportamiento anómalo.

80. **CVE (Common Vulnerabilities and Exposures)**: sistema utilizado para identificar públicamente vulnerabilidades de seguridad mediante identificadores únicos, normalmente con el formato `CVE-AÑO-NÚMERO`.

81. **CVSS (Common Vulnerability Scoring System)**: sistema utilizado para evaluar y expresar la gravedad de una vulnerabilidad mediante una puntuación basada en diferentes características del problema.

82. **Hardening**: proceso de reforzar la seguridad de un sistema reduciendo su superficie de ataque. Puede incluir deshabilitar servicios innecesarios, eliminar software no utilizado, aplicar actualizaciones, configurar correctamente permisos y establecer políticas de seguridad.

83. **Superficie de ataque**: conjunto de puntos, servicios, aplicaciones, interfaces y recursos que podrían ser utilizados para intentar comprometer un sistema.

84. **Vector de ataque**: método o vía utilizada para intentar aprovechar una vulnerabilidad o conseguir acceso a un sistema. Puede ser, por ejemplo, un correo de phishing, una aplicación vulnerable, una contraseña comprometida o un servicio expuesto a Internet.

85. **Persistencia**: capacidad de un atacante para mantener el acceso a un sistema comprometido incluso después de reinicios, cierres de sesión u otras medidas de recuperación.

86. **Command and Control (C2)**: infraestructura o mecanismo mediante el cual un atacante se comunica con sistemas comprometidos para enviar instrucciones, recibir información o controlar sus acciones.

87. **Exfiltración de datos**: proceso mediante el cual información perteneciente a un sistema u organización es transferida sin autorización hacia un sistema controlado por un atacante.

88. **Privacidad**: capacidad de garantizar que la información personal o sensible sea tratada y utilizada de acuerdo con las autorizaciones, políticas y derechos establecidos.

89. **Auditoría de seguridad**: evaluación sistemática de los controles, configuraciones, procedimientos y medidas de seguridad de un sistema u organización para identificar deficiencias y comprobar el cumplimiento de determinados requisitos.

90. **DNS Spoofing**: técnica mediante la cual un atacante intenta proporcionar una dirección IP falsa al resolver un nombre de dominio, haciendo que la víctima sea redirigida hacia un servidor diferente del legítimo.

91. **ARP Spoofing**: técnica mediante la cual un atacante envía mensajes ARP falsificados para asociar su dirección MAC con la dirección IP de otro dispositivo, pudiendo interceptar o modificar el tráfico de la red local.

92. **MAC Spoofing**: técnica que consiste en modificar o falsificar la dirección MAC que utiliza una interfaz de red para hacerse pasar por otro dispositivo o evitar determinados controles basados en direcciones MAC.

93. **SQL Injection**: vulnerabilidad que permite introducir instrucciones SQL manipuladas en una aplicación para alterar las consultas que realiza contra una base de datos y, potencialmente, acceder, modificar o eliminar información.

94. **Cross-Site Scripting (XSS)**: vulnerabilidad que permite insertar código, normalmente JavaScript, en una aplicación web para que sea ejecutado en el navegador de otros usuarios.

95. **Cross-Site Request Forgery (CSRF)**: ataque que consigue que un usuario autenticado realice una acción no deseada en una aplicación web sin ser consciente de ello.

96. **Remote Code Execution (RCE)**: vulnerabilidad o técnica que permite ejecutar código de forma remota en un sistema objetivo. Puede provocar desde la ejecución de acciones concretas hasta el control completo del sistema.

97. **Elevación de privilegios**: proceso mediante el cual un usuario o atacante consigue permisos superiores a los que tenía inicialmente, pudiendo pasar de un usuario con permisos limitados a un usuario con privilegios de administrador o root.

98. **Registro (Log)**: información generada por un sistema, aplicación, dispositivo o servicio que registra diferentes eventos y actividades, como accesos, errores, conexiones o modificaciones. Los registros son fundamentales para la monitorización y el análisis de incidentes.

99. **Análisis forense digital**: proceso de recopilar, preservar, analizar y documentar evidencias digitales con el objetivo de determinar qué ocurrió durante un incidente de seguridad, cómo se produjo y qué sistemas o datos pudieron verse afectados.

100. **CTF (Capture The Flag)**: competición o ejercicio práctico de ciberseguridad en el que los participantes deben resolver diferentes retos relacionados con áreas como hacking, criptografía, análisis forense, redes, ingeniería inversa o seguridad web para obtener una "flag".

[Volver al inicio](./../README.md)