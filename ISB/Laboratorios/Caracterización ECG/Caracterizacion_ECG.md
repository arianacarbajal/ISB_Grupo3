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

![señalecgOG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/31c62ccb-6c84-4c39-a258-1c8fa899f954)


## Análisis en frecuencia de la señal ECG

Se realizó la transformada de fourier a la señal para poder obtener el espectro de frecuencias y detectar los ruidos. Podemos notar un evidente ruido en frecuencias altas, con picos marcados proveniente de la red eléctrica en Perú a 60Hz  y 120Hz. 
![freqECG](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/35ddb531-56ec-4d4a-8d49-2c70608da439)

## Reducir los ruidos con filtro Notch 


## Filtrar la señal con un filtro pasa banda


## Filtrar la señal con un filtro pasa alto


## Realizar el filtrado derivativo



