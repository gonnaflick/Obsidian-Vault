---
cssclass: custom
banner: octavo_semestre/administracion_computo/Practica 1/etc/centro_computo.jpg
Matricula: 338906
Nombre: Jesus Alejandro Jimenez Hernandez
GitHub: https://github.com/gonnaflick
Fecha: 2023-02-25
Universidad: Universidad Autonoma de Chihuahua
---
#### Cálculo de potencias para una sala de cómputo 

---
# Introducción
En esta práctica se nos solicitó medir la corriente que consume una computadora de escritorio a la que tengamos acceso. Dicho consumo puede ser obtenido con cualquiera de las siguientes herramientas: 
- Multímetro
- Pinza amperímetra
- Medidor de consumo de corriente
> *En mi caso, he tomado la decisión de utilizar la pinza amperímetra y realizar los cálculos necesarios para obtener las variables faltantes.*

Como continuación de esta primera actividad, con los resultados obtenida se debe calcular la cantidad de energía que consumirían 20 computadoras.

Finalmente, y como segunda parte de la actividad, se nos solicita calcular y documentar la iluminación necesaria para la sala de un centro de cómputo. Los puntos a tomar en cuenta en dicho análisis deben ser: 
- Tipo de luminaria
- Consumo en watts
- Lux

```ad-note
title: Parámetros a tomar a consideración:
* Se debe considerar un **factor de potencia del 70%** a la hora de hacer el cálculo de la potencia obtenida.
* Considerar un **margen de seguridad del 20%** para los 20 equipos de cómputo.
* El área a iluminar del centro de cómputo hipotético queda a elección del alumno*.
```
# Desarrollo

---
## Medición de consumo de un equipo de cómputo
El objetivo de esta medición es analizar el consumo de energía de una computadora en distintos escenarios de uso, con el fin de tener una idea hipotética del consumo que tendrían un conjunto de computadoras en un centro de cómputo para realizar un análisis al respecto.

```ad-warning
title: Dato importante a considerar
Es importante aclarar que en el lugar donde se realizaron las mediciones, el voltaje de entrada es de **132.8 volts**. Sin embargo, debido a que la computadora está conectada a un regulador, esta recibe una alimentación de **117.6 volts**. A continuación, se presentan imágenes que muestran las mediciones correspondientes:

<div id="tabla-voltajes">


| ![Voltaje sin regular](voltaje_sin_regular.jpg) | ![Voltaje regulado](voltaje_regulado.jpg) |
| --- | --- | 
| **Voltaje sin regular** | **Voltaje regulado** |
</div>


```

### Escenarios de uso
Para este caso tomé la decisión de analizar tres distintos casos en los que se encontró la computadora:
* **Uso mínimo:** este escenario representa el consumo de energía cuando la computadora únicamente se encuentra ejecutando tareas simples como ejecución de programas de fondo, scripts, o simplemente la computadora se encuentra *encendida de fondo*.
* **Uso cotidiano:** este escenario representa el consumo de energía de la computadora cuando se utilizan tareas simples y cotidianas, como el uso de navegadores, editores de texto, clientes de computadora, aplicaciones simples sin mucho poder gráfico o procesamiento.
* **Uso máximo:** este escenario representa el consumo de energía de la computadora cuando se utilizan aplicaciones más exigentes, como juegos o programas de diseño gráfico (edición de imágenes, video, uso de vectores o creación de modelos en 3D), que hacen trabajar a la GPU y el procesador entre un 80% y 100%.

| **Uso mínimo**                | **Uso cotidiano**                   | **Uso máximo**                |
| ----------------------------- | ----------------------------------- | ----------------------------- |
| ![Uso minimo](uso_minimo.jpg) | ![Uso cotidiano](uso_cotidiano.jpg) | ![Uso maximo](uso_maximo.jpg) | 

## Cálculos
A continuación se muestran los cálculos de consumo de energía para cada escenario de uso. Además, se incluirá una tabla en la que se analizará cada caso con mayor detenimiento, esto con el fin de poder analizar de mejor forma el consumo energético que tendrían los 20 equipos de cómputo dependiendo de su uso.

```ad-info
title: La fórmula que utilizaremos para calcular la potencia de la computadora es:
$$P=V \times I \times PF$$

**Donde:**

- $P=$ Potencia
- $V=$ Voltaje
- $I=$ Intensidad
- $PF=$ Factor de potencia
```

### Caso 1: Uso simple
Para este primer caso, los datos que utilizaremos serán los siguientes:
$$PF = 0.7$$
$$I = 0.75\text{A}$$
$$V = 117.6\text{V}$$
Despejamos la ecuación mencionada anteriormente con los datos y resolvemos:
$$P = (0.75\text{A}) \times (117.6\text{V}) \times (0.7) = 61.74\text{W}$$
Tenemos entonces que el valor de la potencia para este caso es igual a **61.74 watts**.

### Caso 2: Uso cotidiano
Para este segundo caso, los datos que utilizaremos serán los siguientes:
$$PF = 0.7$$
$$I = 1.29\text{A}$$
$$V = 117.6\text{V}$$
Despejamos la ecuación mencionada anteriormente con los datos y resolvemos:
$$P = (1.29\text{A}) \times (117.6\text{V}) \times (0.7) = 106.19\text{W}$$
Tenemos entonces que el valor de la potencia para este caso es igual a **106.19 watts**.

### Caso 3: Uso máximo
Para este último caso, los datos que utilizaremos serán los siguientes:
$$PF = 0.7$$
$$I = 2.3\text{A}$$
$$V = 117.6\text{V}$$
Despejamos la ecuación mencionada anteriormente con los datos y resolvemos:
$$P = (2.3\text{A}) \times (117.6\text{V}) \times (0.7) = 189.33\text{W}$$
Tenemos entonces que el valor de la potencia para este caso es igual a **189.33 watts**.

### Tabla de datos
Esta sección tiene como propósito únicamente mostrar en una tabla los datos obtenidos a partir de las mediciones y cálculos analíticos realizados en la sección anterior. Esta información nos proporciona una mejor comprensión sobre el consumo energético que un centro de cómputo podría llegar a tener, según el tipo de tareas que se realicen en él lo que nos puede ayudar a tomar decisiones financieras para buscar eficientar el consumo tal como mejorar el factor de potencia. 


| **Escenario de uso** | **Corriente** | **Voltaje** | **Potencia** |
| -------------------- | ------------- | ----------- | ------------ |
| **Uso mínimo**       | 0.75A         | 117.6V      | **61.74W**   |
| **Uso cotidiano**    | 1.29A         | 117.6V      | **106.19W**  |
| **Uso máximo**       | 2.3A          | 117.6V      | **189.33W**  |

```ad-important
title: Importante
Notese que estos valores no toman en cuenta ningun margen de seguridad en cuenta.
```

## Medición de consumo de 20 equipos de cómputo
Como siguiente punto en la práctica, se debe analizar el consumo que tendrían los 20 equipos de cómputo si tuvieran el mismo consumo energético que la computadora previamente analizada. Se presenta una tabla que analiza dicho comportamiento para los tres tipos de escenarios de uso:


| **Escenario de uso** | **Potencia sin margen de seguridad** | **Potencia con margen de seguridad del 20%** |
| ---------------- | ----------------------------------------- | ----------------------------------------- |
| **Uso mínimo**       | 1234.8W                                   | 1481.76W                                  |
| **Uso cotidiano**    | 2123.8W                                   | 2548.56W                                  |
| **Uso máximo**       | 3786.6W                                   | 4543.92W                                  |

## Iluminación para un centro de cómputo
Como ultima instrucción de esta práctica se nos solicitó realizar, calcular y documentar la iluminación necesaria para un centro de cómputo.
Investigando los distintos tipos de iluminación existentes, tomé la decisión de iluminar el centro de cómputo con luz  tipo LED debido a cuatro principales características que este tipo de iluminaria presenta:
- Eficiencia energética.
- Durabilidad.
- Calidad de la luz.
- Reducción de calor.

```ad-info
title: Datos importantes para esta sección
* Para tema de esta práctica decidí basarme en la hoja de datos de un foco LED de la marca **ENERGETIC**.
* El área a iluminar es de $100m^2$.
* Se requirió asumir ciertos factores para poder dar un estimado.
```

### Hoja de datos
El foco LED a analizar cuenta con las siguientes características:
- Entrada A19.
- Consumo de 8.5 Watts.
- Iluminación de 750 Lumens.
- Ángulo de iluminación de 220°.
- Color blanco frío 5000K.
### Cálculos
En esta sección se muestran dos métodos para calcular la cantidad de focos necesarios dependiendo de las variables que tengamos a disposición. 
#### Método 1
Este primer método probablemente es el **peor** que se puede realizar, simplemente es asumir que un foco LED de 8.5W tiene la capacidad de iluminar alrededor de los 10 metros cuadrados. 
A continuación se muestra el procedimiento a utilizar:
```ad-note
title: Formula a utilizar:
$$
\frac{Area\ a\ iluminar(m^2)}{Area\ que\ el\ foco\ puede\ iluminar(m^2)}=Cantidad\ de\ focos
$$
```

Resolviendo tenemos que:

$$100m^2/10m^2=10\ focos$$
**Se requieren 10 focos LED para un área de 100 metros cuadrados.**

```ad-error
title: Importante
Este método es solo un cálculo rápido que nos puede dar una idea de cuantos focos se requieren. Sin embargo, es incorrecto al no tomar a consideración ninguna característica del foco.
```
#### Método 2
Esta es probablemente el mejor método, ya que toma a consideración todas las características del foco.
1. Lo primero que hay que hacer es recopilar los datos necesarios:
	- El foco tiene una luminosidad de 750 lumens.
	- El centro de cómputo tiene un área de 100 metros cuadrados, es decir, el área a iluminar es un área de 10 metros x 10 metros.
	- Investigando la iluminación recomendada para este tipo de habitaciones, se recomienda una luminosidad entre los 3000 y 5000 lumens (en este caso se tomará el promedio, es decir, 4000 lumens).
2. El siguiente paso es calcular los luxes necesarios para el centro de cómputo, esto debido a que se nos pide en la práctica:
```ad-note
title: La formula a utilizar es la siguiente:
$$
\frac{Luminosidad(lumen)}{Area(m^2)} = Iluminiscencia(lux)
$$
```
- Despejando la fórmula tenemos entonces que:
$$\frac{4000\ lumen}{100m^2}=40\ lux$$
- ** Necesitamos entonces 40 luxes para iluminar la habitación.**
3.  Finalmente lo único que falta por hacer es calcular la cantidad de focos que se requiere para tener un nivel de luminosidad de 4000 lumens.
```ad-note
title: La formula a utilizar es la siguiente:
$$
\frac{Luminosidad\ del\ area(lumen)}{Luminosidad\ del\ foco(lumens)} = Cantidad\ de\ focos
$$
```
- Despejando la fórmula entonces tenemos que:

$$
\frac{4000\ lumen}{750\ lumen} = 5.33\ focos
$$
**Se requieren entre 5-6 focos LED para iluminar un área de 100 metros cuadrados.**
```ad-warning
title: Importante
La cantidad de lux en una habitación se ve afectada por la cantidad de focos que se utilicen, lo que significa que la cifra final para lograr los 40 luxes de luminiscencia puede variar. La cantidad adecuada de focos se especificará en la siguiente sección.
```
### Resultados y análisis del consumo
A continuación, se muestra un vaciado de datos de lo analizado anteriormente:


| **Cantidad** | **Tipo** | **Método de cálculo** | **Luminosidad** | **Luminiscencia** | **Consumo** |
| ------------ | -------- | --------------------- | --------------- | ---------------- | ----------- |
| 5            | LED      | Método 2              | 3750 lumens     | 37.5 lux         | 42.5 watts  |
| 6            | LED      | Método 2              | 4500 lumens     | 45 lux           | 51 watts    |
| 10           | LED      | Método 1              | 7500 lumens     | 75 lux           | 85 watts    |

```ad-check
title: La cantidad correcta
Recomiendo utilizar 6 focos como la cantidad adecuada de iluminación, ya que es un número ligeramente superior al recomendado y no tan excesivo como el metodo 1.
```
## Conclusión
---
Durante este parcial, se trataron diferentes temas relacionados con los centros de cómputo, tales como su diseño, planeación, medición y ahorro. Específicamente, se enfocó en el monitoreo del consumo de energía y los métodos para eficientar costos, esto con el fin de poder buscar las opciones financieramente correctas. 

El analizar el consumo de mi computadora me dio la iniciativa de tomar otras dos medidas para ver como se comportaría un centro de cómputo centrado a distintas tareas, lo cual me dio una idea mejor de que tan importante es el tener inclusive como se mencionó estaciones eléctricas, ya que el consumo si resulto ser elevado al hablar de 20 equipos.

Además, para mí, el tema de la iluminación resultó desconocido hasta este parcial. Sin embargo, se comprendió que es un aspecto esencial para garantizar un ambiente de trabajo seguro y saludable para los empleados. Investigando al respecto, descubrí los puntos negativos al tener una mala iluminación, ya que esta puede causar fatiga ocular, dolores de cabeza y otros problemas de salud, mientras que una iluminación excesiva puede generar molestia y reflejos que dificulten la visualización de las pantallas de los equipos de cómputo.
