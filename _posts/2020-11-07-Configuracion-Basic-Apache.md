---
typora-copy-images-to: ../../assets/img/apache/
typora-root-url: ../../
layout: post
categories: tema3 Capa de enlace de datos

conToc: true
title: Enmarcado de tramas
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
header-left: UD 1. Apache
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

# Enmarcado de tramas

La capa física envía bits de un lado a otro. Es necesario separar los mensajes o tramas para ir comprobando que llegan correctamente(sin errores). Enmarcar mensajes es marcar el inicio y el fin de los mensajes para que el receptor no confunda un mensaje con otro. Los silencios entre una trama y otra pueden no ser eficaces porque pueden modificarse en el medio físico y las estaciones normalmente no están sincronizadas.
Existen diferentes técnicas para enmarcar las tramas:

## Conteo de caracteres

El primer byte de cada trama indica el número de bytes de la trama. El problema de este sistema es que si se produce un error provoca una perdida de la sincronía y es difícil recuperarse.

![Tema4](/PAX/assets/tema4_1.png)

## Banderas con bytes de relleno
En este método se usan caracteres especiales (flags) que indican el inicio y el fin de una trama. El problema es que esos caracteres podrían estar dentro de los datos y llevar a confusión. Para quitar el significado especial, se usa otro carácter especial (esc). Pero también esc podría formar parte de los datos. Lo que se hace es preceder con esc cada aparición de uno de estos dos caracteres en los datos (la carga útil) de la trama. Cuando se recibe la trama, cada vez que se encuentra el carácter esc se retira y se deja el carácter siguiente tomándolo como un carácter normal de los datos. 

![Tema4](/PAX/assets/tema4_2.png)