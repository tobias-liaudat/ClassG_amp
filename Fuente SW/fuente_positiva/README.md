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

Los demas elementos de la fuente y su diseño se analizará a continuación.


### Elementos accesorios

En esta parte se encuentra un circuito de protección contra un baja tensión a la entrada. La tensión elegida fue de 18V que justamente es la tensión del diodo Zener 1N4746A presente en el circuito. Si la tensión es inferior a 18v el diodo Zener se encuentra en inversa y el transistor se despolariza, cambiando la tensión del pin ON/OFF del LM2576-ADJ apagandolo.

Luego, se incluyo un led indicador que se prende cuando la fuente esta encendida.

Finalmente, se incluyo una carga resistiva propia a la fuente para que no trabaje en vacio, y un fusible de protección a la salida. Este puede intercambiarse facilmente, son de bajo costo y se puede elegir el valor del fusible que se desee utilizar.


## Simulación

El circuito utilizado para la simulación es el siguiente y puede encontrarse en el siguiente [enlace](enlace).


<p align="center">
  <img src="imgs/fuente_positiva.png?raw=true" width="1000" title="hover text">
</p>


<p align="center">
  <img src="imgs/simulacion_fuente_pos.jpg?raw=true" width="1000" title="hover text">
</p>











