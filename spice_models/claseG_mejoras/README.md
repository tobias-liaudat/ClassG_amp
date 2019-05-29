# Descripción de mejoras propuestas

## 1: Fuente espejo de corriente Wilson

Se modificó la fuente espejo de corriente del par diferencial. Esta fuente espejo de corriente Wilson reduce la distorsión armónica del amplificador volviendolo más simétrico al igualar las corrientes que circuilan por cada rama. De esta manera se logra disminuir las armónicas pares. En la siguiente figura se puede ver la fuente Wilson:

<p align="center">
  <img src="../imagenes/wilson_current_mirror.png?raw=true" width="300" title="hover text">
</p>

Referencia: Pag 84, Douglas Self, *Audio power amplifier design handbook. – 5th ed*. ([DS])

---

## 2: Par diferencial con par Sziklai como transistor de entrada

Una propuesta para mejorar la linealidad del amplificador en vistas de obtener una baja Distorsión Armónica Total (o THD por sus siglas en inglés) es utilizar pares Sziklai (o CFP, *Complementary Feedback Pair*) como transistores de entrada del par diferencial de la etapa de entrada. De esta manera estamos agregando realimentación local en la etapa de entrada, una buena técnica de diseño para poder aumentar la linealidad. Esta modificación ayuda a reducir la distorsión de las armónicas impares y sobretodo de la tercera armónica como se deja en evidencia en el libro de referencia de Douglas Self, de ahora en mas [DS].

El valor del resistor Rc que se encuentra en el par tiene una relación de compromiso. Si dicho valor es aumentado se aumenta la linealidad del circuito (referencia: Tabla 4.3, pag. 89, [DS]) pero a su vez se agrega más ruido debido al alto valor del resistor. El autor recomienda un valor de 2.2k que parece ser un buen compromiso.


<p align="center">
  <img src="../imagenes/CFP_input_stage.png?raw=true" width="200" title="hover text">
</p>

Referencia: Pag 88, Douglas Self, *Audio power amplifier design handbook. – 5th ed*. ([DS])


---

## 3: Degeneración del emisor del par diferencial 

Esta es una técnica bastante conocida de realimentación local para estabilizar parámetros del circuito. Vale la pena agregar que no solo ayuda en la estabilización de la ganancia de la etapa de entrada sino que mejora el Slew Rate del circuito entero. La posición de los resistores se puede observar en la siguiente figura:

<p align="center">
  <img src="../imagenes/Re_degeneracion.png?raw=true" width="300" title="hover text">
</p>

El análisis del mejoramiento del slew rate no es trivial y puede verse detalladamente en la referencia [GM]. El slew rate depende principalmente de la carga del capacitor de Miller utilizado en la segunda etapa de alta ganancia de tensión, a la salida de la primera etapa como se ve en la siguiente figura:

<p align="center">
  <img src="../imagenes/slew_rate_calc_circuit.png?raw=true" width="400" title="hover text">
</p>

La expresión del slew rate proporcionado por [GM], considerando que siempre mantenemos al circuito compensado modificando el capacitor de Miller, es el siguiente:

<p align="center">
  <img src="../imagenes/slew_rate.png?raw=true" width="300" title="hover text">
</p>

donde *w2* es la frecuencia del segundo polo más bajo del sistema. Al agregar el resistor *Re* que degenera los emisores del par diferencial se logra agregar el término de la derecha que podemos modificar y por lo tanto aumentar el slew rate.


Referencias: 
- Slew Rate: Section 9.6, Gray Paul, Mayer Robert, Lewis Stephen y Hurst Paul (Ed. 5) (2009) *Analysis and Design for Integrated Circuit*. United States of America, New York: Wiley. ([GM])

- Mejora de linealidad: pag 85,..,87, Douglas Self, *Audio power amplifier design handbook. – 5th ed*. ([DS]) 


---

## 4: Capacitor de SpeedUp para el driver del par Darlington de salida

Para mejorar la distorsión del amplificador a altas frecuencias, una posible mejora es el agregado de un capacitor de *SpeedUp* como bien se indica en la referencia [DS]. EL capacitor se conecta entre el resistor que une los transistores *drivers* de las etapas Darlington de salida como se puede ver en la siguiente figura al capacitor *C5*:

<p align="center">
  <img src="../imagenes/speedup_cap.png?raw=true" width="300" title="hover text">
</p>

En la figura 6.52 de la pag. 186 de [DS] se encuentra una simulación que justifica la mejora de THD gracias al capacitor de *SpeedUp*. La mejora se da sobretodo en la altas frecuencias de operación del amplificador. El capacitor proporciona un camino de menor impedancia que ayuda a despolarizar la juntura base-emisor del transistor *driver* de la etapa Darlington de salida. De esta manera logra que la etapa pueda cortar más rápido cuando pasa de un semiciclo de señal negativo a uno positivo y *vice-versa*.

En el archivo de texto *design_notes.txt* se encuentran los resultados de varias simulaciones del circuito al ir variando la frecuencia, la amplitud de entrada y el valor del capacitor de *SpeedUp*. El valor con mejor desempeño resultó ser de *100nF*.


Referencias: *Switching distortion*: pag 185,186, Douglas Self, *Audio power amplifier design handbook. – 5th ed*. ([DS]) 



---

## 5: Protección de corriente de la etapa de salida

Al hacer repetidas simulaciones del circuito se dedujo que la protección existente que limita la corriente de  la etapa de salida introduce mucha THD. Para ilustrar esto se vuelcan algunos resultados de simulaciones para comparar:

Con protección de corriente:

@ f=2kHz | Vin=1.15V | Vout = 26V | P= 42.25W | VCC=50V | PR1=0.3k | C_SpeedUp = 100n	

- THD = 0.0143%


Sin protección de corriente:

@ f=2kHz | Vin=1.15V | Vout = 26V | P= 42.25W | VCC=50V | PR1=0.3k | C_SpeedUp = 100n	

- THD = 0.000383%


Sin protección de corriente:

@ f=2kHz | Vin=0.5V | Vout = 11.3V | P= 8W | VCC=50V | PR1=0.3k | C_SpeedUp = 100n	

THD = 0.000067%


Sin protección de corriente:

@ f=2kHz | Vin=2.0V | Vout = 45V | P= 125W | VCC=50V | PR1=0.3k | C_SpeedUp = 100n	

THD = 0.003969%

En las simulaciones se utilizaron las primeras 40 armónicas para el cálculo de la THD. El cálculo fue realizado integramente con el programa LTSpice.

Como conlcusión se puede extraer que la protección utilizada no es viable si se desea realizar un diseño de muy baja distorsión. Por lo tanto se deberá diseñar otro tipo de protección que mantenga la THD baja.


