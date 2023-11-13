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
Se diseñaron dos tipos de filtros , como principal , se empleó un filtro pasabajo con una frecuencia de paso de 30 Hz , una frecuencia de stop de 40 Hz y un orden de 600. Se empleó la ventana blackman debido a su mejor atenuación en comparación a las otras ventanas hamming , hanning , barlett y triangular.La ventana blackman ofrece Blackman superior supresión de lóbulos laterales (amplitud máxima de -57 dB)y  capacidades efectivas de reducción de ruido  (error de aproximación de pico bajo de -74 dB).

![RTGyj](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/0a07969a-979f-4403-abbb-eea1c17d387b)

Imagen: Características de ventanas[1]


‌
Se situo a la frecuencia de corte en 0.07 aprox de frecuencia normalizada rad /pi  o 35 Hz ya que las señales EEG tienen frecuencias en este rango de 0 a 35 Hz son las frecuencias de interés referidas a las ondas beta, alpha , delta y theta. y filtrarlo a esa frecuencia también nos eliminaria el ruido en 60 Hz proveniente de la alimentación electrica que se muy pronunciado al calcular la FFT inicial.


![descarga (1)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/2f7ba046-0376-4c73-96c1-0c526e0e4ee2)

Imagen : Señal EEG bitalino al realizar abrir y cerrar de ojos

![descarga (2)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/b19a9dab-2e0e-4b97-ba5c-bae3acfb3264)

Imagen:FFT de la señal inicial

En la respuesta en frecuencia del filtro pasabajo podemos ver su comportamiento y como va a filtrar adecuadamente el ruido de 60 hz, y vemos como tiene una correcta atenuación para las frecuencias de paso y corte que hemos indicado . 
![descarga (3)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/09c15a75-b7ad-404e-bab0-253d40ced044)

Imagen: Respuesta en frecuencia del filtro en Hz

![descarga (4)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/0885e2c2-5462-4f49-a77a-b9ea4197d597)

Imagen : Señal EEG bitalino al realizar abrir y cerrar de ojos filtrada


En la FFT de la señal filtrada podemos observar que se ha reducido completamente el ruido de 60 hz ya que ya no vemos ese pico prominente

![descarga (5)](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/93ed75ae-8f3a-43f4-a11a-f516ead5fbe2)

Imagen:FFT de la señal filtrada 

Observamos como para este filtro se requirio un orden de 600 , lo cual requiere bastante costo computacional , pero que atenuo correctamente el ruido deseado
### Codigo utilizado para el filtro pasabajo FIR
```

# Definir frecuencia de corte del filtro pasabajo
wp = 30  / (Fs / 2) # frecuencia de paso
ws = 40  / (Fs / 2) # frecuencia de stop
wc=(wp + ws) / 2 #frecuencia de corte

dw= ws-wp

lowpass_filter= firwin(numtaps=M, cutoff=wc,  window='hamming')

# Definir el orden del filtro
M =  int(np.floor(12 / dw))
print(M)


wHz, Y = fft_fun(lowpass_filter, Fs)

plt.figure(figsize=(8, 6))

plt.plot(wHz, np.abs(Y), "r")
plt.xlabel("Frequencia (Hz)")
plt.ylabel("Amplitud")
plt.title("Respuesta en frecuencia del filtro")
plt.xlim(0, 60)



filtered_signal = lfilter(lowpass_filter, 1, eeg)

wHz, filtered_signal_fft = fft_fun(filtered_signal, Fs)

t = np.arange(1, len(filtered_signal)+1)/Fs

```

El segundo filtro empleado fue el filtro pasabanda , este se utilizó para adquirir las bandas delta, theta, alfa y beta .
Nos basamos en el árticulo "Technological Basics of EEG Recording and Operation of Apparatus" para obtener las frecuencias de corte de las bandas deseadas .

![image](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/38eec8de-3c0f-4a98-9d35-7e1da98945e9)

Imagen: Frecuencias de bandas delta, theta, alfa y beta [2]

Con estas frecuencias pudimos realizar los 4 filtros pasabandas para extraer las ondas cerebrales de la señal EEG, aqui tambien se empleo ventana blackman debido a su mejor atenuación.


![señalesfiltr](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/62648f36-1738-4270-8497-0c7ba7f16b30)

Imagen:Ondas cerebrales bandas delta, theta, alfa y beta a partir de señal EEG

![fftband](https://github.com/arianacarbajal/ISB_Grupo3/assets/56159840/3e97a461-0abc-430d-a4ef-12a9904c0b38)

Imagen:FFT Ondas cerebrales bandas delta, theta, alfa y beta 

Finalmente podemos observar como las señales han sido filtradas correctamente , se pudo segmentar la señal EEG en sus 4 bandas principales y esto también se puede comprobar en las gráficas de FFT en las cuales vemos como la señal de una banda corresponde a el intervalo de frecuencias dado , ya que podemos observar a las ondas delta de 0.5 a 4 Hz , ondas theta de 4 a 8 hZ , ondas alpha de 8 a 12 hz y por último las ondas beta de 12 a 35 Hz.




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

![caract_eeg](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/0831f9fb-3232-4c1f-bfe7-ccd188300f04)


### Archivos 
Por otro lado podemos encontrar los archivos de la informacion de las señales ploteadas 

-[Archivos txt de cada señal elegida](https://github.com/arianacarbajal/ISB_Grupo3/tree/653423cd07d02ac7c8834c24e35e20a8a23843a6/ISB/Laboratorios/6.Dise%C3%B1o%20de%20Filtros/txt)

-[Archivos ipny con código para tipo señal](https://github.com/arianacarbajal/ISB_Grupo3/tree/653423cd07d02ac7c8834c24e35e20a8a23843a6/ISB/Laboratorios/6.Dise%C3%B1o%20de%20Filtros/ipny)


## Bibliografía

‌[1]Why, “Why would one use a Hann or Bartlett window?,” Signal Processing Stack Exchange, Apr. 28, 2017. Available: https://dsp.stackexchange.com/questions/40598/why-would-one-use-a-hann-or-bartlett-window. [Accessed: Oct. 20, 2023]

[2] P. A. Abhang, B. W. Gawali, and S. C. Mehrotra, “Technological Basics of EEG Recording and Operation of Apparatus,” Elsevier eBooks, pp. 19–50, Jan. 2016, doi: https://doi.org/10.1016/b978-0-12-804490-2.00002-6. Available: https://www.sciencedirect.com/topics/agricultural-and-biological-sciences/brain-waves. [Accessed: Oct. 20, 2023]

[3] Mamun, M., Al-Kadi, M., & Marufuzzaman, M. (2013). Effectiveness of Wavelet Denoising on Electroencephalogram Signals. Journal of Applied Research and Technology, 11(1), 156–160. doi:10.1016/s1665-6423(13)71524-4 

