# Diseño final del amplificador clase G

## Polarización

Los valores de polarización más significativos se pueden observar en la siguiente a continuación.

Estos valores se ajustaron para que el amplificador mantenga buenas carácterísticas.

| Componentes                      	| Valores  	|
|----------------------------------	|----------	|
| Fuente corriente par diferencial 	| 5.7 mA   	|
| Fuente corriente VAS             	| 18.2 mA  	|
| Multiplicador Vbe                	| 2.63 V   	|
| Corriente rama salida            	| 22.8 mA  	|
| Tensión salida                   	| 486 uV   	|

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/THD).*

## Total Harmonic Distorsion (THD)

En este caso se simuló a cuatro frecuencias, dos bajas y dos altas, y a dos valores de potencia, una la máxima 50w y otra a un 60% de la misma, 30w.

- C_comp = 30pF:

| Frecuencia [kHz]     	|     1     	|     2     	|     10    	|     20    	|
|----------------------	|:---------:	|:---------:	|:---------:	|:---------:	|
| Pot=50W (Vin=1.74Vp) 	| 0.001492% 	| 0.002958% 	| 0.005022% 	| 0.044571% 	|
| Pot=30W (Vin=1.27Vp) 	| 0.001541% 	| 0.003944% 	| 0.013176% 	| 0.017750% 	|

Podemos observar en la tabla una distorsión considerablemente baja en todo el rango de frecuencia para ambas potencias del amplificador.

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/THD).*

A continuación se encuentra una tabla alternativa que se simulo al usar un capacitor de compensación de 20pF. 
Aunque los valores de distorsión sean mejores el circuito presentaba un sobrepico fuerte en la respuesta al escalon.

- C_comp = 20pF:

| Frecuencia [kHz]     	|     1     	|     2     	|     10    	|     20    	|
|----------------------	|:---------:	|:---------:	|:---------:	|:---------:	|
| Pot=50W (Vin=1.74Vp) 	| 0.001425% 	| 0.002869% 	| 0.004304% 	| 0.030751% 	|
| Pot=30W (Vin=1.27Vp) 	| 0.001445% 	| 0.003932% 	| 0.012930% 	| 0.016209% 	|


## Impedancia de entrada

Se simuló la impedancia de entrada para un amplio rango de frecuencias. En el rango de audio 20Hz - 20kHz la impedancia de entrada es mayor a 12kOhms, siendo 14.4kOhms @1kHz en la zona llana. 

Justamente el anchod de banda del valor de la impedancia de entrada es de 20Hz a 20kHz.


- **Rin > 12kOhm @ 20hz-20kHz**

- **Rin = 14.4kOhm @ 1kHz**


<p align="center">
  <img src="../imagenes/Rin_def.png?raw=true" width="1000" title="hover text">
</p>



- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/Rin).*


## Sensibilidad

Siguiendo los valores típicos de sensibilidad para los equipos de [audio profesional](https://en.wikipedia.org/wiki/Line_level) se buscó que la máxima potencia sobre la carga, 50W, se dé cuando al tensión a la entrada es de Vin = 1.736Vp. Para tal fin se ajusto la ganancia total del circuito para que esta sea de 17.2 y con 1.736Vp obtengamos una tensión a la salida de 29.85Vp que representa 55.7W sobre la carga. Se le dió un margen de 10% al valor.


## Impedancia de salida

El valor de impedancia de salida se mantienenbajo para el ancho de frecuencia de audio con un valor de 1.16mOhm @1kHz. Al aumentar la frecuencia este valor aumenta llegando hasta 20mOhm @20kHz.

- **Rout = 1.16mOhm @ 1kHz**

- **Rout = 206mOhm @ 20kHz**


<p align="center">
  <img src="../imagenes/Rout_def.png?raw=true" width="1000" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/Rout).*


## Factor de amortiguamiento FA

Este factor se puede calcular a partir de la simulación de la impedancia de salida y de que el valor de la carga que vamos a usar es de 8 Ohms.

- **FA = 8 Ohm / 1.16mOhm =  6896 @ 1kHz**


## Slew rate

Se utilizó la siguiente simulación para el cálculo del Slew rate. Para tal motivo se excitó al circuito con un escalón de tensión y se midió el tiempo de crecimiento del 10% hasta el 90% del valor final que fue de 65ns.

- **Slew rate = ( 3.465V / 65ns) = 51.25 V/us**


<p align="center">
  <img src="../imagenes/slew_rate_def.png?raw=true" width="1000" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/SlewRate).*


## Transferencia y ancho de banda

Se simuló la transferencia. Está tiene una zona plana muy amplia con una ganancia de 24.7dB @ 1kHz que va desde los 1.3Hz hasta los 836kHz. Estos puntos están definidos por la caida de 3dB respecto de la ganancia en la zona plana.

- **BW = 1.3Hz - 836kHz **

- **Ganancia = 24.7dB (17.2 veces) @ 1kHz ** 

<p align="center">
  <img src="../imagenes/bandwidth_def.png?raw=true" width="1000" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/Bandwidth).*


## Protección contra cortocircuito a la salida

Se simuló un cortocircuito a la salida para poner a prueba la protección contra cortocircuito. Se lo hizo al poner en paralelo de la carga un resistor de 0.01 Ohms. Como se encuentra descrito en una [sección anterior](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/claseG_mejoras), la corriente de limitación esta fijada alrededor de 5A como se puede ver en la siguiente simulación:


<p align="center">
  <img src="../imagenes/proteccion_def.png?raw=true" width="1000" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/proteccion_corriente).*


## Eficiencia

Se calculó la eficiencia para diferentes valores de potencia. Luego se graficaron los valores obtenidos en las siguientes tablas.

| Potencia RL [W] 	|   0.1  	|  0.5  	|   1   	|   5   	| 10    	| 13    	|
|-----------------	|:------:	|:-----:	|:-----:	|:-----:	|-------	|-------	|
| Vin [V] @ 1kHz  	| 0.0735 	| 0.165 	|  0.23 	|  0.52 	| 0.735 	| 0.84  	|
| Vout [V] @ 1kHz 	|  1.265 	|  2.83 	|  4.0  	|  8.94 	| 12.65 	| 14.42 	|
| Pot Fuentes [W] 	| 4.13   	| 5.96  	| 7.29  	| 13.29 	| 28.57 	| 37.45 	|
| Eficiencia      	| 0.024  	| 0.085 	| 0.134 	| 0.377 	| 0.351 	| 0.349 	|

| Potencia RL [W] 	| 15    	| 17    	| 20    	| 25    	| 30    	| 40    	| 50    	|
|-----------------	|-------	|-------	|-------	|-------	|-------	|-------	|-------	|
| Vin [V] @ 1kHz  	| 0.90  	| 0.96  	| 1.04  	| 1.16  	| 1.27  	| 1.47  	| 1.64  	|
| Vout [V] @ 1kHz 	| 15.49 	| 16.49 	| 17.89 	| 20.0  	| 21.91 	| 25.30 	| 28.28 	|
| Pot Fuentes [W] 	| 41.82 	| 45.95 	| 51.21 	| 58.76 	| 65.46 	| 77.28 	| 87.09 	|
| Eficiencia      	| 0.359 	| 0.372 	| 0.392 	| 0.424 	| 0.457 	| 0.518 	| 0.573 	|

<p align="center">
  <img src="../imagenes/eficiencia_def.png?raw=true" width="1000" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](https://github.com/tobias-liaudat/ClassG_amp/tree/master/spice_models/Amplificador/Dise%C3%B1o%20final/Eficiencia).*

