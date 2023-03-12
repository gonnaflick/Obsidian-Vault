---
cssclass: no-table
---
---
# Introducción
Durante este primer parcial se trabajó con el microcontrolador Arduino Uno y nos enfocamos en aprender todas las opciones que este ofrece, tales como:
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
<div style="page-break-after: always;"></div>

# Desarrollo
---
## Práctica 6 - Interrupciones con push button

Este circuito lo que hace es leer la entrada digital en el pin 2 que corresponde al botón pulsador mientras utiliza el pin 13 como la salida para un LED dependiendo del estado actual del botón pulsador (si se presiona o no). El estado del botón se muestra en el serial monitor. 

```cpp
int pushButton = 2;

void setup() {
  pinMode(13, OUTPUT);
  Serial.begin(9600);
  pinMode(pushButton, INPUT);
}

void loop() {
  int buttonState = digitalRead(pushButton);
  digitalWrite(13,buttonState);
  Serial.println(buttonState);
  delay(1);
}
```
### Diagrama de conexión
![breadboard|300](practica-6_breadboard.svg)

### Evidencia
![evidencia|300](practica-6_evidencia.jpg)

<div style="page-break-after: always;"></div>

## Práctica 7 - Interrupción
En el circuito de esta práctica utilizamos de nuevo el pin 2 como entrada digital del botón pulsador, pero además le asociamos una interrupción que se ejecuta cuando detecta una transición `LOW` en dicho pin. En nuestro caso el servicio de interrupción es llamado `ServicioBoton` y lo que hace es incrementar en 1 el valor del contador. En el servicio de interrupción utilizamos la variable `T0` y la función `millis()` para evitar que el contador detecte pulsaciones “fantasma”. Por último, se muestra el número de veces que se presiona el botón en el serial monitor.
### Código utilizado
```cpp
int contador = 0;
int n = contador;

void setup() {
  Serial.begin(9600);
  attachInterrupt(0, ServicioBoton, FALLING);

}

void loop() {
  if (n != contador){ 
    Serial.println(contador);
    n = contador;
  }
}

void ServicioBoton(){
  contador++;
}
```
### Diagrama de conexión
En esta práctica no se requirió realizar ninguna conexión. El Arduino realizaba el cálculo interno.

### Evidencia
![evidencia|400](practica-7_evidencia.jpg)

<div style="page-break-after: always;"></div>

## Práctica 8 - LED con interrupciones
En este circuito utilizamos un `timer`, el cual asociamos con una interrupción que se activa al alcanzar la cuenta máxima. El servicio de interrupción `ISR_Blink` se encarga de cambiar el estado del LED en el pin 13, además de aumentar un contador que señala en número de parpadeos del LED. Finalmente, el serial monitor muestra el valor del contador o número de ciclos del LED.

```cpp
#include<TimerOne.h>
const int led = 13;
int ledState = LOW;
volatile unsigned long blinkCount = 0;

void setup() {
  pinMode(led, OUTPUT);
  Timer1.initialize(250000);
  
  Serial.begin(9600);
  Timer1.attachInterrupt(0, ServicioBoton, LOW);
}

void ISR_Blink() {
  ledState = !ledState;
  blinkCount++;
}

void loop() {
  unsigned long N;
  digitalWrite(led, ledState);
  noInterrupts();
  N = blinkCount;
  interrupts();
  Serial.print("Ciclos=");
  Serial.println(N);
  delay(500);

}
```
### Diagrama de conexión
![breadboard|300](practica-8_breadboard.svg)

### Evidencia
![evidencia|500](practica-8_evidencia.png)

<div style="page-break-after: always;"></div>

## Práctica 9 - RPM con push button
Para el circuito de esta práctica utilizamos de nuevo las interrupciones, dos en este caso. La primera está asociada al pin 2 y se activa cuando se oprimen el botón pulsador. Este servicio de interrupción `ServicioBoton` incrementa en 1 el contador de las pulsaciones, usando a la vez la función milis para evitar pulsaciones “fantasma” o demasiado rápidas. Por su parte, la segunda interrupción está asociada a un `timer` y se ejecuta cada segundo. El servicio de interrupción `ISR_Blink` incrementa en 1 el contador del tiempo y cuando alcanza el valor de 60 segundos muestra la información sobre la cantidad de pulsaciones y realiza una operación para obtener las revoluciones por minuto (RPM).

### Código utilizado
```cpp
#include<TimerOne.h>

volatile int botonCount = 2;
long T0 = 0;
int desplegar = 0;
int timer = 0;


void setup() {  
  Timer1.initialize(1000000);
  Serial.begin(9600);
  attachInterrupt(0, ServicioBoton, LOW);
  Timer1.attachInterrupt(ISR_Blink);
}

void ServicioBoton(){
  if(millis() > T0 + 20) {
    botonCount++;
    T0 = millis();
  }
}

void ISR_Blink() {
  timer++;
  if(timer==60){
    desplegar = 1;
  }
  Serial.println(timer);
}

void loop() {
  unsigned long N;
  noInterrupts();
  N = botonCount;
  interrupts();
  if (desplegar == 1)
  {
    Serial.print("RPM=");
    Serial.println(N/7);
    Serial.print("Cantidad de pulsaciones = ");
    Serial.println(N);
    desplegar = 0;
    timer = 0;
    botonCount = 0;
  }  
  delay(1);
}
```
### Diagrama de conexión
![breadboard|400](practica-9_breadboard.svg)

### Evidencia
![evidencia|400](practica-9_evidencia.jpg)

<div style="page-break-after: always;"></div>

## Practica 10 - Sensor IR
Para esta práctica se utilizó dos diodos fototransistores, uno con capacidad de transmitir una señal infrarroja y otro con la capacidad de recibir dicha señal. El circuito únicamente tenía que encender un LED además de que no se necesitaba el uso de un Arduino (salvo el voltaje que este proporciona). Este circuito análogo tiene como objetivo ser utilizado en la última práctica de este parcial.
### Código utilizado
Al ser un circuito análogo no fue necesario realizar código.

### Diagrama de conexión
![breadboard|450](practica-10_breadboard.svg)

### Evidencia
![evidencia|450](practica-10_evidencia.jpg)

<div style="page-break-after: always;"></div>

## Practica Final - Medición de RPM de un ventilador con sensor IR
Esta práctica final busca combinar el circuito de RPM con push button y el sensor IR, donde este último realizara la tarea del push button al ser colocado uno de los sensores detrás de las aspas del ventilador y otro frente a las aspas. La idea es simple, las aspas bloquearán la señal infrarroja y de esta forma se medirán las revoluciones por minuto. Debido a que nuestro ventilador cuenta con 7 aspas, estas serán incluidas en la fórmula. Como dato adicional, se requirió una fuente de alimentación exclusiva para el ventilador (en nuestro caso una batería de ácido plomo de 12 volts).
### Código utilizado
```cpp
#include<TimerOne.h>

volatile int receptorCount = 2;
long T0 = 0;
int desplegar = 0;
int timer = 0;

void setup() {  
  Timer1.initialize(1000000);
  Serial.begin(9600);
  attachInterrupt(0, ServicioReceptor, LOW);
  Timer1.attachInterrupt(ISR_Blink);
}

void ServicioReceptor(){
  if(millis() > T0 + 1) {
    receptorCount++;
    T0 = millis();    
  }
}

void ISR_Blink() {
  timer++;
  if(timer==60){
    desplegar = 1;
  }
  Serial.println(timer);
}

void loop() {
  unsigned long N;
  noInterrupts();
  N = receptorCount;
  interrupts();
  if (desplegar == 1)
  {
    Serial.print("RPM de un abanico de 7 aspas=");
    Serial.println(N/7);
    Serial.print("Cantidad de aspas contadas = ");
    Serial.println(N);
    desplegar = 0;
    timer = 0;
    receptorCount = 0;
  }  
  delay(1);
}
```
### Diagrama de conexión
![breadboard|450](practica-final_breadboard.svg)

### Evidencia
![evidencia|450](practica-final_evidencia.jpg)