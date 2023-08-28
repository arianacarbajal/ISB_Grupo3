# Laboratorio 1 _Grupo 3
- Plotear al menos 3 señales en Arduino IDE provenientes del generador de señales.
-  Comparar las señales graficadas del Arduino IDE con las gráficas obtenidas del osciloscopio.
-  Graficar en Arduino cloud.


## Tabla de contenido

- [Código de adquisición de la señal](#Código).
- [Materiales del curso](#Materiales).
- [Objetivo del curso](#Objetivo_del_curso).
- [Contenido del curso](#Contenido_del_curso).
- [Integrantes del proyecto](#Integrantes_del_proyecto).
- [Foto grupal](#Foto_grupal).
- [Temática del proyecto](#Temática_del_proyecto).
- [Justificación del proyecto](#Justificación_del_proyecto).
- [Metodología del proyecto](#Metodología).
- [Docentes del curso](#Docentes_del_curso).
- [Bibliografía](#Bibliografía).

### Código de adquisición de la señal
Se puede observar :
- La frecuencia de sampleo que usaremos sera de 10 hz.
- El pin del cual obtenemos la data del generador de funciones es el A2 y usamos la funcion analogRead() para obtenerla
- Se imprimen estos valores y se mostraran a forma de plot en el Serial plotter 

```
unsigned long lastMsg = 0;
float F=1;                      // 1 hz
double Fs = 10*F;               // 10 hz
double Ts_ms = (1/Fs)*1000;     //  100 ms
int input;  

void setup() {
  Serial.begin(9600);
  while (!Serial);
  //Serial.println("R1:,R2:,");
}

void loop() {

  unsigned long now = millis();

  if (now - lastMsg > Ts_ms) {
    
    lastMsg = now;

    int r1 = analogRead(A2);

    Serial.println(r1);
    
  }

}

```
### Circuito físico

Para el circuito se utilizo un capacitor , el arduino Nano 33ioT , un cable micro USB .

La entrada positiva del cable que se conecta al output del generador de señales estaba conectado al puerto analogico A2 del Arduino Nano 33ioT y el negativo  al puerto GND.

<image src ="Imagen/circuitoref.jpeg"> 


### Materiales del laboratorio


| Modelo | Equipo / Materiales |
| ------------- | ------------- |
| SAMD |Arduino Nano 33 IoT  |
| AFG1022  | Generador de Señales  |
| TBS 1000C Series  |  Osciloscopio Digital  |
|  |Cable BNC Male-Male |
|  | Punta de osciloscopio con conector BNC (Male) |
|  | Par de cables Male -Male  |
|  | Protoboard  |

### Señales provenientes del generador de señales y características

1. Señal 1: Señal sinusoidal
- Amplitud = 3.3 V
- Offset = 1.65 V
- Frecuencia = 500 mHz

2. Señal 2: Señal sinusoidal
- Amplitud = 2 V
- Offset = 1 V
- Frecuencia = 500 mHz

<image src ="Imagen/señal2_gen.jpeg"> 

3. Señal 3: Señal sinusoidal
- Amplitud = 1.5 V
- Offset = 0.75 V
- Frecuencia = 500 mHz

<image src ="Imagen/señal3_gen.jpeg"> 

4. Señal 4: Señal cuadrada
- Amplitud = 2 V
- Offset = 1 V
- Frecuencia = 500 mHz

<image src ="Imagen/señal4_gen.jpeg"> 

Podemos ver que el offset en cada señal esta situado en la mitad de la amplitud de modo que la señal sea siempre positiva , como se pide.

### Justificación del proyecto

La OMS declara  que al año se realizan más de 1 millón de amputaciones, a su vez, según el INR, las amputaciones de miembros superiores representan el 14% de los casos, con mayor incidencia en países de medios a bajos ingresos y en personas jóvenes de alrededor  de 34 años.[2]

Se han identificado obstáculos en el avance de las prótesis controladas por señales EMG para amputaciones como en los casos presentados . La optimización de la usabilidad y la funcionalidad, el aseguramiento de una alta fiabilidad de la señal  y la obtención de una respuesta rápida de la prótesis son desafíos fundamentales que podrían abordarse mediante posibles soluciones. Enfocarse en estos aspectos permitirá el desarrollo de prótesis más eficaces y accesibles, con el potencial de mejorar significativamente la calidad de vida de los usuarios. [3]
Por ello  la importancia del proyecto ya que busca lograr una captura precisa de las señales EMG el cual es un aspecto esencial para crear prótesis eficientes y funcionales que marquen una diferencia en el desarrollo de soluciones innovadoras. [4]



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

### Foto grupal



### Docentes del curso
- Umbert Lewis De La Cruz
- Moisés Meza
- José Alonso Cáceres
- Julissa Venancio

### Bibliografía
[1] Procesamiento y Clasificación de Bioseñales con Inteligencia Computacional. (s.f.). SMIA. http://smia.mx/comia/2017/index.php?option=com_content&amp;view=article&amp;id=12&amp;Itemid=127

[2] Resolución directoral, 132-2021-SA-DG-INR, Ministerio de Salud - Instituto Nacional de Rehabilitación, Lima, 2021. Accedido el 18 de agosto de 2023. [En línea]. Disponible: https://www.inr.gob.pe/transparencia/transparencia%20inr/resoluciones/2021/RD%20132-2021-SA-DG-INR.pdf

[3] Unanyan, N. N., & Belov, A. A. (2021). “Design of upper limb prosthesis using real-time motion detection method based on EMG signal processing”. Biomedical Signal Processing and Control, 70, 103062. doi:10.1016/j.bspc.2021.103062 

[4] Bi, L., Feleke, A. >Genetu, & Guan, C. (2019). A review on EMG-based motor intention prediction of continuous human upper limb motion for human-robot collaboration. Biomedical Signal Processing and Control, 51, 113–127. doi:10.1016/j.bspc.2019.02.011 