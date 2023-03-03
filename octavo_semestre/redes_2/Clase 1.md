**Modelo OSI:** Modelo orintado a promover la comprension de como funcionan los componentes en un sistema de red.
**Modelo TCP:** Modelo utilizado para la transmicion de datos, a diferencia del modelo OSI este no solo es un modelo teorico sino es tangible.
- Protocolo TCP: Transport Control Protocol --> Orientado a conexion
- Protocolo UDP: User Datagram Protocol --> No orientado a conexion

Ethernet: Protocolo de redes de tipo bus, este utiliza un protocolo de nombre CSMA/CD (Carry Sense Medium Access with Collision Detection).

Tipos de topologias:
- Bus: Conocida tambien como red de inundacion de paquetes o flush. La principal desventaja es que no hay privacidad de paquetes al encontrarse n un medio compartido. Su enfoque es a la repeticion de paquetes.
- Anillo: La transmision de paquetes se logra conectando las computadoras entre si, sin embargo, solo se tiene una direccion para el envio de paquetes, se puede implementar un doble anillo para permitir el envio de datos en doble direccion.
- Estrella: Tipo de conexion el cual utiliza un concentrado (HUB) para conectar todas las computadoras, sin embargo, el concetrador utiliza la topologia bus para realizar todas las peticiones.
- Malla: Todos se conectan con todos.
Uba red de malla con un concentrador (hub) no es lo mismo que una red de malla con un switch. A esto se le conoce como:
- Caso HUB: Medico compartido.
- Caso Switch: Medio exclusivo.

Existen dos tipos de cables:
- Cables uno a uno.
- Cables cruzados.
El estandarde colores para ponchar los cables RJ45 se llama TIA/EIA 568.
Los pines reservados para la transmision de datos son el 1 y 2 mientras que el 3 y 6 estan reservados para la conexion. El pin 4,5,7 y 8 unicamente se utilizan para las conexiones de tipo gigabit o para realizar POE.
La segmentacion clasica se logra a partir de una mascara de red. Esta me define un rango de $2^n-2$ en donde $n = numero\ de\ bits$. Las dos direcciones reservadas son:
- Net ID: Todos mis bits se encuentran en 0
- Broadcast: Todos mis bits se encuentran en 1
La mascara tiene una tarea simple, se encarga de discriminar al host y dejar solo el net id y apartir de este net id crea la segmentacion de red.

Las cuatro configuraciones de una red principales son:
- Direccion --> Direccion logica
- Mascara --> Alcance del dominio
- Gateway -> Valida que no este una IP al aclance de la red y rutea fuera de la red
- DNS -> Es mi traductor de direcciones

La mascara cuenta con una Default Mask la cual es 255.255.255.0 o bien es una mascara /24.
En una IP podemos decir que: N.N.N.H donde N = Net ID y H = Host ID.
Cuando una computadora realiza una solicitud, el router determina el alcance de la red, si el destino no coincide con el net ID, significa que la direccion esta fuera de la red (da 30 saltos dentro de la red, si no la encuentra la envia al gatewat).

La segmentacion clasica utiliza los bits de la mascara para crear una subred.
La IPV4 cuenta con 32 bits y se divide en octetos de 8 bits.

