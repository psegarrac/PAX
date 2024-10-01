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

#### Fibra Óptica
Es un medio flexible y fino capaz de conducir energía de naturaleza óptica. Su diámetro varía entre 2 y 125 micrómetros. Se puede construir con diversos tipos de vidreos y plásticos. El mejor material está hecho de fibras de silicio fundido ultra puro. Sin embargo, las fibras de cristal tienen mayores pérdidas, pero son más baratas. Las fibras de plástico tienen mayores pérdidas y menor coste, pro consigue distancias aceptables para distancias cortas (hasta 500 metros).

El principio de funcionamiento de la fibra óptica ensiste en ángulos de emisión de luz que se refleja internamente en la fibra (no existe refracción).
Se pueden usar diferentes ángulos de emisión para enviar varias señales simultáneamente (**fibra multimodo**) o fibras más estrechas en las que no hay rebotes y la luz viaja directamente (**fibras monomodo**).
Ahora mismo como los precios se acercan y las monomodo permiten distancias y anchos de banda mayores son las más usadas. Valores comunes son 100 Gbps a 100km sin amplificadores.

El cable de fibra óptica es cilíndrico y posee 3 secciones concéntricas: el núcleo, el revestimiento y la cubierta. El núcleo es la sección más interna y está constituido por una fibra de vidrio o plástico. Cada fibra está rodeada por su propio revestimiento también de vidrio o de plástico, con propiedades ópticas distintas de las del núcleo. La cubierta envuelve a uno o varios revestimientos y está hecha de plástico y otros materiales dispuestos por capas. En la figura de abajo se muestra una fibra individual y una funda con tres fibras. Una fibra se puede usar para comunicación unidireccional o bien bidireccional. En el segundo caso se emplean diferentes frecuencias en la señal para los dos sentidos.
En una manguera de fibra puede ir varias grupos de fibras. Por ejemplo 8 grupos de 8 fibras, lo que son 64 fibras individuales. Estos grupos luego pueden ir recubiertos por varias capas para darle resistencia y protección. Por ejemplo, resistencia mecánica a la tracción, resistencia a la intemperie o la humedad o incluso protección ante la presencia de roedores.

![Tema1](/PAX/assets/img/tema1/Tema1_9.png)

Es muy utilizada en las telecomunicaciones a larga distancia. Su costo es progresivamente menor y su continuo perfeccionamiento la hacen apropiada para entornos LAN (redes de área local). Las principales ventajas respecto del coaxial y par trenzado son:
* Mayor ancho de banda. De hecho actualmente el límite de tasa de envío se produce por la conversión de luz a señal eléctrica, no por ocupar el ancho de banda el medio.
*Menor tamaño y peso: la reducción de tamaño y peso para capacidades comparables es de 10 a 1.
*Atenuación menor: la atenuación es menor y constante en un gran intervalo de frecuencias.
*Aislamiento electromagnético: la fibra óptica no se ve afectada por los campos electromagnéticos exteriores. No es vulnerable a interferencias, ruido impulsivo ni diafonía, lo cual es una ventaja en entornos industriales.
*Mayor separación entre los repetidores: significa menor costo y menos fuentes de error. Se han conseguido 3.5 Gbps en distancias de 318 Kilómetros sin repetidores.
*El precio actualmente es atractivo frente al cobre.

Se utiliza para transmisiones de larga distancia y metropolitanas. Acceso a zonas rurales, LAN, etc. En telefonía de larga distancia los enlaces troncales tienen distancias medias de 1500 kilómetros, con capacidades de entre 20000 y 60000 canales de voz.
La tendencia es sustituir el bucle de abonado de par trenzado de cobre por fibra óptica hasta el hogar (FTTH, Fiber To The Home). Una familia de tecnologías para hacer estas conexiones es PON (Passive Optica Network), siendo GPON la que se está aplicando actualmente. 
La idea de PON es que con tecnologías pasivas (no tienen elementos activos, ni con lógica ni amplificadores u otros elementos electrónicos) conectan muchas viviendas o edificios a una fibra de salida. Esto se consigue con splitters o puentes ópticos. 
Con GPON los únicos elementos activos están en la centralita, el OLT (Optical Line Termination) y en la vivienda (o edificio si FTTB), que es el ONT (Optical Network Termination). Del OLT sale una fibra que puede ser dividida una primera vez hasta en 128 fibras y cada una de las 128 una segunda vez en 64 fibras. Saldrían 128×64=8192 viviendas a partir de una sola fibra de la centralita.
El OLT debe indentificar los ONT que tiene conectados para aplicar una multiplexación por división de tiempo y un cifrado porque todos los ONT reciben las comunicaciones de todos los demás. Se suele usar con una única fibra por ONT o vivienda y se usan frecuencias diferentes para subida y bajada de datos. De un OLT a un ONT solo se puede pasar por 2 puentes o splitters. Para dar una idea de distancias, se pueden alcanzar hasta 60km entre la centralita y la vivienda, pero normalmente esta distancia se suele limitar a una veintena de km. En todo caso hay que llevar un control de las distancias, soldaduras de fibra y fibras por puente para asegurarse de que a todos los ONT llega suficiente potencia de la señal.
### Medios de transmisión no guiados
#### Transmisión inalámbrica
En la transmisión inalámbrica, emisión y recepción se efectúa mediante antenas. En la emisión se radia energía electromagnética en el medio (generalmente aire). En la recepción se captan las ondas electromagnéticas del medio que rodea a la antena.

![Tema1](/PAX/assets/img/tema1/Tema1_10.png)

Las configuraciones de transmisión son:
* **Direccional**: la antena transmisora emite concentrando la energía electromagnética en un haz, Las antenas de emisión y de recepción deben estar alineadas
* **Omnidireccional**: la antena transmisora emite en todas direcciones con un diagrama de radiación disperso.

Es más sencillo confinar la energía en un haz direccional cuanto mayor es la frecuencia de la señal. Los rangos de frecuencias considerados son los siguientes:

* Microondas: comprende de los 2 a los 60 GHz. Los haces son altamente direccionales y apropiados para enlaces punto a punto. No atraviesan bien los edificios. También se utilizan para comunicaciones vía satélite. Cubren parte de la banda de UHF y totalmente la banda SHF.
* 
*Ondas de radio: comprende de los 30 MHz a 1 GHz. Son adecuadas para aplicaciones omnidireccionales. Cubren la banda VHF y parte de la banda UHF.

*Infrarrojos: comprende de los 3 x 1011 a los 2 x 1014 Hz. Son útiles para conexiones locales punto a punto o para multipunto en áreas muy limitadas. No atraviesan obstáculos por eso se usan en los telemandos y detección de presencia para alarmas.

*Microondas por satélite: un satélite de comunicaciones es básicamente una estación que retransmite microondas. Se utiliza como enlace entre dos o más receptores/transmisores terrestres llamados estaciones base. El modo de funcionamiento es el siguiente:
  El satélite recibe la señal de una banda de frecuencia llamada canal ascendente. La señal es amplificada o repetida a otra banda de frecuencia llamada canal descendente.
  Cada satélite operará en ciertas bandas de frecuencias llamadas transponders.
  Las configuraciones posibles son: punto a punto entre dos antenas terrestres. Enlace de difusión entre una estación base terrestre transmisora y un conjunto de receptores terrestres.

## Red Telefónica
La red telefónica pública conmutada fue diseñada hace años con el propósito de transmitir voz. Su aplicabilidad en las comunicaciones entre ordenadores es limitada, aunque esta situación ha cambiado gracias a las troncales de fibra óptica entre las centralitas y la tecnología digital. Para ver las diferencias con una red local, un cable entre dos computadoras puede transferir a 109 bps, mientras que una línea de acceso telefónico tiene una tasa máxima de 56 kbps, con lo que es casi 20000 veces más lento. En el caso de establecer una conexión ADSL, sigue habiendo una diferencia de un factor de 1000 a 2000 veces.

el sistema telefónico consiste en tres componentes principales:
* Circuitos locales (cables de par trenzado que van hacia las casas y las empresas).
* Troncales (fibra óptica que conecta a las oficinas de conmutación).
*  Oficinas de conmutación (donde las llamadas pasan de una troncal a otra).

>Los circuitos locales son los que llegan a las casas de los usuarios finales. Son la parte más débil del sistema. En el caso de la comunicación a través de troncales, la principal consideración es cómo reunir múltiples llamadas y enviarlas juntas por la misma fibra. Esta operación se llama multiplexión y existen diversas formas de hacerlo. El sistema es jerárquico de forma que para conectar dos usuarios que quieren hablar, se sube en la jerarquía y se baja hasta conectar con el otro extremo.
