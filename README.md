# Laboratorio 1 — Series de Tiempo

Análisis de series de tiempo sobre el **ingreso de viajeros internacionales a Guatemala** (enero 2009 – junio 2026), a partir de datos mensuales de migración. El proyecto cubre el análisis exploratorio, la preparación de los datos, el modelado de varias series mensuales (SARIMA y modelos alternativos) y un análisis comparativo entre ellas.

Para comparar de forma consistente en todo el período, todo el análisis se trabaja sobre las categorías **Turista + Excursionista**, y la partición para modelar es **70/30 temporal** (respetando el orden cronológico).

## Estructura del repositorio

```
.
├── datos/
│   ├── raw/
│   └── processed/
└── notebooks/
    ├── Eda_Inicial_Completo.ipynb
    ├── splitData/
    │   └── Split_Entrenamiento_Prueba.ipynb
    ├── series/
    │   ├── Mensual_Series_de_Tiempo.ipynb
    │   ├── Regiones_Series_de_Tiempo.ipynb
    │   └── Fronteras_Series_de_Tiempo.ipynb
    └── analisisComparativo/
        └── Regiones.ipynb
```

### Qué contiene cada parte

- **`datos/raw/`** — Los datos tal y como se extrajeron.
- **`datos/processed/`** — Salida del notebook de split: `entrenamiento.csv` (2009-01 a 2021-03) y `prueba.csv` (2021-04 a 2026-06), ya filtrados a Turista + Excursionista y con una columna `Fecha` y una bandera `pandemia`.
- **`Eda_Inicial_Completo.ipynb`** — Exploración del dataset: comportamiento temporal, países y regiones con más viajeros, vías y fronteras, valores faltantes, duplicados, atípicos y estadísticas descriptivas.
- **`splitData/Split_Entrenamiento_Prueba.ipynb`** — Limpieza (filtro de categorías consistentes, `Fecha`, agregar bandera de pandemia) y la partición temporal 70/30 que genera los CSV de `processed/`.
- **`series/`** — Un notebook por categoría. Cada serie se analiza de punta a punta: inicio/fin/frecuencia, gráfico, descomposición, transformación, estacionariedad, elección de parámetros SARIMA, comparación de modelos (SARIMA, Holt-Winters, suavizamiento exponencial simple, seasonal naive, Prophet) y predicción.
- **`analisisComparativo/`** — Compara las series entre sí (estacionalidad, tendencia de crecimiento, volatilidad e impacto de la pandemia) con evidencia estadística.
