Estadistica de amputaciones transradiales:

 A su vez, en [7] se menciona que, según estadísticas dadas por el Instituto Nacional de Rehabilitación “Dra. Adriana Rebaza Flores”, ubicado en Perú, el 21.9 % de los pacientes amputados atendidos presentan amputación del miembro superior. 

En el Perú, más de 12 mil personas han perdido parte de su miembro superior, ya sea el brazo completo, el antebrazo o la mano.


![](https://github.com/arianacarbajal/ISB_Grupo3/blob/main/Imagen/tabla%201.png)




Causas de amputaciones transradiales :
Entre las causas que representan el problema, el año 2017, según datos estadísticos que registra la aseguradora con representatividad de 30.8% de las 10 principales aseguradoras en el Perú, en el programa de Seguro Complementario de Trabajo de Riesgo (SCTR), ocurren 48 accidentes de trabajo 19 por día. 

De un total aproximado de 17000 accidentes registrados, 297 fueron amputaciones traumáticas, de estos casos presentados, 244 casos (82.15%) son en extremidad superior. Del grupo de casos con amputación de extremidad superior, el 2.46% ocurrió por encima de la muñeca y el 97.54% de los restantes comprometieron manos o dedos (6).

Según el Boletín Informativo de Accidentes de Trabajo, enero 2020, del Ministerio del Trabajo, se reportaron, s, de un total de 2827 casos, el 23.16% fueron lesiones en el miembro superior, que involucra los dedos de la mano, muñeca y brazo.

 Según las consecuencias del accidente, el 59.39% son accidentes de tipo incapacitante (7). Por ende, se considera que los accidentes industriales generan un elevado índice de amputación traumática en extremidades superiores (73% a 81%) y, los accidentes de tránsito, un porcentaje mayor en extremidades inferiores (63%) (1)

Contexto EMG

La electromiografía (EMG) se basa en la adquisición, registro y análisis de la actividad eléctrica generada en nervios y músculos a través de la utilización de electrodos .Las mediciones extraídas de EMG proporcionan una información valiosa acerca de la fisiología y los patrones de activación muscular.  Dicha información refleja las fuerzas que son generadas por los músculos y la temporización de los comandos motores.

 Además, puede usarse en el diagnóstico de patologías que afectan al Sistema Nervioso Periférico, las alteraciones funcionales de las raíces nerviosas,así como de patologías del músculo y de la unión neuromuscular. 

Las aplicaciones de la electromiografía han evolucionado de modo que ha permitido disponer de sistemas controlados por microprocesadores para captar, almacenar, analizar y clasificar señales  mioeléctricas  que permitan ser utilizadas para suplir pérdidas de algún miembro, principalmente brazos mediante prótesis mioeléctricas. 

Las prótesis mioeléctricas son especialmente útiles para los casos como amputación transradial que se han mencionado ya que puede devolverle a las personas discapacitadas la movilidad del miembro superior mejorando su calidad de vida.

Además debido a que las señales EMG superficiales (EMGS), son esencialmente un patrón unidimensional, se pueden utilizar técnicas de procesamiento de señales para extracción de características y reconocimiento de patrones que permitan el control de dispositivos como prótesis transradial.



Problemática:

Una prótesis mioeléctrica es un sistema accionado por servomotores que se gobierna a partir de señales EMG, bien sean intramusculares, capturadas mediante agujas o superficiales, recogidas en el muñón del paciente mediante electrodos.
El éxito de una prótesis mioeléctrica será medido por su desempeño en la ejecución de movimientos prácticos,se ha experimentado un retraso en la respuesta de la prótesis a las señales EMG, lo que puede afectar la naturalidad y la fluidez de los movimientos controlados. La optimización de la usabilidad y la funcionalidad, el aseguramiento de una alta fiabilidad de la señal. La menor complejidad de operación como sistema y con el menor esfuerzo físico mental por parte del paciente. Para esto, es esencial un adecuado proceso de análisis de las señales motoras EMGS. [][][]

La información extraída de las señales EMGS, es seleccionada de tal manera que se minimice el error en el control de los sistemas de prótesis mioeléctricas. La necesidad de una rápida respuesta de la prótesis limita la longitud de las muestras de la señal sobre las cuales se extraen las características. La tendencia en el control de prótesis a partir de señales EMGS obedece a que se constituye en la técnica más sencilla de implementar por su facilidad en la recolección sin intromisión directa sobre el organismo del usuario, remoción de electrodos y equipo para efectos de mantenimiento y/o calibración y su reutilización de una persona a otra.


Propuesta de solución:
Al tratarse de personas jóvenes y económicamente activas, la reinserción al ambiente laboral es complicada si la persona no logra una recuperación adecuada de sus habilidades motrices, por lo que es recomendable el uso de una prótesis mioeléctrica para tener un control natural y buena funcionalidad, pero estas pueden tener problemas de respuesta rápida o fiabilidad provenientes de una obtención o filtración no adecuadas de las señales EMG. 
Como se vio antes, nos estamos centrando en pérdidas traumáticas de la extremidad, por lo que si bien los músculos aledaños al muñón son recomendables para obtener mejores señales, estos músculos pueden estar atrofiados, emitiendo señales de menor amplitud y calidad, y para estos casos, se recomienda aplicar terapias de rehabilitación.[1]
Es por esto que queremos enfocar nuestro proyecto en la Adquisición, procesamiento  y evaluación de señal EMG para analizar el estado de daño del musculo y verificar si la señal es apta para control de una prótesis mioeléctrica.

Por lo que se concluyó la siguiente propuesta de solución:
 
“Adquisición, procesamiento, filtrado  y evaluación de señal EMG para analizar la gravedad de la atrofia muscular y verificar si la señal es apta para control de una prótesis mioeléctrica transradial”.

Metodología del proyecto
1.Elección del sensor : 
Se utilizará el sensor  muscular MyoWare . El sensor amplifica y procesa la compleja actividad eléctrica de un músculo y la convierte en una señal analógica simple que puede ser leída fácilmente por cualquier microcontrolador con un convertidor de analógico a digital (ADC).
La señal registrada  puede ser utilizada para controlar diversos dispositivos como prótesis, sillas de ruedas, automatismos, etc. 
2. Adquisición de la señal electromiográfica :
 Se realizará mediante la colocación de electrodos superficiales .Luego de la obtención se realizará el filtrado , amplificado y  rectificación  de onda completa.Se utilizará el lenguaje de programación Python.
4.Procesamiento de la señal EMG: 
Una vez, obtenidas las señales EMG de un músculo en específico,  movimientos característicos se procederá a  extraer sus características para su posterior clasificación. Se evaluará la amplitud y la claridad de los picos obtenidos para determinar si el sensor está posicionado en una zona  del músculo que no presenta daños significativos como para alterar la lectura del patrón de movimiento que se quiso realizar. Para ello se utilizarán diferentes técnicas de procesamiento a fin de extraer los patrones de movimientos entre ellos se podria utilizar la Transformada de Fourier y la Transformada de Wavelet.  



Documentación de la investigación:
[1] Unanyan, N. N., & Belov, A. A. (2021). “Design of upper limb prosthesis using real-time motion detection method based on EMG signal processing”. Biomedical Signal Processing and Control, 70, 103062. doi:10.1016/j.bspc.2021.103062 
[2] Bi, L., Feleke, A. >Genetu, & Guan, C. (2019). A review on EMG-based motor intention prediction of continuous human upper limb motion for human-robot collaboration. Biomedical Signal Processing and Control, 51, 113–127. doi:10.1016/j.bspc.2019.02.011 
[3] Bi, L., Feleke, A. >Genetu, & Guan, C. (2019). A review on EMG-based motor intention prediction of continuous human upper limb motion for human-robot collaboration. Biomedical Signal Processing and Control, 51, 113–127. doi:10.1016/j.bspc.2019.02.011
[4] Raurale, S.A. and Chatur, P.N. (2014) ‘Identification of real-time active hand movements EMG signals for control of prosthesis robotic hand’, 2014 International Conference on Computation of Power, Energy, Information and Communication (ICCPEIC) [Preprint]. doi:10.1109/iccpeic.2014.6915412. 
[5] E. Vásquez, Los amputados y su rehabilitación - academia nacional de medicina de México, https://www.anmm.org.mx/publicaciones/ultimas_publicaciones/Rehabilitacion.pdf (accessed Aug. 31, 2023). 
