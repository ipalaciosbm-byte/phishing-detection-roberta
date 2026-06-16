# phishing-detection-roberta
Fine-tuning de RoBERTa para detección de phishing (TFG)
# Detección de phishing con RoBERTa

Fine-tuning de un modelo **RoBERTa** para la detección automática de correos de *phishing*, planteado como un problema de clasificación binaria supervisada (correo legítimo vs. malicioso). Trabajo de Fin de Grado.

## Resultados

El modelo alcanza un rendimiento muy alto sobre el conjunto de validación no visto:

| Métrica   | Valor   |
|-----------|---------|
| Accuracy  | 99,82 % |
| F1-score  | 0,9984  |
| MCC       | 0,9964  |

## Stack técnico

- **Lenguaje:** Python
- **Deep Learning:** PyTorch, Hugging Face Transformers
- **Modelo base:** RoBERTa (fine-tuning)
- **Métricas y utilidades:** scikit-learn, pandas, NumPy, matplotlib

## Datos

- **Dataset:** Phishing Email Dataset (Kaggle), ~39.154 correos.
- El dataset no se incluye en el repositorio por su tamaño y licencia. Puede descargarse desde Kaggle y colocarse en la ruta esperada por el notebook.

## Metodología

1. **Preprocesado:** limpieza de texto con expresiones regulares, concatenación de asunto y cuerpo del correo.
2. **Tokenización:** tokenizador BPE de RoBERTa, con *padding* y truncado a 512 tokens.
3. **Preparación:** construcción de `DataLoaders` de PyTorch y partición 80/20 (entrenamiento/validación).
4. **Entrenamiento:** optimizador AdamW, *learning rate* 2e-5, *scheduler* lineal, 3 épocas, *batch size* 16.
5. **Evaluación:** Accuracy, F1-score y coeficiente de correlación de Matthews (MCC) sobre el conjunto de validación.

## Estructura del repositorio

```
.
├── README.md
└── deteccion_phishing.ipynb   # notebook completo: preprocesado, entrenamiento y evaluación
```

## Cómo ejecutarlo

El proyecto está pensado para ejecutarse en **Google Colab** (con GPU) o en un entorno local con las dependencias instaladas:

```bash
pip install torch transformers scikit-learn pandas numpy matplotlib
```

Abre `deteccion_phishing.ipynb`, descarga el dataset de Kaggle y ejecuta las celdas en orden.

## Autora

Irene Palacios Barrenechea-Moxó — Grado en Matemáticas
