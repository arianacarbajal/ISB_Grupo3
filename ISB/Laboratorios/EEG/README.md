# Laboratorio 5: Adquisición EEG Bitalino y Ultracortex
## Tabla de contenidos:
* [Objetivos](#objetivos)
* [Materiales y equipos](#materiales-y-equipos)
* [Electroencefalograma](#ecg)
* [Entregables](#entregable)
  * [Fotos de conexión usada (Electrodos-cuerpo, BITalino-cables)](#conexión-usada)
  * [Video de señal](#video-de-señal)
  * [Procedimiento realizado de registro EEG](#ejercicio)
  * [Ploteo de la señal en OpenSignals](#gráficos-opensignals)

  * [Archivo de los datos de la señal ploteada](#archivos)
  * [Ploteo de la señal en Python.](#gráficos-en-python)
   * [Explicación de las señales](#explicación-final)
   * [Artefactos](#artefactos)
* [Bibliografía](#bibliografía)
 
## Objetivos:

* Adquirir señales biomédicas de EEG .
* Hacer una correcta configuración de BiTalino.
* * Hacer una correcta configuración de Ultracortex.
* Extraer la información de las señales EeG del software OpenSignals (r)evolution.

## Materiales y equipos:

<div align="center">

|  **Materiales**  | **Descripción** | 
|:------------:|:---------------:|
|  Kit BITalino |  Es un kit de desarrollo y de experimentación con diferentes sensores.   Para este laboratorio el Kit Bitalino se utilizará con el sensor EEG para la adquisición de señales  |
|   Ultracortex    |Es una herramienta para registrar la actividad cerebral (EEG) con fines de investigación que consta de un casco imprimible en 3D diseñado para funcionar con el sistema OpenBCI   |
|    Electrodos   | Son discos de metal planos que se colocan en el cuero cabelludo   |
|   Laptop   |   Se utilizo para obtener las gráficas de la señal EEG en el programa Open signals, Open BCI y el procesamiento en Pyhton |



</div>



## Electroencefalograma

La electroencefalografía (EEG) es una técnica no invasiva que utiliza electrodos en el cuero cabelludo para medir los campos eléctricos del cerebro. Esta prueba registra los potenciales de voltaje producidos por el flujo de corriente en y alrededor de las neuronas. [1]

En los procedimientos de electroencefalografía, se colocan electrodos en el cuero cabelludo del paciente, que están conectados a un electroencefalógrafo. Durante el estudio, el paciente se encuentra en un estado de reposo y relajación, y se pueden realizar pruebas específicas, como la hiperventilación o la estimulación luminosa, para provocar respuestas anormales en el cerebro. Los resultados se registran en un electroencefalograma (EEG) y son evaluados por un especialista en neurofisiología clínica para identificar patrones anormales de actividad cerebral.

El Electroencefalograma tiene como objetivo principal detectar anormalidades en las ondas cerebrales y la actividad eléctrica del cerebro. Su utilidad abarca la evaluación de una amplia gama de condiciones neurológicas, como epilepsia, trastornos mentales, parasomnias, encefalopatías metabólicas, demencia y convulsiones relacionadas con accidentes cerebrovasculares. Además, el EEG desempeña un papel valioso en la predicción del pronóstico en casos de lesiones cerebrales, traumatismos craneoencefálicos, muerte cerebral y toxicidad por medicamentos. Este procedimiento es esencial en la neurología y se utiliza tanto en la práctica clínica como en la investigación científica para comprender mejor la función cerebral y desarrollar terapias de neurorehabilitación basadas en la actividad cerebral. [2]


### Explicación de la onda de ECG


<p align="center">
<img src="Img_ecg/señal.jpg"align="center" />
</p>


## Procedimiento:
### Participantes :

Se adquirieron señales  2 participantes para el laboratorio.

|  **Participante**  | **Edad** | **Sexo** |
|:------------:|:---------------:|:------------:|
| Participante 1 |   20  |    Masculino   |
|     Participante 2   |      20  |Feminino|




### Conexión usada circuito Bitalino:
Para el circuito , se hizo uso del cable de tres hilos con tres de los electrodos no invasivos. 
El cable de 3 hilos se conecto al puerto 4 ya que se utilizara EEG en el laboratorio . Por ultimo se conecto la bateria y se encendio el switch ON/OFF.

<p align="center">

<img src="https://github.com/arianacarbajal/ISB_Grupo3/blob/817e448d75c3dc40c041a78026f0e5bbb8b43369/ISB/Laboratorios/Imagenes/BITALINO.png" alt="Bitalino EEG" align="center"/>
</p>

### Conexión usada - electrodos:
Para plotear  la señal obtenida, se utilizo el Bitalino para medicion de EEG [3]. 


<img src="https://github.com/arianacarbajal/ISB_Grupo3/raw/6aae7f9965a724e9d9c3d24dea07af56b95fb016/ISB/Laboratorios/Imagenes/elec2.jpg" width="400" />

<p align="center">

</p>

Posicionamiento de electrodos para el participante 1 
</p>

<img src="https://github.com/arianacarbajal/ISB_Grupo3/raw/1c44760bb2b864bee4fb86fcd6f6485acc1ffa65/ISB/Laboratorios/Imagenes/elec1.jpg" width="400" />


<p align="center">

</p>
Posicionamiento de electrodos para la participante 2
</p>


Se posiciono el electrodo rojo con polaridad positiva en la parte izquierda de la frente , el electrodo negro con polaridad negativa en la parte derecha de la frente  y el electrodo de referencia blanco en la parte posterior de la oreja del participante.

Se muestran las conexiones en la siguiente figura:

<img src="https://github.com/arianacarbajal/ISB_Grupo3/blob/817e448d75c3dc40c041a78026f0e5bbb8b43369/ISB/Laboratorios/Imagenes/COLOCACION%20ELECTRODOS.png" alt="Imagen de referencia ">
<p align="center">

</p>


Luego de ello , se conectó   el BiTalino por Bluetooth con el programa  OpenSignals para poder visualizar la señal deseada y se realizaron las pruebas a los 2 participantes.

### Procedimiento realizado de registro EEG
1. Registrar una línea base de señal con poco ruido y sin movimientos (respiración normal,
sin movimientos oculares/ojos cerrados) durante 30 segundos.
2. Repetir un ciclo de OJOS ABIERTOS - OJOS CERRADOS cinco veces, manteniendo ambas
fases durante cinco segundos.
3. Registre otra fase de referencia de 30 segundos (paso 1).
4. Que uno de tus compañeros lea en voz alta una serie de ejercicios matemáticos (ver
indicaciones abajo) y resuelve cada uno de ellos mentalmente enfocando tu mirada en un
punto específico para evitar artefactos.
5. Detenga la grabación y guarde sus datos.

### Video de señal 
En el siguiente video de youtube se muestran las conexiones electrodos-cuerpo y visualización de la Señal en OpenSignals para el Participante 1 .
Se muestra  la señal en reposo absoluto 

Video de la señal en reposo:

<div align="center">

[![Video EMG ](https://img.youtube.com/vi/2OWpv3OOGYY/mqdefault.jpg)](https://youtu.be/2OWpv3OOGYY)


Video de la señal despues de ejercicio:

<p align="center">



[![Video EMG ](https://img.youtube.com/vi/14niZ4_Tip4/mqdefault.jpg)](https://youtu.be/14niZ4_Tip4)


Es importante mencionar que no se esta apoyando el Bitalino en la mesa de las computadoras debido a que si estaba posicionado ahi , no se podia adquirir bien la señal , puede deberse al ruido electromagnético.


</div>

### Gráficos OpenSignals
Participante 1
 - Señal  en reposo:
<p align="center">
<img src="Img_ecg/rep_ed.jpg" align="center" />
</p>

 - Señal despues de movimiento:
<p align="center">
<img src="Img_ecg/ej_ed.jpg" align="center"/>
</p>
Participante 2
 - Señal  en reposo:
<p align="center">
<img src="Img_ecg/rep_n.jfif" align="center" />
</p>

 - Señal despues de movimiento:
<p align="center">
<img src="Img_ecg/ej_n.jfif" align="center"/>
</p>



### Archivos
Por otro lado podemos encontrar los archivos de la informacion de las señales ploteadas 

-[Archivos txt de cada participante](https://github.com/arianacarbajal/ISB_Grupo3/tree/d909b519ee5c547a1c889af40f01fbb1b80932ce/ISB/Laboratorios/EEG/TXT)

-[Archivos ipny con codigo de cada participante](https://github.com/arianacarbajal/ISB_Grupo3/tree/d909b519ee5c547a1c889af40f01fbb1b80932ce/ISB/Laboratorios/EEG/ipny)

### Codigo utilizado para los graficos en Phyton
El código contiene comentarios para el mejor entendimiento de la lógica usada.


```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
import re
from scipy import signal
from scipy.signal import medfilt, iirnotch, butter, filtfilt


f = open("ecg1reposo.txt","r")
raw_data = f.read()  # con f.read() leemos todo el contenido
f.close()

raw_data
Fs = 1000
Ts = 1/Fs
print(f" Fs={Fs} hz\n Ts={Ts} s")

a = np.genfromtxt("./ecg1reposo.txt", delimiter="\t",skip_header = 3)
yarray = a[:, 5]
N=len(yarray)
bits = 10 # Bits de la salida
volt_range = 3.3
yarray = (yarray/2**bits -1/2) * volt_range/1009
yarray=yarray*1000 # convertir los bits a mV
yarray = yarray - np.mean(yarray)
xarray = np.arange(1, len(yarray)+1)/Fs
xarray=xarray
plt.figure(figsize=(8, 6))
plt.plot(xarray, yarray, label="señal")
plt.grid(linestyle=":")
plt.figure(figsize=(8, 6))
plt.plot(xarray, yarray, label="señal")
plt.grid(linestyle=":")
plt.xlim(0,3)
#FFT
signal_fft = np.fft.fft(yarray)
frequencies = np.fft.fftfreq(N, Ts)

#-Fs/2 a Fs/2
frequencies = np.fft.fftshift(frequencies)
signal_fft = np.fft.fftshift(signal_fft)
plt.figure(figsize=(8, 6))
plt.plot(frequencies, np.abs(signal_fft), label="FFT Normalizada")
plt.grid(linestyle=":")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Amplitud")
plt.legend(loc="upper right")
plt.xlim(0, Fs/2)

plt.figure()
plt.plot(frequencies, 20*np.log10(np.abs(signal_fft)), label="FFT Normalizada en dB")
plt.grid(linestyle=":")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Amplitud")
plt.legend(loc="upper right")
plt.xlim(0, Fs/2)
#Filtro notch
f0 = 60.0
cutoff_freq = 20.0
filter_order = 2
#Filtro pasa baja
normal_cutoff = cutoff_freq / (0.5 * Fs)
b, a = signal.butter(filter_order, normal_cutoff, btype='low', analog=False)
filtered_signal = signal.lfilter(b, a, yarray)
#Filtro pasa alta
filter_order = 30
cutoff_freq = 0.5
normal_cutoff = cutoff_freq / (0.5 * Fs)
b, a = signal.butter(filter_order, normal_cutoff, btype='high', analog=False)


b, a = signal.iirnotch(f0, 30, Fs)
filtered_signal = signal.lfilter(b, a, filtered_signal)

window_size = 13
filtered_signal = medfilt(filtered_signal, kernel_size=window_size)

plt.figure(figsize=(8, 6))
plt.plot(xarray, filtered_signal)
plt.title("Señal filtrada")
plt.grid(linestyle=":")
plt.xlabel("Tiempo (s)")
plt.ylabel("Amplitud")
plt.xlim(0,3)

#BPM
threshold = -0.2
above_threshold = np.where(filtered_signal[0:3000] < threshold)[0]
new_array = []
for i in range(len(above_threshold)):
  if i == 0 or above_threshold[i] != above_threshold[i - 1] + 1:
    new_array.append(above_threshold[i])
num_beats = len(new_array)
bpm = (num_beats / 3.0) * 60.0
print("Frecuencia cardíaca: {:.2f} bpm".format(bpm))


signal_fft = np.fft.fft(filtered_signal)
frequencies = np.fft.fftfreq(N, Ts)
frequencies = np.fft.fftshift(frequencies)
signal_fft = np.fft.fftshift(signal_fft)
plt.figure(figsize=(8, 6))
plt.plot(frequencies, np.abs(signal_fft), label="FFT Normalizada")
plt.grid(linestyle=":")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Amplitud")
plt.legend(loc="upper right")
plt.xlim(0, Fs/2)

plt.figure()
plt.plot(frequencies, 20*np.log10(np.abs(signal_fft)), label="FFT Normalizada en dB")
plt.grid(linestyle=":")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Amplitud")
plt.legend(loc="upper right")
plt.xlim(0, Fs/2)

```


‌

### Gráficos en Python
Posteriormente se pudo procesar la señal adquirida con ayuda de un codigo compilado en Python, con lo que se obtuvieron las señales.

Participante 1
 - Señal del reposo completa:
<p align="center">
<img src="Img_ecg/ecg1_rep/señalcompleta.png" align="center"/>
</p>

 - Señal del reposo 5 segundos:
<p align="center">
<img src="Img_ecg/ecg1_rep/señal5sec.png" align="center"/>
</p>

 -  Señal del reposo 5 segundos filtrada:
<p align="center">
<img src="Img_ecg/ecg1_rep/filtrada.png" align="center"/>
</p>

 - FFT normalizada en Hz :
<p align="center">
<img src="Img_ecg/ecg1_rep/fft.png" align="center"/>
</p>

 - FFT normalizada en Hz filtrada:
<p align="center">
<img src="Img_ecg/ecg1_rep/fftfiltrada.png" align="center"/>
</p>

  - FFT normalizada en DB  :
<p align="center">
<img src="Img_ecg/ecg1_rep/fftDB.png" align="center"/>
</p>

  - FFT normalizada en DB filtrada  :
<p align="center">
<img src="Img_ecg/ecg1_rep/fftDBfiltrada.png" align="center"/>
</p>

 - Señal despues de ejercicio completa:
<p align="center">
<img src="Img_ecg/ecg1_ej/señalcompleta.png" align="center"/>
</p>

 - Señal despues de ejercicio  5 segundos:
<p align="center">
<img src="Img_ecg/ecg1_ej/señal5sec.png" align="center"/>
</p>

 -  Señal despues de ejercicio 5 segundos filtrada:
<p align="center">
<img src="Img_ecg/ecg1_ej/señalfiltrada.png" align="center"/>
</p>

 - FFT despues de ejercicio en Hz :
<p align="center">
<img src="Img_ecg/ecg1_ej/fft.png" align="center"/>
</p>

 - FFT despues de ejercicio en Hz filtrada:
<p align="center">
<img src="Img_ecg/ecg1_ej/FFTfiltrada.png" align="center"/>
</p>

  - FFT despues de ejercicio en DB  :
<p align="center">
<img src="Img_ecg/ecg1_ej/fftDBsinfiltro.png" align="center"/>
</p>

  - FFT despues de ejercicio en DB filtrada  :
<p align="center">
<img src="Img_ecg/ecg1_ej/fftDBfiltrada.png" align="center"/>
</p>

Participante 2
 - Señal del reposo completa:
<p align="center">
<img src="Img_ecg/ecg2_rep/señalcompleta.png" align="center"/>
</p>

 - Señal del reposo 5 segundos:
<p align="center">
<img src="Img_ecg/ecg2_rep/señal5sec.png" align="center"/>
</p>

 -  Señal del reposo 5 segundos filtrada:
<p align="center">
<img src="Img_ecg/ecg2_rep/señalfiltrada.png" align="center"/>
</p>

 - FFT normalizada en Hz :
<p align="center">
<img src="Img_ecg/ecg2_rep/fft.png" align="center"/>
</p>

 - FFT normalizada en Hz filtrada:
<p align="center">
<img src="Img_ecg/ecg2_rep/fftfiltrada.png" align="center"/>
</p>

  - FFT normalizada en DB  :
<p align="center">
<img src="Img_ecg/ecg2_rep/fftDB.png" align="center"/>
</p>

  - FFT normalizada en DB filtrada  :
<p align="center">
<img src="Img_ecg/ecg2_rep/fftDBfiltrada.png" align="center"/>
</p>

- Señal despues de ejercicio completa:
<p align="center">
<img src="Img_ecg/ecg2_ej/señalcompleta.png" align="center"/>
</p>

 - Señal despues de ejercicio  5 segundos:
<p align="center">
<img src="Img_ecg/ecg2_ej/señal5sec.png" align="center"/>
</p>

 -  Señal despues de ejercicio 5 segundos filtrada:
<p align="center">
<img src="Img_ecg/ecg2_ej/señalfiltrada.png" align="center"/>
</p>

 - FFT despues de ejercicio en Hz :
<p align="center">
<img src="Img_ecg/ecg2_ej/fft.png" align="center"/>
</p>

 - FFT despues de ejercicio en Hz filtrada:
<p align="center">
<img src="Img_ecg/ecg2_ej/FFTfiltrada.png" align="center"/>
</p>

  - FFT despues de ejercicio en DB  :
<p align="center">
<img src="Img_ecg/ecg2_ej/fftDBsinfiltro.png" align="center"/>
</p>

  - FFT despues de ejercicio en DB filtrada  :
<p align="center">
<img src="Img_ecg/ecg2_ej/fftDBfiltrada.png" align="center"/>
</p>

### Señales graficadas en Prosim
- Señal de ejercicio completa:
<p align="center">
<img src="Img_ecg/ecg_ej/señalcompleta.png" align="center"/>
</p>

 - Señal al incio de ejercicio  5 segundos:
<p align="center">
<img src="Img_ecg/ecg_ej/señal5sec.png" align="center"/>
</p>

 -  Señal en los segundos 90_95 de ejercicio:
<p align="center">
<img src="Img_ecg/ecg_ej/señalfiltrada.png" align="center"/>
</p>

 - FFT  de ejercicio en Hz :
<p align="center">
<img src="Img_ecg/ecg_ej/fft.png" align="center"/>
</p>


  - FFT  de ejercicio en DB  :
<p align="center">
<img src="Img_ecg/ecg_ej/fftDBsinfiltro.png" align="center"/>
</p>


### Simulacion señal paro cardiaco Prosim
- Señal de parada cardiaca completa:
<p align="center">
<img src="Img_ecg/ecg_p/señal.png" align="center"/>
</p>

 - Señal ECG normal:
<p align="center">
<img src="Img_ecg/ecg_p/norm.png" align="center"/>
</p>

 -  Señal en Taquicardia ventricular:
<p align="center">
<img src="Img_ecg/ecg_p/Taquicardia_vent.png" align="center"/>
</p>

 -  Señal en Fibrosis ventricular:
<p align="center">
<img src="Img_ecg/ecg_p/fibrosis_vent.png" align="center"/>
</p>

 -  Señal en Asistolia:
<p align="center">
<img src="Img_ecg/ecg_p/asistolia.png" align="center"/>
</p>


 - FFT  en Hz :
<p align="center">
<img src="Img_ecg/ecg_p/fft.png" align="center"/>
</p>


  - FFT  en DB  :
<p align="center">
<img src="Img_ecg/ecg_p/fftDB.png" align="center"/>
</p>


### Filtros empleados  y Resultados obtenidos
ECG1 reposo 100.00 bpm

ECG1 ejercicio 156.00 bpm

ECG2 reposo 96.00 bpm

ECG2 ejercicio 144.00 bpm

Fue necesario aplicar filtros a nuestras señales adquiridas debido a la presencia de artefactos significativos en ellas , para ello fueron de gran importancia el analsis de las Transformadas de Fourier de cada señal. Para abordar esta distorsión, se exploraron diversas configuraciones de filtros que se adaptaran a las particularidades de cada señal. La bibliografía ofreció opciones de filtros recomendados [1], en este escenario específico, optamos por utilizar tres tipos de filtros: un filtro pasa baja, un filtro notch y un filtro de mediana.
Estos filtros se seleccionaron después de considerar las características específicas de nuestras señales y se aplicaron con el propósito de mejorar la calidad de los datos. Cada filtro se ajustó de manera adecuada para abordar las distorsiones particulares presentes en las señales, lo que permitió una interpretación más precisa de los eventos y fenómenos de interés en nuestros datos.

Filtro notch a 60 hz (Q=30):
Este filtro notch se utilizó para eliminar las interferencias de línea de alimentación eléctrica a 60 Hz, ya que se observó un pico en 60 hz en la FFT de ambos sujetos en ambos casos. El valor de Q de 30 indica un filtro relativamente estrecho y selectivo, diseñado para atenuar la frecuencia de 60 Hz y sus armónicos, mientras que conserva las componentes de frecuencia de interés del ECG.

Filtro de mediana:
El filtro de mediana se utilizó en dos configuraciones diferentes: un tamaño de ventana de 13 en un sujeto n°1 y un tamaño de ventana de 3 en el sujeto n°2. El filtro de mediana es eficaz para eliminar ruido impulsivo o picos aislados en la señal del ECG, que pueden ser causados por artefactos o interferencias momentáneas. Se presenció un ruido impulsivo significativo en la señal del sujeto n°1 a comparación del sujeto n°2, por eso se eligieron diferentes tamaños de ventana.

Filtro pasa baja en 20Hz (orden 2):
Se aplicó un filtro pasa baja con una frecuencia de corte de 20 Hz y un bajo orden de 2. La elección de este filtro se basa en la necesidad de atenuar gradualmente las frecuencias más altas presentes en la señal del ECG. Al utilizar un filtro de orden 2, se logra un decaimiento suave de las componentes de alta frecuencia, permitiendo así que se reduzca el ruido de alta frecuencia sin eliminar abruptamente información relevante en la señal. Este enfoque es beneficioso para preservar la forma de onda característica del ECG mientras se elimina el ruido de alta frecuencia, lo que facilita la identificación precisa de los eventos cardíacos.[7]

### Explicación de las señales

REPOSO

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/fb782464-8619-407d-a656-7d9e40d90a12" width="400" />
  <br />
  Voluntario 1: Voluntario 1: Reposo
</p>

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/758b1c21-afbf-4990-a285-34d3ddd3e839" width="400" />
  <br />
  Voluntario 2: Voluntario 2: Reposo
</p>

Tenemos las dos señales en reposo de los voluntarios. Se puede observar que el primero, tiene una mayor amplitud en el reposo, por lo que vemos que tuvo una mayor actividad ya que le costaba mantenerse en reposo absoluto. Sin embargo, en ambas señales vemos una amplitud pequeña propia de las ondas de baja amplitud alfa y theta, las cuales son propias de un estado de reposo[1].

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/b89e426c-906c-497a-82de-18e713e803c8" width="400" />
  <br />
  Voluntario 1: FFT  Normalizada
</p>

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/9f2d4a66-fcbd-4313-9cbd-e2ce0dda55b8" width="400" />
  <br />
  Voluntario 2: FFT  Normalizada
</p>

Se ve que los picos más prominentes están en frecuencias cercanas a 0 y que no existe una actividad superior a los 30Hz[3], lo cual indicaría que el paciente ya no está en reposo, que siente algún dolor, está realizando algún esfuerzo o algún suceso inesperado. Específicamente, en los momentos de relajación, sin atención, baja concentración y con los ojos cerrados; las ondas esperadas son las alfa, las cuales se encuentran entre los 8-13Hz, por lo que vemos una mayor amplitud en este rango, incluso podemos visualizar ondas theta, las cuales son propias del pasaje de la consciencia al sueño[5].

PARPADEO

<table>
  <tr>
    <td>
      <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/900d3844-85d4-46a0-a9bb-21eb4e68453f" alt="Voluntario 1: Señal en parpadeo">
      <p>Voluntario 2: Señal en parpadeo</p>
    </td>
    <td>
      <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/0e83a43a-0ba5-4f75-89b4-47fff416cb55" alt="Voluntario 2: Señal en parpadeo">
      <p>Voluntario 2: Señal en parpadeo</p>
    </td>
  </tr>
</table>

Obtuvimos la señal durante el ejercicio del parpadeo con el bitalino. Si bien se puede observar mayores amplitudes en los momentos de parpadeo, estas no son tan marcadas como idealmente se hubiera querido obtener, principalmente por el posicionamiento de los electrodos, ya que la mayor actividad se da en la región occipital debido a la cercanía de los músculos y movimientos oculares[2], sin embargo si es posible detectar picos de mayor amplitud cada aproximadamente 5 segundos y se puede comparar con las señales obtenidas en otro estudio[3] donde se realizó un filtrado más complejo y en la zona occipital pero se muestra que los mayores picos son los indicadores de actividad y que esta mayor amplitud es el indicador utilizado pues no hay características propias del parpadeo.

![Imagen5](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/3d8a796d-0bdd-423c-adc4-a1d3e2bde0ab)

Señal EEG referencial de parpadeo [4]

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/ba61adff-569f-44e1-a845-39405584a796" width="400" />
  <br />
  Voluntario 1: FFT resolviendo problemas matemáticos
</p>

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4f130730-c764-474a-b818-5c8c8730ec91" width="400" />
  <br />
  Voluntario 2: FFT resolviendo problemas matemáticos
</p>

Para el análisis en frecuencia, si bien pueden haber cambios en las ondas beta(13-30Hz), los cambios más significativos son en las ondas alfa, (8-13Hz) y los vemos en ambas gráficas aunque más pronunciados en Voluntario 2. Vemos que esos picos se presentan de forma simétrica. Poder distinguir estos cambios es complicado debido a los distintos estímulos a los cuales el voluntario esté sometido pues dependiendo de la imagen o sonidos al que se esté sometiendo, las gráficas variarán significativamente[5].

PROBLEMAS MATEMÁTICOS

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/41110d8b-1928-4863-9ed8-de3781449f01" width="400" />
  <br />
  Voluntario 1: Señal resolviendo problemas matemáticos
</p>

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/4a92620f-02d3-49e7-b9de-4f48bd811fa0" width="400" />
  <br />
  Voluntario 1: 5 segundos de señal resolviendo problemas matemáticos
</p>
<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/0556225d-8d3c-48ea-999d-690ed31fcdad" width="400" />
  <br />
  Voluntario 2: Señal resolviendo problemas matemáticos
</p>

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/905229c5-8675-4a6e-aac7-d5ac046629e1" width="400" />
  <br />
  Voluntario 2: 5 segundos de señal resolviendo problemas matemáticos
</p>

Tenemos las señales de los voluntarios mientras resolvían ejercicios matemáticos. En esas señales vemos amplitudes mucho mayores a las obtenidas en reposo y mayores a las de parpadeo, ya que la exigencia de la resolución de problemas requiere una activación global del cerebro. Este aumento de amplitud también puede ser debido al posicionamiento de los electrodos, los cuales estaban en el lóbulo frontal ya que esta zona suele activarse cuando una persona intenta resolver problemas[6], por lo que tenemos señales más fuertes.

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/748de7f7-9279-40b5-ba2f-7e0c07d487ac" width="400" />
  <br />
  Voluntario 1: FFT resolviendo problemas matemáticos
</p>

<p float="left">
  <img src="https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/32046faf-a329-457e-992c-3cf9a10fc817" width="400" />
  <br />
  Voluntario 2: FFT resolviendo problemas matemáticos
</p>

En los espectros de frecuencia podemos visualizar un aumento en las ondas beta específicamente, las cuales se encuentran entre 14-26 Hz. Esto se esperaba ya que estas son las ondas que se suelen visualizar cuando uno intenta resolver problemas. fue importante asegurar que los participantes se mantuvieron en el mayor reposo posible ya que la actividad motora o la estimulación táctil pueden alterar el ritmo de las ondas beta[6].


Entre los participantes, se pudo ver que el voluntario 1 tuvo mayor dificultad para mantenerse completamente relajado, por lo que las variaciones entre las amplitudes de los tres ejercicios no es tan notoria como las del voluntario 2, donde el parpadeo cuadruplica la señal de reposo y los ejercicios matemáticos duplican el anterior, lo cual podría ser por problemas de estrés, concentración y por factores externos como los estímulos externos del laboratorio debido a las actividades ruidosas o llamativas realizadas por otras personas presentes.También cabe resaltar que no hubo presencia significativa de frecuencias entre 31 y 50Hz ya que estas son las ondas "γ" y pueden ser indicadores de enfermedades cerebrales[6]
].

SEÑALES EN INTERFAZ DE ULTRACORTEX
| Imagen 1 | Imagen 2 | Imagen 3 | Imagen 4 |
|----------|----------|----------|----------|
| ![Imagen 1](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/fa549909-31b4-4690-a0b9-541202d448e5) | ![Imagen 2](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/2939138d-a0e0-46f4-a3bd-9661c2010eba) | ![Imagen 3](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/928f9e72-7435-4e6f-bf00-585df693fd64) | ![Imagen 4](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/fd07dce0-2437-4ff5-bc3e-0587cb9fc34c) |
| ![Imagen 5](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/86d8747c-3571-467b-9ba8-63dcf94eae99) | ![Imagen 6](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/b6851cb1-533e-4c0f-b494-b66be33111df) | ![Imagen 7](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/f4c61204-d5a4-4d68-aafb-b3e04556cd1d) | ![Imagen 8](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/db1c14dc-2143-4d97-bdc0-a3082cbcd997) |

En estas señales obtenidas con el utracortex, tenemos 8 canales distribuidos por el sistema 10-20, los cuales nos permiten obtener señales más claras de distintos lugares de colocación ya que, dependiendo del estímulo, la actividad cerebral será predominante en ciertas zonas. Los primeros dos canales se localizan en la zona frontal (evalúan las corteza pre frontal) que interviene en la toma de decisiones, los siguientes dos canales, igual en el lóbulo frontal pero más cercanos al plano frontal (relacionada a la acividad motora y emociones), los canales 4 y 5 son los ubicados en el lóbulo parietal, encargados de detectar la coordinación motora y la percepción sensorial y por último los canales 6 y 7 del lóbulo parietal que detectan tanto la percepción sensorial como la integración de tal información.

### Interferencias  en la señal EEG .
Existen diversas interferencias que pueden alterar la medición de un EEG. Entre las principales fuentes de estas  se encuentran : Movimientos musculares involuntarios, movimientos oculares y latidos del corazón. [7]

La existencia de estas fuentes inauténticas en prácticamente la totalidad de los sensores se origina debido a la rápida difusión de la actividad eléctrica en los tejidos.
Una estrategia para reducir el impacto de esta interferencia implica la captura separada de estas señales contaminantes para posteriormente eliminarlas de la medición mediante el algoritmo BCA( métodos de Análisis de Componentes Acotadas). [7]



Por ejemplo, en estas gráficas (figura 2.2) se visualiza la interferencia  que se genera por movimientos oculares (como parpadeo) que se obtuvo mediante un algoritmo (BCA).



<img src="https://github.com/arianacarbajal/ISB_Grupo3/blob/36a4bd86813132c6172d7043e5646d98c493e788/ISB/Laboratorios/Imagenes/algoritmo_BCA.png" alt="Algoritmo BCA">
</p>


Esta interferencia también se visualiza en el EEG  hallado en el laboratorio. En la figura 3, se  muestra la interferencia generada debido al parpadeo del   participante 2 , muy similar a la interferencia de la anterior figura. 


<img src="https://github.com/arianacarbajal/ISB_Grupo3/blob/8debe27cbe1cad862cff05ff8cbded31493bda5c/ISB/Laboratorios/Imagenes/participante_2.png" alt="Participante 2">
</p>

Por lo tanto, estas interferencias puede llegar a afectar la medicion de EEG;sin embargo, se pueden reducir estas realizando las mediciones un ambiente adecuado e instruyendo al participante que no realice otros movimientos que no sean los requeridos. Además, también se puede realizar algoritmos que permitan filtrar estos ruidos  [7]  para así obtener una señal de mejor calidad para su posterior análisis . 








## Bibliografía


[1] M. Martínez and G. Trout, “Conceptos Básicos de Electroencefalografía,” Dialnet, https://dialnet.unirioja.es/descarga/articulo/4788132.pdf (accessed Oct. 1, 2023). 

[2] L. J. Gómez Figueroa, “Análisis de señales EEG Para detección de Eventos OCULARES, musculares Y Cognitivos,” Inicio, https://oa.upm.es/44379/ (accessed Oct. 1, 2023). 

[3]“BITalino Lab Guides (Home Guides) – Support PLUX Biosignals official”. Support PLUX Biosignals official – Official PLUX support and biosignals knowledge base. Accedido el 1 de octubre de 2023. [En línea]. Disponible: https://support.pluxbiosignals.com/knowledge-base/bitalino-lab-guides/

[4] R. Sepúlveda, O. Montiel, G. Díaz, D. Gutierrez, and O. Castillo, “Clasificación de Señales Encefalográficas Mediante redes Neuronales Artificiales,” Computación y Sistemas, https://paperity.org/p/190632341/clasificacion-de-senales-encefalograficas-mediante-redes-neuronales-artificiales (accessed Oct. 1, 2023). 

[5] R. Cerino, D. Pinto, S. Vergara, and F. Pérez-Téllez, “Estimulación Visual Basada en conceptos y su análisis mediante electroencefalografía,” SciELO, https://www.scielo.org.mx/scielo.php?script=sci_arttext&pid=S1405-55462023000100107 (accessed Oct. 1, 2023). 

[6] F. Vasconcellos, “Procesamiento de señales EEG Basado en Python - UMH,” UNIVERSIDAD MIGUEL HERNÁNDEZ DE ELCHE ESCUELA POLITÉCNICA SUPERIOR DE ELCHE, http://dspace.umh.es/bitstream/11000/26575/1/TFGVasconcellos%20Noailles%2c%20Fernando.pdf (accessed Oct. 2, 2023). 


[7]Aguilera, P., Beeta, D., Sarmiento, A., & Fondón, I. Cancelación de interferencias en eeg mediante el análisis de componentes acotadas,Universidad de Sevilla, Sevilla, España, Accedido el 1 de octubre de 2023. [En línea]. Disponible:https://www.researchgate.net/profile/Pablo-Aguilera-6/publication/266896121_Cancelacion_de_interferencias_en_EEG_mediante_el_Analisis_de_Componentes_Acotadas/links/547f05490cf2c1e3d2dc392e/Cancelacion-de-interferencias-en-EEG-mediante-el-Analisis-de-Componentes-Acotadas.pdf

