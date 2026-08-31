# Criptografía

La criptografía es el conjunto de técnicas matemáticas utilizadas para proteger información frente a terceros que no deberían poder leerla, modificarla o falsificarla. En seguridad informática, su función no se limita a "cifrar datos": diferentes mecanismos criptográficos resuelven problemas diferentes, como mantener la **confidencialidad**, garantizar la **integridad**, demostrar la **autenticidad** de un mensaje o establecer la identidad de una entidad dentro de una comunicación.

Por esta razón, el estudio de criptografía debe comenzar por comprender los problemas que se pretenden resolver antes de estudiar los algoritmos concretos. Un hash no sustituye a un cifrado, una firma digital no es lo mismo que un HMAC y un certificado digital no es simplemente una clave pública almacenada en un archivo. Cada mecanismo forma parte de un modelo de seguridad diferente.

La criptografía moderna también depende de conceptos fundamentales como la generación de números aleatorios seguros, la gestión de claves, la longitud de las claves y los supuestos matemáticos sobre los que se construyen los algoritmos. Un algoritmo considerado seguro puede utilizarse incorrectamente y producir igualmente un sistema vulnerable. Por ello, además de estudiar los algoritmos, será necesario comprender cómo se integran en protocolos y sistemas reales.

## Hashes

Una **función hash criptográfica** transforma una entrada de tamaño arbitrario en una salida de tamaño fijo. El resultado, conocido como *digest* o resumen, debe presentar determinadas propiedades que dificulten la recuperación de la entrada original y la construcción deliberada de entradas que produzcan determinados resultados.

Una propiedad fundamental es la **resistencia a preimagen**: dado un hash, debería resultar computacionalmente inviable encontrar una entrada que produzca ese resultado. También es importante la **resistencia a segunda preimagen**, que dificulta encontrar otra entrada diferente que produzca el mismo hash que una entrada concreta. Finalmente está la **resistencia a colisiones**, que busca impedir que se encuentren dos entradas diferentes con el mismo resultado.

Estas propiedades permiten utilizar hashes para verificar la integridad de información, identificar contenido y construir otros mecanismos criptográficos. Sin embargo, un hash por sí solo **no proporciona confidencialidad**. Si una contraseña se transforma mediante un hash, el resultado no significa que la contraseña haya sido cifrada y pueda recuperarse posteriormente; se trata de una transformación diseñada para ser unidireccional.

Dentro de las funciones hash debe estudiarse la familia **SHA-2**, especialmente SHA-256 y SHA-512. Además de conocer su funcionamiento conceptual, es importante comprender el tamaño de sus salidas, sus propiedades de seguridad y los contextos en los que resulta apropiado utilizarlas.

También debe estudiarse **MD5**, no porque sea una opción adecuada para nuevos sistemas, sino precisamente porque permite comprender cómo una función criptográfica puede dejar de considerarse segura cuando aparecen ataques prácticos contra una de sus propiedades fundamentales. Las colisiones de MD5 hacen que no deba utilizarse como función hash criptográfica para nuevos diseños que requieran resistencia a colisiones.

Otro concepto fundamental es el **salt**. Un salt es un valor adicional, normalmente aleatorio y único por credencial, que se combina con una contraseña antes de aplicar un proceso de derivación o hashing. Su finalidad principal es impedir que dos contraseñas iguales produzcan automáticamente el mismo resultado y dificultar ataques basados en tablas precalculadas. El salt no tiene que mantenerse secreto; su función es diferente de la de una clave criptográfica.

Para el almacenamiento de contraseñas es necesario ir más allá de SHA-2 y comprender las **funciones de derivación de claves para contraseñas**, como Argon2, scrypt, bcrypt o PBKDF2. Estas funciones están diseñadas para hacer costoso el proceso de probar grandes cantidades de contraseñas, algo que un hash rápido como SHA-256 no consigue por sí mismo. La seguridad de un sistema de contraseñas depende, por tanto, tanto del algoritmo utilizado como de parámetros como el coste computacional, memoria, paralelismo y generación adecuada de salts.

## Integridad y autenticación

La **integridad** consiste en poder detectar que una información ha sido modificada. Sin embargo, detectar una modificación no implica necesariamente saber quién realizó el cambio. Cuando además necesitamos demostrar que un mensaje procede de una entidad que posee un secreto determinado, entramos en el terreno de la **autenticación criptográfica**.

Un mecanismo fundamental es **HMAC (Hash-based Message Authentication Code)**. HMAC combina una función hash con una clave secreta compartida para producir un código de autenticación asociado a un mensaje. Una entidad que conozca la misma clave puede verificar que el mensaje no ha sido alterado y que ha sido generado por alguien que dispone de esa clave.

Es importante distinguir HMAC de un hash convencional. Si simplemente calculamos el hash de un mensaje, cualquier persona puede volver a calcularlo después de modificar el mensaje. HMAC incorpora una clave secreta, de manera que un tercero que no posea esa clave no puede generar un código de autenticación válido.

También debe comprenderse la diferencia entre **integridad, autenticidad y confidencialidad**. Un mecanismo puede proporcionar unas propiedades y no otras. HMAC, por ejemplo, proporciona autenticidad e integridad frente a entidades que no conocen la clave, pero no cifra el contenido del mensaje.

## Cifrado simétrico

El **cifrado simétrico** utiliza una clave secreta compartida para proteger la información. La misma clave, o información derivada de ella, interviene tanto en el proceso de cifrado como en el descifrado.

La ventaja fundamental de los algoritmos simétricos es su eficiencia. Son adecuados para cifrar grandes cantidades de información y constituyen una pieza fundamental de protocolos de comunicación modernos.

El algoritmo principal que debe estudiarse es **AES (Advanced Encryption Standard)**. Será necesario comprender conceptos como tamaño de bloque, tamaños de clave y, especialmente, el concepto de **modo de operación**. AES por sí solo no define un sistema completo de cifrado de mensajes arbitrariamente largos. La forma en que se utiliza el algoritmo determina propiedades fundamentales del sistema.

En este contexto deben estudiarse modos modernos como **GCM**, que proporciona cifrado autenticado mediante AEAD (*Authenticated Encryption with Associated Data*). AEAD permite obtener confidencialidad e integridad/autenticidad de manera conjunta y, además, proteger determinados datos asociados que no necesitan ser cifrados.

También será necesario comprender la importancia de los **nonces e IVs (Initialization Vectors)**. No basta con utilizar un algoritmo seguro: utilizar incorrectamente un nonce, reutilizarlo cuando el modo no lo permite o utilizar valores predecibles donde se requiere aleatoriedad puede comprometer las garantías del sistema.

La criptografía simétrica introduce además uno de los problemas centrales de la criptografía aplicada: **la distribución de claves**. Si dos personas necesitan comunicarse de forma segura utilizando una clave secreta, primero deben encontrar una forma segura de compartirla. Este problema conduce directamente al estudio de la criptografía asimétrica.

## Cifrado asimétrico

La **criptografía asimétrica** utiliza pares de claves relacionadas matemáticamente: una clave pública y una clave privada. La clave pública puede distribuirse, mientras que la privada debe mantenerse protegida.

Este modelo permite resolver problemas que resultan difíciles con criptografía simétrica, especialmente el establecimiento de comunicaciones entre entidades que todavía no comparten un secreto. También permite construir mecanismos de **firmas digitales**, que proporcionan propiedades diferentes de las del cifrado.

**RSA** debe estudiarse como uno de los sistemas asimétricos clásicos. Será necesario comprender su funcionamiento conceptual, la relación entre claves públicas y privadas y los fundamentos matemáticos sobre los que se basa. También es importante conocer que RSA no debe utilizarse directamente para "cifrar cualquier cosa": en sistemas reales se utilizan esquemas y construcciones criptográficas específicas, con padding y protocolos correctamente definidos.

Las **curvas elípticas (ECC)** proporcionan otro enfoque a la criptografía de clave pública. Permiten obtener determinados niveles de seguridad utilizando tamaños de clave significativamente menores que RSA. Más que memorizar operaciones matemáticas complejas, en esta etapa interesa comprender por qué las curvas elípticas pueden utilizarse para construir mecanismos de intercambio de claves, firmas y otras primitivas criptográficas.

En este punto debe aparecer una distinción fundamental entre **cifrado y firma digital**. El cifrado busca proteger la confidencialidad de una información, mientras que una firma digital permite verificar la autenticidad e integridad de un mensaje y vincularlo criptográficamente con la clave privada de quien firma. Son mecanismos diferentes aunque ambos utilicen criptografía asimétrica.

Otro concepto importante es el **intercambio de claves**, especialmente mediante mecanismos basados en Diffie-Hellman y sus variantes sobre curvas elípticas. Estos mecanismos permiten que dos partes establezcan un secreto compartido a través de un canal que puede ser observado por terceros, siempre que se cumplan las condiciones de seguridad correspondientes.

En sistemas modernos, la criptografía asimétrica suele utilizarse para resolver problemas de identidad y establecimiento de claves, mientras que la criptografía simétrica se utiliza posteriormente para proteger el volumen principal de los datos. Esta combinación permite aprovechar las ventajas de ambos modelos.

## TLS y comunicaciones seguras

La criptografía adquiere todo su sentido práctico cuando se integra en **protocolos de comunicación**. El objetivo no es simplemente cifrar una conexión, sino establecer un canal en el que las partes puedan negociar algoritmos, autenticar determinadas entidades, establecer claves y proteger posteriormente el tráfico.

**TLS (Transport Layer Security)** es uno de los protocolos fundamentales para comprender este proceso. Es la tecnología que permite proteger numerosos protocolos de aplicación, siendo HTTPS uno de sus usos más conocidos.

El estudio de TLS debe centrarse en el proceso conceptual de establecimiento de una conexión segura. El cliente y el servidor negocian parámetros criptográficos, se establece material de claves y se verifica la identidad del servidor mediante mecanismos basados en certificados. Una vez establecido el contexto criptográfico, la comunicación puede utilizar cifrado autenticado para proteger los datos intercambiados.

Será necesario comprender la diferencia entre **TLS 1.2 y TLS 1.3**, así como la evolución hacia diseños que reducen el número de intercambios necesarios y eliminan mecanismos criptográficos antiguos o inseguros. También deben estudiarse conceptos como *cipher suites*, *handshake*, *key exchange*, autenticación y claves de sesión.

Comprender TLS no significa memorizar todos los mensajes del protocolo. Lo importante es poder responder a preguntas fundamentales: ¿cómo se establece el secreto compartido?, ¿cómo sabe el cliente con quién está hablando?, ¿qué protege las comunicaciones posteriores?, ¿qué ocurre si alguien intenta modificar los mensajes durante el establecimiento de la conexión?

## Certificados y PKI

Los **certificados digitales** permiten vincular una identidad con una clave pública mediante una estructura que puede ser validada criptográficamente. En Internet, esta relación resulta fundamental para que un cliente pueda determinar si una clave pública pertenece realmente al servidor con el que pretende comunicarse.

Los certificados X.509 contienen información como la identidad del sujeto, su clave pública, el periodo de validez, el emisor y diferentes extensiones que determinan para qué puede utilizarse el certificado. Un certificado no debe interpretarse simplemente como una "clave pública": es una afirmación firmada digitalmente por una entidad de confianza.

La **PKI (Public Key Infrastructure)** engloba los componentes y procedimientos utilizados para gestionar estas relaciones de confianza. Dentro de una PKI aparecen elementos como **Certification Authorities (CA)**, certificados, claves, cadenas de confianza, procesos de emisión y mecanismos de revocación.

La existencia de una cadena de confianza permite que un sistema no tenga que conocer previamente la clave pública de cada servidor del mundo. En su lugar, confía en determinadas autoridades raíz y puede verificar una cadena de certificados hasta llegar a una de esas raíces.

Comprender este modelo resulta esencial para analizar problemas de seguridad relacionados con certificados. Una conexión puede utilizar criptografía fuerte y seguir siendo vulnerable si la identidad de la otra parte no se valida correctamente. Del mismo modo, una clave privada comprometida puede permitir que alguien suplante la identidad asociada a un certificado mientras este siga siendo considerado válido.

La PKI también permite comprender conceptos como **certificados raíz, certificados intermedios, cadenas de certificación, validación de nombres, fechas de validez y revocación**. Estos elementos forman una infraestructura de confianza mucho más amplia que el simple algoritmo criptográfico utilizado para firmar el certificado.

## Gestión de claves y aleatoriedad

Uno de los principios más importantes de la criptografía aplicada es que la seguridad de un sistema depende tanto de la **gestión de las claves** como de los algoritmos utilizados.

Una clave debe generarse mediante una fuente de aleatoriedad adecuada, almacenarse de forma segura, utilizarse dentro de los límites establecidos por el algoritmo y sustituirse cuando corresponda. Una implementación criptográfica excelente puede quedar completamente comprometida si las claves son predecibles, se reutilizan incorrectamente o se almacenan de forma insegura.

La **aleatoriedad criptográficamente segura** es especialmente importante para claves, salts, nonces, IVs y otros valores que necesitan ser impredecibles o únicos. Por ello, debe comprenderse la diferencia entre un generador de números pseudoaleatorios convencional y un **CSPRNG (Cryptographically Secure Pseudo-Random Number Generator)**.

También será necesario estudiar la **derivación de claves (KDF)**. Una KDF permite generar claves criptográficas adecuadas a partir de otro secreto, como una contraseña o un secreto compartido obtenido mediante un protocolo de intercambio de claves. Esto permite separar el concepto de secreto original de las diferentes claves utilizadas posteriormente por un sistema.

## Principio

El principio fundamental de este bloque es que **no se debe aprender criptografía como una colección de algoritmos, sino como una colección de problemas y garantías de seguridad**.

Antes de utilizar un mecanismo debe poder identificarse qué propiedad se necesita. Si se quiere detectar modificaciones se necesita integridad; si se necesita demostrar que un mensaje procede de alguien que conoce un secreto, se necesita autenticación; si se necesita impedir que terceros lean los datos, se necesita confidencialidad; si se necesita establecer una identidad asociada a una clave pública, se necesita un mecanismo de confianza como los certificados y la PKI.

Por tanto, el conocimiento de AES no consiste simplemente en saber que es un algoritmo de cifrado. Hay que comprender qué problema resuelve, cómo se utiliza correctamente, qué información necesita como entrada y qué errores de implementación pueden destruir sus garantías. Del mismo modo, conocer SHA-256 no significa simplemente saber calcular un hash, sino comprender qué propiedades proporciona y cuáles no proporciona.

La criptografía debe estudiarse siempre en dos niveles. El primero es el **primitivo criptográfico**, como SHA-256, AES, RSA o ECC. El segundo es el **protocolo o sistema que utiliza ese primitivo**, como HMAC, TLS, almacenamiento de contraseñas o PKI. En la práctica, muchas vulnerabilidades no proceden de romper matemáticamente un algoritmo, sino de utilizar correctamente una primitiva segura dentro de un diseño incorrecto.

El objetivo final es desarrollar la capacidad de analizar una arquitectura y determinar **qué mecanismos criptográficos utiliza, qué amenazas pretende resolver, qué propiedades proporciona y dónde podrían existir errores en su diseño o implementación**. Esta capacidad será posteriormente fundamental para estudiar protocolos de autenticación, aplicaciones web, redes, sistemas operativos, Active Directory, análisis de malware y seguridad de infraestructuras.

En última instancia, la pregunta que debe guiar este bloque no es "¿qué algoritmo tengo que aprender?", sino **"¿qué propiedad de seguridad necesito y cuál es el mecanismo adecuado para proporcionarla?"**.

