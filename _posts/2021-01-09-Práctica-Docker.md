---
typora-copy-images-to: ../assets/img/docker/
typora-root-url: ../../
layout: post
categories: tema2 La capa de red
title: Algoritmos de encaminamiento
conToc: true
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
header-left: 
header-right: 
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
# Algoritmos de encaminamiento

El encaminamiento de mensajes consta de dos partes:
* Construir y mantener la **tabla de rutas**. La tabla de rutas indica la línea o siguiente salto para alcanzar un destino. Este proceso puede er complejo y dinámico ya que se deben tener en cuenta las modificaciones en la red (averías, carga en las líneas, nuevas incorporaciones de oruteres y líneas, nuevos destinos). Los **algoritmos de encaminamiento** o protocolos de encaminamiento se realizan en esta parte.
* Buscar la salida para cada mensaje. Se debe consultar la dirección de destino en la tabla de rutas para efectuar el envío. Este mecanismo es mecánico y es lo que efectúa el **proceso de reenvío**

Por ello se distinguen varios algoritmos de encaminamiento:
* **Encaminamiento estático**. El encaminador carga las rutas al arrancar o los algoritmos actúan de ifugal manera independientemente de cómo esté la red (estado).
* **Encaminamiento dinámico**. En función del estado de la red, la carga y la topología, modifican las decisiones de encaminamiento. Para poder reaizar estas decisiones deben intercambiar información y comprobar el estado de la red. Se puede hacer periódicamente o cuando se detectan cambios.
  
  ´´´´
  El objetivo de un algoritmo de encaminamiento es encontrar las mejores rutas a cada destino. El algoritmo debería aproximarse a una solución óptima.
  ´´´´
![Tema2](/PAX/assets/tema2_2.png) 

En la figura anterior se muestra una red de encaminadores y un árblo que representa las mejores rutas del encaminador B a cada destino. Este árbol es el **arbol sumidero** (sink tree) para B.
Características del árbol sumidero:
* La **métrica** es el número de saltos. La métrica es lo que se quiere optimizar. Podrían ser distancias, saltos, anchos de banda, carga o una mezcla de todas ellas.
* Los enlaces pueden no tener la misma métrica en cada sentido.
* El árbol sumidero es óptimo, pero puede ser no único.
* El árbol sumidero no tiene ciclos, se alcanza cada posible destino en un número finito de saltos.
* Las subrutas son óptimas también. Si la mejor ruta de B a L pasa por F, esta ruta también incluye la mejor de F a L. Se conoce como **principio de optimalidad**
* Pueden existir varias rutas óptimas.

## La ruta más corta
Cuando se habla de **corta** se refiere a la de **menor coste**.
Un algoritmo conocido para encontrar la ruta más corta entre un origen y cualquier destino es un grafo propuesto por Dijkstra.La evolución de este algoritmo se muestra en la figura siguiente:
![Tema2](/PAX/assets/tema2_3.png) 