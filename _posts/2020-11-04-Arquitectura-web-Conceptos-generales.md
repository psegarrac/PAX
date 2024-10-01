---
typora-root-url: ../../
typora-copy-images-to: ../assets/img/AWCG/
layout: post
categories: tema1
categories: tema1 La capa Física
conToc: true
title: Medios de transmisión
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \newcommand{\changefont}{%
    \fontsize{8}{11}\selectfont}
    \fancyhead[CO,CE]{}
    \fancyfoot[LO,CE]{\changefont https://victorponz.github.io/Ciberseguridad-PePS/}
    \fancyfoot[CO,CE]{}
    \fancyfoot[LE,RO]{\thepage}
    \renewcommand{\headrulewidth}{2pt}
    \renewcommand{\footrulewidth}{1pt}
---


## 1 Medios de transmisión

El medio de transmisión es el camino físico entre el emisor y el receptor. En el diseño de sistemas de transmisión es deseable que tanto la distancia como la velocidad de transmisión sean lo más grandes posibles. Entre los factores relacionados con el medio que afectan a la distancia y la velocidad se puede distinguir:
* **El ancho de banda**: si todos los otros factores se mantienen constantes al aumentar el ancho de banda de la señal, la tasa de transmisión puede incrementar.
* **Dificultades en la transmisión**: las dificultades como la atenuación limitan la distancia. En los medios guiados, el par trenzado sufre mayores problemas que el cable coaxial. La fibra óptica es la mejor opción.
* **Interferencias**: la presencia de señales con frecuencias próximas pueden distorsionar o destruir la señal. Las interferencias son especialmente relevantes en medios no guiados como las transmisiones inalámbricas, pero también puede producirse en medios guiados.
* **Número de receptores**: un medio guiado se puede usar tanto para un enlace punto a punto como para un enlace compartido, mediante el uso de múltiples conectores. En este último caso, cada uno de los conectores utilizados puede atenuar y distorsionar la señal, por lo que la distancia y/o velocidad de transmisión disminuyen. En medios guiados está en desuso conectar varios receptores a un medio salvo el caso puentes ópticos pasivos que pueden usarse en fibra óptica.
  
  


