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

**SR = 20.21 V/us**


<p align="center">
  <img src="imgs/slew_rate.jpg?raw=true" width="500" title="hover text">
</p>


## Impedancia de entrada 

Para realizar el cálculo de impedancia de entrada se intercaló en serie con la entrada del amplificador un resistor de un valor conocido y se midió la caida de tensión sobre este resistor para poder calcular la corriente que ingresa del amplificador. Luego, se midió la tensión de entrada con un multímetro. La señal de excitación de entrada es de 1kHz, y el multímetro es True-RMS.

- El resistor se midió y Rtest = 3.79kOhms.

- La caida de tensión en el resistor de prueba es DeltaV_Rtest = 0.0398Vef

- Se puede calcular la corriente: I_in = DeltaV_Rtest / Rtest = 0.0398Vef / 3.79kOhms = 10.5 uAef

- La tensión a la entrada del amplificador es de V_in = 0.1273Vef

- La impedancia de entrada se calcula: Rin = V_in / I_in = 0.1273Vef / 10.5uAef = 12.12kOHm

Impedancia de entrada: **Rin = 12.12 kOhm**


## Impedancia de salida

Esta medición no es simple ya que es dificil medir una impedancia de un valor tan bajo como la impedancia de salida para un amplificador de este tipo.

El procedimiento consiste en utilizar un multímetro de precisión para medir la tensión a la salida del amplificador a máxima potencia funcionando con la carga y en vacio. La frecuencia de excitación senoidal fue de 1kHz.

- Tensión de salida en vacio: Vo_vacio = 12.734Vef

- Tensión de salida con carga: Vo_carga = 12.644Vef

- Impedancia de la carga: RL = 8.4 Ohms

Luego podemos calcular la impedancia de salida con la siguiente fórmula:

- Ro = RL (Vo_vacio / Vo_carga - 1) = 8.4Ohm (12.734Vef / 12.644Vef - 1) = 0.0598 Ohm

Impedancia de salida: **Ro = 59.8 mOhm**


## Factor de amortiguamiento

El factor de amortiguamiento puede calcularse a partir de losl valores obtenidos en la medición previa:

- FA = RL / Ro = 8.4Ohm / 59.8mOhm = 140.5

Factor de amortiguamiento: **FA = 140.5**


## Eficiencia

Se midió la eficiencia del amplificador midiendo la potencia que entrega cada una de las fuentes y la potencia que se le entrega la carga. Para realizar la medición se fue aumentando la amplitud de la tensión a la entrada del amplificador y para cada paso se medían las corrientes de las fuentes como también sus tensiones y la tensión desarrollada sobre la carga. Al tener la tensión sobre la carga y el valor de la carga se puede deducir su potencia.

En el gráfico siguiente se puede observar el pico característico del amplificador clase G que muestra a que potencia el amplificador empieza a tomar corriente de las fuentes superiores.

<p align="center">
  <img src="imgs/eficiencia_medicion.jpg?raw=true" width="1000" title="hover text">
</p>

Yendo más lejos, podemos graficar la potencia que entregan las fuentes y observar varios detalles. Para potencias bajas las fuentes de tensión altas (de 30v) tienen una potencia constante que es la requerida para la polarización del circuito. Luego, a partir de los 7W se llega a la máxima potencia que entregan las fuentes de tensión bajas (de 15v) para que se empiece a entregar mas potencia de las fuentes superiores.

<p align="center">
  <img src="imgs/potencia_de_fuentes.jpg?raw=true" width="1000" title="hover text">
</p>

## Total Harmonic Distortion : THD

Para realizar esta medición se utilizó la placa de sonido de la computadora *PC157* del laboratorio y el programa [SpectraPlus v5](http://www.spectraplus.com/). Este programa permite utilizar la placa de sonido para generar señales senoidales de muy baja distorsión con uno de sus canales y a su vez realizar una FFT en tiempo real con la señal que ingresa en otro canal de la placa.

Para realizar la medición se tuvo que construir una placa complementaría que funcionase como atenuador ya que la placa de sonido no puede recibir señales de grán amplitud. Esta placa estaba constituida de resistores, un potenciometro y jumpers que permitiesen realizar un ajuste grueso y fino de la atenuación requerida para que la señal entre en un nivel óptimo a la placa de sonido.

En el siguiente gráfico se puede ver como evoluciona la THD al ir aumentando la potencia sobre la carga, siempre a 1kHz. Se estima que la THD a muy baja potencia es alta ya que la señal de entrada deja de ser de tan buena calidad.

<p align="center">
  <img src="imgs/THD_a_1k.jpg?raw=true" width="1000" title="hover text">
</p>

En esta medición se midió la THD para varias frecuencias y a varias potencias. Es visible, el hecho de que a baja frecuencia, 100Hz, la THD aumente considerablemente. Sin embargo, para las frecuencias superiores, en todas las potencias la THD se mantiene en niveles bajos. 

Por ejemplo, sin tomar en cuenta la medición a 100Hz, las dos potencias superiores presentad distorsiones debajo del nivel de 0.03% para todo el ancho de banda. Se añade que no se pudo medir la distorsión por niveles superiores a 10kHz, ya que es el límite de frecuencia de la señal senoidal de generación.

<p align="center">
  <img src="imgs/THD_frec.jpg?raw=true" width="1000" title="hover text">
</p>


#### THD sin carga

En interesante observar que teniendo al amplificador sin carga, es decir, operando en vacio se alcanzan distorsiones considerablemente menores. Excitando a 1kHz se logro una **THD = 0.00479%**. Se puede ver en la siguiente captura la medición.

Es interesante observar la composición de armónicas en la transformada. Se puede observar que la amplitud de las armónicas pares es muy bajo, indicando que la simetría del circuito es muy buena. La contribución a la distorsión armónica es principalmente por parte de armónicas impares, dando a notar la alinealidad del circuito. Esto puede ser generado por una ganancia de lazo abierto no tan grande. Sin embargo, la distorsión armónica logra ser muy baja.


<p align="center">
  <img src="imgs/THD_1k_140m_sinRL.png?raw=true" width="1000" title="hover text">
</p>



#### Análisis




## InterModulation Distortion : IMD

Para realizar esta medición, se utilizó el mismo banco de medición que para la medición de la THD, utilizando el mismo programa, *SpectraPlus*. Para realizar esta medición se generan dos señales senoidales, una de 60Hz y otra de 7kHz con una relación de amplitud 4:1. En este caso, seguimos el estandar SMPTE RP120-1994 para el cálculo de IMD ([referencia](http://www.aes.org/par/i/#IM)).

- La medición dió como resultado: **IMD = 0.0123%**

Una captura del programa con la medición de IMD se puede ver en la siguiente imagen:

<p align="center">
  <img src="imgs/IMD_good_good.png?raw=true" width="1000" title="hover text">
</p>





