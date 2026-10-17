# Informe de Resultados: Tratamiento de Imagen con OpenCV

**Asignatura:** Percepción Computacional (Inteligencia Artificial)  
**Integrantes:** 
* Carlos Eduardo Riaño Rodríguez
* Bryan Felipe Roa Albarado
**Universidad:** Universidad de Cundinamarca  
**Semana:** 8 - Tratamiento de Imagen

## 📌 Descripción del Proyecto
Este repositorio contiene la solución práctica para el análisis y tratamiento de imágenes utilizando Python y OpenCV en Google Colab. El objetivo es diagnosticar cómo las condiciones de captura (iluminación, enfoque, fondo, perspectiva) afectan la calidad de una imagen y aplicar una corrección técnica justificada.

El objeto de estudio seleccionado fue un **llavero de Spider-Man**, capturado bajo 5 condiciones diferentes.

## 🖼️ Conjunto de Imágenes
1. `referencia.jpg`: Buena iluminación, fondo neutro y enfoque correcto.
2. `oscura.jpg`: Condiciones de baja iluminación.
3. `desenfocada.jpg`: Captura con movimiento (pérdida de nitidez).
4. `fondo_complejo.jpg`: Objeto frente a un paisaje con múltiples texturas.
5. `angulo.jpg`: Cambio de perspectiva y distancia.

## 🛠️ Tecnologías y Herramientas
* **Python 3**
* **OpenCV** (`opencv-python-headless`)
* **NumPy**
* **Matplotlib**
* **Google Colab**

## 📊 Diagnóstico y Métricas
El script calcula automáticamente las siguientes métricas para cada imagen:
* **Resolución y Canales** (`img.shape`)
* **Brillo promedio** (`gris.mean()`)
* **Contraste** (Desviación estándar `gris.std()`)
* **Nitidez** (Varianza del Laplaciano `cv2.Laplacian().var()`)
* **Tamaño de archivo** (Comparativa entre guardar en JPG vs PNG).

## 🩺 Problema Seleccionado y Tratamiento
* **Problema:** La imagen `oscura.jpg` presenta una severa subexposición (bajo brillo y contraste), lo que impide detectar los detalles del objeto.
* **Solución Técnica:** Conversión del espacio de color BGR a HSV, separación del canal de Valor (V) y aplicación de **Ecualización de Histograma** (`cv2.equalizeHist`) sobre dicho canal. Finalmente, se reconstruye la imagen a BGR.
* **Justificación:** Este tratamiento mejora el contraste y la visibilidad de los detalles sin alterar los tonos originales (rojo y azul) del llavero.

## 🚀 Cómo ejecutar el código
1. Abre el archivo `.ipynb` (Notebook) en Google Colab.
2. Ejecuta la primera celda para instalar las dependencias.
3. Ejecuta la celda de carga y sube las 5 imágenes con los nombres exactos indicados en el código.
4. Ejecuta el resto de celdas para ver el diagnóstico, la tabla comparativa, el tratamiento y la comparación visual antes/después.
