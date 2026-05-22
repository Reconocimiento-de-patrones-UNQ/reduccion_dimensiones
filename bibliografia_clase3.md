# Bibliografía — Clase 3: Reducción de dimensionalidad

**Maestría en Bioinformática y Biología de Sistemas — UNQ**
**Reconocimiento de Patrones en Bioinformática**

---

## Lectura previa recomendada (30 min)

- **Capítulo 14.5 de "The Elements of Statistical Learning"** (Hastie, Tibshirani, Friedman) — *Principal Components, Curves and Surfaces*.
  - PDF gratuito: https://hastie.su.domains/ElemStatLearn/

- **Becht, E. et al. (2019).** *Dimensionality reduction for visualizing single-cell data using UMAP.* **Nature Biotechnology 37(1), 38–44.** El paper que estableció UMAP como estándar en single-cell.

---

## Profundización por tema

### PCA

- **Ringnér, M. (2008).** *What is principal component analysis?* Nature Biotechnology 26(3), 303–304. Introducción breve para biólogos. 2 páginas.

- **Lê, S., Josse, J. & Husson, F. (2008).** *FactoMineR: An R Package for Multivariate Analysis.* Para PCA con extensiones (factor analysis, MFA).

### t-SNE

- **van der Maaten, L. & Hinton, G. (2008).** *Visualizing data using t-SNE.* Journal of Machine Learning Research 9, 2579–2605. El paper original.

- **Wattenberg, M., Viégas, F. & Johnson, I. (2016).** *How to Use t-SNE Effectively.* https://distill.pub/2016/misread-tsne/
  **Lectura obligatoria.** Interactivo. Muestra todos los errores de interpretación comunes.

### UMAP

- **McInnes, L., Healy, J. & Melville, J. (2018).** *UMAP: Uniform Manifold Approximation and Projection for Dimension Reduction.* arXiv:1802.03426. El paper original (técnico).

- **Coenen, A. & Pearce, A. (2019).** *Understanding UMAP.* https://pair-code.github.io/understanding-umap/
  Equivalente interactivo al de t-SNE de distill. Excelente.

### Single-cell aplicaciones

- **Tutorial Scanpy:** https://scanpy.readthedocs.io/en/stable/tutorials.html
  El pipeline canónico PCA → vecinos → UMAP → Leiden clustering.

---

## Videos recomendados (verificados)

- **StatQuest — Principal Component Analysis (PCA), Step-by-Step** (~22 min)
  https://www.youtube.com/watch?v=FgakZw6K1QQ
  La mejor explicación visual de PCA con SVD.

- **StatQuest — PCA main ideas in only 5 minutes!!!** (~5 min)
  https://www.youtube.com/watch?v=HMOI_lkzW08
  Versión rápida si tenés poco tiempo.

- **StatQuest — PCA Practical Tips** (~8 min)
  https://www.youtube.com/watch?v=oRvgq966yZg
  Sobre escalado, número de PCs, etc.

- **StatQuest — t-SNE, Clearly Explained** (~12 min)
  https://www.youtube.com/watch?v=NEaUSP4YerM
  Cómo funciona t-SNE internamente.

- **Leland McInnes (autor de UMAP) — UMAP: Uniform Manifold Approximation and Projection for Dimension Reduction** (SciPy 2018, ~30 min)
  https://www.youtube.com/watch?v=nq6iPZVUxZU
  Charla técnica del propio autor. Para entender la base teórica.

- **t-SNE vs UMAP** (~7 min)
  https://www.youtube.com/watch?v=4NlvatkpV3s
  Comparación con visualizaciones.

---

## Recursos técnicos

### Documentación

- `sklearn.decomposition.PCA`: https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html
- `sklearn.manifold.TSNE`: https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html
- `umap-learn`: https://umap-learn.readthedocs.io/en/latest/

### Datasets para practicar

- **PBMC 3k** (single-cell de 10x Genomics, ~3000 células): https://scanpy.readthedocs.io/en/stable/generated/scanpy.datasets.pbmc3k.html
- **MNIST** (digits): clásico para visualizar t-SNE/UMAP

### Variantes y alternativas

- **PHATE** (https://github.com/KrishnaswamyLab/PHATE): preserva mejor trayectorias (útil para single-cell evolutivo).
- **Diffusion maps**: alternativa basada en cadenas de Markov.
- **Kernel PCA** (`sklearn.decomposition.KernelPCA`): PCA no lineal con kernel trick.

---

## FAQ pedagógico

**1. ¿Cuándo PCA y cuándo t-SNE/UMAP?**
- PCA: análisis cuantitativo, pre-procesamiento (alimentar otro algoritmo), interpretabilidad por loadings.
- t-SNE/UMAP: visualización exploratoria, clustering en single-cell.

**2. ¿Por qué siempre se hace PCA antes de UMAP/t-SNE?**
- Reduce ruido (las PCs bajas suelen ser ruido).
- Acelera muchísimo el cálculo de vecinos.
- Convención: 30–50 PCs antes de t-SNE/UMAP es el estándar.

**3. ¿Puedo usar coordenadas UMAP como features para predecir?**
- **No, casi nunca.** Las coordenadas UMAP no se generalizan bien a datos nuevos. Para predicción usá las PCs.

**4. ¿Por qué el resultado de t-SNE cambia entre corridas?**
- t-SNE tiene inicialización aleatoria y es estocástico. Para reproducibilidad fijá `random_state`. UMAP es más estable.

**5. ¿Qué hago si los clusters están bien en UMAP pero solapados en PCA?**
- Es esperable: PCA captura la estructura lineal global; UMAP captura no linealidades locales. Ambas vistas son válidas y complementarias.

**6. ¿Necesito escalar antes de PCA?**
- Sí, si las variables tienen escalas muy distintas (cm vs kg). Si todas son de la misma naturaleza (expresión génica log-normalizada), se puede omitir, pero suele recomendarse.
