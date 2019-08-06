Para la realización del diseño de la placa del amplificador se utilizó el programa de diseño KiCad en su versión 4. 

Los parámetros de diseño tenidos en cuenta a la hora de diseñar fueron:
  - Material FR4 - Doble Faz
  - Una buena porción de los componentes de la placa debe ser de montaje superficial (SMD)
  - La etapa diferencial debe estar de tal forma que las pistas pertenecientes a un mismo par circulen lo más paralelas posibles y lo
  componentes de baja señal lo más cercanos que se pueden entre sí.
  - Los componentes que disipan una gran cantidad de calor y de gran señal deben estar alejados de los componentes de baja señal para no influir
  sobre estos últimos. Asimismo, los componentes que necesiten acoplamiento térmicos deben estar ubicados sobre el mismo disipador.
  - Las pistas de cobre deben ser adecuadas en relación con la intensidad de corriente que transportan siempre asegurando que las pistas 
  sean invisibles al resto del circuito y no se comporten como componentes resistivos.
  - Los pads y la corona de las pistas deben tener un tamaño acorde para el soldado a mano. De esta forma, las coronas de los pads deben 
  ser de un tamaño mayor al que por defecto KiCad incorpora en alguno de sus footprints (salvo que el footprint diga 'Hand Soldering').
  - Los pads de los componentes de gran señal que van atornillados a los disipadores deben soportar una tensión mecánica mayor y por
  tanto la corona del pad deberá ser acorde a las tensiones exigidas en el componente.
  
Por otro lado, la placa del amplificador se la realizó teniendo en cuenta los parámetros mínimos de diseño del LCI (Laboratorio de 
Circuitos Impresos) de la FIUBA:

Pistas:
(Tamaños mínimos)
12 mils de ancho de pista.
12 mils de separación entre pistas.
12 mils de separación entre pads y pistas.
Diámetro del pad o vía= Diámetro del agujero + 24 mils.
Agujeros
Los tamaños de mechas con los que cuenta el laboratorio son:
0,7 mm
1 mm
1,1 mm
1,2 mm
1,3 mm
3 mm
Observación:
En el caso de trabajar con otro sistema de unidades y pasar al métrico por aproximación se recomienda redondear para abajo. 
Esto se debe a que el software utilizado para la automatización del proceso de agujereado de no encontrar el tamaño especificado toma 
el siguiente dentro de su lista.

### Esquemático de la placa del amplificador

El primer paso en el diseño de la placa del amplificador fue copiar el esquemático de simulación del LTSpice en 





### Asociación de Footprints


### Placement de componentes



### Ruteo de la placa


### Retoques finales




