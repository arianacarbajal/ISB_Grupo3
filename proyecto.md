# Development of a Machine Learning Model for Muscle Fatigue Monitoring in the Lateral Vastus Muscle during Static Bicycle Rehabilitation using sEMG: Optimization of Rehabilitation Routines and Prevention of Muscle Injuries



## Tabla de contenido

- [Introducción](#Introducción).
- [Objetivos del proyecto](#Objetivo).
- [Problemática](#Problemática).
- [Estado del arte](#estado).
- [Propuesta de solución](#propuesta).
- [Metodología del proyecto](#Metodología).
- [Integrantes del proyecto](#Integrantes_del_proyecto).
- [Bibliografía](#Bibliografía).

### Introducción


### Objetivos del proyecto
<div class=text-justify>
General: 
 <div class=text-justify>
Desarrollar un sistema de monitorización de fatiga muscular basado en sensores sEMG que optimice la rehabilitación y prevenga lesiones musculares en pacientes que realizan ejercicios en bicicleta estática durante su proceso de recuperación.
  <div class=text-justify>
Específicos:
<div class=text-justify>
Diseñar y construir un sistema de adquisición de señales sEMG que sea capaz de medir la actividad del músculo vasto lateral de forma precisa.
 <div class=text-justify>
Desarrollar un modelo de aprendizaje automático capaz de analizar las señales sEMG recopiladas y detectar patrones asociados a la fatiga muscular en el músculo vasto lateral.
  <div class=text-justify>
Implementar un sistema de alerta temprana que notifique al paciente y al terapeuta cuando se detecten signos de fatiga muscular, con recomendaciones específicas para disminuir la intensidad del ejercicio.
   <div class=text-justify>
### Problemática
El presente proyecto se está centrando en personas físicamente activas, que presentan o pueden presentar lesiones. Revisando la incidencia de lesiones musculares, podemos notar que las extremidades inferiores son las más afectadas, representando el 51.6% de las lesiones[a]. 

![Texto alternativo](Imagen/Imagen1.png)

Estos datos pueden variar un poco dependiendo de la naturaleza de la actividad física que realiza el sujeto, sin embargo, la prevalencia en las extremidades inferiores suele ser mayor, lo cual otorga mayor importancia al monitoreo de esta zona. De estos datos también es importante notar que las lesiones musculares y de tendón representan el 53.8% y que el 65.7% de las lesiones son causadas por sobreuso[a], estadística que se eleva si se evalúa exclusivamente el tiempo de entrenamiento y no de competencia.

Tomando en cuenta la recurrencia de las lesiones musculares por sobre exigencia en las extremidades inferiores, notamos que el monitoreo de la actividad muscular en esta zona es crucial. Lo ideal sería realizar este  monitoreo tanto en personas sanas como en personas realizando rehabilitación física después de una lesión.
En personas sanas, para evitar que se generen las lesiones por fatiga muscular, la cual es un importante factor de riesgo[d], y en personas que se encuentran en un proceso de rehabilitación porque la falta de una terapia de rehabilitación certera puede generar que la zona se sobre exija y agrave la lesión o empeore el pronóstico inicial[g], consecuentemente no se recupere completamente y sea propensa a volver a lesionarse nuevamente, inhabilitando a la persona por un mayor periodo de tiempo[e].
Para ser más precisos, sin un monitoreo de la fatiga, es difícil poder detener los ejercicios oportunamente para establecer periodos de recuperación que nos permitan evitar la acumulación de fatiga, lo cual genera una baja tolerancia a cargas, disminución de rendimiento, aumento de riesgo de lesiones y alteraciones cognitivas[f].

Hemos decidido concentramos específicamente en el ejercicio de bicicleta estática, por dos razones importantes:  
1. Es un ejercicio idóneo para la rehabilitación de lesiones del miembro inferior ya que es posible modificar la altura del asiento y la posición de los pedales para centrarse específicamente en la actividad de los músculos y aliviar los ligamentos[h].
2. Implica la activación de músculos vasto interno, externo, crural y recto anterior femoral que, como vimos, son propensos a las lesiones de sobrecarga específicamente generadas por las grandes cargas que debe soportar el tendón rotuliano y son los de mayor participación en el proceso de pedaleo[b].

### Estado del arte
<div class=text-justify> 
 
En el contexto de este estado del arte, se ha realizado una revisión exhaustiva de investigaciones previas con el propósito de evaluar metodologías y precisiones, así como de analizar los paquetes musculares que han sido objeto de estudio. Los siguientes estudios han sido examinados detenidamente para comprender las técnicas empleadas en la detección de la fatiga muscular, lo que ha sido esencial en la determinación de nuestra estrategia de investigación.
</div>

<div class=text-justify>
 
El paper, titulado "A Muscle Fatigue Classification Model Based on LSTM and Improved Wavelet Packet Threshold," [A1] se enfocó en proponer un nuevo método para la clasificación automática de la fatiga muscular basado en la electromiografía de superficie (sEMG). Durante este proceso, se analizaron los músculos vasto recto femoral (RF), vasto lateral (VL), vasto medial (VM) y gastrocnemio (GA) de la pierna izquierda en 20 participantes durante una prueba incremental en un ergómetro de ciclo. La metodología incluyó el uso de la transformada wavelet packet y la aplicación de un algoritmo de eliminación de ruido mediante umbral de paquete wavelet mejorado para el análisis de señales sEMG. Se extrajeron características tanto en el dominio del tiempo como en el de la frecuencia de las señales sEMG. Además, se propuso un modelo de reconocimiento de fatiga muscular basado en la red LSTM, que fue entrenado para clasificar la fatiga muscular utilizando estas características. Los resultados revelaron que el algoritmo de umbral de paquete wavelet mejorado superó a otros métodos de umbral, y que el modelo LSTM demostró un mejor rendimiento en la clasificación de la fatiga muscular en comparación con modelos como CNN, SVM y BFA-GSVCM.
</div>

<div class=text-justify>
 
El objetivo del paper, titulado "Strategies to Identify Changes in SEMG Due to Muscle Fatigue During Cycling," [A2]es presentar una técnica no invasiva para medir la fatiga muscular durante actividades cíclicas utilizando análisis espectral de ventanas estrechas de electromiografía de superficie (SEMG). El paquete muscular analizado son los músculos cuádriceps durante el ciclismo. La metodología utilizada consiste en establecer una referencia en cada ciclo para determinar los cambios en la señal SEMG, utilizando una ventana de 100 ms en el pico de la actividad muscular. Además, se considera la relación entre la frecuencia mediana y la raíz cuadrada media para identificar el cambio en la fatiga muscular. El estudio se realizó con 11 voluntarios masculinos moderadamente activos, y se utilizó un ergómetro Lode para realizar una prueba de fatiga de 30 segundos. Los resultados muestran una relación altamente significativa entre la reducción de la frecuencia mediana y el inicio de la fatiga muscular.
</div>

<div class=text-justify>

El objetivo del estudio "Evaluation of the Electromyography Test for the Analysis of the Aerobic-Anaerobic Transition in Elite Cyclists during Incremental Exercise" [A3] fue investigar la validez y fiabilidad de la electromiografía de superficie (EMG) para la detección automática de los umbrales aeróbico y anaeróbico durante una prueba de ejercicio continuo incremental utilizando períodos de ejercicio de 1 minuto en ciclistas de élite. Se analizaron los paquetes musculares vasto lateral, vasto medial, bíceps femoral y glúteo máximo. Dieciséis ciclistas bien entrenados completaron una prueba de ejercicio incremental (25 W/1 min) hasta el agotamiento. Se midieron las siguientes variables para evaluar la fatiga: la potencia máxima alcanzada, la frecuencia cardíaca, la concentración de lactato en sangre y la raíz cuadrada media (RMS) de las señales EMG. Los resultados mostraron que la EMG de superficie es una herramienta válida y fiable para la detección automática de los umbrales aeróbico y anaeróbico en ciclistas de élite durante una prueba de ejercicio continuo incremental.

</div>

<div class=text-justify>
 
El artículo, titulado “Assessment of Muscles Fatigue Based on Surface EMG Signals Using Machine Learning and Statistical Approaches: A Review”[A4],  revisa los métodos para detectar la fatiga muscular a través de señales de EMG de superficie utilizando enfoques estadísticos y de aprendizaje automático. Los autores analizaron 15 estudios que investigan la fatiga muscular en diferentes músculos de la pierna, incluyendo el vasto lateral, gastrocnemio y tibial anterior. Los resultados muestran que los enfoques de aprendizaje automático y estadísticos son efectivos para detectar la fatiga muscular en los músculos de la pierna, con una precisión promedio del 90%. Los métodos que dieron mejores resultados fueron el análisis de componentes principales (PCA) y el análisis de discriminante lineal (LDA). Las variables utilizadas en estos enfoques incluyen la amplitud de la señal EMG, la frecuencia y la duración de la contracción muscular. Estos enfoques permiten una detección temprana de la fatiga muscular, lo que puede ser útil para prevenir lesiones en atletas y mejorar la rehabilitación en pacientes con enfermedades neuromusculares.

</div>

<div class=text-justify>
 
‌El objetivo del estudio "Un estudio comparativo de índices EMG en la evaluación de la fatiga muscular durante el ejercicio de ciclismo al máximo esfuerzo" [A5] fue evaluar la utilidad de diferentes índices EMG en la evaluación de la fatiga muscular inducida por el ejercicio de ciclismo al máximo esfuerzo. Los músculos analizados fueron el vasto lateral (VL), el bíceps femoral (BF) y el gastrocnemio medial (GM). Se reclutaron 12 ciclistas altamente entrenados para realizar un ejercicio de ciclismo al máximo esfuerzo y se midieron los índices EMG de los músculos VL, BF y GM durante el ejercicio. Se utilizó el análisis de correlación gris para evaluar la relación entre los diferentes índices EMG y la fatiga muscular. Las variables utilizadas para medir la fatiga muscular fueron la frecuencia mediana (MF), la frecuencia media (MNF), la potencia media de la frecuencia (MPF) y la relación de potencia mediana (MMP).Además, se encontró que la frecuencia mediana (MF) y la frecuencia media (MNF) fueron los índices EMG más sensibles para detectar la fatiga muscular en los tres músculos analizados.

</div>

### Propuesta de solución
<div class=text-justify>
 
Se seleccionó el músculo vasto lateral de la pierna (VL) como el foco central de este estudio debido a su destacado papel como generador principal de potencia durante la práctica del ciclismo [A6]. Por consiguiente, proponemos el  desarrollo de un Modelo de Aprendizaje Automático para la Monitorización de la Fatiga Muscular en el Músculo Vasto Lateral durante la Rehabilitación con Bicicleta Estática mediante señales de electromiografía de superficie (sEMG). Esta elección se respalda en la capacidad inherente del aprendizaje automático para analizar de forma precisa y eficiente las complejas señales de sEMG, identificar patrones de fatiga muscular y proporcionar retroalimentación en tiempo real. Nuestra propuesta tiene como objetivo optimizar los protocolos de rehabilitación y prevenir lesiones musculares en el contexto de pacientes que utilizan la bicicleta estática como parte de su proceso de recuperación, lo que, indudablemente, contribuirá al bienestar y al rendimiento de este grupo.
 
</div>




### Metodología del proyecto
1. Adquisición de la señal electromiográfica del antebrazo
2. Procesamiento de señal en Phyton
3. Aplicación de filtros digitales a la señal
4. Análisis de la señal para simular movimientos en la prótesis. 
5.  Obtención de resultados preliminares.
6.  Documentación de la investigación.


### Integrantes del proyecto

- Ariana Carbajal (colaborador) - ariana.carbajal@upch.pe 
- Natalia Galindo Concha (colaborador) - natalia.galindo@upch.pe 
- Gianfranco Fabian Feria Maquera (colaborador) - gianfranco.feria@upch.pe 
- Eduardo André Cuti Riveros (colaborador) -  eduardo.cuti@upch.pe 



### Bibliografía

[1] 

[A1]J. Wang, S. Sun, and Y. Sun, “A Muscle Fatigue Classification Model Based on LSTM and Improved Wavelet Packet Threshold,” Sensors, vol. 21, no. 19, pp. 6369–6369, Sep. 2021, doi: https://doi.org/10.3390/s21196369.

[A2] V. P. Singh, D. Kumar, B. Polus, and S. F. Fraser, “Strategies to identify changes in SEMG due to muscle fatigue during cycling,” Journal of Medical Engineering & Technology, vol. 31, no. 2, pp. 144–151, Jan. 2007, doi: https://doi.org/10.1080/03091900500444281.

[A3] Ibán Latasa, A. Córdova, G. Quintana-Ortí, A. Lavilla-Oiz, J. Navallas, and J. Rodríguez-Falces, “Evaluation of the Electromyography Test for the Analysis of the Aerobic-Anaerobic Transition in Elite Cyclists during Incremental Exercise,” Applied sciences, vol. 9, no. 3, pp. 589–589, Feb. 2019, doi: https://doi.org/10.3390/app9030589.

[A4] H. A. Yousif et al., “Assessment of Muscles Fatigue Based on Surface EMG Signals Using Machine Learning and Statistical Approaches: A Review,” IOP conference series, vol. 705, no. 1, pp. 012010–012010, Nov. 2019, doi: https://doi.org/10.1088/1757-899x/705/1/012010.

‌[A5] L. Wang et al., “A Comparative Study of EMG Indices in Muscle Fatigue Evaluation Based on Grey Relational Analysis during All-Out Cycling Exercise,” BioMed Research International, vol. 2018, pp. 1–8, Jan. 2018, doi: https://doi.org/10.1155/2018/9341215. 

[A6] S. Bercier et al., “The vastus lateralis neuromuscular activity during all-out cycling exercise,” Journal of Electromyography and Kinesiology, vol. 19, no. 5, pp. 922–930, Oct. 2009, doi: https://doi.org/10.1016/j.jelekin.2008.03.012.
‌


[2] Resolución directoral, 132-2021-SA-DG-INR, Ministerio de Salud - Instituto Nacional de Rehabilitación, Lima, 2021. Accedido el 18 de agosto de 2023. [En línea]. Disponible: https://www.inr.gob.pe/transparencia/transparencia%20inr/resoluciones/2021/RD%20132-2021-SA-DG-INR.pdf
 
[3] Unanyan, N. N., & Belov, A. A. (2021). “Design of upper limb prosthesis using real-time motion detection method based on EMG signal processing”. Biomedical Signal Processing and Control, 70, 103062. doi:10.1016/j.bspc.2021.103062 

[4] Bi, L., Feleke, A. >Genetu, & Guan, C. (2019). A review on EMG-based motor intention prediction of continuous human upper limb motion for human-robot collaboration. Biomedical Signal Processing and Control, 51, 113–127. doi:10.1016/j.bspc.2019.02.011 
