 # lie-to-me-test
Hay que instalar: 
- [Python 3](https://algoritmos7540-rw.tk/python)
- [Tensorflow](https://www.tensorflow.org/install/install_windows)
- OpenCV 3: [Windows](https://pypi.python.org/pypi/opencv-python) o [Mac, Linux y RaspberryPi](https://www.pyimagesearch.com/opencv-tutorials-resources-guides/)

## MNIST Tutorial
Para correr los ejemplos del [tutorial de MNIST de Tensorflow](https://www.tensorflow.org/tutorials/layers):
```
python ./mnist_tutorial/mnist_beginner.py
python ./mnist_tutorial/mnist_deep.py
```

## Grabar video

### Grabar como secuencia de imágenes
1. Modificar en el archivo `capture_frames.py` la carpeta en donde querés que se te guarden las fotos.
La carpeta **debe existir**.
2. Correr `capture_frames.py`.
Las imágenes van a tener el formato `YYYY-MM-dd hh:mm:ss.ms`

## CNN Inception

### Reentrenamiento
Para reentrenar la última capa de la red Inception con tus propias fotos:

1. Poné tus fotos en la carpeta `cnn/photos`.
Tenés que crear dentro de `cnn/photos` una carpeta por cada categoría que quieras tener y dentro de esas carpetas las fotos.

2. Corré el comando:
```
python ./cnn/retrain.py --bottleneck_dir=./cnn/bottleneck --model_dir=./cnn/inception --output_graph=./cnn/retrained_graph.pb --output_labels=./cnn/retrained_labels.txt --image_dir ./cnn/photos
```

### Clasificación de imágenes real time
Clasifica los frames.

1. Reentrená la red
2. Corré `./cnn/real_time.py`

### Clasificación de imágenes
Clasifica todas las imágenes en una carpeta.

1. Reentrená la red
2. Modificá en el archivo `from_file.py` la carpeta en donde están las fotos.
3. Corré `./cnn/from_file.py` 



## RCNN Inception

### Reentrenamiento

#### Cada video es de una clase en particular
Para casos donde todo el video se clsifica de una clase y no pedazos de él.

1. Tenés que crear dentro de `rcnn/videos` una carpeta por cada categoría que quieras tener y dentro de esas carpetas los videos de esa categoría.

2. Correr el comando `...`.


#### Especificar qué momentos del video son de una clase
Para casos donde el video tiene partes de distintas clases.
Acá importa para la clasificación cómo van apareciendo las clases y sus tiempos.

1. Tenés que ubicar los videos en la carpeta `rcnn/videos` y crear un archivo llamado `rcnn/classes.py` que defina el diccionario `class_per_frame` con el siguiente formato:
```
"nombre_del_video": {
	"clase": [
		{ "start":  "YYYY-MM-dd hh:mm:ss.ms",
		  "end": "YYYY-MM-dd hh:mm:ss.ms" }
	]
}
```

Nota: es de suma importancia los rangos de los timestamps. Pues si no se tiene en cuenta algun frame el mismo va a ser clasificado con clase None.
2. Correr el comando `...`.


### Clasificación de un video real time
Clasifica cada 4 segundos (40 frames), el frame que se está viendo.

1. Reentrená la red
2. 

### Clasificación de un video
Clasifica los distintos frames del video.

1. Reentrená la red
2. 
