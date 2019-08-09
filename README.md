# Diseño: Amplificador de Audio de Potencia Clase G con dos fuentes conmutadas

### Integrantes:

- Tobias Ignacio Liaudat
- Federico Muñoz Macia

---

### Aspectos generales del trabajo

Este trabajo comprende el diseño, la simulación, la construcción y la medición de un amplificador de potencia de audio clase G más dos fuentes de switching.

El informe consiste en este repositorio en donde se pueden encontrar: distintos tipo de explicaciones del diseño; modelos de simulación; simulaciones de las características del amplificador diseñado; archivos del diseño de los distintos PCB y explicaciones conceptuales de las elecciones; mediciones de las características de los circuitos implementados.

Para navegar en este informe solo se debe seguir los distintos enlaces que irán abriendo las distintas carpetas. El informe consiste en dos carpetas principales, una que corresponde al [amplificador](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Amplificador) y otra que corresponde a las [fuentes conmutadas](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Fuente%20SW).

### Especificaciones

Las especificaiones del amplificador son las siguientes:

- Potencia: 40 W RMS @ 8 Ohm

- THD: < 0.1% @ 20Hz-20kHz, 5W / 8 Ohm

- THD: < 0.01% @ 1kHz, 15W / 8 Ohm

- IMD: < 0.05 % @ 60Hz & 7kHz, 4:1 razón de amplitudes

- Ancho de banda: 20Hz a 100kHz @ 0.1W / 8 Ohm

- Tensión continua a la salida: < |10mV|

- Sensibilidad: 1 Vp

- Impedancia de entrada: >10 kOhm

- Factor de Amortiguamiento: > 500

- Slew Rate: > 15 V/us

- Protección: contra cortocircuito y sobrecarga



---



### Algunos enlaces a distintas secciones del informe 

- [Mediciones del amplificador](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Amplificador/Mediciones)

- [Diseño y simulaciones de características del amplificador](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Amplificador/Dise%C3%B1o%20final)

- [Construcción y ruteo del amplificador](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Amplificador/construccion)



### Videos de funcionamiento:

- Amplificador funcionando a máxima potencia y luego a baja potencia : [video](https://photos.app.goo.gl/b69a7zTJsys8Gchi9)

- Fuente de switching positiva trabajando con con carga de 16 Ohm : [video](https://photos.app.goo.gl/x3bsC1SKNY7uwe568)

- Fuente de switching negativa trabajando con con carga de 16 Ohm : [video](https://photos.app.goo.gl/3ddAb1sy1qB68Pso6)

- Amplificador con fuentes de switching trabajando a máxima potencia : [video](https://photos.app.goo.gl/AqDvbGj7fGZXpYhV9)

- Amplificador con fuentes de switching reproduciendo musica desde un celular en un parlante de 8 Ohm de baja potencia : [video](https://photos.app.goo.gl/HTU1mSpep7PGP6fW8)


---

## [Amplificador](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Amplificador)

<p align="center">
  <img src="imgs/amp_classG.jpg?raw=true" width="1000" title="hover text">
</p>


## [Fuentes Conmutadas](https://github.com/tobias-liaudat/ClassG_amp/tree/master/Fuente%20SW)

<p align="center">
  <img src="imgs/fuentes_conmutadas_2.jpg?raw=true" width="1000" title="hover text">
</p>

