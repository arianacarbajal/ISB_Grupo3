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

La fatiga muscular es una disminución de la fuerza máxima y una respuesta muscular más lenta.  La fatiga puede tener un origen central, al reducir el rendimiento cognitivo o disminuir la excitación de las motoneuronas.Las fatigas en las  contracciones musculares van acompañadas de descargas reducidas de las motoneuronas.


La fatiga periférica, es donde la disminución de la fuerza ocurre a nivel de las fibras musculares principalmente o el medio en el cual se encuentran . Puede interferir con el acople excitación contracción, la disponibilidad de sustratos metabólicos, el medio intracelular, el flujo sanguíneo muscular y las propiedades intrínsecas del aparato contráctil [1]

Mecanismos fisiológicos que ocasionan la fatiga muscular son los siguientes: [1]


1)Alteraciones que ocurren durante la propagación del potencial de acción a lo largo del sarcolema con disminución en la sensibilidad de receptores post sinápticos a la acetilcolina, y al calcio en sarcolema y RS3 .Esto ocasiona una  disminución de la velocidad de conducción de los potenciales de acción a lo largo del sarcolema, así como en malfuncionamiento de la capacidad contráctil propia de la fibra muscular.

2)La acumulación de lactato e hidrogeniones (H+), lo que genera una variación en el cociente respiratorio


3)Modificaciones a nivel de la fibra muscular propiamente, la más importante,es el aumento del fosfato inorgánico (Pi) en el sarcoplasma proveniente de: la hidrólisis de la fosfocreatina en creatina y Pi durante el ejercicio y de la hidrolisis de ATP

4)La acumulación de iones de magnesio que limitan la liberación de Ca2+ desde el RS y la depleción de las reservas de glucógeno en la fibra muscular.



**¿Qué es la bicicleta estática?**

Es un nuevo tipo de bicicleta menos convencional(comparado a la bicicleta que todos conocemos ), apodado ‘estática’ pues simula la acción de una bicicleta convencional, pero sin producirse el desplazamiento. 
Esto es debido a que lo que se busca es el desgaste energético, no el movimiento; es decir realizar el esfuerzo provocado por el pedaleo de una bici con fines deportivos. Sin embargo, dentro de esta subclase aparecen nuevas ramificaciones [2]: 

-Convencionales: Las de uso doméstico aunque también se pueden encontrar en instalaciones deportivas. Siguen una estructura básica pero tienen gran variedad de funcionalidades. 

-Spinning: Esta bicicleta aunque posee ruedas no se produce el desplazamiento, destaca por su uso diverso y por la gran variedad de resistencias al pedaleo.Lo utilizan deportistas de alto rendimiento.

-Elípticas: El ejercicio se realiza de pie gracias a esta ya que posee dos pedales sobre los que se marchan y dos barras verticales que ayudan a la realización el ejercicio.

 -De alta resistencia o crossfit: Estas destacan por sus materiales de elaboración pues son resistentes a la oxidación y el desgaste mecánico pues están pensadas para ejercicio de alta intensidad.




El uso de bicicleta estática (ergómetro de ciclo) se utiliza en rehabilitación de deportistas  tanto en lesiones que perjudiquen el análisis de fatiga muscular (como amputaciones, lesiones musculo-tendinosas) o en lesiones que no afecten esta medición como esguinces, contusiones o traumatismos  en la rodilla (**generalmente en jugadores de fútbol**). [3]



**¿Cómo podríamos unir el análisis por sEMG  de fatiga muscular con la rehabilitación con bicicleta estática en deportistas?** [4]

En este artículo, determinamos como el cicloergómetro(bicicleta estática ) en ciclos de ejercicios  nos permite  hallar  un parámetro llamado PWCFT,  que permite clasificar si  el músculo/s  analizados (p.j vasto medial) presenta fatiga.

 En el artículo, propusieron un umbral de fatiga neuromuscular basado en la actividad EMG, definido como la “Capacidad Física de Trabajo en el Umbral de Fatiga” (PWCFT), a través de un test especifico en cicloergómetro.

 En su versión original, la determinación del umbral PWCFT se hacía examinando las curvas EMG-tiempo obtenidas de 4 series de trabajo realizadas en 4 niveles de potencia distintos. Los autores de este método identificaban el umbral PWCFT determinando el mayor nivel potencia (carga) que el ciclista podía mantener en un periodo de 2 minutos sin que la señal EMG se incrementara drásticamente . En su versión original, el método de deVries adolecía de una gran desventaja al tratarse de un test discontinuo que exige al ciclista varias visitas al laboratorio para realizar los análisis . Luego, , este grupo  realizaron un refinamiento de su método que le permitió extraer el umbral PWC mediante la realización de un solo test incremental.




Las señales de EMG se obtienen mediante electrodos colocados en la pierna dominante sobre el músculo VL(vasto lateral ) a un 1/3 de la distancia entre el extremo lateral de la rótula y la proyección del hueso ilíaco. . Durante cada etapa (25w/min) de la prueba incremental, se registran varios segmentos consecutivos de EMG (cada segmento coincidiendo con el intervalo en el que el músculo está activo en una pedalada). Normalmente, los primeros 10-15 segundos de cada etapa de 1 minuto se descartan para el análisis, ya que durante este periodo inicial el ciclista realiza ajustes posturales para adaptarse a la nueva potencia. Para cada nivel de potencia del test, la amplitud sEMG de cada uno de los segmentos se calcula y representada en función del tiempo. Así mismo, se identifica la carga de trabajo (potencia) más baja que genera una pendiente significativa positiva en la relación amplitud sEMG/tiempo y también la carga de trabajo (potencia) más alta que genera una pendiente positiva no significativa en la relación amplitud sEMG/tiempo. El PWCFT se determina haciendo el promedio de las dos potencias arriba mencionadas




### Objetivos del proyecto
<div class=text-justify>
General: 
 <div class=text-justify>
Desarrollar un sistema de monitorización de fatiga muscular basado en sensores sEMG que optimice la rehabilitación y prevenga lesiones de sobre exigencia muscular en pacientes que realizan ejercicios en bicicleta estática.
  <div class=text-justify>
Específicos:
<div class=text-justify>
- Diseñar y construir un sistema de adquisición de señales sEMG para obtener nuestras señales de interés.
 <div class=text-justify>
- Lograr un correcto filtrado y procesamiento de la señal para poder obtener la medición de la actividad del músculo vasto lateral de forma precisa.
   <div class=text-justify>
- Desarrollar un modelo de aprendizaje automático capaz de analizar las señales sEMG recopiladas y detectar patrones asociados a la fatiga muscular en el músculo vasto lateral.
  <div class=text-justify>
- Implementar un sistema de alerta temprana que notifique al paciente y al terapeuta cuando se detecten signos de fatiga muscular, con recomendaciones específicas para disminuir la intensidad del ejercicio.

### Problemática
El presente proyecto se está centrando en personas físicamente activas, que presentan o pueden presentar lesiones. Revisando la incidencia de lesiones musculares, podemos notar que las extremidades inferiores son las más afectadas, representando el 51.6% de las lesiones[5]. 

   ![Texto alternativo](Imagen/Imagen1.png)

   Imagen : Diagrama de incidencia de lesiones musculares dependiendo de la zona.
   


<div class=text-justify>
    
Estos datos pueden variar un poco dependiendo de la naturaleza de la actividad física que realiza el sujeto, sin embargo, la prevalencia en las extremidades inferiores suele ser mayor, lo cual otorga mayor importancia al monitoreo de esta zona. De estos datos también es importante notar que las lesiones musculares y de tendón representan el 53.8% y que el 65.7% de las lesiones son causadas por sobreuso[5], estadística que se eleva si se evalúa exclusivamente el tiempo de entrenamiento y no de competencia.
<div class=text-justify>
Tomando en cuenta la recurrencia de las lesiones musculares por sobre exigencia en las extremidades inferiores, notamos que el monitoreo de la actividad muscular en esta zona es crucial. Lo ideal sería realizar este  monitoreo tanto en personas sanas como en personas realizando rehabilitación física después de una lesión.
<div class=text-justify>
En personas sanas la fatiga muscular, es un importante factor de riesgo para sufrir lesiones futuras[6] y en personas que se encuentran en proceso de rehabilitacion, la falta de una terepia de rehabilitacion certera puede generar que la zona se sobreexija y agrave la lesion o empeore el pronostico inicial[7], consecuentemente no se recupere completamente y sea propensa a volver a lesionarse nuevamente, inhabilitando a la persona por un mayor periodo de tiempo[8].
<div class=text-justify>
Para ser más precisos, sin un monitoreo de la fatiga, es difícil poder detener los ejercicios oportunamente para establecer periodos de recuperación que nos permitan evitar la acumulación de fatiga, lo cual genera en el paciente una baja tolerancia a cargas, disminución de rendimiento, aumento de riesgo de lesiones y alteraciones cognitivas[9].
<div class=text-justify>
Dicho esto, hemos decidido concentramos específicamente en el ejercicio de bicicleta estática, por dos razones importantes:  
 <div class=text-justify>
1. Es un ejercicio idóneo para la rehabilitación de lesiones del miembro inferior ya que es posible modificar la altura del asiento y la posición de los pedales para centrarse específicamente en la actividad de los músculos y aliviar los ligamentos.
  <div class=text-justify>
2. Implica la activación de músculos vasto interno, externo, crural y recto anterior femoral que, como vimos, son propensos a las lesiones de sobrecarga específicamente generadas por las grandes cargas que debe soportar el tendón rotuliano y son los de mayor participación en el proceso de pedaleo[10].
<div class=text-justify>
“falta de monitoreo de fatiga muscular en el músculo vasto lateral durante el ejercicio en bicicleta estatica, en individuos sanos de manera preventiva o que estén en procesos de rehabilitación, para prevenir complicaciones y optimizar el proceso de rehabilitación”

### Estado del arte
<div class=text-justify> 
 
En el contexto de este estado del arte, se ha realizado una revisión exhaustiva de investigaciones previas con el propósito de evaluar metodologías y precisiones, así como de analizar los paquetes musculares que han sido objeto de estudio. Los siguientes estudios han sido examinados detenidamente para comprender las técnicas empleadas en la detección de la fatiga muscular, lo que ha sido esencial en la determinación de nuestra estrategia de investigación.
</div>

<div class=text-justify>
 
El paper, titulado "A Muscle Fatigue Classification Model Based on LSTM and Improved Wavelet Packet Threshold," [11] se enfocó en proponer un nuevo método para la clasificación automática de la fatiga muscular basado en la electromiografía de superficie (sEMG). Durante este proceso, se analizaron los músculos vasto recto femoral (RF), vasto lateral (VL), vasto medial (VM) y gastrocnemio (GA) de la pierna izquierda en 20 participantes durante una prueba incremental en un ergómetro de ciclo. La metodología incluyó el uso de la transformada wavelet packet y la aplicación de un algoritmo de eliminación de ruido mediante umbral de paquete wavelet mejorado para el análisis de señales sEMG. Se extrajeron características tanto en el dominio del tiempo como en el de la frecuencia de las señales sEMG. Además, se propuso un modelo de reconocimiento de fatiga muscular basado en la red LSTM, que fue entrenado para clasificar la fatiga muscular utilizando estas características. Los resultados revelaron que el algoritmo de umbral de paquete wavelet mejorado superó a otros métodos de umbral, y que el modelo LSTM demostró un mejor rendimiento en la clasificación de la fatiga muscular en comparación con modelos como CNN, SVM y BFA-GSVCM.
</div>

<div class=text-justify>
 
El objetivo del paper, titulado "Strategies to Identify Changes in SEMG Due to Muscle Fatigue During Cycling," [12]es presentar una técnica no invasiva para medir la fatiga muscular durante actividades cíclicas utilizando análisis espectral de ventanas estrechas de electromiografía de superficie (SEMG). El paquete muscular analizado son los músculos cuádriceps durante el ciclismo. La metodología utilizada consiste en establecer una referencia en cada ciclo para determinar los cambios en la señal SEMG, utilizando una ventana de 100 ms en el pico de la actividad muscular. Además, se considera la relación entre la frecuencia mediana y la raíz cuadrada media para identificar el cambio en la fatiga muscular. El estudio se realizó con 11 voluntarios masculinos moderadamente activos, y se utilizó un ergómetro Lode para realizar una prueba de fatiga de 30 segundos. Los resultados muestran una relación altamente significativa entre la reducción de la frecuencia mediana y el inicio de la fatiga muscular.
</div>

<div class=text-justify>

El objetivo del estudio "Evaluation of the Electromyography Test for the Analysis of the Aerobic-Anaerobic Transition in Elite Cyclists during Incremental Exercise" [13] fue investigar la validez y fiabilidad de la electromiografía de superficie (EMG) para la detección automática de los umbrales aeróbico y anaeróbico durante una prueba de ejercicio continuo incremental utilizando períodos de ejercicio de 1 minuto en ciclistas de élite. Se analizaron los paquetes musculares vasto lateral, vasto medial, bíceps femoral y glúteo máximo. Dieciséis ciclistas bien entrenados completaron una prueba de ejercicio incremental (25 W/1 min) hasta el agotamiento. Se midieron las siguientes variables para evaluar la fatiga: la potencia máxima alcanzada, la frecuencia cardíaca, la concentración de lactato en sangre y la raíz cuadrada media (RMS) de las señales EMG. Los resultados mostraron que la EMG de superficie es una herramienta válida y fiable para la detección automática de los umbrales aeróbico y anaeróbico en ciclistas de élite durante una prueba de ejercicio continuo incremental.

</div>

<div class=text-justify>
 
El artículo, titulado “Assessment of Muscles Fatigue Based on Surface EMG Signals Using Machine Learning and Statistical Approaches: A Review”[14],  revisa los métodos para detectar la fatiga muscular a través de señales de EMG de superficie utilizando enfoques estadísticos y de aprendizaje automático. Los autores analizaron 15 estudios que investigan la fatiga muscular en diferentes músculos de la pierna, incluyendo el vasto lateral, gastrocnemio y tibial anterior. Los resultados muestran que los enfoques de aprendizaje automático y estadísticos son efectivos para detectar la fatiga muscular en los músculos de la pierna, con una precisión promedio del 90%. Los métodos que dieron mejores resultados fueron el análisis de componentes principales (PCA) y el análisis de discriminante lineal (LDA). Las variables utilizadas en estos enfoques incluyen la amplitud de la señal EMG, la frecuencia y la duración de la contracción muscular. Estos enfoques permiten una detección temprana de la fatiga muscular, lo que puede ser útil para prevenir lesiones en atletas y mejorar la rehabilitación en pacientes con enfermedades neuromusculares.

</div>

<div class=text-justify>
 
‌El objetivo del estudio "Un estudio comparativo de índices EMG en la evaluación de la fatiga muscular durante el ejercicio de ciclismo al máximo esfuerzo" [15] fue evaluar la utilidad de diferentes índices EMG en la evaluación de la fatiga muscular inducida por el ejercicio de ciclismo al máximo esfuerzo. Los músculos analizados fueron el vasto lateral (VL), el bíceps femoral (BF) y el gastrocnemio medial (GM). Se reclutaron 12 ciclistas altamente entrenados para realizar un ejercicio de ciclismo al máximo esfuerzo y se midieron los índices EMG de los músculos VL, BF y GM durante el ejercicio. Se utilizó el análisis de correlación gris para evaluar la relación entre los diferentes índices EMG y la fatiga muscular. Las variables utilizadas para medir la fatiga muscular fueron la frecuencia mediana (MF), la frecuencia media (MNF), la potencia media de la frecuencia (MPF) y la relación de potencia mediana (MMP).Además, se encontró que la frecuencia mediana (MF) y la frecuencia media (MNF) fueron los índices EMG más sensibles para detectar la fatiga muscular en los tres músculos analizados.

</div>

### Propuesta de solución
<div class=text-justify>
 
Se seleccionó el músculo vasto lateral de la pierna (VL) como el foco central de este estudio debido a su destacado papel como generador principal de potencia durante la práctica del ciclismo [16]. Por consiguiente, proponemos el  desarrollo de un Modelo de Aprendizaje Automático para la Monitorización de la Fatiga Muscular en el Músculo Vasto Lateral durante la Rehabilitación con Bicicleta Estática mediante señales de electromiografía de superficie (sEMG). Esta elección se respalda en la capacidad inherente del aprendizaje automático para analizar de forma precisa y eficiente las complejas señales de sEMG, identificar patrones de fatiga muscular y proporcionar retroalimentación en tiempo real. Nuestra propuesta tiene como objetivo optimizar los protocolos de rehabilitación y prevenir lesiones musculares en el contexto de pacientes que utilizan la bicicleta estática como parte de su proceso de recuperación, lo que, indudablemente, contribuirá al bienestar y al rendimiento de este grupo.
 
</div>

### Metodología del proyecto
Criterios de Inclusión:
Edad: Personas de 18 a 40 años.
Actividad física: Individuos con actividad física regular.
Reposo previo al estudio: No haber realizado ejercicio intenso en los tres días previos a la prueba.
Criterios de Exclusión:
Personas con enfermedades cardiovasculares, neuromusculares y metabólicas no serán incluidas en el estudio.

Preparación de la Piel para la Adquisición de Señal:
Depilar el exceso de vello en la zona.
Limpiar la zona con alcohol u otro desinfectante adecuado.
Aplicar gel conductivo en la zona para mejorar la conductividad eléctrica de los electrodos.
Utilizar electrodos de alta adherencia asegurar una buena conexión y minimizar

Posición de Electrodos:
La posición de los electrodos se seleccionará de acuerdo con el consenso SENIAM, una norma europea llamada "Surface ElectroMyoGraphy for the Non-Invasive Assessment of Muscles." Esto garantiza una colocación estandarizada y precisa para la adquisición de señales de EMG.

![3-Figure1-1](https://github.com/arianacarbajal/ISB_Grupo3/assets/56054823/454571d0-a274-4b04-b8ae-c066b16d6417)

Procesamiento de Señal en Python:
La señal se procesará en un entorno Python utilizando filtros pasa baja y alta, así como la transformada wavelet para eliminar el ruido y resaltar características relevantes.

Análisis de la Señal:
Se analizará la amplitud y la frecuencia de las señales de EMG a lo largo del tiempo para detectar cambios que indiquen fatiga muscular. Se considerarán características como la frecuencia mediana, frecuencia media, amplitud RMS y coeficientes de Wavelet.

Monitoreo de la Fatiga Muscular:
Se utilizará el espectro de potencia para seguir la evolución hacia frecuencias más bajas a medida que el músculo se fatiga. Esto permitirá el monitoreo de la fatiga en tiempo real durante el ejercicio.

Modelo de Aprendizaje Automático:
Se evaluarán los tipos de modelos de aprendizaje automático, tanto supervisados como no supervisados, para determinar cuál es más apropiado. La entrada del sistema serán las señales de EMG con sus características, y la salida será la recomendación de un ejercicio óptimo para prevenir lesiones musculares mediante el análisis de fatiga.Esta metodología proporciona un enfoque integral para el estudio de monitorización de fatiga muscular durante la rehabilitación con bicicleta estática. La combinación de técnicas de procesamiento de señales y aprendizaje automático permitirá un análisis detallado de la fatiga y la recomendación de ejercicios óptimos para mantener la salud muscular y prevenir lesiones.
La elección de frecuencias de corte y características importantes a analizar se eligieron mediante el estado del arte, donde se adecuará según la necesidad específica de nuetro proyecto.

### Adquisición de señales

- Protocolo empleado:
- Obtención de peso , talla e IMC de los participantes
- Cuestionario de actividad física
- Depilar la zona de colocación de electrodos
- Estiramiento por 5 minutos
- Colocación de electrodos
- Ejercicio en bicicleta estática (10 minutos)
- Se inició con un pedaleo de baja intensidad
- Se realizó una prueba incremental , cada 1.5 minutos se aumentó la potencia generada hasta llegar a 
  los 10 min
 -Se observó la potencia generada en cada intervalo de 1.5 minutos y se tuvo un registro de estos 
  valores  

Datos de los participantes:

![Imagen2](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/1485fc40-d43d-4713-afdf-798cb7059653)

Cuestionario de Actividad Física IPAQ

Obtención de peso , talla e IMC de los participantes
Se evalúan tres características de la actividad física (AF): intensidad (leve, moderada o vigorosa), frecuencia (días por semana) y duración ( tiempo por día)
Se registra en Mets (Metabolic Equivalent of Task o Unidades de Índice Metabólico) por minuto y semana.
Se clasifica en 3 niveles de  actividad física

![Imagen3](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/c1f2ed7f-2847-421b-bfbe-58ba49761b45)

Resultados : Cuestionario de actividad física IPAQ

![Imagen12](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/215dd4ae-9c10-4440-885b-a7cfd593dd01)

![Imagen1](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/07c615d7-6d53-49c5-9343-0757e1979dff)

Bicicleta Indoor Tour De France de Pro-Form

![Imagen4](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/2dae3bd1-caaa-40e1-bdc6-b7cc67af0b36)

Parámetros: Tiempo , distancia , Potencia en watts 

Protocolo empleado

![Imagen5](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/1115eb08-dbfc-492c-8a61-74386e34f75b)
![Imagen6](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/e57d647d-219c-4f3a-9e0b-94f616fe1618)

![Imagen7](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/7bb9d2e9-1365-43b8-a871-5c826d0cc721)

Procesamiento de señales

Para el procesamiento de señales , se realizó un filtro rechazabanda para la frecuencia de 60 hz ( ruido debido a la alimentación eléctrica) y posteriormente un filtro pasabanda de 10 a 200 hz . Se obtuvo la señal en relación al tiempo y su espectro en frecuencia mediante la transformada de fourier. Los filtros utilizados son filtros FIR y se utilizó la ventana blackman , en ambos casos , debido a su mejor capacidad de atenuación. Por otro lado también se segmento la señal en intervalos de 1.5 minutos debido al cambio de potencia entre esos intervalos y se generó una gráfica de amplitud vs tiempo del RMS de la señal con la señal segmentada en cada intervalo, esto nos permitirá analizar la señal con respecto al threshold como se observo en la literatura. Por último , se obtuvieron características relevantes de las 3 señales adquiridas tales como media , RMS , desviación estándar , mínimo y máximo valor , área bajo la curva , potencia total , frecuencia mediana y frecuencia máxima.

![Imagen8](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/bf1a0178-f9d2-4b21-8213-ccf781fc671e)

![Imagen9](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/024a5c63-aa1f-4bd6-902c-57e6e75f8879)

![Imagen10](https://github.com/arianacarbajal/ISB_Grupo3/assets/89601813/da7d8fa9-06e8-4afe-91f5-30d8e941fbed)

### Integrantes del proyecto

- Ariana Carbajal (colaborador) - ariana.carbajal@upch.pe 
- Natalia Galindo Concha (colaborador) - natalia.galindo@upch.pe 
- Gianfranco Fabian Feria Maquera (colaborador) - gianfranco.feria@upch.pe 
- Eduardo André Cuti Riveros (colaborador) -  eduardo.cuti@upch.pe 

### Bibliografía
[1]“Mecanismos fisiológicos de la fatiga neuromuscular”. Medigraphic - Literatura Biomédica. Accedido el 20 de octubre de 2023. [En línea]. Disponible: https://www.medigraphic.com/cgi-bin/new/resumenI.cgi?IDARTICULO=66431

[2]Rodríguez Ortega, Arturo. “Diseño de un nuevo modelo de bicicleta estática para uso comercial en una empresa multinacional con SAP ERP”. RiuNet repositorio UPV. Accedido el 20 de octubre de 2023. [En línea]. Disponible: https://riunet.upv.es/handle/10251/147867


[3]“Eficacia del ejercicio muscular concéntrico y excéntrico en deportistas aficionados con tendinopatias rotulianas en el centro de rehabilitación ASOFISIO”. DSpace Principal. Accedido el 20 de octubre de 2023. [En línea]. Disponible: http://repositorio.puce.edu.ec/handle/22000/8912


[4]UVaDOC Principal. Accedido el 20 de octubre de 2023. [En línea]. Disponible: https://uvadoc.uva.es/bitstream/handle/10324/57784/Actividad-electromiografica-EMG-durante-el-pedaleo.pdf?sequence=1&amp;isAllowed=y


[5] D. Pérez, “Epidemiología de la lesión deportiva,” Universidad Politécnica de Madrid,2015. https://oa.upm.es/36508/1/TFG_DANIEL_PEREZ_DEL_POZO.pdf (accessed Oct. 2023).

[6] L. Gao et al., “Biomechanical effects of exercise fatigue on the lower limbs of men during the forward lunge,” Frontiers, 2023. https://www.frontiersin.org/articles/10.3389/fphys.2023.1182833/full (accessed Oct. 2023). 

[7] J. A. Pernas, “Lesiones Musculares con y sin daño anatómico ,” VIl Jornadas Nacionales de Fisioterapia en el Deporte, 1999. 
https://ruc.udc.es/dspace/bitstream/handle/2183/10903/CC%2051%20art%204.pdf (accessed Oct. 19, 2023). 

[8] R. D´Onofrio, M. Padasala, A. Bhatt, and L. Febbrari, “The return to sport after muscular injury of the hamstring. A systemic Review,” The return to sport after muscular injury of the Hamstring. A systematic review, 2019. https://www.researchgate.net/profile/Rosario-Donofrio-2/publication/332621616_The_return_to_sport_after_muscular_injury_of_the_Hamstring_A_Systemic_Review/links/5cc068e092851c8d2202d543/The-return-to-sport-after-muscular-injury-of-the-Hamstring-A-Systemic-Review.pdf (accessed Oct. 20, 2023). 

[9] F. Daussin, A. Combes, V. Bougault, and J. Dekerle, “European Journal of Sports Medicine x 8 TH EUROPEAN SPORTS MEDICINE CONGRESS OF EFSMA EUROPEAN FEDERATION OF SPORTS MEDICINE ASSOCIATIONS AND 6 TH JOINT MEETING SFMES AND SFTS FRENCH SOCIETY OF EXERCISE AND SPORTS MEDICINE FRENCH SOCIETY OF SPORTS TRAUMATOLOGY,” Conference: 8TH EUROPEAN SPORTS MEDICINE CONGRESS OF EFSMA EUROPEAN FEDERATION OF SPORTS MEDICINE ASSOCIATIONS, 2013. 
https://www.researchgate.net/publication/297698831_European_Journal_of_Sports_Medicine_x_8_TH_EUROPEAN_SPORTS_MEDICINE_CONGRESS_OF_EFSMA_EUROPEAN_FEDERATION_OF_SPORTS_MEDICINE_ASSOCIATIONS_AND_6_TH_JOINT_MEETING_SFMES_AND_SFTS_FRENCH_SOCIETY_OF_EXERCI (accessed Oct, 2023). 

[10] V. Bourguigne, “Alteraciones posturales y lesiones en ciclistas amateurs - core,” Universidad Fasta,2012.  https://core.ac.uk/download/pdf/49224101.pdf (accessed Oct. 20, 2023). 


[11]J. Wang, S. Sun, and Y. Sun, “A Muscle Fatigue Classification Model Based on LSTM and Improved Wavelet Packet Threshold,” Sensors, vol. 21, no. 19, pp. 6369–6369, Sep. 2021, doi: https://doi.org/10.3390/s21196369.

[12] V. P. Singh, D. Kumar, B. Polus, and S. F. Fraser, “Strategies to identify changes in SEMG due to muscle fatigue during cycling,” Journal of Medical Engineering & Technology, vol. 31, no. 2, pp. 144–151, Jan. 2007, doi: https://doi.org/10.1080/03091900500444281.

[13] Ibán Latasa, A. Córdova, G. Quintana-Ortí, A. Lavilla-Oiz, J. Navallas, and J. Rodríguez-Falces, “Evaluation of the Electromyography Test for the Analysis of the Aerobic-Anaerobic Transition in Elite Cyclists during Incremental Exercise,” Applied sciences, vol. 9, no. 3, pp. 589–589, Feb. 2019, doi: https://doi.org/10.3390/app9030589.

[14] H. A. Yousif et al., “Assessment of Muscles Fatigue Based on Surface EMG Signals Using Machine Learning and Statistical Approaches: A Review,” IOP conference series, vol. 705, no. 1, pp. 012010–012010, Nov. 2019, doi: https://doi.org/10.1088/1757-899x/705/1/012010.

‌[15] L. Wang et al., “A Comparative Study of EMG Indices in Muscle Fatigue Evaluation Based on Grey Relational Analysis during All-Out Cycling Exercise,” BioMed Research International, vol. 2018, pp. 1–8, Jan. 2018, doi: https://doi.org/10.1155/2018/9341215. 

[16] S. Bercier et al., “The vastus lateralis neuromuscular activity during all-out cycling exercise,” Journal of Electromyography and Kinesiology, vol. 19, no. 5, pp. 922–930, Oct. 2009, doi: https://doi.org/10.1016/j.jelekin.2008.03.012.
‌
 
