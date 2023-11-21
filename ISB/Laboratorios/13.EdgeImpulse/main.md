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


Se adquirió la señal de electromiografía (EMG) procedente del músculo vasto lateral. Esta señal se someterá a un análisis mediante RMS con el objetivo de calcular un umbral específico para separar fatiga muscular. Este umbral servirá como indicador, ya que una pendiente notablemente empinada en la señal RMS sugiere la presencia de fatiga muscular como se observa en la imagen. Con base en esta diferenciación, se procederá a separar las dos condiciones de la señal EMG: una correspondiente a la actividad muscular sin fatiga y otra que refleje la presencia de fatiga. 

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/d6584db6-9d1e-4db0-aa6e-b9273c89a603)

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
