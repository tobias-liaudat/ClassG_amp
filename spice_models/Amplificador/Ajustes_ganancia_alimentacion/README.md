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


