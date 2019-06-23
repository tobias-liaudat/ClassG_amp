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


## Cálculo de disipadores

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

</td><td>

| Pot. Etapa Salida inf 	|   P   	|
|-----------------------	|:-----:	|
| Q21 (2SA1943) [W]     	| 25.65 	|
| Q20 (2SA1943) [W]     	| 18.34 	|
| Q15 (2SA1837) [W]     	|  1.36 	|
| Q17 (2SA1837) [W]     	| 0.31  	|

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
| Tj_MAX [C] 	|   150   	|   150   	|   150   	| 150     	|
| Rth_jc [C] 	|   0.84  	|   0.84  	|   6.25  	| 6.25    	|
| Rth_cd [C] 	|    2    	|    2    	|    2    	| 2       	|






