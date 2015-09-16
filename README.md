# Tarea nro. 1
## FI3104B - Métodos Numéricos Para la Ciencia y la Ingeniería
#### Prof. Valentino González

La temperatura efectiva de una estrella corresponde a la temperatura del cuerpo negro que mejor se ajusta a su espectro. El cuerpo negro que mejor se ajusta a nuestro Sol tiene una temperatura aproximada de 5778 K.

1. El archivo `sun_AMO.dat` contiene el espectro del Sol, medido justo afuera de nuestra atmósfera, en unidades de *energía por unidad de tiempo por unidad de área por unidad de longitud de onda*. Lea el archivo y plotee el espectro del Sol (es decir, flujo vs. longitud de onda). Use la convención astronómica para su plot, esto es, usar *cgs* para las unidades de flujo y *angstrom* o *micron* para la longitud de onda. Recuerde anotar los ejes incluyendo las unidades.

	> __Ayuda.__
	>- El módulo `numpy` contiene la rutina `numpy.loadtxt` que le puede ser útil para leer el archivo.
	>- Para plotear se recomienda usar el módulo `matplotlib`. Hay muchos ejemplos, con código incluido en el siguiente [link](http://matplotlib.org/gallery.html), en particular [este ejemplo sencillo](http://matplotlib.org/examples/pylab_examples/simple_plot.html) puede ser útil.

2. Elija un método apropiado para integrar el espectro en longitud de onda y calcule la luminosidad total del sol (energía por unidad de tiempo total). Se pide que escriba su propio algoritmo para llevar a cabo la integración, en el futuro usaremos librerías de libre disposición.

3. La radiación de un cuerpo negro en unidades de energía por unidad de tiempo por unidad de área por unidad de longitud de onda está dada por la función de Planck:

	<img src='eqs/planck.png' alt='Plank' height='70'>

	(latex: $$B_\lambda(T) = \frac{2 \pi h c^2 / \lambda^5}{e^{hc / \lambda k_B T} - 1})

	donde h es la constante de Planck, c es la velocidad de la luz en el vacío, k<sub>B</sub> es la constante de Bolzmann, T es la temperatura del cuerpo negro y &lambda; es la longitud de onda.

	Integre numéricamente la función de Planck para estimar la energía total por unidad de área emitida por un cuerpo negro con la temperatura efectiva del sol (escriba su propio algoritmo). Compárela con la energía total calculada en 2. para estimar el radio efectivo del sol.

	>__Nota__. Se puede demostrar que la integral de la función de Planck corresponde a:

	><img src='eqs/planck_integrated.png' alt='Plank Integrated' height='70'>

	>(latex: $$P = \frac{2 \pi h}{c^2}\left( \frac{k_B T}{h} \right)^4 \int_0^\infty \frac{x^3}{e^x - 1}$$)

	>Y la integral se puede calcular analíticamente con resultado &pi;<sup>4</sup>/15. El problema pide elegir un método apropiado y calcular la integral numéricamente y comparar con el resultado analítico.

	>__Ayuda.__
	>- El módulo `astropy` contiene el submódulo `astropy.constants` que incluye todas las constantes necesarias además de rutinas para cambiar unidades.
	>- La integral que es necesario calcular es entre 0 e &infin; así que requiere ser normalizada. Intente el cambio de variable y=arctan(x).
	>- Implemente un algoritmo que permita ir refinando el valor de la integral con una tolerancia elegida por Ud.

4. El módulo `scipy` en Python incluye los métodos `scipy.integrate.trapz` y `scipy.integrate.quad`. Utilícelos para re-calcular las integrales calculadas en 2. y 3. Compare los valores obtenidos y la velocidad de ejecución del algoritmo escrito por Ud. vs. `scipy` ¿A qué se debe la diferencia?

	>__Ayuda.__

	>En la consola `ipython` existe la `ipython magic` `%timeit` que permite estimar velocidad de ejecución de funciones.


__Otras Notas.__
- Utilice `git` durante el desarrollo de la tarea para mantener un historial de los cambios realizados. La siguiente [*cheat sheet*](https://education.github.com/git-cheat-sheet-education.pdf) le puede ser útil.
- La tarea se entrega como un *pull request* en github. El *pull request* debe incluir todos los códigos usados además de su informe.
- El informe debe ser entregado en formato *pdf*, éste debe ser claro sin información ni de más ni de menos.
