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
  
### Medios de transmisión guiados
En este caso la capacidad de transmisión en términos de velocidad o ancho de banda depende de la distancia.

#### Par trenzado de cables de cobre
Son pares de cables de cobre. Cada cable está aislado con una funda aislante y entrecruzados en forma de espiral. Así se reducen las inducciones.
Cada par constituye sólo un enlace de comunicación. La señal se codifica como diferencias de voltaje entre los dos cables. El uso del trenzado tiende a reducir las interferencias electromagnéticas (diafonía). Los pares adyacentes se trenzan con paso de torsión diferentes. Los conductores que forman el par tienen un grosor entre 0.04 y 0.09 pulgadas.

Son ampliamente utilizados en redes de telefonía y dentro de efificios.En telefonía permite conectar el terminal del abonado a la central local mediante el llamado **bucle de abonado** o **última milla**. 
Es el medio guiado de menor coste y mayor sencillez de manejo, pero está limitado respecto a la tasa de transmisión y a la distancia máxima.

El caso más común es el **par trenzado sin apantallar (UTP**, Unshielded Twisted Pair). Tiene 4 pares de cables. Características:

* Es el medio habitual en telefonía
* Es frecuente en el cableado de edificios
* Es el medio de menor coste en las LAN
* Es fácil de instalar y manipular
* Puede afectarle interferencias electromagnéticas externas, por pares cercanos y por fuentes de ruido.

Un cable menos común aunque se está usando ya bastante y en ambientes industriales es el **par trenzado apantallado (STP**, Shielded Twisted Pair). Características:

* Posee una malla metálica protectora que reduce las interferencias.
* Es más costoso y más difícil de manipular que el UTP. La malla debe estar conectada a la carcasa del conector RJ45, y éste a una toma de tierra.

El STP suele usarse en ambientes industriales por su mayor inmunidad al ruido externo que pueden producir máquinas de gran potencia eléctrica. Para redes normales se usa el UTP.

Hay cables con una cubierta para exterior preparada para la intemperie, especialmente para el sol.

En 1995 se propuso el estándar EIA-568-A que contempla avances en el diseño de cables y conectores. Se considera los pares de cables apantallados de 150 Ohmios y no apantallados de 100 Ohmios. El estandar considera los UTP:

1. Tipo 3: Cables y hardware asociado hasta 16MHz y 16Mbps.
2. Tipo 4: Cables y hardware asociado hasta 20MHz y 20Mbps.
3. Tipo 5: Cables y hardware asociado hasa 100MHz y 100Mbps.
4. Hay tipo 6, 7 ... Se puede buscar la evolución constante....

La diferencia entre los cables tipo 3 y 5 están en el número de tranas por unidad de distancia. Tipo 3 contiene una trenza cada 7 o 10 centímetros mientras que tipo 5 contiene 1 a 2 trenzas por centímetro. En el tipo 5 hay aislamiento de teflón.

![Tema1](/PAX/assets/img/tema1/Tema1_5.png)

La evolución de las categorías van cambienado, existe UTP 5e o 6 que transmiten a 100Mbps y 1Gbps a una distancia de 100m.

> Hay combinaciones de colores para los conectores RJ45. Si se pone el mismo estándar en los dos extremos hacemos un cable directo. Si se pone A en un extremo y B en el otro es un cable cruzado. El cable directo se usa para conectar una tarjeta de red con un dispositivo de red (switch). El cable cruzado para conectar dos tarjetas de red directamente. Ahora cada vez las tarjetas y switches admiten ambas configuracies. OJO con las instalaciones antiguas.

![Tema1](/PAX/assets/img/tema1/Tema1_7.png)

Los cables de categoría 7 llevan apantallamiento para cada par y un apantallamiento para los 4 pares. Así se puede obtener cada vez mayor inmunidad al ruido y mayor ancho de banda. Con categoría 6 se podría alcanzar 10Gbps en enlaces cortos.

Hasta tasas de 100Mbps se puede usar cables de categoría 5 y solo se usan 2 de los 4 pares que contienen. Para tasas mayores se usan los 4 pares de cables.

#### Cable Coaxial

Consiste en un conductor cilíndrico externo que rodea un cable conductor. El conductor interior se mantiene a lo largo del eje axial mediante una serie de anillos aislantes o mediante un sólido dieléctrico. El conductor exterior se cubre con una funda protectora. El diametro va desde 1 a 2.5 centímetros. Es menos susceptible a interferencias y diafonías que el par trenzado. Cubre mayores distancias. 

![Tema1](/PAX/assets/img/tema1/Tema1_8.png)

Se usa el coaxial para:
* Distribución de televisión.
Y tanto para transmitir señales analógicas como digitales. Ahora está llegando la conexión de fibra óptica alas casas y a veces se usa el coaxial entre la fibra y las viviendas.

#### Líneas eléctricas
Las líneas eléctricas pueden usarse como medio de transmisión además de proporcionar potencia eléctrica. Se pueden usar como redes metropolitanas en la red eléctrica o como redes de área local dentro de las casas. Se puede reaprovechar la infraestructura disponible. Su funcionamiento es usando una portadora sobre la que se modula la señal.

En las casas se puede usar como LAN pero el problema viene porque la instalación no está pensada para transmisión de datos y puede sufrir mucho ruido. En las casas puede llegar a tasas de 100Mbps. Hay dispositivos económicos que se conectan a los enfuches de la casa y proporcionan una salida de cable UTP para conectar ordenadores o dispositivos de red. Estos conversores reciben el nombre de **PLC** (Power Line Communication).


