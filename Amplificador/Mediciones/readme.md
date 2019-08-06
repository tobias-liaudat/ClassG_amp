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

- Medicion de entrada con multímetro (true RMS): 0.593Vef

<p align="center">
  <img src="imgs/ganancia_tension_alta.jpg?raw=true" width="500" title="hover text">
</p>



#### Ganancia de tensión con baja potencia 

- Medicion de entrada con multímetro (true RMS): 0.073Vef


<p align="center">
  <img src="imgs/ganancia_tension_baja.jpg?raw=true" width="500" title="hover text">
</p>



## Sensibilidad

La tensión a la entrada, medida con el multímetro true RMS es de: 0.720Vef.

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

### Frecuencias altas

#### f = 1kHz

<p align="center">
  <img src="imgs/BW_1k.jpg?raw=true" width="500" title="hover text">
</p>

#### f = 10kHz

<p align="center">
  <img src="imgs/BW_10k.jpg?raw=true" width="500" title="hover text">
</p>


#### f = 20kHz

<p align="center">
  <img src="imgs/BW_20k.jpg?raw=true" width="500" title="hover text">
</p>

#### f = 50kHz

<p align="center">
  <img src="imgs/BW_50k.jpg?raw=true" width="500" title="hover text">
</p>

#### f = 100kHz

<p align="center">
  <img src="imgs/BW_100k.jpg?raw=true" width="500" title="hover text">
</p>

#### f = 150kHz

<p align="center">
  <img src="imgs/BW_150k.jpg?raw=true" width="500" title="hover text">
</p>

#### f = 200kHz

<p align="center">
  <img src="imgs/BW_200k.jpg?raw=true" width="500" title="hover text">
</p>


#### f = 250kHz

<p align="center">
  <img src="imgs/BW_250k.jpg?raw=true" width="500" title="hover text">
</p>


### Frecuencias bajas


#### f = 100Hz

<p align="center">
  <img src="imgs/BW_100H.jpg?raw=true" width="500" title="hover text">
</p>

#### f = 10Hz

<p align="center">
  <img src="imgs/BW_10H.jpg?raw=true" width="500" title="hover text">
</p>


#### f = 2Hz

<p align="center">
  <img src="imgs/BW_2H.jpg?raw=true" width="500" title="hover text">
</p>

