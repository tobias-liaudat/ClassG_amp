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
