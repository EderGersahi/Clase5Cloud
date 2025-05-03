# Overview
El objetivo de esta actividad es realizar un implementación básica del Aprendizaje Federado utilizando TensorFlow. El modelo se entrenó de manera descentralizada con 5 conjuntos de datos locales y, posteriormente, se agregaron al modelo global mediante diferentes técnicas. 

# Descripción 
La actividad simuló un escenario de Aprendizaje Federado con datos confidenciales pertenecientes a cada cliente (en este caso 5). Cada cliente entrenó de manera independiente el modelo utilizando solamente sus propios datos. Posteriormente, los 5 modelos se combinaron en un modelo global utilizando 3 técnicas:   
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

# Autores
Pamela Cantú Rodríguez | A01285128   
Ana Sofía Ugalde Jiménez | A01702639   
Leslie Ramos Gutiérrez | A01562461   
Eder Gersahí Martínez León | A00831442   
Fernanda Alanis Montfort | A01721959   
