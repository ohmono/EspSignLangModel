# Repositorio de Detección y Captura de Gestos de Manos

## Descripción

Este repositorio contiene el código fuente para un proyecto que implementa un sistema de detección y captura de gestos de manos en tiempo real. El sistema utiliza la biblioteca MediaPipe para la detección de manos y OpenCV para el procesamiento de imágenes.

## Funcionalidades

- Detección de manos en tiempo real.
- Captura de imágenes de las manos detectadas.
- Almacenamiento de las imágenes capturadas en carpetas según el gesto detectado.
- Visualización de información sobre los gestos detectados en la interfaz gráfica.

## Requisitos

- Python 3.7 o superior
- mediapipe
- opencv-python
- tensorflow
- imbalanced-learn
- scikit-learn
- matplotlib
- scikit-image

## Conceptualización

El código implementa un proceso técnico para la detección y captura de gestos de manos en tiempo real. Se basa en el procesamiento de imágenes, analizando los histogramas de los canales de color, transformando la imagen de RGB a BGR y normalizando los valores de los canales. Luego, emplea el modelo de detección de manos de MediaPipe para identificar gestos en los frames capturados por la cámara. Finalmente, se realiza la captura y almacenamiento de los gestos detectados en carpetas correspondientes en escala de grises.

## Próximos Pasos

- Implementar la detección de más gestos.
- Mejorar la precisión de la detección de manos.
- Desarrollar una interfaz gráfica más intuitiva.


## Licencia

Este proyecto está licenciado bajo la licencia MIT.

## Contacto

Si tiene alguna pregunta o comentario, no dude en contactarme a través de la sección de issues del repositorio.