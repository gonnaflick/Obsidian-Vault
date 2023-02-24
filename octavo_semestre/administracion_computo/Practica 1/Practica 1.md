---
cssclass: custom
---
#### Cálculo de potencias para una sala de cómputo 

---
# Introducción
En esta práctica se nos solicitó medir la corriente que consume una computadora de escritorio a la que tengamos acceso. Dicho consumo puede ser obtenido con cualquiera de las siguientes herramientas: 
- Multímetro
- Pinza amperímetra
- Medidor de consumo de corriente
> *En mi caso, he tomado la decision de utilizar la pinza amperimetra y realizar los calculos necesarios para obtener las variables faltantes.*

Como continuacion de esta primera actividad, con los resultados obtenido se debe calcular la cantidad de energia que consumirían 20 computadoras.

Finalmente, y como segunda parte de la actividad, se nos solicita calcular y documentar la iluminación necesaria para la sala de un centro de cómputo. Los puntos a tomar en cuenta en dicho análisis deben ser: 
- Tipo de luminaria
- Consumo en watts
- Lux
```ad-note
title: Parametros a tomar a consideracion:
* Se debe considerar un **factor de potencia del 70%** a la hora de hacer el cálculo de la potencia obtenida.
* Considerar un **margen de seguridad del 20%** para los 20 equipos de computo.
* El area a iluminar del centro de computo hipotetico queda a eleccion del alumno*.
```
# Desarrollo

---
## Medición de consumo de un equipo de cómputo
El objetivo de esta medición es analizar el consumo de energía de una computadora en distintos escenarios de uso, con el fin de tener una idea hipotética del consumo que tendrían un conjunto de computadoras en un centro de cómputo para realizar un análisis al respecto.

```ad-warning
title: Dato importante a considerar
El equipo de computo el cual se utilizo para realizar las tomas cuenta con un regulador de voltaje. El voltaje sin regulador


| Voltaje sin regular | Voltaje regulado |
| --- | --- | 
| ![Voltaje sin regular](voltaje_sin_regular.jpg) | ![Voltaje regulado](voltaje_regulado.jpg) |
```
### Escenarios de uso
Para este caso tomé la decisión de analizar tres distintos casos en los que se encontró la computadora:
* **Uso simple:** este escenario representa el consumo de energía cuando la computadora únicamente se encuentra ejecutando tareas simples como ejecución de programas de fondo, scripts, o simplemente la computadora se encuentra *encendida de fondo*. 
* **Uso cotidiano:** este escenario representa el consumo de energía de la computadora cuando se utilizan tareas simples y cotidianas, como el uso de navegadores, editores de texto, clientes de computadora, aplicaciones simples sin mucho poder gráfico o procesamiento.
* **Uso alto:** este escenario representa el consumo de energía de la computadora cuando se utilizan aplicaciones más exigentes, como juegos o programas de diseño gráfico (edición de imágenes, video, uso de vectores o creación de modelos en 3D), que hacen trabajar a la GPU y el procesador entre un 80% y 100%.
### Cálculos
A continuación se muestran los cálculos de consumo de energía para cada escenario de uso. Además, se incluirá una tabla en la que se analizará cada caso con mayor detenimiento, esto con el fin de poder analizar de mejor forma el consumo energético que tendrían los 20 equipos de cómputo dependiendo de su uso.
```ad-info
title: La formula que utilizaremos para calcular la potencia de la computadora es:
$$P=V \times I \times PF$$

**Donde:**

- $P=$ Potencia
- $V=$ Voltaje
- $I=$ Intensidad
- $PF=$ Factor de potencia
```

##### Caso 1: Uso simple
Para este primer caso, se obtuvo un consumo con medidas alrededor de los 0.8 A teniendo un pico máximo de 1.0 A por ende podemos decir que el consumo de un equipo que se encuentra realizando tareas de fondo es:
* $P =$ ?
* $I =$ 0.8A
* $V =$ 110V
-   P = (0.5 A) x (110 V) x (0.7) = 38.5 W
-   Potencia por hora = 38.5 Wh