--
cssclass: no-table
---
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
<div style="page-break-after: always;"></div>

# Desarrollo
---
## Practica 1 - Potenciómetro
Durante esta práctica, con ayuda del Arduino buscamos comprender el funcionamiento de un potenciómetro, así como la utilidad de los puertos análogos del Arduino y las instrucciones que los acompañan. Para ello, conectamos voltaje y tierra en cada extremo del potenciómetro (tal y como haríamos con una resistencia normal) y del pin medio obtenemos la señal que mandamos al puerto `A0` del Arduino, y que es leído con la instrucción `analogRead`. 
### Código utilizado

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
### Diagrama de conexión y esquemático

![breadboard|600](practica-1_breadboard.svg)
![schematic|500](practica-1_schematic.svg)

### Evidencia

| ![evidencia](practica-1_evidencia.png) | ![evidencia2](practica-1_evidencia-2.png) |
| ---------------------------------------- | -------------------------------------- |
<div style="page-break-after: always;"></div>

## Practica 2 - Delay con potenciómetro
Para esta práctica aplicaremos el conocimiento obtenido durante la práctica anterior para controlar los intervalos de prendido y apagado de un foco led intermitente, esto mandando la lectura del potenciómetro directamente a la función `delay` que viene incorporada en el Arduino, además de incorporar la función `digitalWrite` para prender y apagar el foco led según si le damos el valor `HIGH` o `LOW` en el código.
### Código utilizado
```cpp
void setup() {
  pinMode(9, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  Serial.println(analogRead(A0));

  digitalWrite(9, HIGH);
  delay(analogRead(A0));

  digitalWrite(9, LOW);
  delay(analogRead(A0));
}

```
### Diagrama de conexión y esquemático

![breadboard|600](practica-1_breadboard.svg)
![schematic|500](practica-1_schematic.svg)

### Evidencia
| ![evidencia](practica-2_evidencia.png) | ![evidencia2](practica-2_evidencia-2.png) |
| ---------------------------------------- | -------------------------------------- |
<div style="page-break-after: always;"></div>

## Practica 3 – Control de voltaje con potenciómetro
Al igual que con la práctica anterior, en esta ocasión utilizaremos los conceptos aprendidos en la primera práctica, sin embargo, ahora se utiliza el potenciómetro para calcular una relación entre su propio valor y el de la resistencia, es decir que, digamos si el valor máximo del potenciómetro es igual a 5 volts, según una medida $x$ ¿cuánto voltaje obtenemos?, se puede ver que es una regla de tres, y así mismo viene incluido en el código. 
### Código utilizado
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  float potenRead = analogRead(A0);
  Serial.print("Valor Analogico: ");
  Serial.print(potenRead);
  Serial.print("Voltaje: ");
  Serial.println(5*potenRead/1023);
}
```
### Diagrama de conexión y esquemático

![breadboard|600](practica-3_breadboard.svg)
![schematic|500](practica-3_schematic.svg)

### Evidencia
| ![evidencia](practica-3_evidencia.png) | ![evidencia2](practica-3_evidencia-2.png) |
| ---------------------------------------- | -------------------------------------- |
<div style="page-break-after: always;"></div>
## Practica 4 – PWM con push button
Con esta practica buscamos comprender el funcionamiento y la utilidad de los pulsos PWM al aplicarlos sobre un foco led. Para el funcionamiento entendemos que, como el nombre indica los **pulsos PWM** son claramente pulsos, es decir, subidas y bajadas rápidas de voltaje en intervalos definidos. En este caso utilizamos los pulsos para implementar un foco led que se enciende y apaga de forma gradual en lugar de cambiarse instantáneamente.
### Códigos utilizados
```cpp
int pushButton = 2;
int ledPin = 13;
int cont = 0;

void setup() {
  Serial.begin(9600);
  pinMode(pushButton, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop(){
  int buttonState = digitalRead(pushButton);
  cont++;
  Serial.println(cont);
  digitalWrite(ledPin, buttonState);
  delay(1);
}
```
### Diagrama de conexión y esquemático
![breadboard|600](practica-4_breadboard.svg)
![schematic|500](practica-4_schematic.svg)

### Evidencia
![evidencia](practica-4_evidencia.png)

<div style="page-break-after: always;"></div>

## Practica 5 – PWM con Fade In y Fade Out
Con esta practica buscamos comprender el funcionamiento y la utilidad de los pulsos PWM al aplicarlos sobre un foco led. Para el funcionamiento entendemos que, como el nombre indica los **pulsos PWM** son claramente pulsos, es decir, subidas y bajadas rápidas de voltaje en intervalos definidos. En este caso utilizamos los pulsos para implementar un foco led que se enciende y apaga de forma gradual en lugar de cambiarse instantáneamente.
### Código utilizado
```cpp
int ledPin = 13;
int cont = 0;

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  for (int fadeValue = 0 ; fadeValue <= 255; fadeValue += 5) {
    analogWrite(ledPin, fadeValue);
    delay(30);
  }
  for (int fadeValue = 255 ; fadeValue >= 0; fadeValue -= 5) {
    analogWrite(ledPin, fadeValue);
}
```
### Diagrama de conexión y esquemático
![breadboard|600](practica-5_breadboard.svg)
![schematic|500](practica-5_schematic.svg)

### Evidencia
![evidencia](practica-5_evidencia.png)

<div style="page-break-after: always;"></div>

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
### Diagrama de conexión y esquemático
![breadboard|600](practica-6_breadboard.svg)
![schematic|500](practica-6_schematic.svg)

### Evidencia
![evidencia](practica-6_evidencia.png)
## Práctica 7 - Interrupción
En el circuito de esta práctica utilizamos de nuevo el pin 2 como entrada digital del botón pulsador, pero además le asociamos una interrupción que se ejecuta cuando detecta una transición `LOW` en dicho pin. En nuestro caso el servicio de interrupción es llamado `ServicioBoton` y lo que hace es incrementar en 1 el valor del contador. En el servicio de interrupción utilizamos la variable `T0` y la función `millis()` para evitar que el contador detecte pulsaciones “fantasma”. Por último, se muestra el número de veces que se presiona el botón en el serial monitor.
### Código utilizado
```cpp
int contador = 0;
int n = contador;

void setup() {
  // initialize serial communication at 9600 bits per second:
 
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
### Diagrama de conexión y esquemático
![breadboard|600](practica-7_breadboard.svg)
![schematic|500](practica-7_schematic.svg)

### Evidencia
![evidencia](practica-7_evidencia.png)
## Práctica 8 - LED con interrupciones
En este circuito utilizamos un `timer![[Pasted image 20230309013236.png]]![[Pasted image 20230309013236.png]]![[Pasted image 20230309013236.png]]`, el cual asociamos con una interrupción que se activa al alcanzar la cuenta máxima. El servicio de interrupción `ISR_Blink` se encarga de cambiar el estado del LED en el pin 13, además de aumentar un contador que señala en número de parpadeos del LED. Finalmente, el serial monitor muestra el valor del contador o número de ciclos del LED.

```cpp
volatile int contador = 0;
int n = contador;
long T0 = 0;

void setup() {
  pinMode(2, INPUT);
  Serial.begin(9600);
  attachInterrupt(0, ServicioBoton, LOW);
}

void loop() {
  if (n != contador){ 
    Serial.println(contador);
    n = contador;
  }
}

void ServicioBoton(){
  if(millis() > T0 + 250) {
    contador++;
    T0 = millis();
  } 
}
```
### Diagrama de conexión y esquemático
![breadboard|600](practica-8_breadboard.svg)
![schematic|500](practica-5\8_schematic.svg)

### Evidencia
![evidencia](practica-8_evidencia.png)
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
### Diagrama de conexión y esquemático
![breadboard|600](practica-9_breadboard.svg)
![schematic|500](practica-9_schematic.svg)

### Evidencia
![evidencia](practica-9_evidencia.png)
## Practica 10 - Sensor IR
Para esta práctica se utilizó dos diodos fototransistores, uno con capacidad de transmitir una señal infrarroja y otro con la capacidad de recibir dicha señal. El circuito únicamente tenía que encender un LED además de que no se necesitaba el uso de un Arduino (salvo el voltaje que este proporciona). Este circuito análogo tiene como objetivo ser utilizado en la última práctica de este parcial.
### Diagrama de conexión y esquemático
![breadboard|600](practica-10_breadboard.svg)
![schematic|500](practica-10_schematic.svg)

### Evidencia
![evidencia](practica-10_evidencia.png)
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
### Diagrama de conexión y esquemático
![breadboard|600](practica-final_breadboard.svg)
![schematic|500](practica-final_schematic.svg)

### Evidencia
![evidencia](practica-final_evidencia.png)