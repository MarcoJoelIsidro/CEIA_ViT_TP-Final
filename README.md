# Vision Transformers (ViT) - Proyecto Final

Este proyecto fue desarrollado en el marco de la **Especialización en Inteligencia Artificial** de la UBA, para la materia **Vision Transformers**. 

**Integrantes:**
- Kevin Guerra Huamán
- Marco Joel Isidro
- Víctor David Silva

**Docentes:**
- Abraham Rodriguez
- Oksana Bokhonok

## Introducción

El presente proyecto implementa un modelo para la tarea de **image-captioning**, generando descripciones de texto a partir de imágenes. Se utiliza el modelo BLIP (Bootstrapping Language-Image Pre-training), en su variante base, y el dataset **Flickr30k**. El proyecto incluye desde el análisis exploratorio del dataset hasta el entrenamiento, evaluación y visualización de resultados.

## Estructura de Archivos en el Repositorio

```plaintext
CEIA_VIT_TP-FINAL/
│
├── Imagenes_generadas/       # Backup de imágenes generadas
├── results/                   # Resultados obtenidos
│   ├── test_results.json      # Métricas de modelo entrenado
│   ├── training_loss.json     # Perdida durante el entrenamiento
│   └── val_base_results.json  # Métricas en modelo base
│
├── .gitignore                 # Archivos y carpetas ignoradas por git
├── README.md                  # Descripción del proyecto
│
├── TP_Final_ViT.ipynb         # Notebook principal
└── ViT_Informe_Grupo_2.pdf    # Informe final del proyecto
```

## Instalación 
Para clonar el repositorio localmente, dirigirse al directorio deseado y ejecutar:

```python
git clone https://github.com/MarcoJoelIsidro/CEIA_ViT_TP-Final.git
cd PI_Challenge
```
Dentro de este, se encuentra el archivo TP Final ViT.ipynb, el cual contiene el código fuente. Esté fue ejecutado en Google Colab Pro como se indica más adelante. En caso de no contar con esa versión de Google Colab, puede descargar el modelo entrenado en el link que se indica en la sección de entrenamiento.

## Métricas y Resultados Obtenidos

### Métricas Utilizadas
Para evaluar la calidad de las descripciones generadas por el modelo, se utilizaron dos métricas ampliamente reconocidas en tareas de generación de texto a partir de imágenes:

1. **BLEU (Bilingual Evaluation Understudy):**  
   - Evalúa la similitud entre las descripciones generadas por el modelo y las descripciones de referencia humanas.
   - Se basa en el cálculo de coincidencias de n-gramas entre las frases generadas y las de referencia.
   - Proporciona un enfoque de precisión, midiendo qué tan similares son las palabras utilizadas por el modelo en comparación con las descripciones originales.

2. **CIDEr (Consensus-based Image Description Evaluation):**  
   - Diseñada específicamente para tareas de generación de captions.
   - Evalúa la relevancia semántica y el consenso de las palabras clave en las descripciones generadas.
   - Tiene en cuenta la importancia del contexto, priorizando las descripciones que capturan los aspectos más relevantes de la imagen.

### Proceso de Entrenamiento
- El modelo BLIP (variante base) fue entrenado durante **5 épocas** utilizando un conjunto reducido del dataset **Flickr30k** debido a restricciones computacionales. El mismo se puede descargar desde: https://drive.google.com/file/d/1Hio124GdQnn1dleFEzo_Qf_T1qoHJxiS/view?usp=drive_link

- **Hardware:** Se utilizó una GPU **Tesla A100** en Google Colab Pro con 40 GB de VRAM, lo que permitió realizar el fine-tuning del modelo.
- La pérdida durante el entrenamiento disminuyó de **3.4** a **0.5**, mostrando una convergencia estable.

### Resultados
1. **Métricas Globales:**
   - **BLEU:** ~0.233
   - **CIDEr:** ~1.22

   Estas métricas reflejan una buena capacidad del modelo para generar descripciones que capturan detalles relevantes de las imágenes.

2. **Comparación entre Validación y Pruebas:**
   - El modelo mostró un rendimiento ligeramente superior en el conjunto de prueba en comparación con el de validación, lo que indica una adecuada capacidad de generalización a datos no vistos.

3. **Ejemplos de Predicciones:**
   - **Descripción generada:** _"A young boy in an orange shirt playing with a toy car on the floor of a house."_  
   - **Descripción de referencia:** _"A little boy with an orange shirt is riding his blue and white toy car."_
  
<img width="286" alt="image" src="https://github.com/user-attachments/assets/4ea9b3db-ba88-496e-aa07-06ef106336f3">

   Aunque el modelo logró captar aspectos importantes de la imagen, en algunos casos, las descripciones fueron más generales.

## Conclusión

El modelo BLIP base mostró un desempeño satisfactorio en la tarea de generación de captions. Sin embargo, la reducción del dataset y el número limitado de épocas influyeron en la estabilidad de la validación y en la capacidad de generalización a datos más complejos.

