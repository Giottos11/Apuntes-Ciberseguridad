# Linux y terminal

Linux constituye una de las plataformas fundamentales dentro de la informática y la ciberseguridad. Servidores web, sistemas de infraestructura, dispositivos de red, contenedores, sistemas cloud y numerosas herramientas de seguridad funcionan sobre Linux. Por este motivo, saber utilizar Linux no debe reducirse a conocer una serie de comandos: es necesario comprender cómo está organizado el sistema y cómo interactúan el usuario, la shell, los procesos, los archivos y el kernel.

La terminal proporciona una interfaz directa para trabajar con estos componentes. A través de ella es posible consultar información, modificar archivos, gestionar procesos, administrar servicios, analizar registros y automatizar tareas. Cuanto mayor sea la comprensión del sistema que existe detrás de cada comando, menos dependiente será el trabajo de herramientas gráficas o de procedimientos memorizados.

El objetivo de este bloque es adquirir suficiente fluidez para poder desenvolverse en un sistema Linux desde la terminal y utilizarla como una herramienta de administración, diagnóstico y análisis.

## El sistema de archivos

Antes de estudiar comandos concretos es necesario comprender cómo organiza Linux la información. En Linux prácticamente todo se presenta mediante una estructura jerárquica que parte del directorio raíz, representado por `/`.

Dentro de esta jerarquía existen directorios con funciones específicas. `/home` contiene normalmente los directorios personales de los usuarios, `/etc` almacena gran parte de la configuración del sistema, `/var` contiene información que cambia durante la ejecución, `/tmp` se utiliza para archivos temporales y `/usr` contiene una gran parte de los programas y recursos instalados.

Esta organización permite entender que ejecutar un comando como `ls` no significa simplemente "ver archivos". El comando está consultando una estructura concreta del sistema de archivos y mostrando información que el kernel proporciona sobre las entradas existentes en un directorio.

Los comandos `ls`, `cd` y `pwd` permiten comenzar a interactuar con esta estructura. `pwd` muestra el directorio de trabajo actual, `cd` modifica ese directorio y `ls` permite consultar su contenido. A partir de aquí aparecen operaciones como `cp`, `mv` y `rm`, que permiten copiar, mover, renombrar y eliminar archivos.

La manipulación de archivos debe estudiarse junto con conceptos como **rutas absolutas y relativas, enlaces simbólicos, enlaces físicos, inodos y sistemas de archivos**. Esto permite comprender qué representa realmente un archivo en Linux y por qué dos nombres diferentes pueden apuntar al mismo objeto.

Comandos como `cat` y `less` permiten consultar contenido, mientras que `grep` permite buscar patrones dentro de texto. `find` permite realizar búsquedas sobre el sistema de archivos utilizando criterios como nombre, tipo, tamaño, propietario o permisos.

La finalidad no es memorizar decenas de opciones. Lo importante es aprender a combinar herramientas para responder preguntas concretas. Una búsqueda real puede requerir localizar un archivo, filtrar determinados resultados y posteriormente examinar su contenido. La terminal destaca precisamente por permitir construir estas operaciones de forma incremental.

## Usuarios, grupos y permisos

Linux utiliza un modelo de identidad basado principalmente en **usuarios y grupos**. Cada proceso se ejecuta asociado a una identidad y las operaciones que puede realizar están condicionadas por el contexto de seguridad correspondiente.

Los usuarios poseen identificadores numéricos conocidos como **UID**, mientras que los grupos utilizan **GID**. Aunque normalmente trabajamos con nombres como `jose` o `administradores`, el kernel trabaja fundamentalmente con estos identificadores.

Los grupos permiten asociar usuarios con determinados permisos y capacidades. Un usuario puede pertenecer a varios grupos y esta pertenencia puede modificar los recursos a los que tiene acceso.

El modelo tradicional de permisos de Linux se basa en tres categorías: **usuario propietario, grupo propietario y otros usuarios**. Para cada categoría pueden existir permisos de lectura, escritura y ejecución.

Comprender estos permisos implica mucho más que reconocer las letras `r`, `w` y `x`. Hay que entender qué significa leer un archivo frente a leer un directorio, qué implica escribir sobre un directorio y por qué el permiso de ejecución sobre un directorio permite atravesarlo.

También deben estudiarse los **permisos especiales**, como SUID, SGID y sticky bit. Estos mecanismos modifican el comportamiento convencional de los permisos y son especialmente relevantes desde el punto de vista de seguridad.

El usuario **root** representa tradicionalmente la identidad con máximas capacidades dentro del sistema, aunque los sistemas Linux modernos utilizan mecanismos adicionales para dividir y limitar privilegios. Esta evolución conduce directamente al estudio posterior de capabilities.

## Procesos

Un programa almacenado en disco no es lo mismo que un **proceso**. Un programa es código y datos almacenados, mientras que un proceso representa una instancia de ese programa en ejecución.

Cada proceso posee un identificador denominado **PID** y mantiene un contexto de ejecución que incluye memoria, archivos abiertos, variables de entorno, credenciales y otros recursos.

Comprender los procesos permite responder preguntas fundamentales durante la administración de un sistema: qué está ejecutándose, quién lo ha iniciado, con qué usuario funciona, qué recursos utiliza y qué relación tiene con otros procesos.

Herramientas como `ps`, `top` y `htop` permiten observar procesos, mientras que mecanismos como `kill` permiten enviar **señales** a los procesos. Las señales constituyen un mecanismo fundamental de comunicación entre procesos y permiten solicitar acciones como terminación, suspensión o continuación.

También es importante comprender las relaciones entre procesos. Los procesos pueden crear procesos hijos, formando una jerarquía que puede observarse mediante herramientas como `pstree`. Esta estructura resulta especialmente útil cuando se analiza cómo una aplicación inicia otros programas o servicios.

La administración de procesos debe relacionarse con el modelo de memoria estudiado en el bloque de bajo nivel. Un proceso dispone de diferentes regiones de memoria y un contexto propio proporcionado por el kernel. Esta relación permitirá posteriormente comprender `/proc`, debugging y análisis de comportamiento.

## Servicios y systemd

Los **servicios** son procesos o grupos de procesos diseñados para proporcionar funcionalidades persistentes al sistema. Un servidor web, un servicio SSH o un componente de registro pueden ejecutarse como servicios gestionados por el sistema operativo.

En la mayoría de distribuciones modernas, **systemd** actúa como sistema de inicialización y gestor de servicios. Es responsable de iniciar determinados componentes durante el arranque, gestionar sus estados y controlar sus dependencias.

Comprender `systemd` implica estudiar unidades, servicios, estados, dependencias y archivos de configuración. Comandos como `systemctl` permiten consultar y modificar el estado de los servicios, mientras que `journalctl` permite consultar los registros gestionados por el sistema.

Desde el punto de vista de seguridad es especialmente importante conocer con qué usuario se ejecuta un servicio, qué archivos puede modificar, qué capabilities posee y qué recursos tiene disponibles. Un servicio aparentemente normal puede representar un riesgo significativo si funciona con privilegios excesivos o si su configuración permite que una identidad con pocos privilegios controle componentes ejecutados con privilegios superiores.

## Logs y observabilidad

Linux genera una cantidad considerable de información sobre lo que ocurre en el sistema. Los **logs** permiten registrar eventos relacionados con aplicaciones, servicios, autenticación, kernel y diferentes componentes de la infraestructura.

Comprender los logs implica saber dónde se almacenan, cómo se generan y cómo pueden consultarse y filtrarse. Dependiendo de la distribución y de la configuración, parte de esta información puede encontrarse en archivos tradicionales dentro de `/var/log`, mientras que `systemd` puede gestionar eventos mediante el journal.

La capacidad de analizar logs es fundamental tanto para administración como para seguridad. Permite investigar errores, reconstruir acontecimientos y detectar comportamientos anómalos.

La terminal proporciona herramientas especialmente adecuadas para este trabajo. `grep`, `less`, `tail`, `head`, `sort`, `uniq`, `awk` y `sed` permiten transformar grandes cantidades de texto en información útil.

El objetivo no es dominar inicialmente todas estas herramientas, sino aprender a encadenarlas para responder preguntas concretas. Por ejemplo, localizar determinados eventos, filtrar únicamente aquellos relacionados con un usuario y posteriormente ordenarlos cronológicamente.

## Variables de entorno y PATH

Las **variables de entorno** contienen información que los procesos pueden utilizar durante su ejecución. Entre ellas se encuentra `PATH`, que determina los directorios en los que la shell busca ejecutables cuando el usuario introduce un comando.

Comprender `PATH` permite entender por qué un comando puede ejecutarse escribiendo únicamente su nombre y qué ocurre cuando existen diferentes ejecutables con nombres iguales en diferentes directorios.

También deben estudiarse variables como `HOME`, `USER`, `SHELL` y otras proporcionadas por el entorno de ejecución. Los procesos heredan normalmente el entorno de su proceso padre, lo que permite comprender cómo una configuración establecida en una shell puede terminar afectando a los programas que se ejecutan desde ella.

Este concepto es especialmente importante desde el punto de vista de seguridad porque determinadas configuraciones del entorno pueden alterar el comportamiento de aplicaciones y scripts.

## Bash y la shell

**Bash** es una de las shells más utilizadas en Linux. Una shell no es simplemente una ventana donde se escriben comandos: es un intérprete que permite ejecutar programas y construir operaciones más complejas combinándolos.

Uno de los conceptos fundamentales es la separación entre **stdin, stdout y stderr**. Estos tres flujos permiten que un proceso reciba entrada, produzca salida normal y produzca mensajes de error de forma independiente.

Las **redirecciones** permiten modificar el destino de estos flujos. Es posible enviar la salida de un comando a un archivo, utilizar un archivo como entrada o separar la salida normal de los mensajes de error.

Los **pipes (`|`)** permiten conectar la salida de un proceso con la entrada de otro. Esta característica constituye una de las ideas fundamentales de Unix: construir herramientas pequeñas y especializadas y combinarlas para realizar operaciones más complejas.

Por ejemplo, una herramienta puede generar una gran cantidad de información y otra puede filtrarla. Una tercera puede ordenar el resultado y una cuarta contar las coincidencias. En lugar de depender de una herramienta gigantesca que haga todo, la shell permite construir una pequeña cadena de procesamiento.

Esta filosofía es especialmente útil en administración y análisis de seguridad porque permite trabajar rápidamente con grandes cantidades de información.

## Scripting

Una vez dominados los comandos básicos, la shell puede utilizarse para crear **scripts** que automaticen tareas.

Un script Bash permite combinar comandos, variables, condiciones, bucles, funciones y códigos de retorno. Esto permite transformar una secuencia de acciones manuales en un procedimiento reproducible.

El estudio del scripting debe incluir también el manejo correcto de errores. Los programas devuelven códigos de salida que permiten determinar si una operación ha tenido éxito. Comprender estos códigos permite construir scripts que no continúen ejecutando acciones cuando una operación anterior ha fallado.

También deben estudiarse aspectos como quoting, expansión de variables, sustitución de comandos y manejo de argumentos. Estos conceptos son especialmente importantes porque una shell interpreta determinados caracteres de forma especial y una construcción incorrecta puede producir resultados diferentes de los esperados.

Desde el punto de vista de seguridad, el scripting también obliga a comprender problemas como **inyección de comandos, validación de entradas y gestión de permisos**. Automatizar una operación incorrecta puede convertir un pequeño error en un problema a escala mucho mayor.

## Cron y tareas programadas

Linux proporciona diferentes mecanismos para ejecutar tareas automáticamente. Uno de los más conocidos es **cron**, utilizado para programar acciones periódicas.

Comprender cron implica saber cómo se define una tarea, con qué usuario se ejecuta y qué entorno recibe. Esta última cuestión es importante porque una tarea ejecutada automáticamente puede disponer de un entorno diferente al de una shell interactiva.

Las tareas programadas son relevantes tanto para administración como para seguridad. Scripts de mantenimiento, copias de seguridad, rotación de logs y procesos de limpieza pueden depender de ellas. Una configuración incorrecta puede provocar fallos operativos o proporcionar capacidades innecesarias a usuarios con pocos privilegios.

## SSH

**SSH (Secure Shell)** proporciona acceso remoto seguro a sistemas y permite ejecutar comandos, transferir archivos y crear túneles de comunicación.

El estudio de SSH debe cubrir autenticación mediante contraseña y mediante **claves públicas**, gestión de claves, configuración del servidor y controles de acceso.

Las claves SSH introducen conceptos que conectan directamente con criptografía: existe una clave privada que debe protegerse y una clave pública que puede distribuirse. Comprender esta relación permitirá conectar los conocimientos de criptografía con una herramienta que se utiliza diariamente en administración de sistemas.

También deben estudiarse aspectos como `known_hosts`, agentes SSH, reenvío de puertos y configuración segura del servicio. No se trata únicamente de saber conectarse mediante `ssh usuario@servidor`, sino de comprender qué ocurre durante la autenticación y qué controles determinan si la conexión está permitida.

## `/proc` y `/dev`

Linux expone gran parte de la información interna del sistema mediante interfaces especiales.

`/proc` es un **filesystem virtual** que proporciona información sobre procesos y sobre diferentes componentes del kernel. Directorios como `/proc/<PID>` permiten examinar información asociada a un proceso concreto, incluyendo su entorno, mapas de memoria y archivos abiertos.

Comprender `/proc` proporciona una perspectiva mucho más profunda sobre el sistema. Permite relacionar directamente conceptos como PID, memoria, procesos, descriptores de archivos y estado del kernel con información que puede consultarse desde la terminal.

`/dev` contiene los **device files** mediante los cuales el sistema representa determinados dispositivos y mecanismos especiales. Estos archivos permiten interactuar con dispositivos y componentes del sistema utilizando interfaces coherentes con el modelo Unix de archivos.

El estudio de `/proc` y `/dev` debe servir para comprender que en Linux el sistema de archivos no contiene únicamente documentos y programas. También existen interfaces virtuales que permiten interactuar con el estado del sistema y con diferentes componentes del kernel.

## Administración del sistema

La administración de Linux requiere integrar todos estos conceptos. Un administrador debe poder identificar usuarios, comprobar permisos, localizar procesos, consultar servicios, analizar logs, modificar configuraciones y automatizar tareas.

También será necesario conocer la gestión de paquetes, ya que gran parte del software de un sistema Linux se instala y actualiza mediante gestores como `apt`, `dnf` o `pacman`, dependiendo de la distribución.

La administración debe realizarse siempre teniendo presente el principio de **mínimo privilegio**. No todas las operaciones requieren root y conceder privilegios superiores a los necesarios aumenta la superficie de riesgo.

El objetivo no es convertirse todavía en administrador experto de todas las distribuciones existentes, sino comprender los mecanismos comunes que permiten trabajar con ellas.

## Seguridad

La seguridad de Linux surge de la combinación de diferentes mecanismos. Los permisos determinan quién puede acceder a un recurso; los usuarios y grupos proporcionan identidad; los procesos determinan qué código está ejecutándose; los servicios mantienen funcionalidades disponibles; los logs proporcionan trazabilidad y las capabilities permiten dividir determinados privilegios.

Las **capabilities** representan una evolución del modelo tradicional de root. En lugar de proporcionar a un proceso todos los privilegios administrativos, es posible conceder capacidades específicas. Esto permite construir servicios con un nivel de privilegio más reducido.

Comprender capabilities será especialmente importante al estudiar posteriormente contenedores, servicios Linux y escalada de privilegios. Un proceso puede no ejecutarse como root y, sin embargo, disponer de una capacidad que le permita realizar una operación especialmente sensible.

La seguridad también requiere comprender la relación entre permisos de archivos y procesos. No basta con preguntar "¿quién puede leer este archivo?". Hay que considerar qué proceso intenta acceder a él, con qué UID y GID se ejecuta, qué grupos posee, qué capabilities tiene y qué controles adicionales existen.

## Meta

La meta de este bloque es alcanzar una situación en la que la terminal se convierta en una **herramienta de razonamiento sobre el sistema**, no simplemente en un lugar donde ejecutar comandos memorizados.

Ante una situación desconocida, el objetivo debe ser formular una pregunta y encontrar la herramienta adecuada para responderla. Si se quiere saber dónde estamos, se consulta el directorio de trabajo. Si se quiere saber qué procesos existen, se examina la tabla de procesos. Si se necesita descubrir quién está escuchando en un puerto, se consultan los sockets. Si se necesita determinar qué servicio está ejecutándose, se examina `systemd`. Si se quiere investigar un comportamiento ocurrido anteriormente, se consultan los logs.

Este enfoque transforma el aprendizaje de comandos en **comprensión operacional**.

El objetivo final es poder entrar en un sistema Linux desconocido y orientarse sin depender de una guía paso a paso. Debe ser posible identificar la estructura del sistema, determinar quiénes son sus usuarios, comprender los permisos relevantes, descubrir qué procesos y servicios están activos, localizar información útil en los logs y utilizar la shell para automatizar tareas.

Esta base permitirá posteriormente avanzar hacia Linux avanzado, redes, scripting, administración de servidores, análisis forense, hardening, seguridad de aplicaciones, contenedores y técnicas de análisis y explotación.

La regla fundamental que debe mantenerse durante todo el bloque es sencilla: **cada comando debe responder a una pregunta sobre el sistema**. No se trata de saber que `ps` existe, sino de saber cuándo necesitamos conocer los procesos; no se trata de memorizar `grep`, sino de reconocer cuándo necesitamos filtrar información; no se trata de conocer `chmod`, sino de comprender qué permiso queremos modificar y qué efecto tendrá sobre el acceso al recurso.

Cuando se alcanza ese punto, la terminal deja de ser una colección de comandos y pasa a convertirse en una extensión del propio modelo mental del sistema operativo.
