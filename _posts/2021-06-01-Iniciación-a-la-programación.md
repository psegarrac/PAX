---
typora-copy-images-to: ../assets/img/inicprog/
typora-root-url: ../../
layout: post
categories: tema0 Arquitectura de redes
title: Caracterización de las redes
subtitle: 
conToc: true
titlepage: true
titlepage-background: assets/inicprog/dibujo.png
page-background: assets/fondo-pagina.png
urlcolor: CornflowerBlue
linkcolor: black
toc-own-page: true
toc-title: Contenidos
header-left: UD 0. Arquitectura de redes
header-right: Arquitectura
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
# Redes de ordenadores
Gran número de ordenadores interconectados e interactuando, distribuidos físicamente. Las comunicaciones son prioritarias respecto a la potencia de cálculo. Las redes de ordenadores se preocupan de sistemas independientes, cada ordenador es independiente y con su propio sistema operativo. Para comunicarse un ordenador con otro se usa algún sistema de comunicaciones (hardware y software).

# Tipos de redes
Existen muchos criterios de clasificación. Por ejemplo una clasificación se basa en la transmisión de datos. De esta manera distinguimos entre redes punto a punto y redes de difusión (broadcast).

En las redes **punto a punto**  un mensaje se envía desde un ordenador a otro en una red. El envío puede ser directo (dos ordenadores conectados por un cable) o pueden pasar por routers o switches para establecer la comunicación.

En las redes de **difusión** un mensaje es recibido por todos los ordenadores de la red pero como se pone la dirección de destino, probablemente solo el destinatario tratará el mensaje. Una red Wifi es un ejemplo de difusión, al enviar el mensaje cualquiera puede captarlo. Es estas redes, normalmente hay una dirección especial para indicar que el mensaje se envía a todos los ordenadores. A esta acción se le llama **difusión** o **broadcasting**. Otra posibilidad es enviar un mensaje a un grupo de ordenadores. A esta acción se le llama **multidifusión** o **multicasting**.

Una siguiente clasificación se basa en la escala o tamaño geográfico de la red. Se puede diferenciar los siguientes tipos de red:

* Redes de área personal. Personal Area Network (**PAN**). Cubre distancias de pocos metros. Bluetooth.
* Redes de áreal local. Local Area Network (**LAN**) (de decenas de metros a km). Wifi, Ethernet por ejemplo. Suelen ser redes privadas de una casa o edificio. 
* Redes de área metropolitana, Metropolitan Area Network (**MAN**) (dececnas de km). Por ejemplo redes de televisión por cable.
* Redes de área amplia. Wide Area Network (**WAN**) (miles de Kms). La red de un proveedor de servicios de Internet (**ISP**).
* Redes de redes, interredes (**Internet**). Se trata de conjuntos de redes interconectadas. Proporcionan un direccionamiento uniforme a redes de diferentes tecnologías y diferentes propietarios. Permiten por ejemplo comunicar un teléfono móvil con un servidor web.

# Arquitecturas de red
Los sistemas de redes informáticas se estructura en **capas o niveles** para dividir un problema complejo en problemas más simples (Divide y vencerás). Las normas que organizan la comunicación son los **protocolos** de comunicación. Cada nivel en un punto de la red comunica con el nivel equivalente en la otra parte de la red.

Los protocolos de comunicación contienen el formato de los mensajes, los campos de los mismos, cómo actuar con estos campos, los permisos de comunicación y muchas más propiedades que veremos en detalle en el curso.

La **arquitectura de red** es el conjunto de niveles y protocolos en los que se organiza el sistema de comunicaciones

Un elemento de la red ofrece servicios a un nivel superior y usa los servicios del nivel inferior. El conjunto de funciones a través de las que se ofrecen esos servicios son las interfaces entre los niveles. El hecho de cumplir la misma arquitectura permitirá que los ordenadores con diferentes sistemas operativos (y diferentes implementaciones de la arquitectura de red) puedan comunicar.


![Arquitectura de Red](/PAX/assets/arquitecturaRed.png)

Las normas y formatos de comunicación en un nivel deben respetarse para que la comunicación sea posible. La arquitectura es un estándar para cumplir.
Cuando se envía un mensaje desde el nivel más alto - de aplicación - , el mensaje atraviesa la pila de protocolos desde el nivel de aplicación hasta la **codificación** de información aplicando modificaciones sobre un medio físico (por ejemplo modificaciones de voltaje). Al atravesar cada nivel, cada nivel añade información al mensaje para que sea interpretada por ese mismo nivel en el ordenador que recibe el mensaje. Esta información se añade en **cabeceras** pero en algunos casos se añaden campos al final del mensaje.
El formato de las cabeceras y la interpretación de sus campos se define en los protocolos del nivel respectivo.

Cuando se pasa un mensaje al nivel inferior es necesario a veces trocear el mensaje en varias partes. Los protocolos de ese nivel incluyen medidas para que no se pierdan datos ni se modifique el orden inicial.

![Arquitectura de Red](/PAX/assets/arquitecturaRed2.png)

En la recepción del mensaje se sigue el orden inverso. Desde el nivel del **medio físico** el mensaje va subiendo niveles hasta llegar a la aplicación a la que se destina el mensaje. En cada nivel se recupera, interpreta y elimina la cabecera que se trata en cada caso.

En comunicaciones que implican atravesar diferentes redes para llegar al destino, el mensaje puede retransmitirse muchas veces. En cada salto o envío debe atravesar los niveles de rede en los puntos intermedios. Por ejemplo, cuando se envía un mensaje por internet, el mensaje (hasta el nivel de los protocolos de internet) será tratado y reenviado por cada **encaminador** o **router**.

![Arquitectura de Red](/PAX/assets/arquitecturaRed3.png)

## Modelos de referencia

Hay dos arquitecturas de red que se suelen usar como modelos de referencia para comparar o entender arquitecturas de red: OSI (Open System Interconnexion) de ISO (International Standard Organization) y TCP/IP. La primera no se usa en la práctica pero se suele usar como referencia para comparar otras arquitecturas. TCP/IP es el modelo en uso, pero no describe bien todos los niveles.

## Modelo OSI

OSI es una arquitectura de red. En OSI hay 7 niveles, algunos son muy complejos.

![Arquitectura de Red](/PAX/assets/arquitecturaRed4.png)

La arquitectura de red OSI tiene los siguientes 7 niveles:

1. **Capa Física**. Cómo enviar datos sobre un medio físico.
2. **Capa de Enlace de Datos**. Cómo organizar el envío de datos sobre un canal de comunicación. Preparar los mensajes, fiabilidad, ajuste de velocidad entre emisor y receptor, organización de los turnos de comunicación.
3. **Capa de Red**. Direccionamiento y rutas para conectar diferentes redes y que puedan comunicar.
4. **Capa de Transporte**. Preparar flujos de datos en mensajes. Comunicación fiable entre dos puntos.
5. **Capa de Sesión**. Permisos y organización de la comunicación.
6. **Capa de Presentación**. Tratar estructuras abstractas de datos para que puedan ser interpretadas de igual manera en diferentes ordenadores.
7. **Capa de Aplicación**. Protocolos de las aplicaciones de los usuarios.

Este estándard no ha tenido éxito en la implementación.

## Modelo TCP/IP
Es el modelo que se ha difundido en la industria y es el más utilizado actualmente. Está definido desde un punto de vista práctico más que en un modelo bien estructurado y definido. Describe las capas de los niveles de red, transporte y aplicación de OSI. Por debajo de la capa de red indica que existen primitivas para enviar mensajes.

En este módulo usaremos un modelo de TCP/IP añadiendo una capa de enlace de datos y la capa física del modelo OSI. En definitiva veremos los niveles físico, enlace de datos, de red, de transporte y de aplicación.

## Esquema general de las redes

  ## Origen de Internet
  En 1950 se crea la red que se llamó **ARPANET** y la crea el **Departamento de Defensa** de los EEUU. El número de conexiones fué en aumento y rápidamente se fueron mejorando dorsales de interconexión., La evolución dió en lo que ahora es **Internet**

  ## Estructura actual

  ![Arquitectura de Red](/PAX/assets/arquitecturaRed6.png)

* **POP** Punto de presencia. Los datos son separados del sistema telefónico. También indica dónde un operador llega con su red y puede vender conexión a sus clientes.
* **ISP** Internet Service Provider. Hay diferentes niveles según las conexiones que tienen con otros operadores. Los operadores grandes (Tier I) poseen grandes redes con enlaces dorsales (**backbone**) que conectan países y continentes. Las redes ISPs forman **sistemas autónomos** (redes en las que se optimiza el encaminamiento y tiene un direccionamiento propio). Internet es la conexión de sistemas autónomos.
* **IXP** (Internet eXchange Point). Son lugares donde los ISP llegan con su red y se intercambian tráfico y direccionamiento. Si el acuerdo de intercambio es entre operadores de tamaño similar es gratuito y se llama **peering**. En cambio un operador pequeño puede contratar mediante pago a uno grande para conectar con el resto de Internet. 
* **IANA** (Internet Assigned Numbers Authority) es una organización repartida en regiones del mundo que va repartiendo **bloques de direcciones** de Internet. Cada sistema autónomo posee uno o varios bloques.
* **NAP** (Network Access Point). Las dorsales y redes de operadores llegan a **encaminadores** (routers) que conectan entre ellos con redes de alta velocidad. Los **sistemas autónomos** también se conectan con estas ubicaciones. Lo mismo que los IXP
* **Protocolos de encaminamiento**. Algoritmos para encontrar las rutas y las redes de forma **dinámica** tanto entre sistemas autónomos e internos a los sistemas autónomos.
  
  ## Estándares y unidades

    ## Estándares
    Con los estándares se consiguen que productos de diferentes marcas puedan comunicar entre sí. En las comunicaciones los estándares están destinados a los protocolos que son los que marcan cómo se hace l ainteracción entre los niveles de una arquitectura de red.

    Internamente no se tiene por qué saber cómo está hecho el producto, pero debe cumplir los estándares. Hay estándares que se imponen en el mercado por su uso. Otros estándares se desarrollan en grupos o comités de expertos. En los comités puede haber representantes de gobiernos y generalmente los estándares deben ser de obligado cumplimiento. 
    Algunos grupos que revisan y proponen estándares en el mundo de las telecomunicaciones e Internet:
    * **ITU** (International Telecommunication Union). Es un organismo internacional adscrito a la ONU con representantes de muchos países, fabricantes y empresas de telecomunicaciones. Se encargan de proponer estándares para sistemas de telefonía y comunicaciones de datos.
    * **ISO** (International Standards Organization). Propone estándares internacionales para multitud de áreas. 
    * **NIST** (National Institute of Standars and Technology). Es parte del Departamente de  comercio de EEUU.
    * **IEEE** (Institute of Electrical and Electronics Engineers). Se trata de la mayor organización de profesionales a nivel mundial. El comité 802 se encarga de proponer estándares para la mayor parte de redes de área local. El grupo de trabajo 802.3 se encarga de las redes Ethernet y el 802.11 de las redes Wifi.
    * **W3C** (World Wide Web Consortium). Es un consorcio de industriales que se encarga de protocolos y guías para la web.

      ##Estándares de Internet
      A partir de los RFC, el ITF propone los estándares para Internet. Un RFC es un documento técnico donde se describe un problema o un nuevo sistema y se describe además cómo debe resolverse o qué debe cumplir una implementacñon.
      Los RFC se pueden consultar en www.left.org/rfc

    


  






  






