# Laboratorio 4: Adquisición ECG Bitalino
## Tabla de contenidos:
* [Objetivos](#objetivos)
* [Materiales y equipos](#materiales-y-equipos)
* [Entregables](#entregable)

  * [Archivo de los datos de la señal ploteada](#archivos)
  * [Ploteo de la señal original en Python.](#gráficos-en-python)

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

Imagen 1

En la imagen 2 se puede ver el código utilizado y como se adecuó la señal. Primeramente se abre el documento ecg2reposo.txt, se definr la frecuencia 

![Imagen2](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4add4cc3-69e9-4bb3-b44f-692dde9fef74)

Imagen 2

![señalecgOG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/31c62ccb-6c84-4c39-a258-1c8fa899f954)

Imagen 3


## Análisis en frecuencia de la señal ECG

Se realizó la transformada de fourier a la señal para poder obtener el espectro de frecuencias y detectar los ruidos. Podemos notar un evidente ruido en frecuencias altas, con picos marcados proveniente de la red eléctrica en Perú a 60Hz  y 120Hz. 

![freqECG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/35ddb531-56ec-4d4a-8d49-2c70608da439)

Imagen 4

## Reducir los ruidos con filtro Notch 

Una vez que se identificó las frecuencias de los fitros más prominentes, se utilizó filtros Notch para eliminar específicamente las frecuencias de 60 y 120Hz puesto que en ese rango se tiene información importante del ecg, lo cual impide en uso de un filtro pasa baja. También se realizó un filtro Notch a 50 Hz. En el espectro de frecuencias, se detectó un pequeño ruido en esta frecuencia lo cual puede ser ruido magnetico y si bien es un pico pequeño, la señal mejoró mucho más al filtrar esta frecuencia. En la imagen 5, podemos ver el espectro de frecuencias después de haber filtrado la señal.

![frecdespNotch](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/e22fbec0-1017-48ac-b331-d707216b85bb)

Imagen 5

En la imagen 6 podemos ver la señal ECG después de haber filtrado las señal.

![ECGdespNotch](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4d769b66-27b6-44fc-b56c-5fce12fe67cd)

Imagen 6

## Filtrar la señal con un filtro pasa baja

Ahora se realiza un filtrado pasa baja para concentrarnos específicamente en el rango de frecuencias de un ecg y eliminar todos los ruidos de frecuencia alta, esto permite que las componentes de baja frecuencia relevantes, como las ondas P, QRS y T, pasen sin atenuación significativa. Se utilizó específicamente un filtro Butterworth de segundo orden con una frecuencia de corte de 11.0 Hz. Se escogió Buterworth por su respuesta de paso bajo suave y su fase lineal, lo que evita la distorsión en el dominio del tiempo; y es de segundo orden ya que proporciona una mayor capacidad de atenuación y permite un mayor control de la frecuencia de corte seleccionada.
En la siguiente imagen 7 podemos ver la respuesta en frecuencia del filtro diseñado y en la imagen 8 vemos la señal filtrada, la cual se ve más limpia que la anterior que solo utilizaba filtros Notch

![respFreq](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/c0bc0feb-8931-4b37-88f7-0269d05446f3)

Imagen 7:respuesta en frecuencia del filtro Butterworth pasabaja de segundo orden

![ECG_filtradoBAJAS](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4f1e08f9-6f65-4520-9d4c-10f810b5fdaf)

Imagen 8: Señal filtrada con filtro PasaBaja

## Filtrar la señal con un filtro pasa alto


## Realizar el filtrado derivativo



