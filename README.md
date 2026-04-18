# 🎬 Análisis de Sentimiento en IMDB con NLP y Embeddings

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![NLP](https://img.shields.io/badge/NLP-Sentiment%20Analysis-green)](https://en.wikipedia.org/wiki/Sentiment_analysis)

### 👥 Colaboradores: **Emmanuel Gonzalez Gomez y Dalma Márquez.**

***

## 📝 Descripción General

Clasificación binaria de sentimientos (positivo/negativo) en 50,000 reseñas de películas del portal IMDB, comparando enfoques tradicionales de NLP (TF-IDF) con representaciones semánticas densas (Word2Vec embeddings). Se evaluaron múltiples modelos de clasificación para determinar cuál combinación de representación y algoritmo ofrece el mejor rendimiento.

***

## 📁 Estructura del Proyecto

La organización de los archivos en este repositorio es la siguiente:

```
imdb-sentiment-analysis-nlp/
├── IMDB_Sentiment_Analysis.ipynb        # Notebook principal con EDA, preprocessing y modelos
├── requirements.txt                     # Dependencias de Python para reproducir el entorno
├── LICENSE                              # Licencia MIT
├── .gitignore                           # Archivos y carpetas ignorados por Git
└── README.md                            # Este archivo
```

***

## 📊 Descripción del Dataset

El dataset **IMDB Dataset of 50K Movie Reviews** contiene 50,000 reseñas de películas etiquetadas como positivas o negativas.

- **Tamaño:** 50,000 reseñas
- **Distribución:** 25,000 positivas / 25,000 negativas (perfectamente balanceado)
- **Columnas:**
  - `review`: texto completo de la reseña
  - `sentiment`: etiqueta ("positive" / "negative")
- **Tipo de problema:** Clasificación binaria de sentimientos

**Fuente:** [IMDB Dataset en Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)

***

## 🚀 Modelos y Representaciones Implementadas

### Representaciones de Texto

| Representación | Tipo | Descripción |
| :--- | :--- | :--- |
| **TF-IDF** | Disperso (sparse) | Ponderación estadística de términos (frecuencia en documento vs rareza en corpus) |
| **Word2Vec** | Denso (dense) | Embeddings semánticos entrenados con Skip-gram sobre el corpus de entrenamiento |

### Modelos de Clasificación Evaluados

| Representación | Modelo | Rendimiento (F1-score) |
| :--- | :--- | :--- |
| **TF-IDF** | Regresión Logística | **0.8955 (⭐ Mejor TF-IDF)** |
| | LinearSVC | 0.8937 |
| | Multinomial Naive Bayes | 0.8688 |
| **Word2Vec** | MLP (Red Neuronal) | **0.8825 (⭐ Mejor Embeddings)** |
| | SVC (RBF) | 0.8810 |
| | Logistic Regression | 0.8720 |
| | Random Forest | 0.8650 |
| | Gaussian Naive Bayes | 0.8210 |

### Conclusión Clave

- **TF-IDF + Regresión Logística** logró el mejor rendimiento general (F1 = 0.8955), demostrando que la representación estadística tradicional es altamente efectiva para textos bien estructurados.
- **Word2Vec + MLP** fue la mejor combinación con embeddings densos (F1 = 0.8825), capturando mejor relaciones semánticas complejas y contextos ambiguos.
- Los **modelos lineales** (Logistic Regression, LinearSVC) se desempeñan mejor con representaciones dispersas (TF-IDF).
- Los **modelos no lineales** (MLP, SVC-RBF) aprovechan mejor las representaciones densas (Word2Vec).

Ambos enfoques son **complementarios**: TF-IDF ofrece simplicidad e interpretabilidad, mientras que Word2Vec aporta robustez semántica.

***

## 🔧 Instalación y Uso

Sigue estos pasos para clonar el repositorio, configurar el entorno y ejecutar el análisis en tu máquina local.

### 1. Clonar el repositorio

Abre tu terminal y ejecuta:
```bash
git clone https://github.com/SebastianDeghi/imdb-sentiment-analysis.git
cd imdb-sentiment-analysis-nlp
```

### 2. Crear y activar un entorno virtual (recomendado)

- En **Windows**:
  ```bash
  python -m venv venv
  venv\Scripts\activate
  ```
- En **macOS/Linux**:
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

### 3. Instalar dependencias

Con el entorno virtual activo, instala los paquetes necesarios:
```bash
pip install -r requirements.txt
```

**Nota:** El archivo `requirements.txt` incluye librerías como `pandas`, `numpy`, `scikit-learn`, `nltk`, `gensim` (Word2Vec), `matplotlib`, `seaborn` y `wordcloud`.

### 4. Ejecutar el notebook

Finalmente, lanza Jupyter Notebook para abrir el archivo principal:
```bash
jupyter notebook IMDB_Sentiment_Analysis.ipynb
```

### 5. (Opcional) Descargar el dataset

El notebook descargará automáticamente el dataset desde Kaggle usando `kagglehub`. Si es la primera vez, asegúrate de tener configuradas tus credenciales de Kaggle.

***

## 📚 Referencias y Recursos

- **Artículo Académico:** Maas, A. L., et al. (2011). *Learning Word Vectors for Sentiment Analysis*. ACL-HLT. [PDF](https://aclanthology.org/P11-1015.pdf)
- **Dataset:** [IMDB Dataset of 50K Movie Reviews en Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)
- **Librerías:** `scikit-learn`, `nltk`, `gensim`, `matplotlib`, `seaborn`

***

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Para más detalles, consulta el archivo [`LICENSE`](LICENSE) en la raíz del repositorio.

***

## 🙏 Agradecimientos

- A **Lakshmi N Pathi** por publicar el dataset en Kaggle.
- A la comunidad de código abierto por las herramientas fundamentales (`scikit-learn`, `nltk`, `gensim`, `pandas`, `numpy`).

***

## 👤 Autor

**Sebastián Deghi**
- GitHub: [@SebastianDeghi](https://github.com/SebastianDeghi)
- LinkedIn: [@sebastian-deghi](https://www.linkedin.com/in/sebastian-deghi/)
- Google Scholar: [@Sebastian E. Deghi](https://scholar.google.com/citations?user=3Nq5hTIAAAAJ&hl=en)