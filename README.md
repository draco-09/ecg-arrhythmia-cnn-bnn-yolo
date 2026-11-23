# Clasificación de Arritmias Cardíacas en Imágenes ECG: Comparativa entre Red Híbrida (MobileNetV2+CNN), BNN-2D y YOLO11n-cls

Este repositorio contiene el código fuente reproducible, la partición estratificada y los resultados experimentales multi-semilla para la evaluación comparativa de tres paradigmas de aprendizaje profundo aplicados a imágenes de electrocardiogramas (ECG) de 3 clases (*Normal Person*, *Abnormal Heartbeat* e *History of MI*).

## 📁 Estructura del Repositorio

```text
ecg-arrhythmia-cnn-bnn-yolo/
├── notebooks/
│   └── comparativa_ecg_cnn_bnn_yolo.ipynb   # Cuaderno principal ejecutado en Google Colab
├── utils/
│   └── OP.py                                # Operadores de binarización XNOR-Net
├── results/
│   ├── resultados_hybrid_5_semillas.csv     # Métricas por semilla (Modelo Híbrido)
│   ├── resultados_bnn_5_semillas.csv        # Métricas por semilla (BNN-2D)
│   └── resultados_yolo_5_semillas.csv       # Métricas por semilla (YOLO11n-cls)
├── requirements.txt                         # Dependencias de Python
└── README.md
```

## 📊 Conjunto de Datos

Se empleó el conjunto de datos público balanceado de 513 imágenes ECG (171 imágenes por clase), disponible en Mendeley Data:
* **Fuente:** A. Ray, *"ECG Dataset for Heart Condition Classification,"* Mendeley Data, V2, 2024. DOI: `10.17632/xw9sd3btcs.2`
* **Partición estratificada única (`random_state=42`):** 70% Entrenamiento (357 imágenes), 25% Prueba (129 imágenes) y 5% Validación (27 imágenes).

## 📈 Resumen de Resultados (5 Semillas: 42, 101, 202, 303, 404)

| Arquitectura | F1-Macro (Media ± DE) | Accuracy (Media ± DE) | Tiempo Train [s] | Latencia [ms/img] |
| :--- | :---: | :---: | :---: | :---: |
| **Híbrido (MobileNetV2 + CNN)** | **0.9674 ± 0.0193** | **96.74% ± 1.93%** | 298.80 ± 8.23 | 4.3536 ± 2.7556 |
| **YOLO11n-cls** | 0.7332 ± 0.0515 | 75.66% ± 3.86% | **62.17 ± 11.79** | 10.9820 ± 1.7732 |
| **ECG_XNOR_2D (BNN)** | 0.6560 ± 0.1419 | 68.99% ± 11.09% | 95.78 ± 0.41 | **0.3921 ± 0.1200** |

## 🚀 Instrucciones de Ejecución

1. Clonar este repositorio:
   ```bash
   git clone https://github.com/draco-09/ecg-arrhythmia-cnn-bnn-yolo
   ```
2. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
3. Abrir `notebooks/comparativa_ecg_cnn_bnn_yolo.ipynb` en **Google Colab** (con aceleración GPU T4), ajustar la ruta de Google Drive donde se aloja la carpeta `dataset_balanceado` y ejecutar todas las celdas en orden secuencial.
