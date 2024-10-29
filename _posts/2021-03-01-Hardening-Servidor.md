---
typora-copy-images-to: ../assets/img/hardening/
typora-root-url: ../../
layout: post
categories: tema2 La capa de Red
title: ARP Protocolo de resolución de direcciones
author: Pedro Segarra
conToc: true
titlepage: true
titlepage-background: assets/img/seguridad.png
# No funciona el background :(
apage-background:  assets/img/fondo-pagina.png
urlcolor: CornflowerBlue
linkcolor: black
toc-own-page: true
toc-title: Contenidos
header-left: UD 3. Hardening del servidor
header-right: Ciberseguridad
footer-left: IES El Caminàs
footer-right: \thepage/\pageref{LastPage}
titlepage-rule-color: 1e2c37
header-includes: |
    \usepackage{lastpage} 
    \usepackage{awesomebox}
pandoc-latex-environment:
    noteblock: [note]
    tipblock: [tip]
    warningblock: [warning]
    cautionblock: [caution]
    importantblock: [important]
---

# 8 ARP Protocolos de resolución de direcciones

*+Address Resolution Protocol.*+
Cuando se tiene que enviar un mensaje IP hay que introducirlo en una trama de la capa de enlace de datos para poderlo enviar. En esa trama la dirección no es la dirección IP. Debe usarse la dirección de la capa de enlace de datos, por ejemplo si es una red Ethernet se deberá usar una dirección MAC de 48 bits.
>
Las direcciones MAC están grabadas por los fabricantes en los dispositivos de red y están organizadas para que sean únicas mundialmente.
>
El problema es averiguar la dirección MAC con la que construir la trama que incluirá el mensaje IP. Para automatizar este proceso se usa el protocolo ARP.
Si emisor y receptor están conectados a la misma LAN, el protocolo ARP lo que hace es enviar una difusión de capa 2 preguntando quién tiene la IP destino. El ordenador que la tiene contesta, con lo cual el que en quiere enviar el mensaje IP averigua la dirección MAC del destino.
Si emisor y receptor no están conectados a la misma LAN y a la dirección destino se accede a través de un gateway de la capa de red, entonces la consulta para averiguar la MAC se hace de la IP del gateway y no del destino final.
La figura siguiente muestra diferentes escenarios en los que puede actuar el protocolo ARP.

![Tema2](/PAX/assets/tema2_r9.png)

En el caso de la figura anterior analicemos diferentes casos. Tenemos tres redes IP 192.31.65.0/24, 192.31.60.0/24 y 192.31.63.0/24 que actúan sobre sendas LANs (dos Ethernet y una dorsal FDDI):
* El ordenador 1 quiere enviar un mensaje IP al ordenador 2. En la tabla de rutas ve que está conectado directamente a esa red IP y lanza una consulta ARP para saber la MAC correspondiente a 192.31.65.5. Sin ninguna configuración se encuentra la MAC destino gracias al protocolo ARP.
* Si el ordenador 1 quiere enviar un mensaje IP al ordenador 4 la cosa cambia porque si se consulta por ARP haciendo una difusión en la LAN, el ordenador 4 no contestará porque está en otra LAN. Para esto tenemos dos soluciones:
  * Proxy ARP: el router CS responde a las consultas ARP que preguntan por direcciones de la red 192.31.63.0/24, de forma que el ordenador 1 en la trama pone la direccón Ethernet de CS en esa misma LAN (E3). CS ya lo pasará hacia la red correcta. Esta configuración es poco habitual.
  * Que CS actúe como un encaminador. El ordenador 1 debe saber que el tráfico hacia la 192.31.63.0 debe entregarlo a la MAC del 192.31.65.1. A su vez CS debe saber hacia dónde enviar el tráfico para la 192.31.63.0.
  * En cualquier caso, CS abrirá la trama que le llega y encontrará un mensaje IP que va hacia la IP 192.31.63.8 y actuará de forma análoga para hacerlo llegar al encaminador EE.
Las direcciones MAC que van averiguando los ordenadores y routers, las guardan en una cache para no tener que repetir la consulta si se vuelve a enviar un mensaje a la misma IP. La información en esa caché se borra en poco tiempo (minutos) por si ese ordenador que tenía registrado cambia de IP.

Las difusiones para preguntar por una MAC incluyen la información del que consulta. Entonces después de una consulta todos tendrán esa IP-MAC en su caché. 
Al arrancar un ordenador, éste consulta su propia IP. Así todos sabrán su IP-MAC. Si alguien contestase, hay un problema en la red porque dos estaciones tienen la misma IP y les funcionará mal la red.

>
Este funcionamiento básico se ha ido complicando un poco debido a los ataques por suplantación de MAC.
>