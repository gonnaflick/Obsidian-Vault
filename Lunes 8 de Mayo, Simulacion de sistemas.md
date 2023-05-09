Ahora si, simulando una VA con el metodo dela funcion inversa

Primero, no todas las VA's se dejan simular con este metodo pero una VA con distribucion normal si que lo hace. Para comprender este metodo recordemos que:
$$F_x(k)=\int_{- \infty}^{k}{f_{x}(x) \,}d_x$$
Ademas de que $F_x(k)$ tiene los siguientes atributos:
a) $0<=F_x(k)<=1$
b) Y $F_x(k)$ es lineal monotonicamente es decir que si $k_1<k_2$ entonces $F_x(k)$

¿Y luego que? Pues todo esto nos permite hacer lo siguiente:
1) Tenemos que $0<=F_x(k)<=1$
2) Tambien tenemos que r, si es un numero aleatorio uniforme entre 0 y 1, es decir, $r \Sigma U[0,1]$ entonces $0<=r<=1$.
3) Luego podemos considerar que $r=F_x(k)$, es decir que r (el numero seudo aleatorio) quiza corresponde al valor $F_x(k)$ para alguna k.
$$r=F_x(k)$$
4) Entonces, ¿quien es esa k para quien $F_x(k)=r$? Pues facil:

$$K=F^{-1}_x(r)$$
Graficamente:
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 651 530" width="651" height="530">
  <!-- svg-source:excalidraw -->
  
  <defs>
    <style class="style-fonts">
      @font-face {
        font-family: "Virgil";
        src: url("https://excalidraw.com/Virgil.woff2");
      }
      @font-face {
        font-family: "Cascadia";
        src: url("https://excalidraw.com/Cascadia.woff2");
      }
    </style>
  </defs>
  <rect x="0" y="0" width="651" height="530" fill="#ffffff"></rect><g stroke-linecap="round"><g transform="translate(52 477) rotate(0 43.254723815722386 -0.3006905134442093)"><path d="M0.06 0.98 C14.78 0.98, 73.23 0.53, 87.88 0.36 M-1.37 0.44 C13.31 0.04, 72.56 -1.72, 87.4 -1.57" stroke="#a600ff" stroke-width="1" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(138 476) rotate(0 193.31704232638708 -192.61197205413134)"><path d="M1.2 -1.05 C65.38 -65.24, 322.22 -320.64, 386.27 -384.59 M0.36 1.01 C64.36 -63.55, 321.67 -321.62, 385.73 -386.23" stroke="#a600ff" stroke-width="1" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(378 477) rotate(0 -0.8029919214968544 -118.16832521893083)"><path d="M-0.53 0.64 C-0.7 -38.76, -1.22 -197.07, -1.03 -236.98" stroke="#000000" stroke-width="1.5" fill="none" stroke-dasharray="8 9"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(525 90) rotate(0 -0.43539952604268706 194.18790603006258)"><path d="M0.42 0.61 C0.52 65.28, -0.25 323.88, -0.21 388.5 M-0.82 -0.12 C-0.82 64.16, -1.44 321.65, -1.27 386.64" stroke="#c800ff" stroke-width="1" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(525 476) rotate(0 31.986555686220527 0.2104960605898185)"><path d="M-1.17 -0.83 C9.74 -1.02, 54.3 -0.86, 65.15 -0.91 M0.41 1.35 C11.21 1.26, 53.31 0.44, 64.28 0.15" stroke="#c800ff" stroke-width="1" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(57 510) rotate(0 -0.05991785888559775 -233.17778156707993)"><path d="M0.48 0.52 C0.3 -77.03, -0.9 -387.39, -1.12 -465.18 M-0.72 -0.26 C-0.54 -78.15, 0.61 -389.41, 1 -466.87" stroke="#000000" stroke-width="1" fill="none"></path></g><g transform="translate(57 510) rotate(0 -0.05991785888559775 -233.17778156707993)"><path d="M12 -440.51 C9.48 -448.33, 4.75 -455.64, 1.27 -466.74 M11.64 -439.39 C7.47 -448.77, 3.4 -458.04, 0.72 -466.66" stroke="#000000" stroke-width="1" fill="none"></path></g><g transform="translate(57 510) rotate(0 -0.05991785888559775 -233.17778156707993)"><path d="M-8.52 -440.59 C-4.96 -448.48, -3.62 -455.76, 1.27 -466.74 M-8.88 -439.48 C-6.15 -448.78, -3.33 -458.02, 0.72 -466.66" stroke="#000000" stroke-width="1" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(23 477) rotate(0 290.2855152064096 0.605247333515436)"><path d="M0.18 0.39 C97.01 0.33, 484.91 0.15, 581.76 0.08 M-1.19 -0.45 C95.48 -0.33, 484.23 1.37, 581.21 1.67" stroke="#000000" stroke-width="1" fill="none"></path></g><g transform="translate(23 477) rotate(0 290.2855152064096 0.605247333515436)"><path d="M553.62 13.08 C563.4 8.55, 573.55 3.4, 580.7 3.27 M552.13 11.85 C560.24 10.33, 566.88 7.35, 581.35 1.4" stroke="#000000" stroke-width="1" fill="none"></path></g><g transform="translate(23 477) rotate(0 290.2855152064096 0.605247333515436)"><path d="M553.7 -7.44 C563.52 -4.47, 573.64 -2.12, 580.7 3.27 M552.2 -8.67 C560.43 -5.26, 567.05 -3.31, 581.35 1.4" stroke="#000000" stroke-width="1" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(525 90) rotate(0 -232.6449031446129 0.18850757391012962)"><path d="M0.18 -0.02 C-77.39 -0.07, -388 0.51, -465.47 0.38" stroke="#000000" stroke-width="1.5" fill="none" stroke-dasharray="8 9"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(375 243) rotate(0 -159.95718478895725 0.23305128535898234)"><path d="M0.87 -0.31 C-52.53 -0.31, -267 0.71, -320.79 0.77" stroke="#000000" stroke-width="1.5" fill="none" stroke-dasharray="8 9"></path></g></g><mask></mask><g transform="translate(10 75) rotate(0 3.5 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">1</text></g><g transform="translate(628 469) rotate(0 6.5 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">x</text></g><g transform="translate(18 235) rotate(0 5.5 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">r</text></g><g transform="translate(373 489) rotate(0 6 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">k</text></g><g transform="translate(522 487) rotate(0 6 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">b</text></g><g transform="translate(132 495) rotate(0 7.5 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">a</text></g><g transform="translate(37 485) rotate(0 8 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">0</text></g><g transform="translate(34 10) rotate(0 25.5 12.5)"><text x="0" y="18" font-family="Virgil, Segoe UI Emoji" font-size="20px" fill="#000000" text-anchor="start" style="white-space: pre;" direction="ltr">Fx(x)</text></g></svg>

Pero siempre recordemos que r es un numero seudo aleatorio, uno que tiene distribucion unifome entre 0 y 1. Entonces, dada la variable aleatorio X con funcion de densidad acumulada $F_x(x)$ conocida y con $D_x=[a,b]$ Como simular X para que nos genere un $k \Sigma D_x$ dado r? Le hacemos asi:
1) Generemos r
2) Hagamps $k=F^{-1}(r)$
Y listo, alli tenemos un $k \Sigma D_x$, ¿queremos n valores k?

Pues entonces hagamos:
```python
for i=0 to n:
	# Resetear al generador de rs
	# Generar r
	# Hacer k=Fx^(-1)(r)
```

- Sea X una VA con distribucion uniforme U[a,b]. ¿Como generar un $k \Sigma D_x$? Segun esta tecnica le hacemos asi:
	Primero, si $X \Sigma U[a,b]$ entonces $f_x(x)=\frac{1}{b-a}$
	Segundo, calcular $F_x(k)=\int_{\infty}^{k}f_x(x)d_x=\int_{a}^{k}(\frac{1}{b-a})d_x=\frac{1}{b-a}\int_{a}^{k}d_x$ asi que:
	$$F_x(k)=\frac{1}{b-a}(k-a)$$
	Y por lo tanto, dado $r=F_{x(k)}$ entonces:	$$r=F_x(k)=\frac{1}{b-a}(k-a)$$ Ahora hagamos $k=F^{-1}_x(r)$:
	$$k=r(b-a)+a$$
- En la bomba 17 de cierta gasolinera el que atiende entre las 10:00 y 12:00 tarda entre 2 y 6 minutos en atender un cliente. Simulemos el tiempo de atencion que esta persona tiene par alos primeros tres clientes. Modelemos el tiempo de atencion $t_{atiende}\Sigma U[2,6]$ lo que implica que:
	$$f_{tatiende}(x)=\frac{1}{6-2}=\frac{1}{4}$$
	Luego: 
	$$k=F^{-1}(r)=4r+2$$
	Asi que debemos simular $k_1$,$k_2$ y $k_3$, el tiempo de atencion para el cliente 2 y el cliente 3 respectivamente. Asi que:
	1) Resetear generador
	2) Generar $r_1$
	3) Hacer $k_1=4r_1+2$
	4) Resetear generador
	5) Generar $r_2$
	6) Hacer $k_2=4r_3+2$
	7) Resetear generador
	8) Generador 3
	9) Hacer $k_3 =4r_4+2$
	10) Python tiene un gneerador de numeros seudo aleatorios que realmente no necesita resetearse por lo que los pasos 1,4 y 7 no seran necesarios.