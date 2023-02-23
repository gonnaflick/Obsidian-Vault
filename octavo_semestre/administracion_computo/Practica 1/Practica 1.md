# Cálculo de potencias para una sala de cómputo 
## Introducción
En esta práctica se nos solicitó medir la corriente que consume una computadora de escritorio a la que tengamos acceso. Dicho consumo puede ser obtenido con cualquiera de las siguientes herramientas: 
- Multímetro
- Pinza amperímetro
- Medidor de consumo de corriente
Tambien debemos calcular la cantidad de potencia que consumirían 20 computadoras, suponiendo que tengan el mismo consumo que la computadora originalmente medida, dando un margen de seguridad del 20%.
```ad-important
title: Importante
Se debe considerar un factor de potencia del 70% a la hora de hacer el cálculo de la potencia obtenida.
```
Finalmente, se nos solicita calcular y documentar la iluminación necesaria para la sala de un centro de cómputo. Los puntos a tomar en cuenta en dicho análisis deben ser: 
- Tipo de luminaria
- Consumo en watts
- Lux

## Desarrollo
### Medición de consumo de un equipo de cómputo
El objetivo de esta medicion es analizar el consumo de energía de una computadora en distintos escenarios de uso, con el fin de tener una idea hipotetica del consumo que tendrian un conjunto de computadoras en un centro de computo  para realizar un analisis al respecto.
```ad-warning
title: Dato importante a considerar
El equipo de computo el cual se utilizo para realizar las tomas cuenta con un regulador de voltaje. El voltaje sin regulador
![[voltaje_sin_regular.jpg]]{width=10%}
```

#### Escenarios de uso
Para este caso tome la decision de analizar tres distintos casos en los que se encontro la computadora:
* **Uso simple:** este escenario representa el consumo de energía cuando la computadora unicamente se encuentra ejecutando tareas simples como ejecucion de programas de fondo, scripts, o simplemente la computadora se encuentra en *stand by*. 
* **Uso cotidiano:** este escenario representa el consumo de energía de la computadora cuando se utilizan tareas simples y cotidianas, como el uso de navegadores, manejadores de texto, clientes de computadora, aplicaciones simples sin mucho poder grafico o procesamiento.
* **Uso alto:** este escenario representa el consumo de energía de la computadora cuando se utilizan aplicaciones más exigentes, como juegos o programas de diseño gráfico (edicion de imagenes, video, uso de vectores o creacion de modelos en 3D), que hacen trabajar a la GPU y el procesador entre un 80% y 100%.
#### Calculos
A continuación se muestran los cálculos de consumo de energía para cada escenario de uso. Ademas, se incluira una tabla en la que se analisara cada caso con mayor detenimiento, esto con el fin de poder analizar de mejor forma el consumo energetico que tendrias los 20 equipos de computo dependiendo de su uso.
```ad-info
title: La formula que utilizaremos para calcular la potencia de la computadora es:
$$P=V*I*PF$$
Donde:
* $P =$ *Potencia*
* $V =$ *Voltaje*
* $I =$ *Intensidad*
* $PF =$ *Factor de potencia*
```

##### Caso 1: Uso simple
Para este primer caso, se obtuvo un consumo con medidas alrededor de los 0.8A teniendo un pico maximo de 1.0A por ende podemos decir que el consumo de un equipo que se encuentra realizando tareas de fondo es:
* *$P =$ ?
* $I = 0.8A$
* $V = 110V$
-   P = (0.5 A) x (110 V) x (0.7) = 38.5 W
-   Potencia por hora = 38.5 Wh