## Simulando en Python las respuestas (aproximadas)
Una vez que contamoscon las aproximaciones de Euler a la respuesta de un sistema podemos pasar a su simulacion usando Puthon para ello solo recuerdese que:
	1) Cualquier termino evaluado en $t=t_n$ es "el valor anterior".
	2) Cualquier termino evaluado en $t=t_{n+1}$ es el "nuevo valor".
		1) Y que en la simulacion iteramos para cada instante $tEt_s$, los instantes de simulacion, por lo que se debe calcular cada nuevo termino a partir del anterior y luego hacer el nuevo como e l anterior.
		2) veamos entonces como simular los sistemas de primer, segundo y tercer orden que resolvimos en clase
- El sistema de primer orden es $\frac{dy(t)}{dt}+10y(t)=10x(t)$ cuya aproximacion con euler es:
$$y(t_{n+1})=y*t_n+h(10x(t_n)-10y(t_n))$$

Simular esta respuesta para $0<= t<= 10$ usando $\Delta t =0.1$ y con $y(t_o)=y(0)=0$, ademas hayamos $x(t)=u(t)$ por lo que la aproximacion de Euler es:
$$y(t_{n+1})=y(t_n)+0.1(10u(t_n)-10y(t_n))$$
El script de Python que simula esta repuesta es el siguiente:
```python
import numpy as np
import matplotlib.pyplot as mpl

def u(A,k,t):
	resp = 0
	if t >= k:
		resp = A
	return resp

def ppal(tini,tfin,h,yo):
	ts = np.arange(tini,tfin,h)
	ys = []
	yante = yo
	for t in ts:
		y = yante+h*(u(10,0,t)-10+yante)
		ys.append(y)
		yante = y

mpl.plot(ts,ys)
mpl.title('Respuesta de primer orden al escalon')
mpl.xlabel('t')
mpl.ylabel('Amperes')
mpl.grid()
mpl.show()

if __name__ == '__main__':
	ppal(0,10,0.1,0)
```

- El sistema de segundo orden cuya EDO  es:
$$\frac {d^2y(t)}{dt^2}+12\frac{dy(t)}{dt}+32y(t)=10x(t)$$
tiene una aproximacion a su solucion con Euler como la siguiente:
- $y(t_{n+1})=y(t_n)+hu_1(tn)$
	- $u_1(t_{n+1})=u_1(t_n)+h(10x(t_n)-12u_1(t_n)-32y(t_n))$
Simulemos esta respuesta en Python usando los siguientes parametros:
1) $0<=t<=10 y h=0.1$
2) $y(t_o)=y(0)=0$
3) $\frac{dy(t)}{dt}|_{t=to=0}=0$
4) $x(t)=u(t)$
Esto significa que las expresiones de Euler a somular son:
- $y(t_{n+1})=y(t_n)+0.1u_1(t_n)$
	- $u_1({t_n1+1})=u_1(t_n)+0.1(10u(tn)-12u_1(t_n)-32y(t_n))$
	- En donde $u(t_n)$ es el escalon unitario
El script de Python que lo simula es:
```python
import numpy
import matplotlib.pyplot

def u(A,k,t):
	# Esta en el codigo anterior

def ppal(tini,tfin,h,y0,yprima0):
					# y(0), derivada de y(t)
	ts = np.arange(tini,tfinh)
	ys = []
	yante = y0
	u1ante = yprima0
	for t int ts:
		y = yante+h*u1ante
		u1 = u1ante+h*(u*10,0,t)-12u1
		ys.append(y)
		ys
```
