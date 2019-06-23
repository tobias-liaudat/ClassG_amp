# Ajustes al diseño 

En esta sección vamos a realizar algunos ajustes para que el amplificador pueda trabajar con tres tensiones de alimentación distintas. Esto es, la tensión del riel superior de alimentación podría ser tanto 30v, 40v o 50v (utilizando como riel inferior el mismo valor con distinto signo) pudiendo entregarle distintas potencias a la carga de 8 Ohms.

En la tabla siguiente se pueden ver varias características del amplificador para los tres distintos modos de funcionamiento en función de la tensión de alimentación de los rieles superiores. En todos los casos los rieles inferiores se mantuvieron en +15v y -15v.

| VCC sup.[V] 	|   30  	|   40  	|  50  	|
|-------------	|:-----:	|:-----:	|:----:	|
| Ganancia     	|  23.9 	|   31  	|  39  	|
| Po(max) [W] 	|   35  	|   60  	|  95  	|
| R_FB [Ohm]  	| 53.74 	| 27.72 	| 10.6 	|
| R_Vbe [Ohm] 	| 300   	| 300   	| 220  	|

Se utilizaron dos potenciómetros para poder ajustar los valores del multiplicador de Vbe y de la ganancia del amplificador para cada caso de tensión de alimentación.


## Disipadores

### Potencias en los transistores

Para el cálculo de disipadores vamos a cosiderar el caso más exigido, es decir cuando estamos trabajando con una VCC de 50v y a máxima potencia, 95W sobre la carga. 

Se utiliza el programa LTSpice que permite mediante los comandos *.meas* realizar cálculos con los valores simulados. De esta manera podemos integrar en varios períodos, el producto corriente tensión para varios transistores trabajando a máxima potencia. La siguiente tabla resume los valores obtenidos:

<table>
<tr><th> Potencia salida NPN </th><th> Potencia salida PNP </th></tr> 
<tr><td>
  
| Pot. Etapa Salida sup 	|   P  	|
|-----------------------	|:----:	|
| Q18 (2SC5200) [W]     	| 27.5 	|
| Q19 (2SC5200) [W]     	| 15.9 	|
| Q14 (2SC4793) [W]     	| 1.15 	|
| Q16 (2SC4793) [W]     	| 0.28 	|
| Total [W]               | 44.83 |

</td><td>

| Pot. Etapa Salida inf 	|   P   	|
|-----------------------	|:-----:	|
| Q21 (2SA1943) [W]     	| 25.65 	|
| Q20 (2SA1943) [W]     	| 18.34 	|
| Q15 (2SA1837) [W]     	| 1.36 	  |
| Q17 (2SA1837) [W]     	| 0.31  	|
| Total [W]               | 45.6    |

</td></tr> </table>


<table>
<tr><th> VAS </th><th> Mult. Vbe </th></tr> 
<tr><td>
  
| Pot. VAS          	|   P  	|
|-------------------	|:----:	|
| Q7 (2SA1837) [W]  	| 0.84 	|
| Q11 (2SC4793) [W] 	| 0.79 	|

</td><td>
  
| Pot. Mult Vbe    	|   P   	|
|------------------	|:-----:	|
| Q8 (2SC4793) [W] 	| 0.067 	|

</td></tr> </table>


A continuación se presentan las características de las hojas de datos de los componentes comprometidos con la disipación de potencia.

| Transistor 	| 2SC5200 	| 2SA1943 	| 2SC4793 	| 2SA1837 	|
|------------	|:-------:	|:-------:	|:-------:	|---------	|
| Tj_MAX [℃] 	|   150   	|   150   	|   150   	| 150     	|
| Rth_jc [℃/W] 	|   0.84  	|   0.84  	|   6.25  	| 6.25    	|
| Rth_cd [℃/W] 	|    2    	|    2    	|    2    	| 2       	|

En todos los casos consideramos que la resistencia térmica entre la capsula y el disipador (Rth_cd) tiene el mismo valor que es uno típico. 

### Cálculo de disipadores

Para calcular el valor de los disipadores y ver si es que realmente necesitamos de ellos vamos a tener que realizar los circuitos térmicos correspondientes. Se realizaran con cada transistor en paralelo como una fuente de corriente de potencia o una fuente de tensión de temperatura seguido por dos resistencias térmicas, Rth_jc (juntura-capsula) y Rth_cd (capsula-disipador). Luego, todas las potencias iran hacia el disipador donde se encuentren montados los transistores, que tendrá una única Rth_da (disipador-ambiente). Un caso simple con dos transistores montados sobre el mismo disipador se puede observar en la figura siguiente:

<p align="center">
  <img src="../imagenes/circuito_termico.png?raw=true" width="750" title="hover text">
</p>

Dadas las potencias que estamos considerando y visto que no deseamos utilizar ventilación forzada vamos a utilizar dos disipadores, uno para la etapa superior de salida y otro para la etapa inferior. El transistor del multiplicador de Vbe tiene que estar acoplado termicamente a la etapa de salida superior. No es necesario utilizar disipadores para los transistores de la etapa VAS (amplificación de tensión).

Vamos a analizar el aumento de temperatura debido a *Rth_jc + Rth_cd* para cada transistor:

<table>
<tr><th> Temperatura Etapa Salida Sup. </th><th> Temperatura Etapa Salida Inf. </th></tr> 
<tr><td>
  
| P_Q*(Rth_jc + Rth_cd) 	| Delta T	|
|-----------------------	|:----:	|
| Q18 (2SC5200) [℃]     	| 78.1 	|
| Q19 (2SC5200) [℃]     	| 45.16 	|
| Q14 (2SC4793) [℃]     	| 9.5 	|
| Q16 (2SC4793) [℃]     	| 2.31 	|
| Q8 (2SC4793) [℃]     	| 0.56 	|

</td><td>

| P_Q*(Rth_jc + Rth_cd) 	|   Delta T   	|
|-----------------------	|:-----:	|
| Q21 (2SA1943) [W]     	| 72.85 	|
| Q20 (2SA1943) [W]     	| 52.1 	|
| Q15 (2SA1837) [W]     	| 11.22 	  |
| Q17 (2SA1837) [W]     	| 2.56  	|


</td></tr> </table>

Vamos a considerar que la temperatura ambiente es de 25℃. Para calcular la Rth_da mínima que requerirá cada grupo de componentes hacemos:


Rth_da1_min = (Tj_max - Delta T1_max - Ta) / (Ptot1) = (150℃ - 78.1℃ - 25℃) / 44.9W = 1.05 ℃/W



Rth_da2_min = (Tj_max - Delta T2_max - Ta) / (Ptot2) = (150℃ - 72.85℃ - 25℃) / 45.6W = 1.15 ℃/W


En ambos casos necesitamos disipadores. No se mostró pero no es posible usar disipadores comerciales sin ventilación forzada para evacuar el calor si colocásemos todos los transistores sobre el mismo disipador.


### Elección del disipador

Para elegir el disipador vamos a buscar en los catalogos comerciales, como [este](https://www.disipadores.com/) que tiene una lista extensa de disipadores con sus respectivas dimensiones y sus respectivas resistencias térmicas.

En nuestro caso vamos a usar el **ZD-2K** de 75mm que tiene una Rth_da de **0.92℃/W**. Las dimensiones son de **145mm x 50mm x 75mm** (ancho x largo aletas x alto).


En la siguiente figura se puede observar una imagen del disipador elegido:

<p align="center">
  <img src="../imagenes/disipador.png?raw=true" width="400" title="hover text">
</p>










