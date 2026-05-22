# Clase 3 — Reducción de Dimensionalidad: Extracción y Visualización

Bienvenido al repositorio de la **Clase 3** de la materia **Reconocimiento de Patrones en Bioinformática**. En esta sesión, abordamos el problema $p \\gg n$ desde una perspectiva diferente: en lugar de seleccionar variables originales, proyectamos el espacio de alta dimensión a uno de menor dimensión, combinando las variables para resumir la información.

Este enfoque es fundamental en bioinformática cuando la señal biológica está distribuida en programas de expresión o módulos de genes co-regulados.

## Objetivos de aprendizaje

Al finalizar esta clase, serás capaz de:

  * **Diferenciar Paradigmas:** Distinguir conceptualmente entre **selección** (mantener variables originales) y **extracción** (crear nuevas combinaciones).
  * **Dominar PCA:** Aplicar el Análisis de Componentes Principales entendiendo *scores*, *loadings*, varianza explicada y el uso del *scree plot* para determinar el "codo" de la señal.
  * **Visualización No Lineal:** Implementar **t-SNE** y **UMAP**, comprendiendo parámetros críticos como la `perplexity` y la preservación de estructuras locales vs. globales.
  * **Análisis Single-Cell:** Aplicar estas técnicas a un pipeline real, como la exploración de datasets de tipo PBMC (células mononucleares de sangre periférica).

## Estructura del Repositorio

  * [**`Clase3_Reduccion_de_Dimensionalidad.ipynb`**](https://drive.google.com/file/d/1AwfFpsLga7C61pdv57ZNHGNmCOyl1s26/view?usp=sharing): Notebook práctico con simulaciones de datos ómicos y aplicaciones sobre los datasets *Digits* y *PBMC sintético*.
  * **`bibliografia_clase3.md`**: Referencias a textos fundamentales como *The Elements of Statistical Learning* y artículos clave sobre UMAP y t-SNE.

## Cómo ejecutar el material

Para garantizar que el entorno cuente con todas las dependencias necesarias (incluyendo `umap-learn`), sigue estas opciones:

### Opción A: Google Colab (Recomendado)

> ### Abrir el notebook utilizando el enlace citado a continuación para aprovechar el entorno de Google Colab preconfigurado con todas las dependencias necesarias:
> 
> [**`Clase3_Reduccion_de_Dimensionalidad.ipynb`**](https://drive.google.com/file/d/1AwfFpsLga7C61pdv57ZNHGNmCOyl1s26/view?usp=sharing)

### Opción B: Ejecución Local

Si prefieres trabajar localmente, asegúrate de instalar la biblioteca para UMAP además del stack científico estándar:

``` bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy umap-learn

```
