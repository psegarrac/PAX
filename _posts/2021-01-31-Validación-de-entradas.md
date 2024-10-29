---
typora-copy-images-to: ../assets/img/validacion/
typora-root-url: ../../
layout: post
categories: tema2 La capa de Red
title: IPv6
conToc: true
subtitle: 
author:
- Pedro Segarra
lang: es
titlepage: true
titlepage-background: assets/img/seguridad.png
# No funciona el background
apage-background: assets/img/fondo-pagina.png
urlcolor: CornflowerBlue
linkcolor: black
toc-own-page: true
toc-title: Contenidos
header-left: UD 3. Validación de entradas
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

# 6 IPv6

Internet Protocol versión 6.
Se empezó a diseñar en 1990 al prever la explosión de uso que tendría Internet. Vieron que el tamaño de la direcciones IPv4 se quedaba pequeño. Es un estándar desde 1998. Además se aprovechó para aplicar otras mejoras, que principalmente han servido para simplificar la cabera de los mensajes y reducir el trabajo de los routers.
En la figura siguiente se muestra la parte fija de una cabecera IPv6.

![Tema2](/PAX/assets/tema2_r5.png)

Campos de la parte fija de una cabecera IPv6:
* Versión. 4 bits. Contiene un 6.
* Clase de tráfico. 8 bits. Para indicar calidad de servicio basada en servicios diferenciados o clases de servicios. Se usa como en IPv4. Los dos últimos bits se usan para indicar congestión.
* Etiqueta de flujo. 20 bits. Para utilizar a modo de servicios integrados para calidad de servicio. Un flujo se identifica mediante IP origen y destino y la etiqueta de flujo. Para un flujo se podría requerir un tipo de tratamiento en los routers.
* Longitud de la carga útil. 16 bits. Los bytes del mensaje después de la cabecera fija de 40 bytes.
* Siguiente cabecera. 8 bits. En IPv4 había un tamaño máximo para las cabeceras opcionales. Esto ha limitado el uso de las cabeceras opcionales. En IPv6 no existe un límite. Se pueden ir encadenando varias cabeceras opcionales. En cada una hay un byte que dice el tipo de la siguiente cabecera, y en cada cabecera opcional, se indica el tamaño que ocupa. En la última cabecera opcional en el campo «siguiente cabecera» se indica el protocolo de la capa superior al que hay que entregar en mensaje (por ejemplo, TCP o UDP).
* Límite de saltos. 8 bits. Como el time to live de IPv4. Para limitar el número de saltos que puede dar un mensaje. En cada salto los routers decrementan este campo y cuando llega a 0 ya no se sigue enviando.
* Direcciones IP origen y destino. 16 bytes cada una.
  
**Notación para las direcciones.** 
Se usan 8 grupos de 4 cifras hexadecimales (4 bits cada cifra hexadecimal). Por ejemplo 8000:0000:0000:0000:0123:4567:89AB:CDEF . Para reducirlas se permiten algunas facilidades:

* Los ceros a la izquierda de un grupo pueden omitirse. :00A3: se puede poner :A3:
* Si hay grupos consecutivos de 16 ceros se pueden resumir (pero solo una vez). La dirección anterior puede escribirse como 8000::123:4567:89AB:CDEF
* Las direcciones IPv4 pueden expresarse como una dirección IPv6 precediéndola por una de : Por ejemplo ::192.31.20.46
** Diferencias respecto IPv4 **
Con 2^128 direcciones, caben 7*1023 direcciones por m2 en la superficie del globo terráqueo. Lo que ocurre es que muchas direcciones se bloquearán para facilitar el encaminamiento jerárquico. Además la previsión para cada usuario final es que le asignen una dirección IPv6 /64, con lo que cada cliente posee una red con 264 IPs (dos veces todo el direccionamiento IPv4 para cada cliente!!). Tantos bits para los clientes permite que éstos puedan construirse su dirección IP gracias a su dirección MAC (48 bits) lo cual facilita la configuración.
http://www.6deploy.eu/index.php?page=tutorials
Hay que remarcar que IPv6 tiene menos campos que IPv4 en la cabecera fija. Por ejemplo, todo lo relacionado con la fragmentación se ha eliminado. Es preferible indicar error al origen y que éste envíe mensajes más pequeños, a que los routers pierdan tiempo en estas operaciones. 
Por otro lado se eliminó el campo de suma de verificación de la cabecera ya que si hace falta fiabilidad, se puede proporcionar en las capas superiores o inferior. Esto agiliza el trabajo, porque en IPv4 la suma de comprobación tiene que comprobarse en cada salto.

## 6.1. Cabeceras opcionales IPv6

La siguiente figura muestra algunas de las cabeceras opcionales que se han definido.

![Tema2](/PAX/assets/tema2_r6.png)

Hay cabeceras opcionales de tamaño fijo o de tamaño variable, las cuales pueden tener a su vez varias opciones o partes. Cada parte de una cabecera opcional de tamaño variable se codifica como una tupla: **tipo**, **longitud** y **valor**:
* Tipo. 1 byte indicando el tipo de esa opción. Los identificativos de tipo se seleccionan de forma que los dos primeros bits indican qué deben hacer los routers que no conocen esa opción:
     * Saltarse la opción.
     * Descartar el mensaje.
     * Descartar el mensaje y devolver un mensaje de control (ICMP).
     * Descartar el mensaje y no devolver un mensaje de control a una dirección de multicast.
* Longitud. 1 byte para indicar los bytes de campo valor (máximo 255 bytes).
* Valor. Sería la información o carga útil de la opción.

