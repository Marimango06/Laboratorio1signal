# Laboratorio1signal
Este código está diseñado para evaluar diferentes estadísticas descriptivas de una señal de ECG captada de un banco de datos.
 
En primera instancia se descargaron los archivos dat. y hat. de una señal fisiológica del banco de datos physionet, esto con el fin de estudiar su comportamiento de la señal, esta se gráfica en python con la ayuda de las librerías  ctypes y  matplotlib.pyplot. La primera para leer los datos de la señal y poder describir sus valores, y la segunda para generar las gráficas pertinentes. Dicho esto podemos ver la señal ECG graficada en python de esta manera:

(imagen señal)

Posteriormente se inició con el estudio de la señal, calculando la media aritmética, la cual es el promedio de los valores, esta es utilizada para determinar la detección de tendencias, esto para determinar si la señal cambia a lo largo del tiempo y poder tomar acción frente a esta información. Esta estadística se realizó inicialmente con la fórmula matemática (la sumatoria de los valores dividido el total de datos), en segunda instancia se ejecutó una función (mean) de la biblioteca  Numpy de phyton. Dando como resultado 0,085.

También se evaluó la desviación estándar, la cual cuantifica la  variación o dispersión en un conjunto de datos en relación con la media aritmética, una desviación alta significa que los valores están más dispersos respecto a la media de los mismos. En este caso práctico, podemos notar que se cuenta con una desviación elevada respecto a la media.Este estudio se realizó con la fórmula matemática asociada (la raíz cuadrada del 1 sobre el número de muestras multiplicado la sumatoria de los datos menos la media al cuadrado), también se calculó mediante la función std. Dando como resultado 0,16.

Adicionalmente se registró el valor porcentual de la relación entre la desviación estándar y la media, la cual se denomina como coeficiente de variación, En este caso se cuenta con un coeficiente de variación de 190% lo que nos indica que los valores están dispersos en relación con la media. 

Continuando de esta manera, se obtuvo el histograma de dos maneras diferentes, gracias a la función hist de la librería matplotlib.pyplot., y de manera manual teniendo presente el rango de la señal al igual que los intervalos también llamados bins.
Esta herramienta gráfica  representa la distribución de un conjunto de datos numéricos mostrando la frecuencia (o la densidad) de los datos agrupados en intervalos (o "bins") a lo largo del eje horizontal. En otras palabras es una herramienta para saber con qué frecuencia se repiten los datos de determinados intervalos. Esta gráfica se visualiza a continuación. 

( imagen  histograma)

Como podemos observar, la distribución de este histograma es normal o en forma de campana de Gauss, esto quiere decir que los valores están más próximos a la media de la señal. 

Finalmente tenemos la función de probabilidad, como su nombre indica describe la densidad de probabilidad en un punto específico. Para ello se utilizó la función  PDF de la librería scipy.stats. 

(grafica de funcion de probabilidad )

Como podemos observar en la gráfica, se muestra que datos son más probables que ocurran teniendo en cuenta el número de datos. Esto nos permite conocer que valor es más probable que aparezca en la señal que estamos estudiando.
