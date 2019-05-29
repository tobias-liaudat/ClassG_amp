# Descripción de mejoras propuestas

## 1: Fuente espejo de corriente Wilson

Se modificó la fuente espejo de corriente del par diferencial. Esta fuente espejo de corriente Wilson reduce la distorsión armónica del amplificador volviendolo más simétrico al igualar las corrientes que circuilan por cada rama. De esta manera se logra disminuir las armónicas pares. En la siguiente figura se puede ver la fuente Wilson:

<p align="center">
  <img src="../imagenes/wilson_current_mirror.png?raw=true" width="300" title="hover text">
</p>

Referencia: Pag 84, Douglas Self, *Audio power amplifi er design handbook. – 5th ed*. ([DS])

---

## 2: Par diferencial con par Sziklai como transistor de entrada

Una propuesta para mejorar la linealidad del amplificador en vistas de obtener una baja Distorsión Armónica Total (o THD por sus siglas en inglés) es utilizar pares Sziklai (o CFP, *Complementary Feedback Pair*) como transistores de entrada del par diferencial de la etapa de entrada. De esta manera estamos agregando realimentación local en la etapa de entrada, una buena técnica de diseño para poder aumentar la linealidad. Esta modificación ayuda a reducir la distorsión de las armónicas impares y sobretodo de la tercera armónica como se deja en evidencia en el libro de referencia de Douglas Self, de ahora en mas [DS].

El valor del resistor Rc que se encuentra en el par tiene una relación de compromiso. Si dicho valor es aumentado se aumenta la linealidad del circuito (referencia: Tabla 4.3, pag. 89, [DS]) pero a su vez se agrega más ruido debido al alto valor del resistor. El autor recomienda un valor de 2.2k que parece ser un buen compromiso.


<p align="center">
  <img src="../imagenes/CFP_input_stage.png?raw=true" width="200" title="hover text">
</p>

Referencia: Pag 88, Douglas Self, *Audio power amplifi er design handbook. – 5th ed*. ([DS])


---

## 3: Degeneración del emisor del par diferencial 

Esta es una técnica bastante conocida de realimentación local para estabilizar parámetros del circuito. Vale la pena agregar que no solo ayuda en la estabilización de la ganancia de la etapa de entrada sino que mejora el Slew Rate del circuito entero. La posición de los resistores se puede observar en la siguiente figura:

<p align="center">
  <img src="../imagenes/Re_degeneracion.png?raw=true" width="200" title="hover text">
</p>

El análisis del mejoramiento del slew rate no es trivial y puede verse detalladamente en la referencia [GM]. El slew rate depende principalmente de la carga del capacitor de Miller utilizado en la segunda etapa de alta ganancia de tensión, a la salida de la primera etapa como se ve en la siguiente figura:

<p align="center">
  <img src="../imagenes/slew_rate_calc_circuit.png?raw=true" width="200" title="hover text">
</p>

La expresión del slew rate proporcionado por [GM], considerando que siempre mantenemos al circuito compensado modificando el capacitor de Miller, es el siguiente:

<p align="center">
  <img src="../imagenes/slew_rate.png?raw=true" width="200" title="hover text">
</p>

donde *w2* es la frecuencia del segundo polo más bajo del sistema. Al agregar el resistor *Re* que degenera los emisores del par diferencial se logra agregar el término de la derecha que podemos modificar y por lo tanto aumentar el slew rate.


Referencias: 
- Slew Rate: Section 9.6, Gray Paul, Mayer Robert, Lewis Stephen y Hurst Paul (Ed. 5) (2009) *Analysis and Design for Integrated Circuit*. United States of America, New York: Wiley. ([GM])

- Mejora de linealidad: pag 85,..,87, Douglas Self, *Audio power amplifi er design handbook. – 5th ed*. ([DS]) 




