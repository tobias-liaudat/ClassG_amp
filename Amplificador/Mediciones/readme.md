# Mediciones sobre el amplificador

## Polarización

La polarización se puede ver en la imagen a continuación en donde se midió la tensión en varios puntos del circuito cuando este se encuentra funcionando sin señal a la entrada.

En la siguiente tabla se pueden observar algunos valores importantes de la polarización del circuito. Se puede ver la gran similitud entre la simulación y la medición.

| Componentes                      	| Valores simulador 	| Valores medidos |
|----------------------------------	|----------	          |----------	      |
| Fuente corriente par diferencial 	| 5.7 mA   	          | **5.62mA**      |
| Fuente corriente VAS             	| 18.2 mA  	          | **20.0mA**      |
| Multiplicador Vbe                	| 2.63 V   	          | **2.08V**       |
| Tensión salida                   	| 486 uV   	          | **8.0mV**       |


<p align="center">
  <img src="imgs/polarizacion.jpg?raw=true" width="1000" title="hover text">
</p>


## Ganancia de Tensión

Se ajusto la señal de entrada un valor de alta potencia y luego a uno de baja y se midió cual fue la ganancia de tensión en cada caso.

#### Ganancia de tensión con alta potencia 

- Medicion de entrada con multímetro (true RMS): 0.593Vef (aprox 0.84Vp)

- Medición de tensión de salida en el osciloscopio: 21Vp

- Ganancia de tensión @ 27.6W : 25 (27.96dB)

<p align="center">
  <img src="imgs/ganancia_tension_alta.jpg?raw=true" width="500" title="hover text">
</p>



#### Ganancia de tensión con baja potencia 

- Medicion de entrada con multímetro (true RMS): 0.073Vef (aprox 0.103Vp)

- Medición de tensión de salida en el osciloscopio: 2.4Vp

- Ganancia de tensión @ 0.36W : 23.3 (27.35dB)

<p align="center">
  <img src="imgs/ganancia_tension_baja.jpg?raw=true" width="500" title="hover text">
</p>



## Sensibilidad

La tensión a la entrada, medida con el multímetro true RMS es de: 0.720Vef que es aproximadamente 1.02Vp. La tensión de salida es de 24Vp.

<p align="center">
  <img src="imgs/sensibilidad.jpg?raw=true" width="500" title="hover text">
</p>


## Potencia a la salida

#### Entrada senoidal

- El valor de la tensión de alimentación era de 0.72Vef medico con el multímetro true RMS.

- La tensión a la salida es de 24Vp. Como la carga conectada es de 8 Omh, la potencia desarrollada es de 36W.

- Frecuencia de entrada: 1kHz

<p align="center">
  <img src="imgs/potencia_senoidal.jpg?raw=true" width="500" title="hover text">
</p>



#### Entrada cuadrada

- Señal de entrada cuadrada de 1Vp.

- Señal de salida cuadrada de 24Vp.

- Frecuencia de entrada: 1kHz

<p align="center">
  <img src="imgs/potencia_cuadrada.jpg?raw=true" width="500" title="hover text">
</p>


## Ancho de banda

Para esta medición se fijo una baja potencia y se fue elevando la frecuencia de la onda senoidal de excitación a la entrada. La idea es ver hasta que frecuencias se mantiene la ganancia de tensión y frenar una vez que esta cayó 3dB.

La amplitud de entrada se fijó en 60mVp.

- El ancho de banda medido fue desde los 2Hz hasta los 250kHz. 

Finalmente, se puede observar en el siguiente gráfico el ancho de banda del amplificador, el mismo va desde los **2 Hz** hasta los **250kHz**. Lo cual es considerablemente grande. Vale la pena destacar que a pesar de que la ganancia se mantiene hasta frecuencias altas, la forma de onda tiene distorsiones notables a simple vista.

Para ver las imágenes de las mediciones se puede seguir el siguiente [enlace](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Amplificador/Mediciones/ancho_de_banda).

<p align="center">
  <img src="imgs/ancho_de_banda.jpg?raw=true" width="1000" title="hover text">
</p>

## Slew rate

Para realizar esta medición se excito el amplificador con una onda cuadrada de 2.4Vpp de amplitud, es decir con una cuadrada a máxima potencia, y de 10kHz. Con el osciloscopio se midió la tensión de salida del amplificador con la carga conectada. Para calcular el *slew rate* vamos a ver el tiempo que le lleva a la señal ir desde el 10% hasta el 90% del valor final.

- Vlow = -23V & Vhigh = 25V  -->  V_10 = -18.2V & V_90 = 20.2V

- Delta_V = 38.4V

- Delta_T = 1.9us

- SR = Delta_V / Delta_T = 38.4V / 1.9us = 20.21 V/us

- **SR = 20.21 V/us**


<p align="center">
  <img src="imgs/slew_rate.jpg?raw=true" width="500" title="hover text">
</p>





