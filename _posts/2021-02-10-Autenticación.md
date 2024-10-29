---
typora-copy-images-to: ../assets/img/autenticacion/
typora-root-url: ../../
layout: post
categories: tema 2
title: ICMP Protocolo de mensaje de control en internet
conToc: true
author:
- Pedro Segarra
lang: es
titlepage: true
titlepage-background: assets/img/seguridad.png
page-background: assets/img/fondo-pagina.png
urlcolor: CornflowerBlue
linkcolor: black
toc-own-page: true
toc-title: Contenidos
header-left: UD 3. Autenticación
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

# 7 ICMP Protocolo de mensajes de control en internet

Internet Control Messages Protocol. Este protocolo se utiliza para notificar de errores en la capa de red y para hacer pruebas. Los mensajes ICMP actúan sobre la capa de red sin llegar a la de transporte.
La figura siguiente muestra los mensajes ICMP más importantes.

![Tema2](/PAX/assets/tema2_r7.png)

* Los tres primeros son mensajes de error en el que los routers indican al origen que no han podido entregar o seguir enviando un mensaje.
* Source quench es para enviar paquetes reguladores cuando se detecta congestión. Actualmente no se usa.
* Redirect. 
* El resto de la tabla es para aplicaciones como ping. Sirven para probar conectividad o tiempos de respuesta.

