# Laboratorio 13: Edge Impulse

## Tabla de contenidos:
* [Objetivos](#objetivos)
* [Entregables](#entregable)
 
  * [Obtencion de la grafica en RMS de la señal EMG en el tiempo analizado ](#emg)
  * [Obtención de ventanas:Tiempo en que se cambia de potencia)(#emg)
  * [Dataset en Edge Impulse ](#emg)
  * [Creacion de las variables](#explicación-emg)
  * [Creacion del spectral features  ](#emg)
  * [Análisis de la clasificación](#explicación-emg)

  
## Obtención de caracteristicas y segmentado de la señal
Para la adquisición del dataset, comenzamos calculando el umbral en la señal de EMG. Dividimos la señal en grupos de 600 muestras y determinamos el máximo valor en cada grupo. Este enfoque nos permitió establecer un umbral relevante para destacar cambios significativos en la amplitud de la señal. Luego se aplicó, el cálculo del valor RMS , un suavizado y  filtros, con el objetivo de resaltar patrones en la señal. La identificación de puntos de cambio brusco, utilizando el modelo 'l1', fue determinante para definir los valores antes y después de la fatiga en la señal de EMG.
![1](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/051936d4-4494-4f75-83ae-5f607dac5eff)


Luego de definir el umbral en la señal de EMG, procedimos a separar la señal en dos clases distintas: antes de fatiga y después de fatiga, que luego se llamarán clase 1 y clase 2 para el modelo de Edge Impulse. Utilizando el punto de cambio brusco hallado anteriormente, multiplicamos este valor por 8000 para obtener el índice correspondiente en la señal original. A partir de este índice, realizamos la indexación para crear dos conjuntos de datos separados.

![2](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/dba895d8-90a9-4d8e-a9b4-e5c97099d6b0)
Después de la separación de las dos clases, procedimos a segmentar cada clase en ventanas de 90 segundos, ya que se identificó que cada 90 segundos ocurrió un aumento de potencia en el ejercicio de bicicleta estática. Para realizar esta segmentación, utilizamos la función divide_en_ventanas, que toma como entrada la señal de cada clase, el tamaño de la ventana (90 segundos), el tamaño del paso y la frecuencia de muestreo. Cabe destacar que la Clase 1 tuvo un total de 6 ventanas, mientras que la Clase 2 solo tuvo una. Esto se debe a que el cambio brusco en la señal, indicativo de fatiga, ocurrió solo en los últimos 90 segundos del ejercicio. Las gráficas resultantes muestran claramente las diferentes ventanas de cada clase y respaldan la observación de la variación de potencia antes y después de la fatiga.

![3](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/f2906a84-5fef-4b58-ad1f-f95e4055ad2a)



Finalmente, se realizaron cálculos detallados de características para cada señal de ventana. Utilizando una función que toma como entrada las listas de arrays correspondientes a las ventanas antes y después de la fatiga, se obtuvieron datos clave como el Root Mean Square (rms), la media, la desviación estándar, la amplitud, el valor máximo y mínimo. 

![WhatsApp Image 2023-11-20 at 11 51 26 PM](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/225280f3-d53a-45d8-81ef-6da12e41e05f)


## Obtención de archivos csv
Se obtuvieron dos archivos csv , uno el cual se uso para edge impulse que clasifico la amplitud antes y despues del corte 
![WhatsApp Image 2023-11-20 at 11 54 31 PM](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/925eafa3-3a23-431c-9364-fc549fb57d46)


El segundo es el que clasifico la data en la clase , ventana correspondiente y cada una de sus caractersiticas 
![WhatsApp Image 2023-11-20 at 11 54 13 PM](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/1ed654bf-4e8f-4d6d-804d-73a2bb37bb0b)



En primera instancia, pasamos el archivo Classification.CSV que se obtuve en el anterior código, y luego cortamos la señal cada 1minuto  con 30 segundos, esto de acuerdo a la clasificación antes realizada(Clase1: No fatiga, Clase2 :Fatiga). Un total de 11 minutos con 30 segundos y 2 archivos de 2 text y 6 archivos de training.  (Fs=1000 hz9


![im1](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/d2ae3593-5cf4-4405-909f-3fa8d5c00884)
[Dataset]

Luego creamos spectral features y classification de acuerdo a los valores adecuados.


![im2](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/13379ae2-90ff-4b91-b304-1b28d4e99ff9)

Vemos la señal cortada durante 90 segundos.

![im3](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/31feb7b6-5913-4d85-bae5-963614d5e033)


Se aplica un analisis en wavelet de un db1.

![im4](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/687467f7-d1e4-4001-9989-04cbfe5f2faf)

Se realiza la clasificacion entre clase 1 y clase 2 correctamente (una exactitud de 100% )

![Imagen14](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/471e5600-7ec4-443a-99df-6f0b0bb90481)

Se determina que la clase 1 es correcta (No fatiga) y la clase 2 es incorrecta (Fatiga). Esto corresponde a lo hallado anteriormente ya que en la fatiga, lo recomendable es no seguir realizando ejercicio.

![Imagen15](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/ef429f47-683c-4206-897a-97779a3a8269)

Por último , se puede generar un codigo en una libreraría (este C++) para la creacion del machine learning que analiza estas 2 clases.

![Imagen16](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/669b660b-7f7d-4c5f-9f4b-4caf52d722f3)
