### Diseño de la fuente positiva (Boost Converter)

Se plantea diseñar una fuente elevadora de +15V a +40V que pueda proporcionar hasta 2.5A de salida. La fuente deberá tener una buena respuesta a la regulación de carga ya que la carga a la salida puede variar en cuestión de milisegundos desde 20 ohms hasta 3kohms. 

La topología utilizada para la fuente positiva será Boost (elevadora sin aislación) elegida por su sencillez. Queda a definir el modo de operación: CCM (Continuous Control Mode) o DCM (Discontinuous Control Mode).

El modo de operación a elegir depende basicamente de las especificaciones que necesitemos y del tamaño de los componentes que estemos dispuestos a utilizar.

#### Control DCM:

- Mas estable ya que la respuesta en frecuencia posee un cero de alta frecuencia bastante alejado de la frecuencia de conmutación.
- Las corrientes pico sobre el inductor, transistor y diodo son mucho más elevadas que en el modo de operación CCM, en consecuencia, el calibre de alambre utilizado en el inductor debe ser más grueso. De igual manera, transistor y diodo encarecen su valor ya que deben soportar una corriente pico máxima más elevada.
- El inductor al tener que almacenar menos energía es de un valor menor
- La tensión de salida no depende unicamente del ciclo de trabajo sobre el transistor de conmutación. Tambien depende fuertemente del valor de la corriente de salida.
- Circuito más complejo
- En general, se consigue menor eficiencia ya que las perdidas transitorias en diodo y componentes parásitos del inductor suelen ser mucho mayores a las perdidas en conducción.

#### Control CCM:

- Menos estable ante cambios en la carga. La respuesta en frecuencia posee dos ceros en alta frecuencia donde uno de los ceros puede llegar a quedar en RHP si la corriente de salida cae por debajo de un valor crítico (corriente crítica).
- Circuito más sencillo, admite control por corriente o por tensión.
- El valor de la inductancia del inductor debe ser mucho más elevado para evitar caer en zona DCM.
- La corriente de salida debe ser asegurada por encima de una corriente mínima. A menor corriente mínima de salida, el valor del inductor aumenta exponencialmente.
- Las corrientes pico sobre inductor, diodo y transistor son de un valor mucho más chico en comparación con el modo DCM.
- La tensión de salida depende unicamente del ciclo de trabajo en el transistor de conmutación.
- Suelen tener mejor eficiencia que en modo DCM

A continuación se detallan los valores necesarios de componentes para cada modo así como sus limitaciones:

Vi = 15V
Vi_min = 14V
Vi_max = 16V
Vo = 40V
Frecuencia de conmutación: 52 kHz

**Modo CCM**:

Duty Cycle = 1-Vi/Vo = 0.638
Ton = 12.3 us;
Toff = 7 us;

Corriente | Inductancia mínima (CCM) 
----------------|----------------
Iout_min = 20mA | L_min = 7.6 mH 
Iout_min = 50mA | L_min = 3.0 mH 
Iout_min = 100mA | L_min = 1.5 mH 
Iout_min = 2.5 A | L_min = 60 uH 

Tomando un **L = 5mH**,en regimen estacionario: **IL_max (peak) = 7.3A**

**Modo DCM**:

Duty Cycle (2.5A) = 0.373
Ton = 7.17 us;

Considerando n = 0.8; Iout = 2.5A --> L_max(DCM) = 10.2 uH

Elegimos una inductancia **L = 8uH** (Cuanto mayor la inductancia menor el pico de corriente así que conviene elegirlo lo más cercano al teórico máximo).

En regimen estacionario: **IL_max(peak) = 16.0A**

### Simulaciones en modo CCM - L = 10mH 

Se simulo en LTSpice un modelo de fuente Boost dual donde la carga varía abruptamente entre 600 y 16 ohms a fin de probar la regulación de carga y el tiempo que tarda en estabilizarse ante cambios en la carga. La simulación se realizo de tal manera que el circuito enciende con la carga de 600 ohms (amplificador sin señal a la entrada) y a partir de 350ms se realizan los cambios de carga alternando cada 10ms entre 600 y 16 ohms.

<p align="center">
  <img src="./CCM_10mH_circ.png" width="800" title="hover text">
</p>


<p align="center">
  <img src="./CCM_10mH.png" width="500" title="hover text">
</p>






