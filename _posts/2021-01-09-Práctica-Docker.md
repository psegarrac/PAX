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
´´´
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

El funcionamiento del algoritmo de Dijstra es el siguiente. La primera figura (a) se muestran los pesos de los enlaces. El algoritmo actúa en iteraciones. Los nodos se etiquetan con el coste para llegar desde el origen a cada nodo Estas etiquetas pueden ser tentativas o definitivas (inicialmente el coste para llegar a cualquier nodo es infinito). En cada iteración se eligen el nodo con el menor coste tentativo, se pone como definitivo y se actualizan los costes de los vecinos de ese nodo.
En cada fase el algoritmo realiza:
1. Se elige el siguiente nodo a tratar. El que tenga menor peso o distancia y no esté etiquetado como definitivo (no tratado antes en el algortimo).
2. Se actualizan las etiquetas de distancia pasando por el nodo que se está tratando.
   
## Algoritmos de inundación

El algoritmo de inundación (flooding) consiste en que cuando se recibe un mensaje se envía por todas las líneas menos por la que se ha recibido.

El algoritmo es óptimo en número de saltos ya que incluyen todas las rutas posibles. Pero es ineficaz por la cantidad de mensajes que genera.

Hay que tener cuidado con una red que tiene ciclos ya que los envíos no pararían nunca. Una solución es poner un contador a un valor igual o superior al diámetro de la red y decrementarlo en cada envío. Si llega un mensaje con el contador a 0 ya no se sigue propagando.

Otra posibilidad es usar números de secuencia. Cuando se inicia una inundación se le añade un número de secuencia a los mensajes. Cuando se reenvía un mensaje, se anota el origen y el número de secuencia. Si se vuelve a recibir el mismo par origen, número de secuencia, ya no se sigue reenviando. Si cada origen usa números de secuencia consecutivos, para cada origen sería suficiente anotar la última difusión en la que se ha participado si todos los números anteriores ya han sido propagados.

Una mejora es la **inundación selectiva**. En este caso los mensajes no se envían por todas las líneas sino por las que se tiene algún indicio de que van en la dirección apropiada (por ejemplo, por las que le llegan antes mensajes del destino).
Dos características de este algoritmo son muy deseables: incluye las rutas óptimas y es muy fiable. Aunque caiga parte de la red, si el destino es alcanzable, le llegarán los mensajes.
No se usa como método de encaminamiento aislado por su gran consumo de recursos, pero sí que forma parte de alguno de los pasos de otros algoritmos de encaminamiento.

## Enrutamiento por vector distancia
Se conoce también como **algoritmo de enrutamiento de Bellman-Ford**. 
Es un algoritmo de encaminamiento dinámico que se usó inicialmente en **ARPANET**.

Los pasos son los siguientes:
1. Cada router descubre a sus vecinos directos y evalúa el coste del enlace. La distancia o coste podría ser simplemente el número de saltos, pero podrían ser otros valores. Por ejemplo, se podría estimar el retardo de un enlace enviando un ping y viendo lo que cuesta en responder (esto es la métrica utilizada). En este proceso los dos vecinos aprenden la dirección del otro.
2. Se rellena una tabla con los destinos conocidos, la línea del siguiente salto para alcanzar ese destino y el coste estimado (inicialmente aparecerán los vecinos directos y el coste medido).
3. Periódicamente se envían los vectores de distancias que contienen los destinos conocidos por el router y el coste estimado para llegar. Es un resumen de tabla de rutas.
4. Cuando un router recibe los vectores de distancias de los vecinos:
* Para cada destino que aparece en los vectores, calcula el mínimo del coste al vecino respectivo más la distancia que nos anuncia ese vecino.
* Ese mínimo se incorpora a la tabla de rutas. 

![Tema2](/PAX/assets/tema2_4.png) 

En la figura anterior se muestra un ejemplo. El router J recibe los vectores de distancia de sus vecinos (A, I, H, K). Las distancias respectivas medidas por J son 8, 10, 12 y 6. Ahora para los vectores que recibe, para cada destino suma la distancia del vecino con el coste que le promete ese vecino.
Por ejemplo: para llegar a D, debe calcular el mínimo entre: 40+8=48, 27+10=37, 8+12=20 y 24+6=30. Decide que la mejor ruta es enviar el siguiente salto a H y el coste para llegar a ese destino es 20.

La métrica con la que se miden la distancia a cada vecino podría calcularse en base a varios parámetros. Por ejemplo:
* Retardo.
* Carga que hay en esa línea. Por ejemplo incluyendo el tiempo en cola para la medición.
* Ancho de banda.
* Tasa de fallos.

`````
Un ejemplo es el protocolo **RIP** (Routing Information Protocol). La métrica usada en este protocolo es el número de saltos.

`````
Con una métrica pobre se puede liar mucho. 

`````
Imaginemos 3 routers (A, B y C). A-B y B-C conectados por 1Gbps ethernet y A-C conectados por una línea de 50Kbps. Para enviar mensajes de A a C RIP elegiría la línea directa (un salto) cuando es una decisión catastrófica porque es mejor enviar a través de B (dos saltos).

`````
### Problema de la cuenta hasta infinito

Los protocolos de vector de distancia tienen un problema de convergencia. 
Por **convergencia** se entiende que si una red no sufre cambios, el algoritmo debería tender (converger) a la solución óptima. Cuanto más se aproxime a la solución óptima y lo haga en menor tiempo, mejor es el algoritmo.

![Tema2](/PAX/assets/tema2_5.png)

En la figura anterior se muestra este defecto. En la parte (a) se añade un nuevo router, A, y después de 4 intercambios de vectores de distancia, los cuatro routers (B, C, D y E) aprenden su presencia y el coste para llegar. El algoritmo ha funcionado bien.
En cambio si el cambio es al revés (se cae el enlace hacia A y este router ya no es alcanzable), resulta que al intercambiarse vectores de distancia, los routers creen que pueden llegar a A y van engañándose unos a otros aumentando cada vez la distancia. Es decir que ante este cambio, el algoritmo diverge.
El algoritmo pararía al alcanzar un concepto de infinito. Por ejemplo sobrepasar el diámetro conocido de la red. Pero tarda en darse cuenta. 
Se han propuesto algunas soluciones a este problema para mejorar el tiempo de reacción pero ninguna es óptima para todos los casos.

## Enrutamiento por estado de enlace
Es la otra gran familia de protocolos de encaminamiento dentro de sistemas autónomos. Los sistemas autónomos, vienen a ser redes de empresas o instituciones que tienen bloques de direcciones asignadas y buscan las mejores rutas dentro de su red.
En gran medida estos algoritmos sustituyeron en Internet a los de vector de distancia por el problema de la cuenta a infinito que éstos sufren, pero se siguen usando protocolos de los dos tipos porque para redes de pequeño tamaño los protocolos de vector de distancia son más fáciles de configurar.
Ejemplos de protocolos de estado de enlace: OSPF (Open Short Path First) e IS-IS (Intermediate System - Intermediate System).
Para decidir cambios de rutas, los dos tipos de algoritmos, de vector de distancia o de estado de enlace, podrían trabajar periódicamente o en los momentos en los que se detectan cambios en la red. En cambio, los primeros suelen enviar los vectores de distancia periódicamente, mientras que los segundos suelen reaccionar cuando detectan cambios en la red.
Los pasos de estos algoritmos son los siguientes:
    1. Descubrir los vecinos directos.
    2. Medir el coste para cada uno de los vecinos.
    3. Construir un mensaje que indique los vecinos y los costes.
    4. Difundir el mensaje con los vecinos.
    5. Con los mensajes que se recibe de los demás encaminadores se conoce la topología de la red. Cada nodo calcula su árbol sumidero (las mejores rutas a cada destino).
Cada uno de los pasos anteriores tiene sus particularidades.

### Descubrimiento de vecinos
Se envía un mensaje de capa 2 por cada conexión que tenga un router. En ese mensaje de **hello** el router se identifica y espera respuesta. Con esto detecta a todos sus vecinos directos. Este descubrimiento se suele hacer periódicamente (por ejemplo cada 30 segundos) para detectar cambios en la red (nuevas conexiones, nuevos vecinos, o desapariciones).
Un caso especial es cuando un router está conectado a la misma LAN que otros routers. En ese caso tendría varios vecinos en la misma conexión. Entonces se enviarían mensajes entre todos ellos (todas las combinaciones de pares). Una solución es considerar la LAN como un nodo ficticio como se muestra en la figura siguiente.

![Tema2](/PAX/assets/tema2_6.png)

Para tratar este problema, algunas implementaciones de este tipo de algoritmos eligen un router designado para que actúe como el nodo N de la figura. De esta forma los otros intercambian información con el router designado y no tienen que hacer todos los intercambios por pares.

### Coste del enlace
Lo deseable sería que el coste del enlace resultase de la combinación de una serie de factores y que además éstos se fuesen comprobando periódicamente. Por ejemplo:
* Retardo. Se puede enviar un ping y ver lo que tarda en llegar la respuesta.
* Ancho de banda. Se puede enviar una ráfaga de datos de forma intensa y estimar cuándo se empiezan a perder mensajes.
* La carga de la línea. En este caso en la medición usando una especie de ping se incluiría los tiempos en colas del router. Cuanta más carga, pasará más tiempo encolado.
* Fiabilidad. 

Si la carga se tiene en cuenta en la **métrica** hay que tener en cuenta que no lleve a situaciones de **inestabilidad**. Esto puede ocurrir si de forma continuada se va cambiando dos posibles rutas. Cuando se elige una, luego aparecerá cargada. En la siguiente medición se cambia a la otra y así irán cambiando continuamente.

En la realidad, muchas implementaciones no hace mediciones reales y utilizan métodos **administrativos**. Por ejemplo, en **OSPF** lo más común es usar como coste de un enlace a un valor inversamente proporcional del ancho de banda del dispositivo de red. Por ejemplo, se puede usa 108/ancho. Esto daría una valor 1 a una tarjeta fastehernet (100Mbps), y 0.1 a una Gbps. Pero estos valores no se extraen de una medición real.

Hay algoritmos que pueden equilibrar tráfico entre varias rutas del mismo coste (para evitar la inestabilidad).

### Mensajes de estado de enlace
En los mensajes de estado de enlace se resume los vecinos de cada router y el coste que ha medido hasta ese vecino. En los mensajes se añaden campos con edad (para que caduquen) y número de secuencia para tener información actualizada y no verse afectado por las **inundaciones** que se hacen de estos mensajes. La edad se va decrementando en cada re-envío y cuando el valor sea cero los routers dejarían de difundirlo.