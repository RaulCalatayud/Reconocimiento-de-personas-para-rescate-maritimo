# Reconocimiento de personas para rescate maritimo
Trabajo de fin de grado en el cual se realiza la creación de un sistema de visión artificial utilizando una red neuronal con arquitectura YOLOv3 para el reconocimiento de náufragos. Este sistema busca ser implantado en un grupo de drones autónomos que trabajen cooperativamente con los sistemas de búsqueda y rescate marítimo.

RESUMEN

Las tecnologías actuales empleadas para ayudar a los equipos humanos en la búsqueda y rescate de náufragos en entornos marítimos son escasas, con muy poca intervención de la inteligencia artificial. Si se suma esto a los escasos recursos de los que disponen los equipos de rescate en comparación con la gran extensión de costa a cubrir, queda claro que se necesita actuar en este campo. Es por ello que este proyecto está enfocado a aumentar en lo posible las posibilidades de salvar vida en entornos marítimos mediante la creación de un dron que realice misiones de rescate.

Con este objetivo se va a realizar un sistema de visión artificial Para ello se va a crear y entrenar una red YOLOv3 debido a su gran velocidad de procesamiento de imagen, puesto que el sistema debe estar diseñado para realizar detecciones en vivo a un mínimo de 30fps. Esta red neuronal alcanza sin problemas estos valores de procesamiento, sacrificando a cambio un poco de precisión.

Para el entrenamiento de la red se necesita un dataset con imágenes de personas en el agua para que el algoritmo aprenda a detectarlas. Tras una larga búsqueda infructuosa por varios bancos de datos, tan solo se encontró un dataset que cumplía estos requisitos, aunque las imágenes de las personas estaban hechas en un entorno simulado, por tanto eran modelos 3D y no eran tan útiles para el entrenamiento. Por tanto se decidió crear un dataset propio, buscando imágenes y vídeos de bancos de datos y etiquetándolos manualmente. Este etiquetado se pudo acelerar gracias a una función de pseudoetiquetado que se consiguió implementar en la que se utilizaba la propia red neuronal para etiquetar los datos.

Al realizar pruebas para comprobar el funcionamiento de la red entrenada, se descubrieron problemas relacionados con solapamientos y parpadeo de detecciones a causa del fallo de detección en algunos frames, por tanto se idearon distintos algoritmos para corregir estos dos fallos.

El entrenamiento de la red se realizó de forma progresiva, añadiendo conjuntos de imágenes nuevas a cada entrenamiento y realizando numerosas pruebas para intentar obtener el mayor porcentaje de acierto posible dentro de las limitaciones que causaba el dataset. También se modificaron parámetros internos de la red que proporcionaron mayor porcentaje de acierto al sistema de detección.

Finalmente, para comprobar el comportamiento que debía realizar el dron junto al sistema de visión, se diseñó una simulación de un entorno marítimo en el que se ha colocado un modelo 3D de una persona. El comportamiento del dron fue programado y puesto a prueba en la simulación para imitar una operación de rescate en la que debe detectar la persona y acercarse a ella.


CREACIÓN DEL DATASET

Una gran parte de la creación de este dataset proviene del repositorio creado por 2897winter https://github.com/winter2897/Airsim-Search-and-Rescue-SAR-at-sea-with-UAV, el cual realiza una simulación de un naufragio y utiliza un dron controlado con la librería AirSim en un entorno de UnrealEngine para la toma de imágenes.

<img src="/Imagenes/ue1.png" alt="Dron en el entorno simulado"/>

CREACIÓN DE LA RED YOLOv3

Se ha utilizado el fork del darknet original AlexeyAB https://github.com/AlexeyAB/darknet. Se ha entrenado 


