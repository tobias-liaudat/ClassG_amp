﻿## Realizaci�n de la placa

Para la realizaci�n del dise�o de la placa del amplificador se utiliz� el programa de dise�o KiCad en su versi�n 4.

 

Los postulados tenidos en cuenta a la hora de dise�ar fueron:

  - El material de la placa ser� FR4 - Doble Faz

  - Una buena porci�n de los componentes de la placa debe ser de montaje superficial (SMD)

  - La etapa diferencial debe estar de tal forma que las pistas pertenecientes a un mismo par circulen lo m�s paralelas posibles y los componentes de baja se�al lo m�s cercanos que se pueden entre s�.

  - Los componentes que disipan una gran cantidad de calor y de gran se�al deben estar alejados de los componentes de baja se�al para no influir sobre estos �ltimos. Asimismo, los componentes que necesiten acoplamiento t�rmicos deben estar ubicados sobre el mismo disipador.

  - Las pistas de cobre deben ser adecuadas en relaci�n con la intensidad de corriente que transportan siempre asegurando que las pistas sean invisibles al resto del circuito y no se comporten como componentes resistivos.

  - Los pads y la corona de las pistas deben tener un tama�o acorde para el soldado a mano. De esta forma, las coronas de los pads deben ser de un tama�o mayor al que por defecto KiCad incorpora en alguno de sus footprints (salvo que el footprint diga 'Hand Soldering').

  - Los pads de los componentes de gran se�al que van atornillados a los disipadores deben soportar una tensi�n mec�nica mayor y por tanto la corona del pad deber� ser acorde a las tensiones exigidas en el componente.

 

Por otro lado, la placa del amplificador se la realiz� teniendo en cuenta los par�metros m�nimos de dise�o del LCI (Laboratorio de Circuitos Impresos) de la FIUBA:

 

Pistas:

(Tama�os m�nimos)
12 mils de ancho de pista.
12 mils de separaci�n entre pistas.
12 mils de separaci�n entre pads y pistas.

Di�metro del pad o v�a = Di�metro del agujero + 24 mils.

Agujeros. Los tama�os de mechas con los que cuenta el laboratorio son:
0,7 mm; 1 mm; 1,1 mm; 1,2 mm; 1,3 mm; 3 mm
 
Observaci�n:
En el caso de trabajar con otro sistema de unidades y pasar al m�trico por aproximaci�n se recomienda redondear para abajo.
Esto se debe a que el software utilizado para la automatizaci�n del proceso de agujereado de no encontrar el tama�o especificado toma el siguiente dentro de su lista.

### Esquem�tico de la placa del amplificador

El primer paso en el dise�o de la placa del amplificador fue copiar el esquem�tico de simulaci�n del LTSpice al eeSchema del KiCad.
En el esquem�tico del eeSchema se optimizaron los valores y cantidad de resistores de manera de unificar los valores de componentes lo mejor posible (por ejemplo un resistor de 1.1k puede ser pensado como dos resistores de 2.2k en paralelo si los resistores de 2.2k
abundan en el dise�o). De igual manera, se tuvo en cuenta la tecnolog�a de los componentes en ciertos casos como en el de los capacitores electrol�ticos de manera que se los asoci� con capacitores cer�micos en paralelo para mejorar la respuesta en alta frecuencia ya que los capacitores de tecnolog�a electrol�tica tienen una frecuencia de autorresonancia mucho menor a la que presentan los capacitores cer�micos.

Por �ltimo se incluyeron en el dise�o esquem�tico las borneras de entrada y salida tanto de la fuente de alimentaci�n como de la carga, pines para puentear y probar las distintas etapas del circuito por separado y un conector jack para la entrada de audio.

### Asociaci�n de Footprints

El segundo paso consiste en la asociaci�n de los �footprint� correspondientes a cada elemento del circuito. Para ello se tuvieron que dimensionar los componentes teniendo en cuenta la potencia m�xima que deben soportar, la tensi�n de operaci�n y la tecnolog�a de fabricaci�n a fin de tener una idea de la distancia entre pines de los resistores, capacitores e inductores del circuito. En el caso de los componentes activos este paso fue m�s sencillo ya que la hoja de datos del componente inmediatamente relaciona el c�digo del componente con un encapsulado en particular. Por otro lado, los resistores SMD se eligieron para que tengan encapsulado 0608 de manera que no sean ni muy grandes ni muy chicos como para entorpecer el trabajo de soldado a mano.

Los footprints asociados fueron asociados una vez comprados los componentes en base a los valores de distancia entre pines (pitch), cuerpo (�body�) y ancho (�width�) de los componentes conseguidos.

### Placement de componentes

Una vez realizada la asociaci�n de footprints de los componentes, se realiz� desde el eeSchema la exportaci�n de la NetList y la importaci�n de la misma en el pcbNew.
Por defecto pcbNew acomoda todos los componentes de la NetList en el centro del dibujo, todos superpuestos con todos por lo manualmente se acomodaron todos los componentes en posiciones �a priori� sobre la placa teniendo en cuenta que se produjeran los m�nimos cruces posibles entre conexiones y separando de una manera coherente las diferentes etapas del amplificador en base a los postulados expuestos anteriormente.

### Ruteo de la placa

Una vez realizado el placement de los componentes se pas� a la etapa de ruteo donde cada componente se uni� con sus asociados por medio de pistas. El pcbNew fue configurado de tal manera que respete los tama�os m�nimos de separaci�n y de ancho del LCI. Para los anchos de pista se tuvo en cuenta la siguiente tabla:

### Retoques finales

Una vez realizado el ruteo de la placa se agregaron ciertos pasos finales:
- Se agregaron los agujeros correspondientes a los soportes de placa en cada una de la esquinas.
- Se agregaron los �footprint� correspondientes a los disipadores de poder calcular donde insertar los agujeros para los tornillos de soporte de los disipadores.

Como �ltimo paso se corri� la comprobaci�n de errores del pcbNew a fin de detectar si hab�a algun problema con las directivas de pads y pistas impuestas. Se comprob� que hab�a dos pads que se encontraban demasiado cercanos a pistas aleda�as. Se corrigi� el error y se volvi� a correr la comprobaci�n de errores dando resultado satisfactorio.  Concluido el dise�o de la placa se exportaron los archivos Gerber necesarios para la construcci�n.