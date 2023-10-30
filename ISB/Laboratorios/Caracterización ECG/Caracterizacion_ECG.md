# Laboratorio 7: Filtrado y caracterización de señal ECG
## Tabla de contenidos:
* [Objetivos](#objetivos)
* [Materiales y equipos](#materiales-y-equipos)
* [Entregables](#entregable)
  * [Leer el Dataset](#dataset)
  * [Análisis en frecuencia de la señal ECG](#frecuencia)
  * [Reducir los ruidos con filtro Notch ](#Notch)
  * [Filtrar la señal con un filtro pasa baja](#Pasa_BAJA)
  * [Filtrar la señal con un filtro pasa alto](#Pasa_alto)
  * [Realizar filtrado wavelet](#filtrado_wavelet)
  * [Realizar el filtrado derivativo](#filtrado_derivativo)
  * [Elevar al cuadrado la señal](#cuadrado)
  * [Emplear el operador Moving Window Integration](#moving_window_integration)
  * [Marcar los picos](#marcado_picos)
  * [Realizar el análisis de Threshold](#theshold)

* [Bibliografía](#bibliografía)

## Objetivos:

*Realizar un análisis en frecuencia de la señal
* Uso de filtro Notch
* Uso de filtro pasa banda
* Uso de filtro pasa alto
* Realizar filtrado derivativo
* Elevar la señal al cuadrado
* Uso de operador Moving Window Integration
* Detectar los picos y análisis de threshold
* Obtener el complejo QRS

## Materiales y equipos:

<div align="center">

|  **Materiales**  | **Descripción** | 
|:------------:|:---------------:|
|   Laptop   |   Se utilizo para obtener las gráficas de la señal ECG y realizar el procesamiento en Python |
|    Google collab   |  Se utilizó como entorno de desarrollo de python |

</div>

## Leer el Dataset

Para leer los datos obtenidos, primeramente hay que realizar la conversión de los datos tomando en cuenta el dispositivo de adquisición utilizado. En nuestro caso, anteriormente se obtuvieron las señales en la configuración D1, utilizando el dispositivo BITalino. En la Imagen 1 vemos las indicaciones de BITalino para obtener la señal adecuada.

![Imagen1](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/65d9234a-9540-4612-a8a4-fb657fd45692)

Imagen 1: Datos para la conversión de la señal a las unidades de voltaje correctas [1]

En la imagen 2 se puede ver el código utilizado y como se adecuó la señal del archivo ecg2reposo.txt, obtenido con el BITalino.

![Imagen2](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4add4cc3-69e9-4bb3-b44f-692dde9fef74)

Imagen 2: Codigo de la conversión de unidades de la señal

![señalecgOG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/31c62ccb-6c84-4c39-a258-1c8fa899f954)

Imagen 3: Grafica de la señal completa


## Análisis en frecuencia de la señal ECG

Se realizó la transformada de fourier a la señal para poder obtener el espectro de frecuencias y detectar los ruidos. Podemos notar un evidente ruido en frecuencias altas, con picos marcados proveniente de la red eléctrica en Perú a 60Hz  y 120Hz. 

![freqECG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/35ddb531-56ec-4d4a-8d49-2c70608da439)

Imagen 4: espectro de frecuencias

## Reducir los ruidos con filtro Notch 

Una vez que se identificó las frecuencias de los fitros más prominentes, se utilizó filtros Notch para eliminar específicamente las frecuencias de 60 y 120Hz puesto que en ese rango se tiene información importante del ecg, lo cual impide en uso de un filtro pasa baja. También se realizó un filtro Notch a 50 Hz. En el espectro de frecuencias, se detectó un pequeño ruido en esta frecuencia lo cual puede ser ruido magnetico y si bien es un pico pequeño, la señal mejoró mucho más al filtrar esta frecuencia. En la imagen 5, podemos ver el espectro de frecuencias después de haber filtrado la señal.

![frecdespNotch](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/e22fbec0-1017-48ac-b331-d707216b85bb)

Imagen 5

En la imagen 6 podemos ver la señal ECG después de haber filtrado las señal.

![ECGdespNotch](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4d769b66-27b6-44fc-b56c-5fce12fe67cd)

Imagen 6

## Filtrar la señal con un filtro pasa baja

Señales de 0 a 11Hz
Ahora se realiza un filtrado pasa baja para concentrarnos específicamente en el rango de frecuencias de un ecg y eliminar todos los ruidos de frecuencia alta, esto permite que las componentes de baja frecuencia relevantes, como las ondas P, QRS y T, pasen sin atenuación significativa. Se utilizó específicamente un filtro Butterworth de segundo orden con una frecuencia de corte de 11.0 Hz. Se escogió Buterworth por su respuesta de paso bajo suave y su fase lineal, lo que evita la distorsión en el dominio del tiempo; y es de segundo orden ya que proporciona una mayor capacidad de atenuación y permite un mayor control de la frecuencia de corte seleccionada.
En la siguiente imagen 7 podemos ver la respuesta en frecuencia del filtro diseñado y en la imagen 8 vemos la señal filtrada, la cual se ve más limpia que la anterior que solo utilizaba filtros Notch

![respFreq](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/c0bc0feb-8931-4b37-88f7-0269d05446f3)

Imagen 7:respuesta en frecuencia del filtro Butterworth pasabaja de segundo orden

![ECG_filtradoBAJAS](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4f1e08f9-6f65-4520-9d4c-10f810b5fdaf)

Imagen 8: Señal filtrada con filtro PasaBaja

## Filtrar la señal con un filtro pasa alto

Ahora se tiene el diseño de un filtro pasa alta, el cual tiene frecuencia de corte de 5Hz, lo cual es útil para eliminar la línea de base y las componentes de baja frecuencia. Se escogió una relación de rechazo en escala de 3 paa obtener una atenuación más fuerte de las frecuencias no deseadas por debajo de la frecuencia de corte.
En la imagen 9 se tiene la respuesta en frecuencia del filtro en cuestión y en la imagen 10, se tiene la señal ya filtrada.

![pasaalto_respFREQecg](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/b44d7f77-57a7-4f89-b017-ceea37b75e16)

Imagen 9: Respuesta en frecuecnia del filtro del filtro Butterworth pasa alto de primer orden

![pasaaltoECG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/c988ac27-6335-45de-8034-491b62886e0c)

Imagen 10: Señal ECG filtrada con Butterworth pasa altas

El filtro pasa baja y pasa alta, nos permiten tener un filtro pasabanda para las frecuencias deseadas.

## Realizar filtrado wavelet

Para poder obtener una señal más limpia, se decidió utilizar un filtro wavelet ya que la descomposición en niveles de detalle que utiliza este tipo de filtro, permite una mejor detección de los cambios típicos de una señal ECG, con un umbral bajo para no perder información.

![detallesECG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/c1d9997c-32d9-48ef-bdbf-93b2ce7e1824)

Imagen 11: Grafica de coeficientes de aproximación

![ECGfiltwavelet](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/73991697-a562-4708-98db-15d0c10e71b5)

Imagen 12: Comparación de señal antes y después del uso del filtro wavelet

## Realizar el filtrado derivativo

Ahora se tiene el uso de un filtro derivativo el cual, debido a la naturaleza de los picos y sobre todo el R, nos permitirá obtener datos de la pendiente del complejo QRS y de esta forma, identificar el complejo. Este método solo, es útil mientras no se presenten anomalías que alteren la duración de las ondas ya que la pendiente no sería tan pronunciada y sería más complicado identificarla. 
En la imagen 13 vemos la respuesta en frecuencia del filtro, en el cual vemos que se tiene uncomportamiento cercano al lineal a frecuencias bajas, por lo que es útil en las gráficas ECG y en la imagen 14, vemos la señal ya filtrada. 

![freqderiv](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/73e10230-a99b-4e28-93b7-2d65453d0517)

Imagen 13: respuesta en frecuencia del filtro derivativo

![descarga](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/50df8f72-a8d1-437f-8866-ff69b81aa0da)

Imagen 14: señal filtrada con el filtro derivativo



## Elevar al cuadrado la señal

Se eleva al cuadrado la señal para resaltar aún más las partes más prominentes de la señal, atenuar las partes menos significativas y eliminar los componentes negativos, gracias a esto se destaca aún más los picos y las partes de mayor amplitud en la señal.

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/70066f14-2e3e-427f-a82f-ca0a0f542463)

## Emplear el operador Moving Window Integration

Se aplica un operador del tipo Moving Window Integration para suavizar la señal, reducir el ruido y destacar las áreas con mayor energía.

y[n]=(1/N)(x[n−(N−1)]+x[n−(N−2)]+..+x[n])

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/0b87456d-25ca-4d65-9533-0cc2f114687d)


## Marcar los picos

Se detectan los picos R en la señal ECG, que corresponden a la contracción del ventrículo para así identificar los puntos de máximo valor en la señal, que son fundamentales para calcular la frecuencia cardíaca y otros parámetros como segmentos de las ondas.

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/4c9cd906-7020-405d-b064-f6043065a911)

Se observa que el ruido de baja amplitud tambien se esta marcando, por lo que debemos aplicar un umbral para eliminarlos


## Realizar el análisis de Threshold

Se establece un umbral para distinguir entre los picos R y el ruido en la señal.

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/8c5af961-30bf-4f1f-884f-15c92b56d44c)

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/e8243d14-7209-49aa-bb36-2424a3178713)

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/d2f3418b-9f8e-4d59-9fc2-10f5dfcd3140)



## Obtener los complejos QRS en la señal ECG inicial

Se identifican y extraen los complejos QRS, que representan la actividad eléctrica de la contracción ventricular.

Complejo QRS en un intervalo de 1 segundo
![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/0445c3d2-e26b-45e6-a4b5-60a0d00a6574)

Complejo QRS en un intervalo de 10 segundo
![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/f1bba0a9-911e-4d70-ba55-98819065cd12)


## Bibliografía
[1][1] BITalino, “Bitalino (R)Evolution User Manual - Plux Biosignals,” BITalino (r)evolution,(2020) https://support.pluxbiosignals.com/wp-content/uploads/2021/11/bitalino-revolution-user-manual.pdf (accessed Oct. 30, 2023). 
[2][1] J. Pan and W. Tompkins, “A real-time QRS detection algorithm - IEEE Xplore,” IEEE,(1985) https://ieeexplore.ieee.org/document/4122029 (accessed Oct. 30, 2023). 
