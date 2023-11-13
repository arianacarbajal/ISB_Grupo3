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

### Filtrado de señal EEG
### Filtrado de señal EEG FIR
Se diseñaron dos tipos de filtros , como principal , se empleó un filtro pasabajo con una frecuencia de paso de 30 Hz , una frecuencia de stop de 40 Hz y un orden de 600. Se empleó la ventana hamming en base al paper "Digital filtering in EEGIERP analysis: Some
technical and empirical comparisons" debido a su gran atenuación y debido a que   la ventana de Hamming es relativamente gradual entre las funciones de disminución , reduciendo los pesos en aproximadamente un 46 % a la mitad desde el centro de la serie de pesos hasta el peso más externo. Reduce, pero no elimina, la ondulación relacionada con el truncamiento y amplía la banda de transición del filtro, haciéndolo menos selectivo en todo el espectro de frecuencias. En comparación con la ventana de Blackman, la ventana de Hamming es menos grave y tiene efectos más moderados, lo que es adecuado para esta aplicacion.[4]
![RTGyj](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/0a07969a-979f-4403-abbb-eea1c17d387b)

Imagen: Características de ventanas[1]


‌
Se situo a la frecuencia de corte del rechazabanda en 58.8 Hz y 61 hz para eliminar el pico de 60 hz pero es un filtro con frecuencias seguidas debido a que no queremos perder información valiosa de la señal EEG .


![descarga (1)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/2f7ba046-0376-4c73-96c1-0c526e0e4ee2)

Imagen : Señal EEG bitalino al realizar abrir y cerrar de ojos

![descarga (2)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/b19a9dab-2e0e-4b97-ba5c-bae3acfb3264)

Imagen:FFT de la señal inicial

En la respuesta en frecuencia del filtro pasabajo podemos ver su comportamiento y como va a filtrar adecuadamente el ruido de 60 hz, y vemos como tiene una correcta atenuación para las frecuencias de paso y corte que hemos indicado . 

![download (2)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/a0019f6a-68b8-4a6c-a96d-5bfc54345a91)

Imagen: Respuesta en frecuencia del filtro en Hz

![download (3)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/ff193126-6ac5-4dd9-b7d1-656c3665ae53)


Imagen : Señal EEG bitalino al realizar abrir y cerrar de ojos filtrada


En la FFT de la señal filtrada podemos observar que se ha reducido completamente el ruido de 60 hz ya que ya no vemos ese pico prominente


![download (4)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/65af0d53-150c-476e-8fac-ba213ae74342)

Imagen:FFT de la señal filtrada 

Observamos como para este filtro se requirio un orden de 600 , lo cual requiere bastante costo computacional , pero que atenuo correctamente el ruido deseado
### Codigo utilizado para el filtro rechazabanda FIR
```
# Creamos un filtro rechazabanda en 60 Hz
# Definir frecuencias de corte para filtro rechazabanda (RUIDO DE 60 HZ)
wp = 55  / (Fs / 2)
ws = 58  / (Fs / 2)
wc=(wp + ws) / 2
print(wc)
wp1 = 65  / (Fs / 2)
ws1 = 62  / (Fs / 2)
wc1=(wp1 + ws1) / 2

print(wc1)

dw= ws-wp
# Definir el orden del filtro
M =  int(np.floor(8 / dw))
print(M)

stopband_filter= firwin(numtaps=M, cutoff=[58.8/ (Fs / 2),61/ (Fs / 2)],  window='hamming')


wHz, Y = fft_fun(stopband_filter, Fs)

plt.figure(figsize=(8, 6))

plt.plot(wHz, np.abs(Y), "r")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title("Respuesta en frecuencia del filtro")
plt.xlim(0,100)



filtered_signal = lfilter(stopband_filter, 1, eeg)

wHz, filtered_signal_fft = fft_fun(filtered_signal, Fs)

t = np.arange(1, len(filtered_signal)+1)/Fs



plt.figure(figsize=(8, 6))
plt.plot(t, filtered_signal, label="Señal filtrada")
plt.title("Señal EEG filtrada")
plt.xlabel("Tiempo (s)")
plt.ylabel("Amplitud uV")
plt.legend(loc="upper right")
plt.grid(linestyle=":")


#Grafica FFT EEG filtrada
plt.figure(figsize=(8, 6))
plt.plot(wHz, np.abs(filtered_signal_fft), "r")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title("Respuesta en frecuencia señal EEG filtrada")
plt.xlim(-100, 100)
```

El segundo filtro empleado fue el filtro pasabanda , este se utilizó para adquirir las bandas delta, theta, alfa y beta .
Nos basamos en el libro citado en BioSignals Notebook  “Advances in Applied Mathematics and Global Optimization,”  para obtener las frecuencias de corte de las bandas deseadas .

En este libro se determina que  EEG sin procesar generalmente se describe  en términos de bandas de frecuencia: Delta (0,1-3 Hz), Theta (4-8 Hz), Alfa (8-12 Hz), Beta (13-30 Hz) y Gamma (por encima de 30 Hz).

Con estas frecuencias pudimos realizar los 5 filtros pasabandas para extraer las ondas cerebrales de la señal EEG, aqui tambien se empleo ventana blackman debido a su mejor atenuación.



![bandas](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/db42a495-ec08-4e85-82d6-f04898577e83)

Imagen:Ondas cerebrales bandas delta, theta, alfa , beta y gamma a partir de señal EEG
![fft bandas](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/08dbb6b2-f8ff-4dc5-b291-b20b5439df58)


Imagen:FFT Ondas cerebrales bandas delta, theta, alfa , beta  y gamma 

Finalmente podemos observar como las señales han sido filtradas correctamente , se pudo segmentar la señal EEG en sus 5 bandas principales y esto también se puede comprobar en las gráficas de FFT en las cuales vemos como la señal de una banda corresponde a el intervalo de frecuencias dado , ya que podemos observar a las ondas delta de 0.1 a 3 Hz , ondas theta de 4 a 8 hZ , ondas alpha de 8 a 12 hz,las ondas beta de 12 a 30 Hz y las ondas gamma por encima de 30 hz .




### Codigo utilizado para el filtro pasabanda FIR
```
# Definir la longitud de la ventana y la frecuencia de muestreo
M = 1000

# Definir las frecuencias de corte para las bandas de interés
f_delta = (0.5, 4)  # Frecuencia para la banda delta (en Hz)
f_theta = (4, 8)    # Frecuencia para la banda theta (en Hz)
f_alpha = (8, 12)   # Frecuencia para la banda alfa (en Hz)
f_beta = (12, 35)   # Frecuencia para la banda beta (en Hz)



# Crear los filtros para cada banda
f1=0.5/(0.5 * Fs)
f2=4/(0.5 * Fs)
w_delta = firwin(numtaps=M, cutoff=[f1 ,f2], pass_zero=False , window='blackman')
f1=4/(0.5 * Fs)
f2=8/(0.5 * Fs)
w_theta = firwin(numtaps=M, cutoff=[f1 ,f2], pass_zero=False , window='blackman')
f1=8/(0.5 * Fs)
f2=12/(0.5 * Fs)
w_alpha = firwin(numtaps=M, cutoff=[f1 ,f2], pass_zero=False , window='blackman')
f1=12/(0.5 * Fs)
f2=35/(0.5 * Fs)
w_beta = firwin(numtaps=M, cutoff=[f1 ,f2], pass_zero=False , window='blackman')


# Aplicar cada filtro pasabanda a la señal EEG
eeg_delta = lfilter(w_delta, 1, eeg)
eeg_theta = lfilter(w_theta, 1, eeg)
eeg_alpha = lfilter(w_alpha, 1, eeg)
eeg_beta = lfilter(w_beta, 1, eeg)

# Calcular la transformada de Fourier de cada banda
wHz_delta, delta_spectrum = fft_fun(eeg_delta, Fs)
wHz_theta, theta_spectrum = fft_fun(eeg_theta, Fs)
wHz_alpha, alpha_spectrum = fft_fun(eeg_alpha, Fs)
wHz_beta, beta_spectrum = fft_fun(eeg_beta, Fs)


# Plot de cada banda
plt.figure(figsize=(12, 8))

# Delta
plt.subplot(4, 1, 1)
plt.plot(wHz_delta, delta_spectrum, "r")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title("Banda Delta  FFT")
plt.xlim(0, 40)

# Theta
plt.subplot(4, 1, 2)
plt.plot(wHz_theta, theta_spectrum, "g")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title(" Banda Theta FFT")
plt.xlim(0, 40)

# Alpha
plt.subplot(4, 1, 3)
plt.plot(wHz_alpha, alpha_spectrum, "b")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title(" Banda Alpha FFT")
plt.xlim(0, 40)

# Beta
plt.subplot(4, 1, 4)
plt.plot(wHz_beta, beta_spectrum, "m")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title(" Banda Beta FFT")
plt.xlim(0, 40)

```



### Filtrado de ruido del EEG mediante transformada wavelet
Para la supresión de ruido, se utilizó la transformada wavelet con una configuración de 4 niveles y un umbral de 5.6. Dado que la característica principal de la señal de EEG son los picos que aparecen cada 5 segundos, se buscó que la señal filtrada conservara estos picos, que son los más distintivos. Para lograr esto, se revisó la bibliografía sobre la transformada discreta de wavelet como método de filtrado de ruido en EEG. Se encontró que se pueden utilizar de 3 a 5 niveles con "db4", y el umbral se ajusta empíricamente. En función de nuestras necesidades, optamos por la mejor configuración, que consiste en 4 niveles y un umbral de 6.6. Este último valor se determinó empíricamente, y logramos generar una señal con los picos correspondientes al parpadeo cada 5 segundos.[3]

![download](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/5fdae431-b5d8-40f5-9030-22624f19962b)

![download](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/1b9a10ad-2f2d-4cf6-b1a2-4fd40b9824f6)


![download](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/94094678-c3e0-48a8-8216-564b49dc7767)

### Extracción de características de la señal

Media: Se obtiene la media de la señal para poder un nivel general de la actividad cerebral.
Desviación estandar: Se mide la dispersión de la señal para poder conocer la variabilidad de la señal
Amplitud máxima de la señal: Indica la actividad de las neuronas pues a mayor amplitud, se observa mayor sincronización en la actividad cerebral.
Frecuencia dominante: Nos permite conocer qué ondas se presentaron más durante la medición.
Potencia: Nos otorga información de la cantidad total de energía de la señal.
RMS: Nos da la amplitud promedio de la señal lo cual nos indica la fuerza general que tienen las ondas cerebrales.
Obtenemos la magnitud total de la señal ante el estímulo específico del parpadeo.

![caract_eeg](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/0831f9fb-3232-4c1f-bfe7-ccd188300f04)

**Ventanas: Hamming o Blackman:**
Los autores del paper [5] recomiendan utilizar la ventana de Hamming para el filtrado tanto en el dominio del tiempo como en el dominio de la frecuencia. Esto se debe a que la ventana de Hamming es relativamente gradual entre las funciones de disminución ilustradas en la Figura 4, reduciendo los pesos en aproximadamente un 46 % a la mitad desde el centro de la serie de pesos hasta el peso más externo. Reduce, pero no elimina, la ondulación relacionada con el truncamiento y amplía la banda de transición del filtro, haciéndolo menos selectivo en todo el espectro de frecuencias. En comparación con la ventana de Blackman, la ventana de Hamming es menos grave y tiene efectos más moderados.

**Respecto a la potencia:** [6]
La potencia total es la cantidad total de energía contenida en la señal EEG. Además,es la integral de la densidad espectral de potencia (PSD) sobre todo el rango de frecuencias. Una mayor potencia total indica una mayor actividad cerebral global. Puede relacionarse con la intensidad de la actividad cerebral.

En las bandas de frecuencias [6]
Aumento en Delta: Puede indicar una mayor proporción de sueño profundo.
Aumento en Theta: Puede relacionarse con estados de relajación o con procesos de memoria.
Aumento en Alpha: Puede indicar un estado de relajación o atención sostenida.
Aumento en Beta: Puede relacionarse con estados de alerta, procesos cognitivos, o actividad motora.
Aumento en Gamma: Puede asociarse a procesos cognitivos superiores y procesamiento sensorial.


### Archivos 
Por otro lado podemos encontrar los archivos de la informacion de las señales ploteadas 

-[Archivos txt de cada señal elegida](https://github.com/arianacarbajal/ISB_Grupo3/tree/653423cd07d02ac7c8834c24e35e20a8a23843a6/ISB/Laboratorios/6.Dise%C3%B1o%20de%20Filtros/txt)

-[Archivos ipny con código para tipo señal](https://github.com/arianacarbajal/ISB_Grupo3/tree/653423cd07d02ac7c8834c24e35e20a8a23843a6/ISB/Laboratorios/6.Dise%C3%B1o%20de%20Filtros/ipny)


## Bibliografía

‌[1]Why, “Why would one use a Hann or Bartlett window?,” Signal Processing Stack Exchange, Apr. 28, 2017. Available: https://dsp.stackexchange.com/questions/40598/why-would-one-use-a-hann-or-bartlett-window. [Accessed: Oct. 20, 2023]



[2]
“Advances in Applied Mathematics and Global Optimization,” Google Books, 2023. https://books.google.pt/books?id=e-Ex6VHd1UEC&pg=PA111&dq=alpha+8-12+Hz&hl=en&sa=X&ved=0ahUKEwi_1tj098LhAhWy34UKHRMeA2oQ6AEIKDAA#v=onepage&q=alpha%208-12%20Hz&f=false (accessed Nov. 13, 2023).
‌

[3] Mamun, M., Al-Kadi, M., & Marufuzzaman, M. (2013). Effectiveness of Wavelet Denoising on Electroencephalogram Signals. Journal of Applied Research and Technology, 11(1), 156–160. doi:10.1016/s1665-6423(13)71524-4 

[4]“Digital filtering in EEG/ERP analysis: Some technical and empirical comparison”. Research Gate. Accedido el 12 de noviembre de 2023. [En línea]. Disponible: https://www.researchgate.net/publication/225269297_Digital_filtering_in_EEGERP_analysis_Some_technical_and_empirical_comparisons

[5]“Digital filtering in EEG/ERP analysis: Some technical and empirical comparison”. Research Gate. Accedido el 12 de noviembre de 2023. [En línea]. Disponible: https://www.researchgate.net/publication/225269297_Digital_filtering_in_EEGERP_analysis_Some_technical_and_empirical_comparisons

[6]“SISTEMA DE ADQUISICIÓN Y PROCESAMIENTO DE SEÑALES ELECTROENCEFALOGRAMA”. [En línea]. Disponible: https://www.researchgate.net/profile/Ofelia-Valdes-Rodriguez/publication/272941273_SISTEMA_DE_ADQUISICION_Y_PROCESAMIENTO_DE_SENALES_ELECTROENCEFALOGRAFICAS/links/54f342410cf24eb8794c2aa1/SISTEMA-DE-ADQUISICION-Y-PROCESAMIENTO-DE-SENALES-ELECTROENCEFALOGRAFICAS.pdf
