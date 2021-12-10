# Deep Learning
En este práctico trabajamos en el problema de clasificación de texto del MeLi Challenge 2019. El datasets tiene información acerca de títulos de publicaciones, categoría de los mismos, información de idioma y confiabilidad de la anotación. Cuenta con anotaciones de títulos para 632 categorías distintas. El dataset también cuenta con una partición de test que está compuesta de 63680 de ejemplos con las mismas categorías. También hay datos en idioma portugues, aunque filtramos para trabajar solamente el idioma español.

### Grupo 10
+ Altamirano Marlen
+ Cattaneo Matias
+ Díaz Federico Raul
+ Luque Melina
+ Oliverio Sofia

## Procedimiento

Decidimos realizar la clasificacion empleando Redes Convolucionales. Para ello, se realizó primeramente un preprocesamiento del dataset y se eligió el dataset en español como lenguaje a trabajar. Luego dividimos el dataset en los datos de entrenamiento y de test, 80% y 20%, respectivamente. 
Los titulos de las publicaciones serán nuestros datos de entrada y el target será la categoría de cada item. Para ello, los titulos se vectorizan haciendo uso del diccionario "glove...", mientras que las categorias son representadas por valores numericos. 
La clase PadSequences fue empleada para asegurar que todos los vectores de entrada tengan la misma dimension. 

## Modelo CNN

Se optó por usar una arquitectura que incluyera Redes Neuronales Convolucionales y diversos hiperparámetros fueron variados con el fin de optimizar los resultados. Empleamos MLFlow para gestionar el proceso de aprendizaje automático. La métrica elegida para determinar la eficacioa de nuestro modelo fue la "balanced accuracy". 

Dado el tamaño del dataset y las limitaciones de los recursos disponibles, si bien hicimos uso de Nabucodonosor2 se decidió acotar el dataset a 1.000.000 de líneas y basado en ese dataset reducido es que presentamos los siguientes resultados.

## Resultados

Corrimos nuestro modelo con hiperparametros por Default y luego, ciertos hiperparámetros fueron modificados con el fin de explorar la optimización de nuestro modelo. 

### Hiperparámetros


| Experimento n° | Épocas | Learning Rate | Filters_Count | Freeze_Embeddings | Batch_Size | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 1  | 3 | 1e-3 | 100 | True | 128 |
| 2  | 3 | 1e-3 | **150** | True | 128 |
| 3  | **2** | 1e-3 | 100 | True | 128 |
| 4  | **5** | 1e-3 | 100 | True | 128 |
| 5  | **10** | 1e-3 | 100 | True | 128 |
| 6  | 10 | 1e-3 | 100 | **False** | 128 |
| 7  | 10 | 1e-3 | 100 | False | **256** |
| 8  | 3 | **5e-3** | 100 | False | 256 |

### Métricas Obtenidas

| Experimento n° | Test Balanced Accuracy | Test Loss | Train Loss | 
| ------------- | ------------- | ------------- | ------------- |
| 1  | 0.452 | 2.47 | 2.54 |
| 2  | 0.430 | 2.49 | 2.59 |
| 3  | 0.417 | 2.77 | 2.71 | 
| 4  | 0.492 | 2.16 | 2.35 |
| 5  | 0.531 | 1.79 | 2.07 |
| 6  | x | x | x | 
| 7  | x | x | x |
| 8  | x | x | x | 






