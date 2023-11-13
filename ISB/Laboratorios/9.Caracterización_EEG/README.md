# Laboratorio 9: Filtrado y caracterización de señal EEG
## Tabla de contenidos:
* [Objetivos](#objetivos)
* [Materiales y equipos](#materiales-y-equipos)
* [Entregables](#entregable)
  * [Leer el Dataset](#dataset)
  * [Análisis en frecuencia de la señal EEG](#frecuencia)
  * [Reducir los ruidos con filtrado](#filtrado)
  * [Realizar filtrado wavelet](#filtrado_wavelet)
  * [Separación de las 5 ondas representativas de un EEG](#5_ondas)
  * [Extracción de características de la señal](#theshold)

* [Bibliografía](#bibliografía)

## Objetivos:

*Realizar un análisis en frecuencia de la señal
* Atenuar ruidos de la señal
* Filtrar la señal
* Obtener las ondas características de la señal
* Obtener características de la señal

## Materiales y equipos:

<div align="center">

|  **Materiales**  | **Descripción** | 
|:------------:|:---------------:|
|   Laptop   |   Se utilizo para obtener las gráficas de la señal EEG y realizar el procesamiento en Python |
|    Google collab   |  Se utilizó como entorno de desarrollo de python |

</div>

## Leer el Dataset

La señal se obtuvo utilizando el BITalino, por lo que se realizó la conversión de unidades para poder obtener la señal en las unidades de tiempo y mV.

![eeg_original](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/523b0023-e357-440a-8a8f-503dd6502576)

![eeg_3seg](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/d515c465-2b8d-4246-a015-57b0800bf5f0)

## Análisis en frecuencia de la señal EEG

![fft_eeg](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/119dfb4c-3362-4987-83cf-3493e41fb609)

![eeg_fft_db](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/567511ec-fcb3-41c9-9b63-a45ff920c4cd)

## Reducir los ruidos con filtrado

