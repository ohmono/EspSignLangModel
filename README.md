# Proyecto de Reconocimiento de Lengua de Señas

Este proyecto se desarollo para las materias Procesamiento Digital de Imágenes e Introducción al Deep Learning de la carrera de Ingeniería en Sistemas en la Universidad de Antioquia, Colombia.

Se utilizan OpenCV y MediaPipe para detectar y clasificar gestos de manos en tiempo real. El objetivo principal es reconocer letras de la lengua de señas americana (ASL) utilizando un modelo de aprendizaje profundo entrenado con TensorFlow y Keras.

## Señas Reconocidas

![[Señas Reconocidas]](data/esp_sign.png)

## Requisitos

- Python 3.7 o superior
- OpenCV
- MediaPipe
- TensorFlow y Keras
- Matplotlib
- NumPy
- Imbalanced Learn
- Scikit Learn
- Scikit Image
- Pandas
- seaborn

Puedes instalar las dependencias necesarias con el siguiente comando:

```bash
pip install -r requirements.txt
```

## Descripción del Proyecto

Este proyecto captura frames de video en tiempo real desde la cámara, detecta los puntos de referencia de la mano y clasifica los gestos en letras de la lengua de señas. Además, muestra las letras reconocidas en pantalla y permite la interacción en tiempo real para formar palabras y guardarlas en un archivo de texto.

## Datasets

Se utilizaron dos datasets para entrenar el modelo de clasificación:

- **MNIST**:
    - 28x28 imágenes en escala de grises
    - 24 clases
    - [![MNIST](https://img.shields.io/badge/Dataset-MNIST-blue)](https://www.kaggle.com/datasets/datamunge/sign-language-mnist/data)

- **Spanish Sign Language Alphabet (Static)**:
    - 28x28 imágenes en escala de grises
    - 19 clases
    - [![SSLAS](https://img.shields.io/badge/Dataset-SSLAS-blue)](https://www.kaggle.com/datasets/kirlelea/spanish-sign-language-alphabet-static)


## Desempeño del Modelo

El modelo de clasificación alcanzó una precisión del 97.89% en el conjunto de datos de prueba. Se utilizó una red neuronal convolucional (CNN) con 3 capas convolucionales y 2 capas densas.

### Graficas de desempeño

![[Grafica de Accuracy]](data/imgs/01%20AccuracyCurve.png)

![[Grafica de Loss]](data/imgs/02%20LossCurve.png)

![[Matriz de Confusion]](data/imgs/03%20ConfusionMatrix.png)


### Estructura del Código

1. **Importación de Librerías**:
    ```python
    import cv2
    import time
    import mediapipe as mp
    import numpy as np
    from matplotlib import pyplot as plt
    from tensorflow import keras
    import os
    import warnings
    ```

2. **Configuración de Entorno**:
    ```python
    warnings.filterwarnings("ignore")
    os.environ['GLOG_minloglevel'] = '2' 
    os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'
    ```

3. **Funciones Principales**:
    - `draw_hand_landmarks`: Dibuja los puntos de referencia y conexiones de la mano en el frame capturado.
    - `getLetter`: Mapea el resultado del modelo a la letra correspondiente.
    - `capture_frames`: Captura frames de la cámara, procesa los datos, clasifica los gestos y guarda las letras reconocidas.

4. **Carga del Modelo**:
    ```python
    model = keras.models.load_model('./models/model3.h5')
    ```

5. **Inicialización de MediaPipe Hands**:
    ```python
    mp_hands = mp.solutions.hands
    hands = mp_hands.Hands(max_num_hands=1)
    ```

6. **Ejecución del Programa**:
    ```python
    capture_frames(hands, model, 'out/')
    ```

### Funcionalidades

- **Detección de Manos**: Utiliza MediaPipe para detectar los puntos de referencia de las manos en tiempo real.
- **Clasificación de Gestos**: Usa un modelo preentrenado para clasificar los gestos en letras de la lengua de señas.
- **Interacción en Tiempo Real**: Permite formar palabras con los gestos reconocidos y guardarlas en un archivo de texto.
- **Visualización**: Muestra el video en tiempo real con las letras reconocidas y el tiempo transcurrido.

### Ejecución

Para ejecutar el proyecto, asegúrate de tener una cámara conectada a tu computadora y ejecuta el script principal. El programa abrirá una ventana de video que mostrará los gestos reconocidos y las letras correspondientes.

![Ejecución del Proyecto](data/imgs/04%20Funcionamiento.png)


### Notas

- La clasificación se realiza cada 90 frames para evitar clasificaciones erróneas debido a movimientos rápidos.
- Las letras 'Q' y 'O' tienen funciones especiales: 'Q' para borrar la última letra y 'O' para añadir un espacio.
- La letra 'B' se usa para guardar el texto reconocido en un archivo.


### Desempeño del Modelo

El modelo de clasificación alcanzó una precisión del 97.89% en el conjunto de datos de prueba. Se utilizó una red neuronal convolucional (CNN) con 3 capas convolucionales y 2 capas densas.

### Video de Demostración

Puedes ver un video de demostración del proyecto en el siguiente enlace:


### Contribuciones

Si deseas contribuir a este proyecto, por favor realiza un fork del repositorio y envía tus pull requests.

### Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

---

Espero que este README proporcione una visión clara y concisa de cómo funciona el proyecto y cómo puedes ejecutarlo y contribuir a él.