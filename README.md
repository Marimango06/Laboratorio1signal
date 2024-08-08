# Laboratorio1signal
Este código está diseñado para evaluar diferentes estadísticas descriptivas de una señal de ECG captada de un banco de datos.
 
En primera instancia se descargaron los archivos dat. y hat. de una señal fisiológica del banco de datos physionet, donde se registaron el ECG de 28 atletas de alto rendimiento de Noruega, cabe aclarar que cada medicion se tomo en un estado de reposo, para examinar las diferencias anatomicas en el corazón de los atletas, ya que las paredes del ventriculo izquierdo se distiende en comparación con personas que no entrenan deportes.
Esto con el fin de estudiar su comportamiento de la señal, esta se gráfica en python con la ayuda de las librerías  ctypes y  matplotlib.pyplot. La primera para leer los datos de la señal y poder describir sus valores, y la segunda para generar las gráficas pertinentes. Dicho esto podemos ver la señal ECG graficada en python de esta manera:

![image](https://github.com/user-attachments/assets/fdb33ab0-a250-40b1-a5f6-15f9af715537)


Posteriormente se inició con el estudio de la señal, calculando la media aritmética, la cual es el promedio de los valores, esta es utilizada para determinar la detección de tendencias, esto para determinar si la señal cambia a lo largo del tiempo y poder tomar acción frente a esta información. Esta estadística se realizó inicialmente con la fórmula matemática (la sumatoria de los valores dividido el total de datos), en segunda instancia se ejecutó una función (mean) de la biblioteca  Numpy de phyton. Dando como resultado 0,085.

También se evaluó la desviación estándar, la cual cuantifica la  variación o dispersión en un conjunto de datos en relación con la media aritmética, una desviación alta significa que los valores están más dispersos respecto a la media de los mismos. En este caso práctico, podemos notar que se cuenta con una desviación elevada respecto a la media.Este estudio se realizó con la fórmula matemática asociada (la raíz cuadrada del 1 sobre el número de muestras multiplicado la sumatoria de los datos menos la media al cuadrado), también se calculó mediante la función std. Dando como resultado 0,16.

Adicionalmente se registró el valor porcentual de la relación entre la desviación estándar y la media, la cual se denomina como coeficiente de variación, En este caso se cuenta con un coeficiente de variación de 190% lo que nos indica que los valores están dispersos en relación con la media. 

Continuando de esta manera, se obtuvo el histograma de dos maneras diferentes, gracias a la función hist de la librería matplotlib.pyplot., y de manera manual teniendo presente el rango de la señal al igual que los intervalos también llamados bins.
Esta herramienta gráfica  representa la distribución de un conjunto de datos numéricos mostrando la frecuencia (o la densidad) de los datos agrupados en intervalos (o "bins") a lo largo del eje horizontal. En otras palabras es una herramienta para saber con qué frecuencia se repiten los datos de determinados intervalos. Esta gráfica se visualiza a continuación. 

![image](https://github.com/user-attachments/assets/dde794d4-8ccd-4878-9a78-9bb690e82fd5)


Como podemos observar, la distribución de este histograma es normal o en forma de campana de Gauss, esto quiere decir que los valores están más próximos a la media de la señal. 

Finalmente tenemos la función de probabilidad, como su nombre indica describe la densidad de probabilidad en un punto específico. Para ello se utilizó la función  PDF de la librería scipy.stats. 

![image](https://github.com/user-attachments/assets/bcf482ec-7d2c-4ac1-a39f-aacca8414d3c)


Como podemos observar en la gráfica, se muestra que datos son más probables que ocurran teniendo en cuenta el número de datos. Esto nos permite conocer que valor es más probable que aparezca en la señal que estamos estudiando.


Ruido
En esta sección se describirán los tipos de ruidos aplicados en la señal, estos son: Ruido Gaussiano, Ruido de impulso y Ruido de artefacto.

Ruido Gaussiano: este se describe como un ruido frecuente que sus variaciones siempre tiene su gráfica similitud con la campana de Gauss, esta se puede observar en eventos de electromagnetismo o radiación, en este caso al ser una señal de corrientes en el corazón se puede este tipo de ruido.

![image](https://github.com/user-attachments/assets/2df03c85-3c33-48b6-a21d-83eb3f009ad1)


Con respecto al código este ruido se puede variar a partir del cambio de límites de variación aleatoria 
             ruido_gaussiano = np.random.normal(0.2, 0.4, tamano)

esto se teniendo en cuenta la amplitud de la señal original, ya que esto va a afectar la relación señal-ruido.

Ruido de impulso: Este tipo de ruido se caracteriza por ser de corta duración y una amplitud muy alta, esto de forma aleatoria en el tiempo, esto al igual que el ruido gaussiano se puede observar en eventos electromagnéticos pero se puede describir en situaciones físicos mecánicos

![image](https://github.com/user-attachments/assets/d224eba1-ee43-4090-8fbe-c9119dbbd203)


Este ruido se puede modificar en dos variables, una en la probabilidad de la frecuencia de este ruido pulse probability = 0.001, generando que haya más o menos pulsos según su probabilidad de aparición el cual es afectado por el número de datos a analizar, por otra parte se puede modificar la amplitud de la onda pulse_noise = np.where(random_numbers < pulse_probability, 0.2, 0), como se puede observar la amplitud son los dos números de la línea del código, aumentando o disminuyendo el cambio con respecto a la señal.

Ruido de artefacto: Se caracteriza por estar en cualquier dispositivo de recolección de señales, esta se pude observar como un impulso único por el método de uso del usuario, o puede ser la resolución del dispositivo.

![image](https://github.com/user-attachments/assets/f537ed0b-deb8-45f3-a652-7f8deaac5d99)



Este ruido se puede modificar de dos maneras, uno es la posición donde va a aparecer el ruido transitorio, en esta linea se puede modificar esta ubicación en la gráfica según el tamaño de datos impulse_index = int(0.75* tamano), lo siguiente sería variar la amplitud del ruido este se puede modificar en la siguiente línea impulse_amplitude=2.

Después de la descripción de cada ruido cabe mencionar la importancia de conocer la relación de señal-ruido y la potencia de la señal, el primero describe si la señal es mas fuerte que el ruido o viceversa, esto se puede determinar con el valor resultante de esta operación, si es menor a 1, será más grande el ruido que la señal descrita, si es mayor a uno la señal es más grande que el ruido, el SNR afecta a la potencia de ruido, como se mencionó al ser una función logarítmica, si el valor es menor a 1, la potencia de la señal será negativa, mientras si es mayor a 1, la señal será positiva, cabe mencionar que la potencia es descrita por la unidades de medida “decibeles”, en el codigo para calcular la relación señal-ruido, utilizamos el promedio de los valores aleatorios, para que diera un valor único y no un arreglo matricial.
