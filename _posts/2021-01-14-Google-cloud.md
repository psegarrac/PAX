---
typora-copy-images-to: ../assets/img/cloud/
typora-root-url: ../../
layout: post
categories: tema2 La capa de Red
title: IPv4
conToc: false
subtitle: 
author:
- Pedro Segarra
lang: es
titlepage: true
titlepage-background: assets/img/despliegue.png
page-background: assets/img/fondo-pagina.png
urlcolor: CornflowerBlue
linkcolor: black
toc-own-page: true
toc-title: Contenidos
header-left: UD 2. Google Cloud
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

## 5 IPv4
Internet Protocol version 4. 
Se trata del protocolo más usado en Internet. Desde hace años se inició la migración a IPv6 y esta migración que hasta ahora ha ido lentamente está previsto que se acelere porque algunas regiones del mundo prácticamente han agotado las direcciones IPv4 que tenían asignadas y por tanto no se pueden asignar nuevos rangos a nuevos operadores o instituciones. La principal diferencia entre IPv4 e IPv6 es el tamaño de las direcciones (de 32 bits a 128 bits), pero también se ha aprovechado para aplicar algunas mejoras.
La siguiente figura muestra el formato de las cabeceras de los mensajes IPv4. Este protocolo es datagrama.

![Tema2](/PAX/assets/tema2_10.png)

* Versión: 4. 4 bits.
* IHL: longitud de la cabecera en palabras de 32 bits. 4 bits. Al poder contener opciones, la longitud es variable. Longitud mínima, 5 y máxima 15 (60 bytes, 40 bytes para partes opcionales).
* Type Of Service (TOS). 8 bits. Para indicar calidad de servicio indicada en clases (servicios diferenciados). 6 bits se usan para indicar clases de tráfico y los 2 últimos bits se usan para notificar problemas de congestión.
* Longitud total en bytes. 16 bits. Tamaño del mensaje con cabecera y carga útil. Esto puede dar paquetes de 65.535 bytes. Lo que ocurre es que normalmente el tamaño se ajusta a la carga útil de las tramas Ethernet (1500 bytes).
* Identificación. 16 bits. Si un mensaje no cabe entero al pasar por una red se tiene que fragmentar. Todos los fragmentos llevarán el mismo valor en este campo para poder recomponer el mensaje.

* DF (Do not Fragment). 1 bit. Si se quiere indicar que el mensaje no debe fragmentarse.
* MF (More Fragments). 1 bit. El último fragmento lleva 0 y los demás fragmentos llevan 1.
* Desplazamiento del fragmento. 13 bits. Para poder ordenar los fragmentos de un paquete. Se numeran los fragmentos como múltiplos de 8 bytes (fragmento mínimo).
* TTL Time To Live. 8 bits. Cuando se envía un mensaje se pone un valor inicial (máximo 255). Cada vez que un router reenvía el mensaje decrementa en 1 el valor de este campo. Cuando un router recibe el campo a cero se descarta el mensaje. De esta forma se elimina la posibilidad de que un mensaje se quede indefinidamente viajando por la red ya que el número de saltos que puede dar un paquete está limitado.
* Protocolo. 8 bits. Se indica a qué protocolo de la capa superior (TCP, UDP u otros). Los valores para cada protocolo se definen como estándar. Por ejemplo, 98 indica que es un mensaje para el protocolo de encaminamiento OSPF.
* Suma de verificación del encabezado. 16 bits. Solo se verifica la cabecera, por si los routers han introducido algún error al tratar el mensaje. Como el campo tiempo de vida se modifica en cada salto, la suma de verificación se tiene que recalcular cada vez. Se trata de una suma complemento a 1 de bloques de 16 bits.
* Dirección origen. 32 bits. IP origen del mensaje.
* Dirección destino. 32 bits. IP destino del mensaje.
* Opciones. Para pruebas y usos futuros. Algunas opciones están estandarizadas. El primer byte indica de qué opción se trata. Luego, la opción puede ocupar un tamaño variable, pero siempre limitado por el tamaño máximo de la cabecera. En ocasiones el segundo byte indica la longitud de la opción (que siempre son múltiplos de 4 bytes para ocupar palabras enteras de 32 bits).
  
La figura siguiente muestra algunos ejemplos de opciones para las cabeceras IPv4. 

![Tema2](/PAX/assets/tema2_11.png)

De la figura anterior, algunas de las opciones:
* Seguridad. Para indicar que una trama debía viajar de forma segura o confidencial, y por tanto se tenían que enviar ciertos routers. En la práctica no se usa.
* Enrutamiento estricto desde el origen. Para hacer pruebas de prestaciones o enviar mensajes urgente. Se pone la ruta de direcciones IP hasta alcanzar el destino.
* Enrutamiento libre desde el origen. No se pone la ruta estricta pero se indican algunos routers por los que hay que pasar, y además en el orden indicado.
* Registrar ruta. Para que los routers por los que pasa un mensaje graben su dirección. Así se pueden detectar fallos en el enrutamiento. Algo parecido a las órdenes como traceroute o mtr. El problema es que para trayectorias largas, se ha quedado corto el espacio que queda en la cabecera (40 bytes).
* Marca de tiempo. Como la anterior, pero además los routers también escriben una marca de tiempo.
Las opciones de IPv4 prácticamente no se usan y muchos routers las ignoran.

### 5.1 Direcciones IPv4
Las direcciones IP se asignan a los dispositivos de red de los ordenadores, estaciones (hosts) y routers. Es decir que si un ordenador está conectados a varias redes con diferentes tarjetas de red (o incluso podría ser la misma), puede tener varias direcciones IP. Las direcciones conectadas a una misma red o a Internet deben ser únicas.
Una dirección IP contiene dos partes: una parte que indica la red IP en la que está esa dirección y otra parte para diferenciar las direcciones de una misma red.
Inicialmente se utilizó el **direccionamiento por clases** en el que la diferencia entre la parte de red y la parte de ordenador (dirección dentro de la red) se distribuía según los primeros bits de la dirección IP. Este direccionamiento **ya no se usa** pero es común que aún se hagan referencias a él en los documentos. En la figura siguiente se muestra el direccionamiento por clases.

![Tema2](/PAX/assets/tema4_5.png)

Las direcciones de red las asigna mundialmente un organismo sin ánimo de lucro: **ICANN** (Corporación de Internet para la Asignación de Nombres y Números). Este organismo delega en otras organizaciones que se reparten las asignaciones para continentes (RIR) y éstas a su vez en organizaciones regionales (LIR). Estas organizaciones son las que hacen las asignaciones a los ISPs y a las empresas o instituciones.
La notación que se usa en las direcciones IPv4 consiste en separar los 4 bytes de una dirección y convertir cada byte a notación decimal. Los valores decimales se separan por puntos: por ejemplo 192.168.1.1 .
La siguiente figura muestra algunas direcciones especiales.

![Tema2](/PAX/assets/tema2_r1.png)

* Una dirección todo a ceros se usa cuando arranca una máquina y no tiene IP asignada. Probablemente pide la configuración por la red.
* Una dirección con la parte de red a ceros, indica que es para la red local
* Una dirección todo a unos es una difusión (broadcast) en la red local.
* Una dirección con toda la parte de ordenador a unos es una difusión para esa red pero se envía desde otra red.
* Cualquier IP que empieza por 127 es para dispositivos loopback. Se usan para dispositivos virtuales que devuelven el mensaje. Así alguna aplicaciones que necesitan tener dispositivos de red, pueden funcionar aún sin estar conectados a una red real.

#### 5.1.1 Subredes

Es común que una organización que tenga una dirección red asignada necesite fraccionarla internamente en varias redes. Para esto ya no sirve el direccionamiento por clases, y es necesario definir el uso de un nuevo elemento de la red: la **máscara** de red.
La máscara de red divide la parte de bits de la red y la parte de direcciones dentro de esa red. La máscara tiene todos los bits de la parte de red a uno y el resto a ceros, de forma que si se hace la operación y entre una dirección de la red y su máscara, se obtiene la dirección cero de la red.
Por ejemplo, en una universidad es común tener una red IP para cada departamento o uso y que estas redes estén conectadas mediante una LAN rápida que a su vez también conecta con el router que les conecta con Internet o con un ISP. Esta estructura se muestra en la figura siguiente.

![Tema2](/PAX/assets/tema2_r2.png)

Para una red dividirla en subredes (redes IP más pequeñas pero contenidas en la red inicial), lo que se hace es pasar algunos bits (dependiendo de las subredes que se necesiten) de la parte de ordenador a la parte de red. La cantidad de bits usados deben también añadirse a la máscara.
La figura siguiente muestra lo que era una red de clase B (actualmente con máscara de 16 bits) dividida en 26 subredes (se han usado 6 bits de la parte de ordenador para diferenciar cada subred). Dentro de esa red, ahora se usará una máscara 255.255.252.0 y cada subred puede tener hasta 210 direcciones.

>
>Se puede usar dos notaciones para indicar la máscara:
 >   • Una notación como para la IP, pasando cada byte a decimal: 255.>255.252.0
 >   • Simplemente indicando el número de unos de la máscara (que han de ser los de mayor peso): /22
>

>
>Las subredes son internas. No se comunican a los organismos que >reparten los bloques de red. 
>Desde fuera de la red no son visibles. 


#### 5.1.2 CIDR
Classless InterDomain Routing. Como ya se ha mencionado, el direccionamiento por clases ya no se usa. Además se ha introducido el concepto de máscara de red para poder subdividir redes. El uso de la máscara para indicar el prefijo de red en la dirección ha sido imprescindible por el uso que se estaba haciendo de las asignaciones de redes. Cuando se asignaban direcciones, los solicitantes no querían de clase C (255 direcciones) y solicitaban al menos de clase B (65.536 direcciones). Como se agotan las direcciones disponibles rápidamente, se empezó a hacer las asignaciones adaptando la máscara de red a algo aproximado a las direcciones solicitadas. De esta forma se aprovecha más las direcciones.
A partir del uso de CIDR es necesario conocer la máscara de cualquier dirección IP para direccionarla. El proceso de reenvío es un poco más complicado porque hay que comprobar cada destino con la máscara de cada dirección de la tabla de rutas hasta encontrar por dónde se debe enviar el mensaje. 

`````
El proceso para encontrar por dónde enviar un mensaje. Cada línea de la tabla de rutas tiene una IP destino, una máscara, y una indicación de dónde enviar el mensaje. Por orden decreciente de máscara en la tabla de rutas se hace la operación AND entre la IP destino y la máscara y se compara el resulado con el destino de la línea de la tabla que se está probando. Si coinciden se usará esa ruta.
Luego en la capa 2 igual hay que enviar a otro router (gateway) para encaminar hacia el destino final o bien es una red conectada y se envía al destino directamente.
`````

``````
En una tabla de rutas puede que más de una línea de la tabla que acierte. Se usará la que tenga una máscara con más unos (la más específica o con un prefijo mayor).
``````

En la figura siguiente se muestra un ejemplo de asignaciones de direcciones. Se supone un prefijo de red 194.24.0.0 a partir del cual se piden redes que hay que ir asignando por orden de llegada. Cambridge (2048 direcciones), Edimburgo (1024 direcciones) y Oxford (4096 direcciones). 

![Tema2](/PAX/assets/tema2_r3.png)

En la figura anterior, el bloque marcado como disponible es porque la red de Oxford no cabría con todas sus direcciones. En cambio se debe marcar para asignarlo a otras redes que se soliciten y quepan completamente dentro de él.

>Hay que tener en cuenta que si se pide una cantidad de direcciones siempre se debe asignar una potencia de 2 igual o superior porque las redes deben caber enteras con un prefijo y una máscara de red