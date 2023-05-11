## Simulando VA's normales y uniformes en Python

Ahora que ya vimos los fundamentosformales de como simular una VA normal y una uniforme, vamos a implementar dicho simulador en Python. Primero veamos como simular una VA uniforme entrea y b.
$$X\, \Sigma \,U[a,b]$$
Asi que queremos simular un valor k tal que:
$$k=F^{-1}_x(r)\text{ donde r es un numero seudoleatorio}$$
de modo que si $x \Sigma U{a,b}$ entonces:
$$k=(b-a)\times r+a$$
En Python esto lo implementamos con la siguiente funcion:

```python
def uniforme(a,b):
	r=random.random()
	k=(b-a)*r+a
	reutrn k
```
Notese que esta funcion nos exige importar la libreria **random** (ya viene instalada nativamente en Python), podriamos hacerle asi:

```python
def uniforme(a,b):
	r=rnd.random()
	k=(b-a)*r+a
	return k
```

```ad-info
title: Nota
La funcion random() de la libreria random genera numeros seudo aleatorios con distribucion $U[0,1]$.
```
¿Como  simulamos una VA con distribucion normal con media $m$ y varianza $v$? Es decir, queremos simular lo siguiente:
$$X\, \Sigma \, N(m,v)$$
Queremos simular un valor $k\,\Sigma\,X\,\Sigma\,N(m,v)$ usando el teorema central del limite:
$$k=(\frac{(\Sigma_{i=1}^{12}r_i)-\frac{1}{2}}{\frac{1}{144}})\times v+m$$
Como siempre $r_i$ para $i=1,2,...,12$ son numeros seudoaleatorios uniformes entre 0 y 1, $r_{i}\,\Sigma\, u[0,1]$.
Y esto en Python ocurre asi:
```python
import random as rnd

def normal(m,v):
	suma=0.0
	
	for i in range(12):
		suma+=rnd.random()
	s=suma/12
	
	k=(((5-0.5)/(1/144))*v)+m
	
	return k
```

¿Y como se utilizan estas funciones? Es decir, ¿como generamos valores para $X\,\Sigma\,U[a,b]$ o para $X\,\Sigma\,N[m,v]$? Suponiendo una funcion `ppal()` que existe en el mismo script de las funciones `uniforme()` y `normal()`:

```python
def ppal():
	print("Generando 5 valores U[5,10]")
	
	for i in range(5):
		print(uniforme(5,10))
	print("Generando 5 valores N(10,1)")
	
	for i in range(5):
		print(normal(10,1))

if __name__=="__main__":
	ppal()
```

Esto genera 5 "muestras" o valores de una VA $U[5,10]$ e imprime cada una, y luego genera e imprime 5 muestras de una VA $N(10,1)$.
- Usando estas dos funciones `uniforme()` y `normal()` para generar valores de una VA $X \Sigma U[a,b]$ o una VA $X\Sigma N(m,v)$, simulemos los tiempos de llegada de los primeros cuatro clientes que llegan a cierto cajero automatico sabiendo que en ese cajero llega un cliente en prmedio cada 5 minutos. L simulacion inicia en $t=\text{10:00 horas}$.
Lo primero, ¿que vamos a simular? Queremos simuar la llegada de un cliente, mas especificamente los minutos que pasan de que llega un cliente a que llega el segundo, luego el tercero y luego el cuarto. Llamese $t_{llega}$ a tal VA. Y, ¿como modelamos $t_{llega}$? La descripcion del problema:
$$t_{llega} \Sigma N(5,1) \text{ donde N(5,1) es un cliente en promedio cada 5 minutos}$$
```ad-info
title: Nota
La varianza se asume unitaria si no se nos idica nada al respecto.
```

El plan de trabajo es el siguiente:
Simulemos en $k_1$ los minutos que transucrren para la llega del primer cliente:
$$k_{1}\,\Sigma\,N(5,1)$$
Luego simulemos los minutos que transcurren par la llegada del segundo cliente (despues de que llego el primero):
$$k_{2}\,\Sigma\,N(5,1)$$
Luego los que transcurren par ala llegada del tercero (luego del segundo):
$$k_{3}\,\Sigma\,N(5,1)$$
Y por ultimo los que transcurrieron para la llegada del cuarto (luego del tercero):
$$k_{4}\,\Sigma\,N(5,1)$$
Puesto que la simulacion inicia en $t=10:00$ el tiempo de llegada del primer cliente esL
$$t_{llega_1}=t+k_1$$
El tiempo de llegada del segundo cliente es:
$$t_{llega_2}=t_{llega_1}+k_2=(t+k_1)+k_2$$
El tiempo de llegada del tercero es:
$$t_{llega_3}=t_{llega_2}+k_3=((t+k_1)+k_2)+k_3$$
Y el cuarto cliente es:

$$t_{llega_4}=t_{llega_3}+k_4=(((t+k_1)+k_2)+k_3)+k_4$$
Esto nos deja ver que **en la simulacion de eventos discretos y aleatorios el tiempo avanza conforme suceden los eventos** ( la llegada de clientes en este caso). En Python esto lo podemos simular asi:

```python
def simula(tini):
	t=ini
	cuenta=1
	tllega=normal(5,1)
	
	t+=tllega

	print("El primer cliente llego a los " + str(t) + "minutos de que abrieron")
	while cuenta < 4:
		tllega=normal(5,1)
		t+tllega
		print("El siguiente cliente llego a las" + str(t) + "minutos de que abrieron")

def ppal():
	simula(0)
```
