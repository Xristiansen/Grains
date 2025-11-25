# N-Grains
Introducción

N-Grains es una herramienta de segmentación con generalización superior al nivel humano, aplicable en 2D y 3D. Funciona incluso en imágenes con ruido, desenfoque (an)isotrópico, submuestreo, inversiones de contraste y diferentes tamaños u órdenes de canales.

Además de células y núcleos, puede aplicarse a nanopartículas, permitiendo:

Detectarlas automáticamente en la imagen.

Extraer sus contornos.

Medir tamaño, ancho, largo, área u otras propiedades morfológicas, facilitando la caracterización cuantitativa de muestras.

Para más información, consulta el artículo o la presentación oficial. Tutoriales y ejemplos de fine-tuning están disponibles en la documentación. Para soporte, abre un issue.

Instalación

Puede utilizarse directamente en Google Colab.

# GUI
<img width="380" height="380" alt="image" src="https://github.com/user-attachments/assets/5cc33f32-9215-48be-842b-2de38a38230b" />





<img width="500" height="949" alt="image" src="https://github.com/user-attachments/assets/9e183b9a-6df2-4c56-99b9-999f186f5f8f" />

<img width="500" height="1013" alt="image" src="https://github.com/user-attachments/assets/f920075d-3f38-4c61-82d5-a297613531fe" />


#Mascaras

Parámetros de la segmentación

A continuación se describen los controles incluidos en la interfaz y su efecto sobre la detección y delineado de los objetos en la imagen:

1. Umbral de detección (cellprob_threshold)

Controla la confianza mínima que debe tener el modelo para decidir que una región pertenece a un objeto (por ejemplo, una célula).

Valores bajos (0.0 – 0.2):
El modelo acepta detecciones con baja certeza. Esto genera un mayor número de objetos detectados, pero también puede introducir falsos positivos y ruido.

Valores altos (0.6 – 1.0):
El modelo solo acepta detecciones con alta probabilidad, lo que reduce el número de objetos detectados, pero aumenta la precisión y la fiabilidad de cada detección.

Este parámetro actúa como un filtro sobre la decisión final del modelo.

2. Normalización (tile_norm_blocksize)

Determina la intensidad de la normalización aplicada a la imagen antes de procesarla.
La normalización corrige variaciones de iluminación y contraste entre diferentes zonas de la imagen.

Valores bajos (0.0 – 0.2):
La imagen se utiliza prácticamente sin correcciones. Es útil cuando la iluminación es homogénea y estable.

Valores altos (0.6 – 1.0):
Se aplica una normalización mucho más marcada, lo que puede mejorar la segmentación en imágenes con cambios de brillo o zonas más oscuras.
Sin embargo, una normalización excesiva puede alterar el contraste natural de la imagen.

Este parámetro es especialmente útil cuando las imágenes presentan iluminación irregular.

3. Sensibilidad de bordes (flow_threshold)

Controla la fuerza mínima que deben tener los gradientes o bordes para que el modelo los considere válidos al generar los contornos.

Valores bajos (0.0 – 0.3):
Se aceptan bordes débiles, lo que puede generar contornos más completos y detallados, pero también incrementa la presencia de ruido o bordes poco reales.

Valores altos (0.7 – 1.0):
Solo se aceptan bordes bien definidos. Esto produce contornos más limpios y definidos, aunque puede llevar a perder detalles finos o bordes sutiles.

Este parámetro permite ajustar el balance entre detalle y limpieza en la detección del borde.
#aada 
Sliders de selección de región

La interfaz incluye cuatro barras que permiten definir una región rectangular dentro de la imagen sobre la cual se realiza el análisis. Los valores están en porcentaje (%), por lo que son independientes del tamaño de la imagen.

Top (%): fija el límite superior de la región. Valores mayores recortan más desde arriba.

Bottom (%): fija el límite inferior. Valores menores recortan desde abajo.

Left (%): fija el borde izquierdo. Valores mayores recortan desde la izquierda.

Right (%): fija el borde derecho. Valores menores recortan desde la derecha.

Internamente, cada porcentaje se convierte a coordenadas en píxeles y se filtran los objetos (regionprops) cuyo bounding box quede totalmente dentro del rectángulo definido. Solo esos objetos se muestran, se miden y se incluyen en el histograma.

### CITATION

**cite the Cellpose-SAM [paper](https://www.biorxiv.org/content/10.1101/2025.04.28.651001v1):**
Pachitariu, M., Rariden, M., & Stringer, C. (2025). Cellpose-SAM: superhuman generalization for cellular segmentation. <em>bioRxiv</em>.

**cite the Cellpose 1.0 [paper](https://t.co/kBMXmPp3Yn?amp=1):**  
Stringer, C., Wang, T., Michaelos, M., & Pachitariu, M. (2021). Cellpose: a generalist algorithm for cellular segmentation. <em>Nature methods, 18</em>(1), 100-106.
