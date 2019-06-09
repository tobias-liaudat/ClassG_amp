# Diseño final del amplificador clase G




## Total Harmonic Distorsion (THD)

En este caso se simuló a cuatro frecuencias, dos bajas y dos altas, y a dos valores de potencia, una la máxima 50w y otra a un 60% de la misma, 30w.


| Frecuencia [kHz]     	|     1     	|     2     	|     10    	|     20    	|
|----------------------	|:---------:	|:---------:	|:---------:	|:---------:	|
| Pot=50W (Vin=1.74Vp) 	| 0.001425% 	| 0.002869% 	| 0.004304% 	| 0.030751% 	|
| Pot=30W (Vin=1.27Vp) 	| 0.001445% 	| 0.003932% 	| 0.012930% 	| 0.016209% 	|

Podemos observar en la tabla una distorsión considerablemente baja en todo el rango de frecuencia para ambas potencias del amplificador.

- *El circuito utilizado para la simulación se encuentra [aqui](LINK).*


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





