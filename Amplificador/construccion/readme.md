## Realización de la placa

Para la realización del diseño de la placa del amplificador se utilizó el programa de diseño KiCad en su versión 4.

 

Los postulados tenidos en cuenta a la hora de diseñar fueron:

  - El material de la placa será FR4 - Doble Faz

  - Una buena porción de los componentes de la placa debe ser de montaje superficial (SMD)

  - La etapa diferencial debe estar de tal forma que las pistas pertenecientes a un mismo par circulen lo más paralelas posibles y los componentes de baja señal lo más cercanos que se pueden entre sí.

  - Los componentes que disipan una gran cantidad de calor y de gran señal deben estar alejados de los componentes de baja señal para no influir sobre estos últimos. Asimismo, los componentes que necesiten acoplamiento térmicos deben estar ubicados sobre el mismo disipador.

  - Las pistas de cobre deben ser adecuadas en relación con la intensidad de corriente que transportan siempre asegurando que las pistas sean invisibles al resto del circuito y no se comporten como componentes resistivos.

  - Los pads y la corona de las pistas deben tener un tamaño acorde para el soldado a mano. De esta forma, las coronas de los pads deben ser de un tamaño mayor al que por defecto KiCad incorpora en alguno de sus footprints (salvo que el footprint diga 'Hand Soldering').

  - Los pads de los componentes de gran señal que van atornillados a los disipadores deben soportar una tensión mecánica mayor y por tanto la corona del pad deberá ser acorde a las tensiones exigidas en el componente.

 

Por otro lado, la placa del amplificador se la realizó teniendo en cuenta los parámetros mínimos de diseño del LCI (Laboratorio de Circuitos Impresos) de la FIUBA:

 

Pistas:

(Tamaños mínimos)
12 mils de ancho de pista.
12 mils de separación entre pistas.
12 mils de separación entre pads y pistas.

Diámetro del pad o vía = Diámetro del agujero + 24 mils.

Agujeros. Los tamaños de mechas con los que cuenta el laboratorio son:
0,7 mm; 1 mm; 1,1 mm; 1,2 mm; 1,3 mm; 3 mm
 
Observación:
En el caso de trabajar con otro sistema de unidades y pasar al métrico por aproximación se recomienda redondear para abajo.
Esto se debe a que el software utilizado para la automatización del proceso de agujereado de no encontrar el tamaño especificado toma el siguiente dentro de su lista.

### Esquemático de la placa del amplificador

El primer paso en el diseño de la placa del amplificador fue copiar el esquemático de simulación del LTSpice al eeSchema del KiCad.
En el esquemático del eeSchema se optimizaron los valores y cantidad de resistores de manera de unificar los valores de componentes lo mejor posible (por ejemplo un resistor de 1.1k puede ser pensado como dos resistores de 2.2k en paralelo si los resistores de 2.2k
abundan en el diseño). De igual manera, se tuvo en cuenta la tecnología de los componentes en ciertos casos como en el de los capacitores electrolíticos de manera que se los asoció con capacitores cerámicos en paralelo para mejorar la respuesta en alta frecuencia ya que los capacitores de tecnología electrolítica tienen una frecuencia de autorresonancia mucho menor a la que presentan los capacitores cerámicos.

Por último se incluyeron en el diseño esquemático las borneras de entrada y salida tanto de la fuente de alimentación como de la carga, pines para puentear y probar las distintas etapas del circuito por separado y un conector jack para la entrada de audio.


<p align="center">
  <img src="imgs/Ampli_clase_G.jpg?raw=true" width="1000" title="hover text">
</p>


### Asociación de Footprints

El segundo paso consiste en la asociación de los ‘footprint’ correspondientes a cada elemento del circuito. Para ello se tuvieron que dimensionar los componentes teniendo en cuenta la potencia máxima que deben soportar, la tensión de operación y la tecnología de fabricación a fin de tener una idea de la distancia entre pines de los resistores, capacitores e inductores del circuito. En el caso de los componentes activos este paso fue más sencillo ya que la hoja de datos del componente inmediatamente relaciona el código del componente con un encapsulado en particular. Por otro lado, los resistores SMD se eligieron para que tengan encapsulado 0608 de manera que no sean ni muy grandes ni muy chicos como para entorpecer el trabajo de soldado a mano.

Los footprints asociados fueron asociados una vez comprados los componentes en base a los valores de distancia entre pines (pitch), cuerpo (‘body’) y ancho (‘width’) de los componentes conseguidos.

### Placement de componentes

Una vez realizada la asociación de footprints de los componentes, se realizó desde el eeSchema la exportación de la NetList y la importación de la misma en el pcbNew.
Por defecto pcbNew acomoda todos los componentes de la NetList en el centro del dibujo, todos superpuestos con todos por lo manualmente se acomodaron todos los componentes en posiciones ‘a priori’ sobre la placa teniendo en cuenta que se produjeran los mínimos cruces posibles entre conexiones y separando de una manera coherente las diferentes etapas del amplificador en base a los postulados expuestos anteriormente.

### Ruteo de la placa

Una vez realizado el placement de los componentes se pasó a la etapa de ruteo donde cada componente se unió con sus asociados por medio de pistas. El pcbNew fue configurado de tal manera que respete los tamaños mínimos de separación y de ancho del LCI. Para los anchos de pista se tuvo en cuenta la siguiente tabla:

| Corriente máxima | Ancho mínimo de pista |
|------------------|-----------------------|
|		0.3 A	   |		10 mils		   |
|       0.4 A      |        15 mils        |
|       0.7 A      |        20 mils        |
|       1.0 A      |     	25 mils        |
|       2.0 A      |        50 mils        |
|       4.0 A      |       100 mils        |
|       6.0 A      |       150 mils        |
|       8.0 A      |       200 mils        |
|      10.0 A      |       250 mils        |
|      16.0 A      |       400 mils        |

### Retoques finales

Una vez realizado el ruteo de la placa se agregaron ciertos pasos finales:
- Se agregaron los agujeros correspondientes a los soportes de placa en cada una de la esquinas.
- Se agregaron los ‘footprint’ correspondientes a los disipadores de poder calcular donde insertar los agujeros para los tornillos de soporte de los disipadores.

Como último paso se corrió la comprobación de errores del pcbNew a fin de detectar si había algun problema con las directivas de pads y pistas impuestas. Se comprobó que había dos pads que se encontraban demasiado cercanos a pistas aledañas. Se corrigió el error y se volvió a correr la comprobación de errores dando resultado satisfactorio.  Concluido el diseño de la placa se exportaron los archivos Gerber necesarios para la construcción.


### Imagenes de la placa

#### PCB atras

<p align="center">
  <img src="imgs/PCB_back.png?raw=true" width="800" title="hover text">
</p>

#### PCB adelatne

<p align="center">
  <img src="imgs/PCB_f.png?raw=true" width="800" title="hover text">
</p>

#### Realización del circuito

<p align="center">
  <img src="imgs/amp_classG.jpg?raw=true" width="800" title="hover text">
</p>

