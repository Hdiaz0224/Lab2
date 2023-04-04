# Laboratorio 2
## Ivan Gutierrez, Hector Diaz, Juan Deutsch
El objetivo es adquirir conocimientos sobre las redes LAN-WAN, y los protocolos de enrutamiento IPv4 e IPv6. Luego, se construirá una red empresarial basada en ambos protocolos y se implementarán técnicas de subnetting y configuración de servicios de red, como DHCPv6 y ACL. Se explorarán los métodos de migración Dual Stack y Tunneling. Además, se reconocerán y configurarán los protocolos dinámicos OSPFv2, OSPFv3, EIGRP y EIGRPv6 en las interfaces requeridas para el enrutamiento de paquetes IP en la red empresarial e Internet. Por último, se configurará un servicio informático basado en HTTP para contenidos web y el servicio DNS, y se realizará una simulación y análisis del flujo de datos del servicio HTTP a través de la red empresarial.

### Procedimiento:
En esta parte del procedimiento vamos a explicarlo en 4 diferentes partes y es el como organizamos la topología: Internet, DMZ, intranet BOG , Intranet MAD.

#### Internet:
En este caso, internet se configuraba con IPV4 y necesitabamos configurar los protocolos EIGRP, OSPF asi como una redistribucion en 2 routers para que conectaran ambos protocolos y finalmente tunneling para que conectara de forma conecta IPV4 con IPV6



#### DMZ e INTRANET BOG:
Frente a la configuración del DMZ contestamos unas preguntas para guiarnos entre estas estaban: ¿Cuántos subnets necesitamos?, ¿Cuántos hosts se necesitan?, ¿ Que dispositivos/interfaces hacen parte de la subred?, ¿ Que partes de la red son públicas o privadas?. Después de esto, se realizan las configuraciones básicas a los diferentes switches que se encuentran entre el DMZ y la intranet BOG. Asimismo realizamos una tabla donde se evidencia el dispositivo, interfaz, Direccion IP, WildCard, Mascara de subred y puerta de enlace.



La configuración se resume en qué hay dos servidores los cuales uno es para el servidor web, dónde se está alojando la página y la otra el DNS dónde se está alojando la direccion IP de la misma página web, el ISP_BOG se está encargando de ser parte de la comunicación de routers de la OSPF por el lado izquierdo de la topología. Asimismo, El servidor DNS es el encargado de almacenar la dirección IP del servidor web y proporcionar esta información a los clientes que desean acceder al sitio web. Los clientes envían una solicitud de DNS al servidor DNS, que responde con la dirección IP del servidor web correspondiente.



#### Intranet MAD:
En esta parte en teoría era la misma que el Intranet BOG ya que nos encontrábamos con una red compuesta por switches y pc’s. Por lo que la configuración era la de configurar los switches de manera normal sin embargo aquí los pc se configuraron para que tuvieran direcciones estáticas. Todo esto con el fin de que se pudiera conectar sin problema a los servidores que habíamos configurado antes y que se observaba que se ejecutaban de manera correcta.



#### Analisis:

Segun lo visto en imagenes presentadas se configuro la red con dos procesos de enrutamiento que fueron EIGRP y OSPF en sus dos versiones de IPv6 e IPv4, iniciando con EIGRP (Enhanced Interior Gateway Routing Protocol) de IPv6 se tiene en cuenta que este, segun los requerimientos se configuro por el lado ESP, que son el ISP_ESP y el R2_ESP de manera que se comunicara el internet de IPv4 con la intranet de Madrid teniendo en cuenta que este tiene una rápida convergencia de rutas, eficiencia de ancho de banda y escalabilidad para una configuracion en caso de que la red sea mas grande ademas que ofrece una autoconfiguración que hace que los dispositivos se descubran automaticamente, siguiendo con la configuracion del OSPF en IPv6 que se realizo por el lado BOG, mas especificamente en ISP_BOG y R1_BOG que de igual manera comunica la red de BOG configurada en IPv6 con el internet que esta configurado con IPv4, con relacion al OSPF que tiene casi las mismas ventajas con relación a EIGRP, con la diferencia de en OSPF la red se segmenta de mejor manera siendo asi que soporta areas de multiple enrutamiento y autenticación de mensajes, siguiendo con la configuracion de enrutamiento en IPv4, se tiene encuenta que en la zona de Internet se tiene que comunicar los protocolos de IPv6 con los de IPv4, para esto se configuro un tunneling para comunicar estas dos redes, en los routers de frontera de BOG y ESP, ya mas puntualmente dentro de IPv4 se configuro tambien los protocolos de EIGRP y OSPF redistribuyendo estos mismos dentro de la red

Con relación a las tablas de enrutamiento de IPv6 e IPv4, como se ve en la imagen, inciando con BOG, usando el comando show ipv6 route se puede ver que tipo de enrutamiento hay presente y si esta conectado o si esta local, en cuando al enrutamiento que nos da noscomunica que esta usando el OSPF para comunicarse en cuando a IPv6 mientras que si usamos el comando de show ip route nos muestra la tabla de enrutamiento en cuanto IPv4, por lo que este nos manda que se esta comunicando principalmente con EIGRP pese que se espera que se comunique con OSPF, aun asi se comunica entre los routers de IPv4 por medio de EIGRP, siguiendo con ESP en cuanto a IPv6 se nos muestra que en principio no tiene un enrutamiento que se pueda ver pero al ingresar el comando show ipv6 eigrp neighbours se nos muestra que se esta comunicando por medio de EIGRP dentro de la red de IPv6, mientras que en IPv4 simplemente se nos muestra que esta efectivamente conectado.



#### Retos:
En este laboratorio los retos que nos encontramos fueron muy dificiles pero a la vez interesantes de resolver, ya que, estabamos por primera vez manejando la configuracion de direcciones IPV6 asi como los protocos en esta version. Los pudimos resolver gracias a las lecturas que el profesor dejo en clase como material de apoyo y buscando por nuestra propia cuenta. Otro reto que nos encontramos fue el conectar redes IPV4 con IPV6 ya que tampoco sabiamos pero indagando y analizando diferentes lecturas pudimos sobrepasar este desafio

#### Conclusiones:
Para concluir aprendimos la diferencia en las configuraciones e implementacions de IPV6 e IPV4 y sus diferentes protocolos. Asi como, la redistribucion y el tunneling y la parte mas importante el conectar redes ipv4 con ipv6.

####Bitacora

#### Link del video explicatorio:

####Archivo .txt con las configuraciones:
