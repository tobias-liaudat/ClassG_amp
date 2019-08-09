# Buck converter

La topología elegida sirve para reducir tensiones, es decir que la tensión de salida sea menor a la de entrada. El esqumático del circuito elegido es el siguiente:

<p align="center">
  <img src="imgs/buck_schema.jpg?raw=true" width="1000" title="hover text">
</p>

En este circuito se pueden identificar varias partes, los elementos principales de la fuente conmutada y elementos accesorios.

### Elementos esenciales

Para realizar la fuente, se debe elegir entre varios controladores por modulación de ancho de pulso para poder controlar las llaves y regular la tensión en un valor constante. En el mercado se encuentran varios modelos de controladores como el TL494 o el UC3843 que ya tienen trayectoria y son de bajo costo (~ USD 0.5). Sin embargo, no se encuentran modelos de SPICE oficiales para poder simular estos integrados, y además se deben complementar con un transistor de potencia que actúe como una de las llaves de la fuente de switching.

También existen otros integrados que incluyen a la llave de potencia como el LM2576-ADJ que puede ajustarse la realimentación para elegir la tensión de salida y esta diseñado para construir fuentes de switching reductoras como la topología buck. El precio no es tan elevado (~ USD 1.2) y puede manejar hasta 3A a la salida. El fabricante proporciona un modelo de SPICE del integrado que funciona bien, es decir con un tiempo de simulación acpetable. Por lo tanto, se decidió elegir al LM2576-ADJ como controlador. 

En este controlador la frecuencia de oscilación esta fijada en 52kHz y además incluye una protección que reduce la frecuencia a 11kHz cuando la corriente que se le pide al integrada es mucha y supera cierto valor. Esto es útil para limitar la corriente en el transitorio de encendido además de servir como una limitación contra un cortocircuito a la salida.

El modelo del diodo Schottky de conmutación se eligió teniendo en cuenta la simulación realizada para ver cuanta corriente debía soportar. Se sobredimensionó al elelgir el MUR820. El capacitor de entrada se eligió teniendo en cuenta la recomendación de la hoja de datos del LM2576-ADJ, y el capacitor de salida se ajusto según considerando el ripple a la salida y siguiendo lo detallado en la hoja de datos del controlador.

Los demas elementos de la fuente y su diseño se analizará a continuación.


### Elementos accesorios

En esta parte se encuentra un circuito de protección contra un baja tensión a la entrada. La tensión elegida fue de 18V que justamente es la tensión del diodo Zener 1N4746A presente en el circuito. Si la tensión es inferior a 18v el diodo Zener se encuentra en inversa y el transistor se despolariza, cambiando la tensión del pin ON/OFF del LM2576-ADJ apagandolo.

Luego, se incluyo un led indicador que se prende cuando la fuente esta encendida.

Finalmente, se incluyo una carga resistiva propia a la fuente para que no trabaje en vacio, y un fusible de protección a la salida. Este puede intercambiarse facilmente, son de bajo costo y se puede elegir el valor del fusible que se desee utilizar.


## Simulación

El circuito utilizado para la simulación es el siguiente y puede encontrarse en el siguiente [enlace](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Fuente%20SW/fuente_positiva/simulacion).

<p align="center">
  <img src="imgs/fuente_positiva.png?raw=true" width="1000" title="hover text">
</p>

El modo de operación elegido fue el discontinuo. La razón es que esta fuente se encontrara con la necesidad de estar sin entragar corriente por momentos, el caso en donde no hay señal a la entrada, ya que la polarización del amplificador proviene de los rieles superiores. Luego cuando el amplificador se encuentre funcionando, la fuente deberá entregar corriente solo en los momentos en que la señal de salida esté por debajo del valor de salida de la fuente, es decir 15V. Por lo tanto deberá entregar corriente por cortos periodos de tiempo para luego trabajar en vacio y repetir este ciclo. Se considero al modo discontinuo mejor adaptado para trabajar con una variación de carga de este tipo.

Este modo hace que el inductor requerido por la fuente sea menor, aunque va a exigir pico de corriente mayor.

En el siguiente grafico puede verse una simulación de la fuente operando primero en 'vacio' (con la carga interna de 330 Ohms) y luego con una carga de aproximadamente 2.4 A de media con una senoidal montada de 0.5A de amplitud. Se puede observar que no presenta ningún inconveniente para la fuente diseñada.

<p align="center">
  <img src="imgs/simulacion_fuente_pos.png?raw=true" width="1000" title="hover text">
</p>

## Diseño del inductor

El inductor requerido debe ser de **30uH**. Se eligió este valor para que la fuente opere en modo discontinuo en todo el rango de operación. Para el diseño del inductor es importante realizar los cálculos para que este pueda soportar la corriente de la fuente sin saturarse. Para el diseño se siguieron los pasos especificados en el libro:

- *Sistemas de Alimentación Conmutados, de J. Luis Muñoz Sáez y S. Hernández González.*

Primero realizamos algunas especificaiones de la fuente que necesitamos para el diseño del inductor:

|        Parámetros de diseño        	|     Valor     	|
|:----------------------------------:	|:-------------:	|
|             Inductancia            	|      30uH     	|
|       Modo de funcionamiento       	|  Discontinuo  	|
|         Tensión de entrada         	|      +30V     	|
|          Tensión de salida         	|      +15V     	|
|                 Fs                 	|     52kHz     	|
|   Imp (corriente máxima pulsante)  	|      5.8A     	|
| Ie_max (corriente efectiva máxima) 	|      2.0A     	|
|             Delta_Temp             	| 40°C (típico) 	|
|             K = K_u K_p            	|  0.7 (típico) 	|
|               Delta_I              	|      5.8A     	|


Lo primero que hay que hacer es calcular el PA (Producto Area) que es justamente el producto del Ae (Area efectiva) y del Aw (Area de la ventana). Para esto existen dos fórmulas, que depende de si el tamaño del núcleo estará limitado por la saturación del mismo o por las pérdidas en el núcleo. Normalmente se utiliza la primera expresión si la operación es en modo continuo y a una frecuencia inferior a 500kHz, la segunda expresión se utiliza para el funcionamiento en modo discontinuo o caso de que la frecuencia de operación supere los 500kHz.

- Modo continuo:

<p align="center">
  <img src="imgs/PA_1.png?raw=true" width="400" title="hover text">
</p>

- Modo discontinuo:

<p align="center">
  <img src="imgs/PA_2.png?raw=true" width="400" title="hover text">
</p>

Una buena técnica de diseño consiste en calcular ambas expresiones y elegir el valor más grande. Al realizar el cálculo obtenemos:

- PA = 2376 mm4

Con este valor y conociendo la frecuencia de operación podemos hacer una elección provisora del núcleo en el fábricante de nucleos de ferrite que tengamos disponible. En nuestro caso, es el distribuidor [elemon](http://www.elemon.net/) que comercializa núcleos de distintos fabricantes.

Vamos a sobredimensionar el núcleo por protección. Primero se había seleccionado el núcleo E25/10/07 pero como no había stock se seleccionó el núcleo de ferrite **EER2811A** de material **CF196** del fabricante [Cosmo Ferrites](http://www.cosmoferrites.com/). En su página se encuentra las características del material como así las dimensiones del núcleo. 

A continuación se extrae del catálogo los extractos que describen al núcleo elegido:


### Material: CF196

<p align="center">
  <img src="imgs/material.png?raw=true" width="1000" title="hover text">
</p>


### Forma: EER2811A

<p align="center">
  <img src="imgs/cosmo_parameters.png?raw=true" width="1000" title="hover text">
</p>


Del catálogo podemos extraer el valor de PA y también el valor de B_max del material.

- **PA = 8938 mm4**

- **B_max = 400mT @ 100°C**

Vamos a tomar un coeficiente de seguridad de 0.6 y establer que B_max_ef = 0.6 B_max = 240mT para los cálculos siguientes de número de espiras, largo del entrehierro y diametro del conductor.

#### Número de espiras

Para la determinación del número de espiras se utiliza la fórmula presente en la bibliografía mencionada que viene de una deducción de distintas ecuaciones.

<p align="center">
  <img src="imgs/n_min.png?raw=true" width="200" title="hover text">
</p>

Reemplazando con nuestros valores obtenemos:

- **N_min = 8.84 --> 9**

#### Longitud de entrehierro

Para la longitud del entrehierro se utiliza la formula siguiente donde *ur* es 1 ya que en el entrehierro habrá aire. *N* es el número de espiras que se calculó previamente.

<p align="center">
  <img src="imgs/l_eh.png?raw=true" width="200" title="hover text">
</p>

Al reemplazar los valores obtenemos:

- **L_eh = 0.27mm**

#### Diametro del conductor

Utilizaremos las siguientes fórmulas donde reemplazaremos con nuestros valores. Luego de determinar el area de la sección del conductor realizamos una simple cuenta que vincula el área de una circunferencia con su diámetro.


<p align="center">
  <img src="imgs/AC_max.png?raw=true" width="200" title="hover text">
</p>


<p align="center">
  <img src="imgs/J_max.png?raw=true" width="400" title="hover text">
</p>

El valor obtenido es:

- **D_c = 0.931 mm**


## Construcción del inductor

El alambre de cobre fue proporcionado por un amigo. Como este es de 0.7mm de diámetro y necesitamos de un diámetro mayor se decidió de trenzar el alambre para poder cumplir la condición planteada. Al ser una inductancia pequeña no es necesario muchas vueltas por lo que el espacio proporcionado por el nucleo alcanzará para poder construirlo.

Como comercialmente no se encuentra cualquier valor de entrehierro, se tomó una logitud de 0.5mm que se encontraba disponible por el fabricante.

### Núcleo de ferrite

<p align="center">
  <img src="imgs/EER2811A.JPG?raw=true" width="200" title="hover text">
</p>

### Carrete horizontal

<p align="center">
  <img src="imgs/carrete_inductor.JPG?raw=true" width="200" title="hover text">
</p>

### Yugo plástico

<p align="center">
  <img src="imgs/yugo_inductor.JPG?raw=true" width="200" title="hover text">
</p>

### Alambre de cobre esmaltado

<p align="center">
  <img src="imgs/alambre_cobre.png?raw=true" width="200" title="hover text">
</p>


### Inductor contruido

<p align="center">
  <img src="imgs/inductor_positivo.png?raw=true" width="300" title="hover text">
</p>

### Medición de la inductancia

<p align="center">
  <img src="imgs/inductor_pos.jpg?raw=true" width="400" title="hover text">
</p>




