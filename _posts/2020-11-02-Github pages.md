---
typora-copy-images-to: ../assets/img/github-pages/
typora-root-url: ../../
layout: post
categories: tema1 La capa Física
title: Dificultades en la transmisión
conToc: false
subtitle: Dificultades en la transmisión
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
header-left: UD 1. Dificultades en la transmisión
header-right: Planificación y administración de redes
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
# Dificultades en la transmisión
Las dificultades más importantes son:

* La **atenuación** y la **distorsión de la atenuación**
* La **distorsión de retardo**
* El **ruido**
  

## Atenuación
En cualquier medio de trasmisión la energía de la señal decae con la distancia. En medios guiados, esta reducción de energía es por lo general exponencial y se expresa como un número constante de decibelidos por unidad de longitud. En medios no guiados, la atenuación es una función más compleja y depende de las condiciones atmosféricas.

> En los **medios guiados** la señal se confina en un medio físico, por ejemplo en cables de cobre. fibra óptica. En medios **no guiados** se usa el aire como medio físico.

Se pueden establecer consideraciones respecto a la atenuación:
* La señal recibida debe tener suficiente energía para que el receptor pueda reproducirla adecuadamente.
* La atenuación es una función creciente con la frecuencia. A frecuencias más altas se pierde o usa más energía.
* La atenuación no afecta igual a todos los armónicos. Este efecto produce lo que se llama **distorsión por atenuación**

