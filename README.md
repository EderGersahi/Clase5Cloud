# Overview
El objetivo de esta actividad es realizar un implementación básica del Aprendizaje Federado utilizando TensorFlow. El modelo se entrenó de manera descentralizada con 5 conjuntos de datos locales y, posteriormente, se agregaron al modelo global mediante diferentes técnicas. 

# Descripción 
La actividad simuló un escenario de Aprendizaje Federado con datos confidenciales pertenecientes a cada cliente (en este caso 5). Cada cliente entrenó de manera independiente el modelo utilizando solamente sus propios datos. Posteriormente, los 5 modelos se combinaron en un modelo global utilizando 4 técnicas:   
* **FedAvg**: promedia los modelos entrenados por cada dispositivo y los distribuye nuevamente, permitiendo el aprendizaje sin compartir datos privados.
* **FedMedian**: usa la mediana en lugar del promedio para reducir el impacto de valores extremos, mejorando la estabilidad frente a datos inconsistentes.
* **FedNova**: ajusta la contribución de cada integrante según cuánto haya entrenado, equilibrando mejor los modelos en dispositivos con diferentes capacidades.
* **Promedio ponderado**: técnica para combinar los modelos locales teniendo en cuenta la cantidad de datos con la que fue entrenado cada modelo.

# Dependencias y librerías
Este proyecto utliza Python y las siguientes librerías:    
* numpy: Biblioteca optimizada para cálculos numéricos y manipulación de arreglos y matrices.
* matplotlib: Herramienta para crear gráficos y visualizaciones de datos.
* scikit-learn: Conjunto de herramientas para machine learning, esto incluye algoritmos de clasificación, regresión y clustering.
* keras: Conjunto de herramientas fácil de usar para crear redes neuronales y modelos de inteligencia artificial.

* Versiones de Librerías:

  
  keras==3.1.1

   
  numpy==1.26.4

  
  scikit-learn==1.6.1

  
  matplotlib==3.7.1

  

# Orden de ejecución
El entrenamiento del modelo se organizó en los siguientes componentes:    
1. Se dividió la base de datos en 5 conjuntos estadísticamente equivalentes. Cabe destacar que los datos, al ser confidenciales, no se encuentran en el repositorio.     
2. TheModel.py: contiene la arquitectura del modelo utilizado local y globalmente. El modelo utilizado fue...  
3. implementar_entrenar.ipynb: cada uno de los conjuntos de datos se utilizó para entrenar un modelo localmente. Posteriormente, cada modelo se exporta con formato ".keras" para después agregarlo al modelo global. La única modificación necesaria es el nombre del archivo con los datos a utilizar; y, si así se desea, el nombre con el cual se exportará el modelo.   
4. modelos_gloables.ipynb: Contiene el código utilizado para la agregación global incluyendo 4 técnicas: FedAvg, FedMedian, Promedios Ponderados y FedNova.

# Explicación de Resultados

El aprendizaje federado permite distribuir el entrenamiento de los modelos en diversas máquinas, lo cual resulta muy beneficioso al trabajar con modelos que requieren un alto rendimiento computacional. En el ejemplo desarrollado en la actividad, se utilizó la base de datos MNIST, la cual fue dividida en cinco partes con la misma distribución y cantidad de datos. Posteriormente, se entrenaron cinco modelos locales que fueron combinados para generar modelos globales y así obtener un resultado final.   


De manera individual, el modelo de red neuronal convolucional propuesto se desempeñó de forma eficiente, alcanzando una precisión superior al 95 % en todos los casos. Sin embargo, al generar los modelos globales, el rendimiento disminuyó considerablemente en tres de los cuatro casos evaluados: los tres primeros obtuvieron una precisión entre el 50 % y el 55 %, mientras que el mejor modelo global alcanzó un 94 % de precisión.      

Para calcular los pesos de los modelos globales se utilizaron cuatro estrategias. En primer lugar, FedAvg, que promedia los pesos de los cinco modelos locales. En segundo lugar, se utilizó la mediana, una medida robusta a valores atípicos. En tercer lugar, se aplicó el promedio ponderado, que a diferencia de FedAvg, considera la cantidad de datos utilizados por cada modelo local, sin embargo, su resultado fue similar al de FedAvg, debido a que todos los modelos locales tenían la misma cantidad de datos. Por último, se utilizó FedNova, que también se basa en promedios, pero incorpora una normalización de la contribución de cada modelo en función del número de pasos locales realizados. Esta característica permite que la combinación sea proporcional y reduce inconsistencias, lo que mejora la convergencia del modelo global.      

En términos generales, FedAvg, FedMedian y el promedio ponderado presentaron un rendimiento regular, con precisiones de 53 %, 51 % y 53 %, respectivamente. En contraste, el modelo global generado con FedNova alcanzó una precisión del 94 %, posicionándose como el mejor modelo. A pesar de contar con la misma arquitectura y una distribución equitativa de datos, el buen desempeño de FedNova se atribuye a su mecanismo de normalización de actualizaciones. Las trayectorias de optimización locales, aunque sutilmente diferentes, provocan variaciones que FedNova es capaz de corregir, mientras que FedAvg o FedMedian simplemente combinan los resultados sin mitigar estas diferencias. Esto hace que FedNova sea más robusto frente a pequeñas asimetrías presentes incluso en la configuración de este ejercicio.   

# Autores
Pamela Cantú Rodríguez | A01285128   
Ana Sofía Ugalde Jiménez | A01702639   
Leslie Ramos Gutiérrez | A01562461   
Eder Gersahí Martínez León | A00831442   
Fernanda Alanis Montfort | A01721959   
