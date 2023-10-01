# Laboratorio 5: Adquisición EEG Bitalino y Ultracortex
## Tabla de contenidos:
* [Objetivos](#objetivos)
* [Materiales y equipos](#materiales-y-equipos)
* [Electrocardiograma](#ecg)
* [Entregables](#entregable)
  * [Fotos de conexión usada (Electrodos-cuerpo, BITalino-cables)](#conexión-usada)
  * [Video de señal](#video-de-señal)
  * [Ejercicio utilizado](#ejercicio)
  * [Ploteo de la señal en OpenSignals](#gráficos-opensignals)

  * [Archivo de los datos de la señal ploteada](#archivos)
  * [Ploteo de la señal en Python.](#gráficos-en-python)
  * [Que se ve una señal de primera derivada.](#gráficos-en-python)
   * [Explicación de las señales](#explicación-final)
   * [Artefactos](#artefactos)
* [Bibliografía](#bibliografía)
 

## Objetivos:

* Adquirir señales biomédicas de ECG .
* Hacer una correcta configuración de BiTalino.
* Extraer la información de las señales ECG del software OpenSignals (r)evolution.

## Materiales y equipos:

<div align="center">

|  **Materiales**  | **Descripción** | 
|:------------:|:---------------:|
|  Kit BITalino |  Es un kit de desarrollo y de experimentación con diferentes sensores.   Para este laboratorio el Kit Bitalino se utilizará con el sensor ECG para la adquisición de señales  |
|   ProSim 4 vital signal simulator    | Es un comprobador funcional portátil del monitor de signos vitales.En el laboratorio se utilizó para simular una señal ECG en ejercicio intenso y paro cardiáco    |
|    Electrodos   |    Son los dispositivos que ponen en contacto al paciente con el electrocardiógrafo. A través de ellos se obtiene la información eléctrica para la impresión y el análisis del electrocardiograma. En este laboratorio se utilizaron 3 de ellos para hallar la primera derivada de ECG|
|   Laptop   |   Se utilizo para obtener las gráficas de la señal ECG en el programa Open signals y el procesamiento en Pyhton |



</div>

## Electrocardiograma

Un electrocardiograma (ECG) es un procedimiento que evalúa las señales eléctricas que regulan el ritmo del corazón. La prueba evalúa cómo los impulsos eléctricos viajan a través del músculo del corazón cuando se contrae y se relaja.[1]


El electrocardiograma es una herramienta esencial para diagnosticar y monitorear diversas enfermedades cardíacas, como arritmias, cardiomiopatías, enfermedades de las arterias coronarias, ataques cardíacos, insuficiencia cardiaca, enfermedades de las válvulas cardíacas y defectos cardiacos congénitos.[2]

El ECG utiliza derivaciones para obtener vistas del corazón desde diferentes ángulos: las bipolares (I, II, III) miden la actividad entre extremidades, las precordiales (V1-V6) se enfocan en el tórax y las aumentadas ofrecen perspectivas adicionales para evaluar la actividad eléctrica cardíaca.[3]
Para este laboratorio utilizaremos la derivada bipolar I la cual mide la actividad eléctrica entre el brazo derecho y el brazo izquierdo.

### Explicación de la onda de ECG

Las ondas de electrocardiografía (ECG) son representaciones gráficas de la actividad eléctrica del corazón. Aquí se resumen las principales características de cada onda:

1. **Onda P:** Representa la despolarización de las aurículas. Puede ser bifásica en algunas derivaciones y su amplitud aumenta con la hipertrofia auricular.

2. **Intervalo PR:** Es el tiempo entre la despolarización auricular y la despolarización ventricular. Su prolongación indica un bloqueo auriculoventricular de primer grado.

3. **Complejo QRS:** Representa la despolarización ventricular. Se compone de la onda Q (descendente), la onda R (ascendente), y la onda S (segunda descendente). 

4. **Intervalo QT:** Es el tiempo entre la despolarización ventricular y la repolarización ventricular. 

5. **Segmento ST:** Representa la despolarización completa del miocardio ventricular. La elevación puede indicar varias condiciones, incluyendo isquemia o infarto, mientras que la depresión puede estar relacionada con hipopotasemia u otros problemas.

6. **Onda T:** Refleja la repolarización ventricular.  Cambios en su forma o amplitud pueden indicar desequilibrios electrolíticos o problemas cardíacos.[4]

<p align="center">
<img src="Img_ecg/señal.jpg"align="center" />
</p>


## Procedimiento:
### Participantes :

Se adquirieron señales  2 participantes para el laboratorio.

|  **Participante**  | **Edad** | **Actividad fisica** |
|:------------:|:---------------:|:------------:|
| Participante 1 |   20  |     Hace ejercicio una vez por semana     |
|     Participante 2   |      21   | Practica ejercicio de 4/5 veces a la semana|


La participante 2 es del sexo femenimo , mientras que el 1 es del masculino.


### Conexión usada circuito:
Para el circuito , se hizo uso del cable de tres hilos con tres de los electrodos no invasivos. 
El cable de 3 hilos se conecto al puerto 2 ya que se utilizara ECG en el laboratorio . Por ultimo se conecto la bateria y se encendio el switch ON/OFF.

<p align="center">
<img src="Img_ecg/conec.jpg"align="center" />


### Conexión usada - electrodos:
Para plotear  la señal obtenida, se colocó los electrodos en la posición que se muestra en la siguiente figura. 

<p align="center">
<img src="Img_ecg/elec.jpg" align="center" />



Se posiciono el electrodo rojo con polaridad positiva en la muñeca izquierda , el electrodo negro con polaridad negativa en la muñeca derecha y el electrodo de referencia blanco en la cresta iliaca del participante.

Se muestran las conexiones en la siguiente figura:

<p align="center">
<img src="Img_ecg/ele.jfif" align="center" />
</p>

Se utilizó la configuración bipolar de los electrones y se obtuvo la derivada 1 del ECG.

Luego de ello , se conectó   el BiTalino por Bluetooth con el programa  OpenSignals para poder visualizar la señal deseada y se realizaron dos pruebas: una con el participante en reposo  y la segunda se realizo cuando el participante haya realizado 2 minutos de ejercicio .

### Ejercicio realizado : Burpee
Los burpees son ejercicios breves y de alta intensidad que trabajan diversos músculos como el abdomen, la espalda, el pecho, los brazos y las piernas. Es un tipo de ejercicio anaeróbico ya que se realiza en un ritmo más intenso y es más corto en duración , en comparación a ejercicios aeróbicos .Durante el ejercicio aeróbico, la frecuencia cardíaca se mantiene en un rango moderado, mientras que durante el ejercicio anaeróbico se eleva significativamente, por ello es que se utilizó este tipo de ejercicio para el procedimiento del laboratorio.[5] [6]


Prueba 1 :Señal ECG en reposo

<p align="center">
<img src="Img_ecg/rep.jfif" align="center" />

</p>

Prueba 2: Señal ECG luego de ejercicio (2 minutos de Burpees)

<p align="center">
<img src="Img_ecg/ej.jfif" align="center" />
</p>

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

-[Archivos txt de cada participante](https://github.com/arianacarbajal/ISB_Grupo3/tree/d909b519ee5c547a1c889af40f01fbb1b80932ce/ISB/Laboratorios/4.Adquisicion_ECG/Txt_ecg)

-[Archivos ipny con codigo de cada participante](https://github.com/arianacarbajal/ISB_Grupo3/tree/d909b519ee5c547a1c889af40f01fbb1b80932ce/ISB/Laboratorios/4.Adquisicion_ECG/Ipny_ecg)

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

![Imagen3](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/c2bfb3b1-38e5-462d-9917-ee99ed8799d5)

Tenemos las dos señales en reposo de los voluntarios. Se puede observar que el primero, tiene una mayor amplitud en el reposo, por lo que vemos que tuvo una mayor actividad ya que le costaba mantenerse en reposo absoluto. Sin embargo, en ambas señales vemos una amplitud pequeña propia de las ondas de baja amplitud alfa y theta, las cuales son propias de un estado de reposo[a].

![Imagen4](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/d82f7a80-90c9-4770-825a-757ca0453690)

Se ve que los picos más prominentes están en frecuencias cercanas a 0 y que no existe una actividad superior a los 30Hz[c], lo cual indicaría que el paciente ya no está en reposo, que siente algún dolor, está realizando algún esfuerzo o algún suceso inesperado.

![download (3)](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/900d3844-85d4-46a0-a9bb-21eb4e68453f)
![download (4)](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/0e83a43a-0ba5-4f75-89b4-47fff416cb55)

Obtuvimos la señal durante el ejercicio del parpadeo con el bitalino. Si bien se puede observar mayores amplitudes en los momentos de parpadeo, estas no son tan marcadas como idealmente se hubiera querido obtener, principalmente por el posicionamiento de los electrodos, ya que la mayor actividad se da en la región occipital debido a la cercanía de los músculos y movimientos oculares[b], sin embargo si es posible detectar picos de mayor amplitud cada aproximadamente 5 segundos y se puede comparar con las señales obtenidas en otro estudio[c] donde se realizó un filtrado más complejo y en la zona occipital pero se muestra que los mayores picos son los indicadores de actividad y que esta mayor amplitud es el indicador utilizado pues no hay características propias del parpadeo.




### Artefactos que pueden afectar la señal ECG 
Según ese análisis en este paper [13], se demuestra que una mala ubicación de los electrodos en el torso puede provocar la modificación de las señales adquiridas, errores de diagnóstico y una mala interpretación de la información de la señal. 

Por lo tanto, se recomienda realizar una  correcta modificación de la posición de los electrodos. Este cambio en la posición de los electrodos también tiene el propósito de reducir la influencia del ruido y los artefactos, tratando de colocar los electrodos en lugares con menos tejido adiposo, lo que actúa como un dieléctrico que modifica de manera impredecible las propiedades eléctricas del conductor de volumen cuando el sujeto realiza movimiento. Sin embargo, esto último puede afectar la calidad del ECG al no utilizar el método de triángulo de Einthoven. Por lo tanto, se utiliza un modelo computacional para determinar la influencia que tiene las posiciones de los electrodos en la medición . Esto precisamente se utilizaría para medir la determinar el nivel de distorsión de la señal ECG permitiendo que las señales medidas se puedan  ajustar a las derivaciones propuestas en el triángulo de Einthoven. Además, sería posible conocer la posición donde la señal muestra poca distorsión y obtener una reducción significativa de los artefactos de movimiento.

Aparte de la posición de electrodos, artefactos que emitan un campo electromagnético también afectan la calidad y medición del ECG. Por ejemplo, se demostró que la radiación electromagnética emitida de los celulares influye en los registros del ECG [14]. Incluso, las terapia de campos electromagnéticos pulsados de frecuencia extremadamente baja (ELF-PEMF)  también pueden llegar a afectar la medición del electrocardiograma. [15] 

### ¿ Que ocurre con el ECG cuando realizamos la medición  en una persona en reposo y  luego de realizar ejercicio? 

Los dos participantes reposaron durante 2 min para luego realizarse la medición de ECG.Luego , ambos  participantes realizaron ejercicios de burpees durante 2 minutos, luego se  procedió a medir el ECG.El tipo de  ejercicio no influye significativamente a la medición de ECG ,ya que lo importante es que aumenten sus bpm-latidos por minuto(de 90 a 150 generalmente). 
 
A continuación se muestra las gráficas de ECG en reposo y luego de la actividad física  de los participantes.

Participante 1 : Comparación de  ECG en reposo  y  ECG luego del ejercicio.
<p align="center">
<img src="Img_ecg/pip.jpg" align="center"/>
</p>



Participante 2 : Comparación de  ECG en reposo  y  ECG luego del ejercicio.

<p align="center">
<img src="Img_ecg/pep.jpg" align="center"/>
</p>













Participante  analizado del paper : Comparación  ECG en reposo y  ECG luego del ejercicio. [ 16] 
<p align="center">
<img src="Img_ecg/pap.jpg" align="center"/>
</p>



Se visualiza que la señal obtenida de los participantes comparada   con la encontrada en la literatura varían debido a muy probablemente a la colocación de los electrodos o efectos de electromagnetismo explicadas anteriormente. No obstante,sí  se puede llegar a visualizar que después del ejercicio en las 3 gráficas,, la frecuencia cardíaca aumenta, los intervalos PR y QT se acortan, la onda S se vuelve más prominente, la onda T es más pronunciada, acercándose incluso al pico de la onda R cuya amplitud también aumenta. [16] 



## Bibliografía


[1]“Electrocardiograma,” Medlineplus.gov, 2022. Available: https://medlineplus.gov/spanish/pruebas-de-laboratorio/electrocardiograma/. [Accessed: Sep. 17, 2023]


‌[2]“Electrocardiograma,” Medlineplus.gov, 2022. Available: https://medlineplus.gov/spanish/pruebas-de-laboratorio/electrocardiograma/. [Accessed: Sep. 17, 2023]


[3]Euroinnova Business School, “Derivaciones de electrocardiograma,” Euroinnova Business School, Aug. 08, 2023. Available: https://www.euroinnova.pe/blog/latamelectrocardiograma-derivaciones#:~:text=La%20derivaci%C3%B3n%20I%20mide%20laizquierdo%20y%20la%20pierna%20izquierda.. [Accessed: Sep. 17, 2023]

‌
[4]T. Cascino and M. J. Shea, “Electrocardiografía,” Manual MSD versión para profesionales, Jul. 06, 2021. Available: https://www.msdmanuals.com/es-pe/professional/trastornos-cardiovasculares/pruebas-y-procedimientos-cardiovasculares/electrocardiograf%C3%ADa. [Accessed: Sep. 17, 2023]
‌

[5]L. Delgado, “Cómo entender fácilmente la diferencia entre aeróbico y anaeróbico,” Sportlife, Jan. 23, 2023. Available: https://www.sportlife.es/entrenar/fitness/como-entender-facilmente-diferencia-entre-aerobico-anaerobico_271079_102.html. [Accessed: Sep. 17, 2023]
‌

[6]Promax Nutrition, “The Benefits of Burpees,” Promax Nutrition, Jun. 29, 2016. Available: https://www.promaxnutrition.com/blogs/news/benefits-burpees. [Accessed: Sep. 17, 2023]

‌
[7] Yuan Weiting and R. Zhou, “An Improved Self-Adaptive Filter Based on LMS Algorithm for Filtering 50Hz Interference in ECG Signals,” Aug. 2007, doi: https://doi.org/10.1109/icemi.2007.4351057. Available: https://ieeexplore.ieee.org/document/4351057. [Accessed: Sep. 17, 2023]


[8]“Introduction - Cardiology Teaching Package - Practice Learning - Division of Nursing - The University of Nottingham,” Nottingham.ac.uk, 2023. Available: https://www.nottingham.ac.uk/nursing/practice/resources/cardiology/introduction/index.php. [Accessed: Sep. 17, 2023]
‌

[9]
“Cátedra de Clínica Médica - Facultad de Ciencias Médicas - Universidad Nacional de Rosario,” Clinica-unr.com.ar, 2023. Available: http://www.clinica-unr.com.ar/2015-web/Educacion_distancia/Curso_ECG_01.htm. [Accessed: Sep. 17, 2023]

[10] J. Gallo Villegas, "Exercise Electrocardiogram Testing: Usefulness in the Diagnosis and Prognosis of Coronary Artery Disease," 2015.

[11]
“Latidos cardíacos rápidos, lentos e irregulares (arritmia),” HealthyChildren.org, 2023. Available: https://www.healthychildren.org/Spanish/health-issues/conditions/heart/Paginas/Irregular-Heartbeat-Arrhythmia.aspx. [Accessed: Sep. 17, 2023]
‌

‌[12]Business Bliss FZE, “Effects and Functions of an Electrocardiogram Under the Influence of Exercise,” Ukessays.com, Mar. 21, 2023. Available: https://www.ukessays.com/essays/physiology/effects-and-functions-of-an-electrocardiogram-under-the-influence-of-exercise.php?vref=1. [Accessed: Sep. 17, 2023]
‌
[13]Sensitivity and Adjustment Model of Electrocardiographic Signal Distortion Based on the Electrodes’ Location and Motion Artifacts Reduction for Wearable Monitoring Applications. (s.f.). MDPI. https://www.mdpi.com/1424-8220/21/14/4822


[14] . MEASUREMENT SCIENCE REVIEW. https://www.measurement.sk/2013/Buczkowski.pdf(2013)

[15]An Investigation on the Effect of Extremely Low Frequency Pulsed Electromagnetic Fields on Human Electrocardiograms (ECGs). (s.f.). MDPI. https://www.mdpi.com/1660-4601/13/11/1171


