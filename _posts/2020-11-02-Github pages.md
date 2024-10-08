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

Los dos primeros factores se resuelven controlando la energía de la señal con repetidores o amplificadores. El tercer factor, la **distorsión por atenuación** influye en la señal recibida con distorsión. Es más difícil reconocer la señal inicial. Se usan técnicas que ecualizan la atenuación.

## Distorsión de retardo

La distorsión de retardo es un fenómeno provocado por la velocidad de propagación de una señal a través de un medio guiado y que varía con la frecuencia. Esto hace que los distintos componentes en frecuencia de la señal lleguen al recpetor en diferentes instantes de tiempo dando lugar a desplazamientos de fase entre las diferentes frecuencias. Esto fenómeno es conocido como **distorsión de retardo** ya que la señal recibida está distorsionada debido al retardo.

## Ruido

Aparecen señales no deseadas en la transmisión de la señal entre el emisor y el receptor. La señal de ruido se puede clasificar en cuatro categorías:
* **Ruido térmico**. Este es debido a la agitación térmica de los electrones y está presente en los dispositivos electrónicos y medios de transmisión. Se puede calcular la pérdida de energía por Hz en función de la tenperatura.
* **Ruido de intermodulación** Se produce cuando las señales de distintas frecuencias comparten el mismo medio de transmisión. El efecto que se produce es la aparición de señales a frecuencias que sean suma o diferencia de las dos frecuencias originales.
* **La diafonía**. Es típocio en comunicaciones telefónicas y consiste en acoplamiento no deseado entre diferentes líneas que transportan las señales. Este fenómeno se puede encontrar en líneas telefónicas, en líneas de cable coaxial, antenas de microondas, etc..
* **El ruido impulsivo**. No es continuo y está constituido por pulsos o picos irregulares de corta duración y amplitud grande. Se produce por tormentas atmosféricas, fallos en sistemas de comunicaciones, etc...

