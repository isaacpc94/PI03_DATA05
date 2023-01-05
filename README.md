# PROYECTO INDIVIDUAL #2 : MACHINE LEARNING


<p align="center">
<img src="https://raw.githubusercontent.com/isaacpc94/PI02_DATA05/main/images/MChospital.jpg"  height=300><br><br>

# DESCRIPCIÓN DEL PROYECTO :

El siguiente proyecto tiene como objetivo predecir si un paciente estará hospitalizado más de 8 dias o no, por lo cual se cuenta con una data de 410000 registros, para el cual se aplicó modelos de clasificación en busca de obtener métricas "recall" y "accuracy" mayor a 70%.
<br>
El código utilizado para el presente proyecto se encuentra en el archivo "ProyectoML.ipynb"
<br>
<br>

# FEATURE ENGINEER :

-  Se carga el archivo "hospitalizacions_test.csv de la carpeta "Archivos train y test".
-  Se hace un EDA de los datos, no encontrando duplicados ni vacíos.
-  Se encuentra los valores únicos para cada feature con el fin de conocer si son categóricos o numéricos.
<br>
<br>

# FEATURE ENCODING :

-  Se convierte valores categóricos a numericos de cada feature aplicando "One hot encoder", "label encoder".
-  Se aplica un escalado a las features numéricas como MinMaxScaler y StandardScaler.
-  El feature "patientid" no se considera para el modelo ya que en su mayoria son unicos y no se les puede relacionar con el objetivo que es la columna "Stay (in days)" .
-  Despues de transformar los datos se obtiene un Dataframe con solo valores numéricos y se obtendrán 6 tipos de muestra:<br>
    Las 3 primeras muestras presenta outliers en el feature "Admission_Deposit".
    - Dataframe con todas las features .
    - Dataframe excluyendo las features con un factor de correlacion <0.1 .
    - Dataframe excluyendo las featues con un factor de correlacion <0.01 .<br>

    Las 3 últimas muestras no presentan outliers en el feature "Admission_Deposit".
    - Dataframe con todas las features
    - Dataframe excluyendo las features con un factor de correlacion <0.1 .
    - Dataframe excluyendo las features con un factor de correlacion <0.01 .
<br>
<br>

# MODELING:
- Se divide el Dataframe en una muestra de 70% para entrenamiento y 30% para testeo.
- Se busca los mejores hiperparámetros con scoring = "accuracy " y un "CV" de 5  ,para los modelos de "DecisionTreeClassifier" y "KNeighborsClassifier" entrenándolos con el 70% de datos que se obtubo del proceso "split".
- De todas las pruebas la primera prueba es la mejor con los siguientes hiperpárametros:
    - 'criterion': 'gini' 
    - 'max_depth': 22
- Se comprueba este resultado con un "cross validation" con "CV"=5, para el mismo modelo.
- Usando este modelo se predice usando como datos de entrada el 30% de datos seleccionados como testeo durante el proceso de "split" ,obteniendo las siguientes métricas:
     - 'accuracy' > 75%
    - 'recall' > 80% 
- Estas metricas superan lo esperado, lo cual podemos concluir que el modelo trabaja eficentemente y es óptimo para su uso.
<p align="center">
<img src="https://raw.githubusercontent.com/isaacpc94/PI02_DATA05/main/images/resultadoML.jpg"  height=100>
<br><br>


# PREDICTION : 

- En la carpeta "pred", se encuentra el archivo "isaacpc94.csv", resultado de la predicción del mejor modelo usando como datos de entrada el archivo "hospitalizaciones_test.csv" que se encuentra en la carpeta "Archivos train y test".

