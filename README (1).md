# 📡 TelecomX — Análisis de Evasión de Clientes (Churn)

> Proyecto de análisis de datos orientado a identificar los factores que impulsan la cancelación de clientes en TelecomX LATAM, como base para modelos predictivos y estrategias de retención.

---

## 📋 Descripción del Proyecto

TelecomX enfrenta una alta tasa de cancelaciones que compromete sus ingresos recurrentes. Este proyecto aplica un pipeline completo de **ETL + EDA** sobre 7 267 registros de clientes para descubrir patrones de evasión y proporcionar recomendaciones accionables al negocio.

---

## 🗂️ Estructura del Repositorio

```
telecomx-churn/
├── TelecomX_Data.json               # Dataset fuente (7 267 registros)
├── TelecomX_Churn_Analysis.ipynb    # Notebook principal con todo el análisis
└── README.md                        # Este archivo
```

---

## 🔄 Pipeline del Análisis

```
JSON (API)  ──►  Extracción  ──►  Transformación  ──►  EDA  ──►  Informe
               json_normalize     limpieza / ETL    visualizaciones   insights
```

### 1. 📌 Extracción
- Carga del archivo JSON simulando una llamada a API con `json.load()`
- Aplanamiento de la estructura anidada con `pd.json_normalize`

### 2. 🔧 Transformación
- Estandarización de columnas a `snake_case` con manipulación de strings (`str.lower`, `str.replace`)
- Exploración de tipos de datos con `df.info()` y `df.dtypes`
- Detección de nulos, duplicados e inconsistencias
- Conversión de `total_charges` a numérico e imputación de valores faltantes
- Creación de variable binaria `churn_flag` (0 = No, 1 = Sí)

### 3. 📊 Carga y EDA
- Estadísticas descriptivas con `df.describe()`
- Distribución global del Churn (barras + pie chart)
- Tasa de Churn por 10 variables categóricas (contrato, método de pago, servicio de internet, etc.)
- Distribución de variables numéricas (antigüedad, cargos) segmentada por Churn
- **Regresión lineal con NumPy** — antigüedad vs. cargo total
- Análisis de servicios adicionales como factores de retención
- Heatmap de correlaciones numéricas

### 4. 📄 Informe Final
Informe en Markdown integrado al notebook con introducción, hallazgos clave, conclusiones y recomendaciones estratégicas priorizadas.

---

## 📊 Principales Hallazgos

| Factor | Observación |
|--------|-------------|
| **Tasa de Churn global** | ~26–27% de los clientes cancelaron |
| **Tipo de contrato** | Mes a mes supera el 40% de Churn; contratos anuales < 5% |
| **Servicio de internet** | Fibra óptica presenta la mayor tasa de evasión (~42%) |
| **Antigüedad** | Clientes que cancelan tienen media de ~10 meses vs. ~37 meses de los que permanecen |
| **Método de pago** | Cheque electrónico concentra ~45% de Churn |
| **Servicios adicionales** | OnlineSecurity y TechSupport reducen significativamente la evasión |
| **Senior Citizens** | Tasa de Churn ~10 pp mayor que el resto de clientes |

---

## 🛠️ Tecnologías y Librerías

| Librería | Uso |
|----------|-----|
| `Python 3.x` | Lenguaje principal |
| `pandas` | Manipulación y limpieza de datos |
| `numpy` | Cálculos numéricos y regresión lineal |
| `matplotlib` | Visualizaciones estáticas |
| `json` | Carga del dataset desde archivo/API |

---

## ▶️ Cómo Ejecutar

1. Clona o descarga este repositorio
2. Asegúrate de tener instaladas las dependencias:
   ```bash
   pip install pandas numpy matplotlib
   ```
3. Coloca `TelecomX_Data.json` en el mismo directorio que el notebook
4. Abre el notebook y ejecuta las celdas en orden:
   ```bash
   jupyter notebook TelecomX_Churn_Analysis.ipynb
   ```

---

## 💡 Recomendaciones Estratégicas

| Prioridad | Acción |
|-----------|--------|
| 🔴 Alta | Descuentos para migrar contratos M2M a contratos anuales en el primer trimestre |
| 🔴 Alta | Programa de onboarding intensivo durante los primeros 12 meses |
| 🟡 Media | Revisar propuesta de valor y precios de Fibra Óptica |
| 🟡 Media | Upselling de OnlineSecurity y TechSupport como paquete de retención |
| 🟢 Baja | Incentivar pago automático con descuento mensual |
| 🟢 Baja | Programa dedicado para Senior Citizens con soporte preferencial |

---

## 🚀 Próximos Pasos

Con las variables identificadas en este análisis, el equipo de Data Science puede avanzar hacia:

- Modelos de clasificación supervisada: **Logistic Regression**, **Random Forest**, **XGBoost**
- Variable objetivo: `churn_flag`
- Features principales: `contract`, `tenure`, `internet_service`, `monthly_charges`, `payment_method`

---

*Proyecto desarrollado como parte del programa de análisis de datos — TelecomX LATAM*
