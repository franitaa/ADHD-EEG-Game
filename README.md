# ADHD-EEG-Game

## Introduction
### ADHD
Attention Deficit Hyperactivity Disorder (ADHD) is a chronic condition that affects attention span, impulsivity, and restlessness. Its symptoms range from mild to severe and can lead to issues with relationships, poor academic or work performance, and low self-esteem, among others. For this reason, early detection of ADHD is vital in order to treat it (through medication, psychotherapy, and more) and help normalize the patient's life [1].

It is estimated that globally, around 5% of children and adolescents suffer from ADHD. A similar figure applies to adults, although there is some debate about the diagnostic criteria for this age group.

### Diagnosis
Typically, diagnosis is based on evaluations conducted by qualified physicians and psychiatric specialists. These assessments include both physical and psychological exams, which help rule out other disorders that may be causing the symptoms, such as depression, anxiety, or substance abuse.

Currently, there are numerous publications on the identification of ADHD through exams like electroencephalograms (EEG), and this remains an ongoing area of research. In general, the goal is to find patterns in these signals that correlate with the presence of the disorder. These patterns range from a decrease in theta rhythm power to correlations with fractal dimension [2].

### Dataset
The dataset [3] includes EEG recordings from two groups (ADHD and control) during a game controlled by a brain-computer interface (BCI), and then the same game controlled by a keyboard. There are 4 and 5 subjects in each group, respectively, with multiple sessions per player. The goal of these types of games is to provide cognitive training for those with the disorder to improve their focus. Game durations vary per player, as recording ends when each session is completed.

The researchers first compared the results of the control group using the keyboard and the BCI-based game (called "Emotiv") to train a model to distinguish between the two. The idea was to see if it was possible to detect a difference, since using the Emotiv required more concentration than using the keyboard. They were able to classify both situations effectively.
They then repeated this with ADHD subjects, and finally, separating keyboard and Emotiv data, they combined the results with the control group to try to distinguish ADHD subjects from non-ADHD ones.

An interesting case is that one of the subjects had received ADHD treatment during childhood and had therefore learned concentration-enhancing skills that the others had not. This caused differences in his signals compared to both groups. This is clearly reflected by the fact that when the rest of the dataset was used to train a model and then applied to this subject's game signals, the model classified most (or many) of his signals as non-ADHD.

The data is in CSV format. For non-ADHD subjects, there are two types of files:

* Raw EEG channel data with corresponding timestamps
* Data already divided into relevant frequency bands

However, for ADHD subjects, only the band information is available, so the analysis is conducted using only that information in both cases. The paper does not specify exactly how the frequency bands were divided, which can vary slightly depending on the researchers, but they can generally be considered as follows [4]:

* Theta: 4–8 Hz, deep relaxation
* Alpha: 8–12 Hz, relaxed and passive attention
* Low-beta: 13–21 Hz, calm, introspective concentration
* High-beta: 21–30 Hz, significant stress, anxiety, paranoia, and high energy
* Gamma: >30 Hz, cognitive function

Variations in beta and gamma rhythms are expected between the two groups.

## Objectives
The goal of this project is to find relevant differences between the EEG signal features of both groups in order to classify them as ADHD or control. Additionally, using an unsupervised learning algorithm, we aim to characterize the differences between the subject who received treatment and the ADHD and control groups.

------------------------------------------

## Introducción
### ADHD
El Trastorno por Déficit de Atención con Hiperactividad (o ADHD, por sus siglas en inglés) es una condición crónica que afecta la capacidad para prestar atención, impulsividad e inquietud. Sus síntomas oscilan de leves a graves, y pueden conllevar problemas para relacionarse, desempeños laborales o académicos negativos y baja autoestima, entre otros. Por este motivo, es de vital importancia la detección del ADHD, para poder tratarlo (a través de fármacos y psicoterapia, entre otros) y colaborar a la normalidad de la vida del paciente [1].

Se estima que, globalmente, alrededor de un 5% de los niños y adolescentes padecen de ADHD. En adultos se tiene una cifra similar, aunque existe cierto debate acerca de los criterios de diagnóstico para dicho grupo etario.

### Diagnóstico
Normalmente, el diagnóstico se basa en evaluaciones realizadas por médicos calificados y especialistas en psiquiatría. Los exámenes incluyen revisiones físicas y psicológicas, que sirven para descartar otros trastornos que puedan estar causando los síntomas, como depresión, ansiedad o abuso de sustancias.

Actualmente existen numerosas publicaciones acerca de la identificación de ADHD a partir de exámenes como el electroencefalograma (EEG), y es una cuestión que continúa bajo investigación. En líneas generales, se buscan patrones en dichas señales que se correlacionen con la presencia del trastorno. Estos varían desde una disminución en la potencia de los ritmos theta, hasta una correlación con la dimensión fractal [2].

## Dataset
El dataset [3] cuenta con registros de EEG de dos grupos (ADHD y control) durante un juego controlado por BCI (*brain-computer interface*) y, luego el mismo juego pero controlado por teclado. Son 4 y 5 sujetos en cada grupo, respectivamente, con varias partidas por jugador. El objetivo de esta clase de juegos es dar un entrenamiento cognitivo a quienes padecen este trastorno para mejorar su concentración. Los tiempos del juego varían entre cada jugador, ya que se terminaba de registrar una vez que finalizaban la partida.

Los investigadores en primer lugar compararon los resultados del grupo de control utilizando teclado y el juego basado en BCI (llamado “Emotiv”), con la intención de entrenar una red para diferenciarlos. La idea detrás de esto, era ver si se podía detectar una diferencia ya que al utilizar el Emotiv los sujetos debían concentrarse más que al utilizar teclado. Pudieron clasificar de buena manera ambas situaciones.
Luego se realizó lo mismo con sujetos con ADHD y por último, separando por teclado y Emotiv, se juntaron los resultados con los de control para lograr diferenciarlos con los de ADHD.

Una particularidad es que uno de los sujetos recibió tratamiento de ADHD durante su niñez y por lo tanto aprendió habilidades para mejorar su concentración que los otros no. Esto genera diferencias en sus señales respecto a los sujetos de ambos grupos. Esto se puede ver claramente reflejado ya que al utilizar el resto del dataset como entrenamiento y luego utilizarlo para analizar las señales durante el juego de este sujeto, se encontraron con que el modelo clasificaba que la mayoría (o muchas) de las señales no eran ADHD.

Los datos se hallan en formato csv. Para sujetos non-ADHD, hay dos tipos de archivos
  * Información cruda de los canales de EEG, con sus respectivos *timestamps*
  * Datos ya divididos en las bandas de frecuencia de interés

Sin embargo, para los sujetos ADHD sólo se halla disponible la información de las bandas, y por eso se decide trabajar solo con esa información en ambos casos para el análisis. En el paper no se aclara qué clase de división específica se realiza para las bandas frecuenciales, que pueden variar ligeramente según los investigadores, pero en líneas generales pueden considerarse [4]:

  * Theta: 4-8 Hz, relajación profunda
  * Alfa: 8-12 Hz, estado de relajación y atención pasiva
  * Low-beta: 13-21 Hz, concentración tranquila e introspectiva
  * High-beta: 21-30 Hz, estrés significativo, ansiedad, paranoia y alta energía
  * Gamma: > 30 Hz, función cognitiva

Es esperable ver variaciones en los ritmos beta y gamma entre los dos grupos.

## Objetivos

La finalidad de este proyecto será hallar diferencias relevantes entre las características señales de EEG de ambos grupos para clasificarlos en ADHD y control. Además, con un algoritmo de aprendizaje no supervisado se buscará caracterizar las diferencias entre el sujeto que recibió el tratamiento, y los grupos de ADHD y control.

## Bibliography
[1] “Trastorno de déficit de atención con hiperactividad (TDAH) en adultos - Síntomas y causas - Mayo Clinic,” Mayoclinic.org, 2023. https://www.mayoclinic.org/es/diseases-conditions/adult-adhd/symptoms-causes/syc-20350878#:~:text=El%20trastorno%20por%20d%C3%A9ficit%20de,atenci%C3%B3n%2C%20hiperactividad%20y%20conducta%20impulsiva (accessed Jun. 02, 2024).
‌

[2] Majid Moghaddari, Mina Zolfy Lighvan, and Sebelan Danishvar, “Diagnose ADHD disorder in children using convolutional neural network based on continuous mental task EEG,” Computer methods and programs in biomedicine, vol. 197, pp. 105738–105738, Dec. 2020, doi: https://doi.org/10.1016/j.cmpb.2020.105738.


[3] Alaa Eddin Alchalabi, Shervin Shirmohammadi, Amer Nour Eddin, and M. Elsharnouby, “FOCUS: Detecting ADHD patients by an EEG-based serious game,” ResearchGate, Jun. 2018. https://www.researchgate.net/publication/325522566_FOCUS_Detecting_ADHD_patients_by_an_EEG-based_serious_game (accessed Jun. 02, 2024).
‌

[4] H. Diaz, Fernando Maureira Cid, J. Otarola, and L. Cañete, “EEG Beta band frequency domain evaluation for assessing stress and anxiety in resting, eyes closed, basal...,” ResearchGate, Dec. 29, 2019. https://www.researchgate.net/publication/338281912_EEG_Beta_band_frequency_domain_evaluation_for_assessing_stress_and_anxiety_in_resting_eyes_closed_basal_conditions (accessed Jun. 02, 2024).
