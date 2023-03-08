##### Prácticas de laboratorio
---
# Introducción
Durante este primer parcial se trabajó con el microcontrolador Arduino Uno y nos enfocamos en aprender todas las opciones que este ofrece, tales como
- Interrupciones
- Timers
- Señales de tipo:
	- Analógicas
	- Digitales
	- PWM

Además, aprendimos a trabajar con distintos componentes electrónicos, como:
- LEDs
- Resistencias
- Potenciómetros
- Switches pulsadores
- Sensores IR
- Transistores
- Fuentes de energía.

Todos estos conceptos fueron vistos realizando diversas prácticas durante el parcial, además de una práctica final, la cual comprende todo lo visto en clase. 
Adicionalmente, en este reporte incluimos la descripción de la práctica correspondiente, una imagen del circuito como evidencia de la realización de la práctica, el código utilizado para programar el Arduino Uno y una hoja de datos que muestra la conexión de cada uno de los circuitos utilizados.

# Desarrollo
## Practica 1
En esta primera práctica se aprendió a trabajar con señales analógicas configuradas como input. Este código en específico únicamente se encarga de leer el valor y mostrarlo en la pantalla serial del IDE de Arduino.

```cpp
void setup() {
   Serial.begin(9600);
}

void loop() {
  int value = analogRead(A0);
  Serial.print("Valor A0: ");
  Serial.println(value);
  delay(1);
}
```
A continuación se muestra el diagrama de conexión del circuito:

Finalmente se incluye la foto de evidencia del laboratorio:
![[Pasted image 20230308115116.png]]![[Pasted image 20230308115209.png]]
