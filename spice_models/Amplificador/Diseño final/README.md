# Diseño final del amplificador clase G




## Total Harmonic Distorsion (THD)

En este caso se simuló a cuatro frecuencias, dos bajas y dos altas, y a dos valores de potencia, una la máxima 50w y otra a un 60% de la misma, 30w.

- C_comp = 30pF:

| Frecuencia [kHz]     	|     1     	|     2     	|     10    	|     20    	|
|----------------------	|:---------:	|:---------:	|:---------:	|:---------:	|
| Pot=50W (Vin=1.74Vp) 	| 0.001492% 	| 0.002958% 	| 0.005022% 	| 0.044571% 	|
| Pot=30W (Vin=1.27Vp) 	| 0.001541% 	| 0.003944% 	| 0.013176% 	| 0.017750% 	|

Podemos observar en la tabla una distorsión considerablemente baja en todo el rango de frecuencia para ambas potencias del amplificador.

- *El circuito utilizado para la simulación se encuentra [aqui](LINK).*

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
  <img src="../imagenes/Rin_def.png?raw=true" width="300" title="hover text">
</p>



- *El circuito utilizado para la simulación se encuentra [aqui](LINK).*


## Impedancia de salida

El valor de impedancia de salida se mantienenbajo para el ancho de frecuencia de audio con un valor de 1.16mOhm @1kHz. Al aumentar la frecuencia este valor aumenta llegando hasta 20mOhm @20kHz.

- **Rout = 1.16mOhm @ 1kHz**

- **Rout = 206mOhm @ 20kHz**


<p align="center">
  <img src="../imagenes/Rout_def.png?raw=true" width="300" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](LINK).*


## Slew rate

Se utilizó la siguiente simulación para el cálculo del Slew rate. Para tal motivo se excitó al circuito con un escalón de tensión y se midió el tiempo de crecimiento del 10% hasta el 90% del valor final que fue de 65ns.

- ** Slew rate = ( 3.465V / 65ns) = 51.25 V/us**


<p align="center">
  <img src="../imagenes/slew_rate_def.png?raw=true" width="300" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](LINK).*


## Transferencia y ancho de banda

Se simuló la transferencia. Está tiene una zona plana muy amplia con una ganancia de 24.7dB @ 1kHz que va desde los 1.3Hz hasta los 836kHz. Estos puntos están definidos por la caida de 3dB respecto de la ganancia en la zona plana.

- ** BW = 1.3Hz - 836kHz **

- ** Ganancia = 24.7dB (17.2 veces) @ 1kHz ** 

<p align="center">
  <img src="../imagenes/bandwidth_def.png?raw=true" width="300" title="hover text">
</p>

- *El circuito utilizado para la simulación se encuentra [aqui](LINK).*




