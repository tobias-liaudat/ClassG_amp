# Simulaciones de potencia 

En este caso se configuró el LTSpice para que haga un barrido de tensiones de entrada (y podría también de frecuencias de entrada) y se calculó la potencia entregada a la carga y la potencia entregada por las fuentes de alimentación para distintos valores de los rieles de alimetnación. Además, se calculó la THD para todos los casos y también la eficiencia del amplificador.

## Simulación 1

- VCC = 30V
- VCC1 = 15V
- Freq = 1kHz


- step1: Vi=0.5V
- step2: Vi=0.9V
- step3: Vi=1.2V

### Potencias
Potencia media de fuentes [W]:
- step1:	23.1147
- step2:	49.0835
- step3:	64.2288


Potencia media en al carga [W]:
- step1:	8.03109	
- step2:	26.0242	
- step3:	44.971	


Eficiencia:
- step1:	0.347446
- step2:	0.530203
- step3:	0.70017


### THD

step1:
- DC component:-0.0222145
- THD = 0.009467%


step2:
- DC component:-0.0404196
- THD = 0.001062%


step3:
- DC component:0.0850236
- THD = 2.451953%


*Nota: En el step3 la forma de onda ya se encuentra recortada en sus extremos, de ahí el alto THD.*

***

## Simulación 2

- VCC = 40V
- VCC1 = 15V
- Freq = 1kHz


- step1: Vi=0.5V
- step2: Vi=0.9V
- step3: Vi=1.2V
- step4: Vi=1.4V
- step5: Vi=1.6V


### Potencias

Potencia media de fuentes [W]:
- step1:	24.2839
- step2:	62.9986
- step3:	85.4635
- step4:	100.099
- step5:	114.006


Potencia media en al carga [W]:
- step1:	8.03183	
- step2:	26.0244	
- step3:	46.2658	
- step4:	62.9732	
- step5:	81.5757	


Eficiencia:
- step1:	0.330747
- step2:	0.413094
- step3:	0.541351
- step4:	0.629112
- step5:	0.715538


### THD

step1:
- DC component:-0.0223611
- THD = 0.004690%

step2:
- DC component:-0.0403925
- THD = 0.001081%

step3:
- DC component:-0.0540103
- THD =  0.001105%

step4:
- DC component:-0.0631402
- THD =  0.000932%

step5:
- DC component:-0.00225789
- THD =  1.044296%


*Nota: En el step5 la forma de onda ya se encuentra recortada en sus extremos, de ahí el alto THD.*

