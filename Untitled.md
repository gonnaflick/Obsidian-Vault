Ahora tenemos un sistema de tercer orden como el siguiente

$\frac{d^3y(t)}{dt^3}+22\frac22{d^2y(t)}{dt^2}+152\frac{dy(t)}{dt}+320y(t)=10x(t)$
Debemos simular la respuesta de este sistema a la señal de entrada $x(t)=e^{-2t}$ para $0 \le t \le 10$ y usando $\Delta t=1$ y tambien considerando que:
1) $y(t) |_{t=0}=0$
2) $\frac {dy(t)}{dt} |_{t=0}=0$
3) $\frac {d^2y(t)}{dt^2} |_{t=0}=0$
Como el sistema es de tercer orden se requieren tres variables tontas:
- $u_1(t)=\frac{dy(t)}{dt}$
- $u_2(t)=\frac{du_1(t)}{dt}=\frac{d^2y(t)}{d^2t}$
- $u_3(t)=\frac{du_2(t)}{dt}=\frac{d^3y(t)}{d^3t}$
Asi que este sistema se simula con las siguientes expresiones de Euler:
1) $y(t_{n+1}=y(t_n)+h\frac{dy(t)}{dt}|_{t=t_n}=y(t_n)+hu_1(t_n)$
2) $u_1(t_{n+1}=u_1(t_n)+h\frac{du_1(t)}{dt}|_{t=t_n}=u_1(t_n)+hu_2(t_n)$
3) $u_2(t_{n+1}=u_2(t_n)+h\frac{du_2(t)}{dt}|_{t=t_n}=u_2(t_n)+hu_3(t_n)$
Ademas de que, observando la EDO original se tiene que:
Dado q ue $u_3(t)=\frac{du_2(t)}{dt}=\frac{d^3y(t)}{dt^3}$, y de la EDO se sabe que:
$\frac{d^3y(t)}{dt^3}=10x(t)-\frac{22d^2y(t)}{dt^2}-152\frac{dy(t)}{dt}-320y(t)$
De aqui que:
$u_3(t)=\frac{d^3y(t)}{dt^3}=10x(t)-22\frac{d^2y(t)}{dt^2}-152\frac{dy(t)}{dt}-320y(t)$
Y puesto que $x(t=e^{-2t})$, $u_1(t)=\frac{dy(t)}{dt}$, $u_2(t=\frac{d^2y(t)}{dt}$ entonces:
$u_3(t)=10e^{-2t}-22u_2(t)-152u_1(t)-320y(t)$
Asi que al final:
$u_3(t_n)=10e^{-2t_n}-22u_2(t_n)-152u_1(t_n)-320y(t_n)$
Y por lo tanto, dado que $\Delta t=h=1$:
1) $y(t_{n+1})=y(t_n)+u_1(t_n)$
2) $u_1(t_{n+1})=u_1(t_n)+u_2(t_n)$
3) $u_2(t_{n+1})=u_2(t_n)+u_3(t_n)$
O tambien:
1) $y(t_{n+1})=y(t_n)+u_1(t_n)$
2) $u_1(t_{n+1})=u_1(t_n)+u_2(t_n)$
3) u_2({t_n+1})=u_2(t_n)+[10e^]

