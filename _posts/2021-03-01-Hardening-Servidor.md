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

