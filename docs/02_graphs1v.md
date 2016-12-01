# Gráficos para una variable

En este capítulo se presentan funciones para la creación de gráficos con una sola variable.

## Función `stem`

Nos permite obtener el gráfico llamado de tallo y hoja debido a su apariencia. Este gráfico fue propuesto por Tukey (1977) y a pesar de no ser un gráfico para presentación definitiva se utiliza a la vez que el analista recoge la información para ver rápidamente la distribución de los datos.

¿Qué muestra este gráfico? 

1. El centro de la distribución. 
2. La forma general de la distribución:
	- Simétrica: Si las porciones a cada lado del centro son imágenes espejos de las otras. 
	- Sesgada a la izquierda: Si la cola izquierda (los valores menores) es mucho más larga que los de la derecha (los valores mayores).
	- Sesgada a la derecha: Opuesto a la sesgada a la izquierda.
3. Desviaciones marcadas de la forma global de la distribución.
	- Outliers: Observaciones individuales que caen muy por fuera del patrón general de los datos. 
	- Gaps: Huecos en la distribución

Ventajas del gráfico:

1. Muy fácil de realizar y puede hacerse a mano.
2. Fácil de entender.

Desventajas del gráfico:

1. El gráfico es tosco y no sirve para presentaciones definitivas. 
2. Funciona cuando el número de observaciones no es muy grande. 
3. No permite comparar claramente diferentes poblaciones

### Ejemplo {-}
Como ilustración vamos a crear el gráfico de tallo y hoja para la variable altura (cm) de un grupo de estudiantes de la universidad. Primero se leerán los datos disponibles en github y luego se usará la función `stem` para obtener el gráfico. A continuación el código usado.


```r
url <- 'https://raw.githubusercontent.com/fhernanb/datos/master/medidas_cuerpo'
datos <- read.table(file=url, header=T)
stem(datos$altura)
```

```
## 
##   The decimal point is 1 digit(s) to the right of the |
## 
##   14 | 7
##   15 | 3
##   15 | 679
##   16 | 0001
##   16 | 68888
##   17 | 001334
##   17 | 5678899
##   18 | 000033
##   18 | 88
##   19 | 1
```

De este gráfico sencillo se puede ver que la variable presenta una mayor frecuencia para alturas ente 170 y 179 cm y que no tiene una distribución simétrica.

## Función `boxplot` {-}
La función `boxplot` sirve para crear un diagrama de cajas y bigote \index{boxplot} para una variable cuantitativa. La estructura de la función `boxplot` con los argumentos más comunes de uso se muestran a continuación.


```r
boxplot(x, formula, data, subset, na.action,
        range, width, varwidth, notch, names, 
        plot, col, log, horizontal, add, ...)
```

Los argumentos de la función `boxplot` son:

- `x`: vector numérico con los datos para crear el boxplot.
- `formula`: fórmula con la estructura `x ~ g` para indicar que las observaciones en el vector `x` van a ser agrupadas de acuerdo a los niveles del factor `g`. 
- `data`: marco de datos con las variables.
- `subset`: un vector opcional para especificar un subconjunto de observaciones a ser usadas en el proceso de ajuste.
- `na.action`: una función la cual indica lo que debería pasar cuando los datos contienen ``NA's''.
- `range`: valor numérico que indica la extensión de los bigotes. Si es positivo, los bigotes se extenderán hasta el punto más extremo de tal manera que el bigote no supere \code{range} veces el rango intercuatílico ($IQ$). Un valor de cero hace que los bigotes se extiendan hasta los datos extremos.
- `width`: un vector con los anchos relativos de las cajas.
- `varwidth`: Si es  `TRUE`, las cajas son dibujadas con anchos proporcionales a las raíces cuadradas del número de observaciones en los grupos.
- `notch`: si es `TRUE`, una cuña es dibujada a cada lado de las cajas.  Cuando las cuñas de dos gráficos de caja no se traslapan, entonces las medianas son significativamente diferentes a un nivel del 5\%.
- `names`: un con las etiquetas a ser impresas debajo de cada boxplot.
- `plot`: si es `TRUE` (por defecto) entonces se produce el gráfico, de lo contrario, se producen los resúmenes de los boxplots.
- `col`: vector con los colores a usar en el cuerpo de las cajas.
- `log`: para indicar si las coordenadas `x` o `y` o serán graficadas en escala logarítmica.
- `...`: otros parámetros gráficos que pueden ser pasados como argumentos para el boxplot.

### Ejemplo {-}
Como ilustración vamos a crear tres boxplot para la variable altura (cm) de un grupo de estudiantes de la universidad, el primer boxplot será sobre la variable altura, el segundo será un boxplot para altura diferenciando por sexo y el tercer boxplot será igual que el primero pero modificando los nombres a imprimir en el eje horizontal. Primero se leerán los datos disponibles en github y luego se usará la función `boxplot` para obtener ambos gráfico. A continuación el código usado.


```r
url <- 'https://raw.githubusercontent.com/fhernanb/datos/master/medidas_cuerpo'
datos <- read.table(file=url, header=T)

par(mfrow=c(1, 3))
boxplot(x=datos$altura, ylab='Altura (cm)')

boxplot(altura ~ sexo, data=datos,
        xlab='Sexo', ylab='Altura (cm)')
				
boxplot(altura ~ sexo, data=datos, horizontal=TRUE,
        ylab='Género', xlab='Altura (cm)',
        names=c('Masculino', 'Femenino'))
```

![(\#fig:boxplots)Boxplot para la variable altura.](02_graphs1v_files/figure-latex/boxplots-1.pdf) 

En la Figura \@ref(fig:boxplots) se presentan los boxplots obtenidos con las instrucciones anteriores. El segundo y tercer boxplot son el mismo, lo único que se modificó fueron los nombres o etiquetas a colocar debajo de cada boxplot por medio del argumento `names` y la orientación.

## Función `hist`
La función `hist` sirve para crear el histograma \index{histograma}\index{hist} para una variable cuantitativa. Como argumentos esta función recibe un vector con los datos y opcionalmente puede ingresarse como argumento el número de intervalos a ser graficados o en su defecto el número de clases se determina con la fórmula de Sturges.

Nota: los programas de computador usualmente construyen los histogramas automáticamente, sin embargo, un buen programa debe permitirnos elegir el número de intervalos del histograma. Si usted posee un programa que no le permite hacer cambios, cambie de programa.

La estructura de la función `hist` con los argumentos más comunes de uso se muestran a continuación.















