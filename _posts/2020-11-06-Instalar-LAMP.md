---
typora-root-url: ../../
typora-copy-images-to: ../assets/img/LAMP/
layout: post
categories: tema2 Capa de enlace de datos 
conToc: true
title: Tipos de servicio a la capa de red
subtitle: 
author:
- Pedro Segarra
lang: es
titlepage: true
titlepage-background: assets/img/git-basico/dibujo.png
page-background: assets/img/fondo-pagina.png
urlcolor: CornflowerBlue
linkcolor: black
toc-own-page: true
toc-title: Contenidos
header-left: UD 1. LAMP
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
# Tipos de servicio a la capa de red
Los ejemplos de servicios de comunicación que pueden ofrecer a la capa de red:

1. **Datagrama sin fiabilidad**. Servicio no orientado a la conexión sin confirmación de recepción. Se envían mensajes independientes. Se usa sobre medios fiables. El servicio más usado en LANs.
2. **Datagrama con fiabilidad**. Servicio no orientado a la conexión con confirmación de recepción. Se envían mensajes independientes pero el receptor envía un acuse de recepción (acknowledge). El emisor puede repetir el mensaje si no recibe el acuse de recepción. Se usa en redes poco fiables como las inalámbricas.
3. **Circuito virtual con fiabilidad**. Servicio orientado a la conexión con confirmación de recepción. En este caso se establece una conexión (un circuito virtual) sobre la que van a enviarse tramas numeradas y se puede garantizar que cada trama se recibe una sola vez y de forma ordenada. Por el momento, este tipo de servicio no es común en las redes de ordenadores en la capa de enlace de datos, pero por ejemplo es común en telefonía o en otras capas.
