Simulando una VA con distribucion normal
Recordemos que si $X$ es una VA con distribucion normal, con media $\mu$ y varianza $\sigma ^2$ (es decir $x \Sigma N(\mu \sigma ^2)$) entonces su funcion de densidad es:
$$f_x(x)=\frac{1}{\sigma \sqrt{2 \pi}}e^{- \frac{(x- \mu)^2}{2 \sigma ^2}}$$
Y su funcion de densidad acumulada es:
$$F_x(k)=\int_{-\infty}^{k}{\frac{1}{\sigma \sqrt{2 \pi}}e^{-\frac{(x- \mu)^2}{2 \sigma^2}}}\,d_x$$
Si intentamos simular esta variable X con el metodo de la funcion inversa, como en:
$$k=F_x^{-1}(r)$$
nos vamos a encontrar con un gran problema a decir verdad, **la integral para calcular $F_x(k)$ no tiene forma cerrada** y por lo tanto nunca podemos hacer aquello de $k=F^{-1}_x(r)$. Lo bueno es que podemos recurrir a otro metodo: a buscar del teorema central del limite para simular a $X\, \Sigma \,(\mu ,\sigma^2)$. ¿Como es este metodo? Es relativamente simple. Este metodo se vale del teorema central del limite, un principio estadistico que nos dice lo siguiente:
1) Tenemos $n$ valores $x_1,x_2,...,x_n$ y todos ellos provienen de la misma VA cuya distribucion tiene media $\mu_o$ y varianza $\sigma^2_o$.
2) Luego hacemos $s=\frac{\Sigma^n_{i=1}x_i}{n}$, es decir que $S$ es el promedio de los $n$  valores $x_i(i=1,2,...,n)$.
3) Entonces el teorema central del limite nos dice que: 
$$S\,\Sigma \,N(\mu_o,\frac{\sigma^2_o}{n})$$
Es decir que al promediar $n$ numeros que provienen de alguna distribucion (de la cual conocemos su media $\mu_o$ y su varianza $\sigma^2$) lo que nos queda es un numero de una distribucion normal (con media $\mu_o$ y varianza $\frac{\sigma^2_o}{n}$), y de esto es de lo que nos vamos a "aprovechar":
$$\text{Si: }S\,\Sigma\,N(\mu_o,\frac{\sigma^2}{n})\text{ entonces: }\frac{S-\mu_o}{\frac{\sigma^2_o}{n}}\,\Sigma\,N(0,1)$$
$$\text{Y si:} \frac{S-\mu_o}{\frac{\sigma^2_o}{n}}\,\Sigma\,N(0,1)\text{entonces: }(\frac{S-\mu_o}{\frac{\sigma^2_o}{n}})\sigma^2_x+\mu_x\Sigma\,N\,(\mu_x,\sigma^2_x)$$
en donde $\mu_x$ es la media de la distribucion normal que queremos simular y $\sigma^2_x$ es su varianza.
Ahora nos preguntamos ¿que pasa si promediamos $n=12$ numeros seudoaleatorios $r$? Solo recordemos que $r\,\Sigma\,U[0,1]$ y resulta que para una distribucion $U[0,1]$:
1) $\mu=\frac{1}{2}$
2) $\sigma^2=\frac{1}{12}$
De acuerdo al teorema central del limite:
$$S=\frac{r_1+r_2+...+r_12}{12}\,\Sigma\,N(\frac{1}{2},\frac{1}{144})$$

