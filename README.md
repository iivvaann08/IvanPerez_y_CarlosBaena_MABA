
# Python en práctica: Red de Centros Deportivos (MABA)

Este repositorio contiene la resolución de la **Sesión 2** de la materia de Python en práctica, donde se analiza la actividad de una red de seis centros deportivos en Madrid, Barcelona y Valencia, integrando datos de asistencia con variables meteorológicas históricas de la API de Open-Meteo.

## 📋 Estructura del Proyecto y Fuentes

El proyecto integra tres fuentes de datos principales:
1. **`actividad.csv`**: Contiene el registro de 504 sesiones deportivas de 14 días (del 1 al 14 de septiembre de 2026) para 6 centros, detallando actividad, turno, duración, plazas y visitas.
2. **`centros.xlsx`**: Catálogo con el identificador del centro, nombre, ciudad y coordenadas geográficas de referencia.
3. **API de Open-Meteo**: Datos de temperatura máxima, mínima y precipitación diaria para cada una de las tres ciudades.

## 🚀 Pasos para ejecutar el proyecto en Colab

1. Abre el notebook `practica_centros.ipynb` en Google Colab.
2. Sube simultáneamente los archivos `actividad.csv` y `centros.xlsx` de la carpeta `datos` cuando la celda de carga de archivos lo solicite.
3. Ejecuta las celdas en orden. El script descargará automáticamente los datos del clima histórico y generará las exportaciones en la carpeta `salidas/`.

## 📊 Resultados obtenidos

El análisis genera los siguientes entregables exportados en la carpeta `salidas/`:
- `actividad_preparada.csv`: Dataset unificado con información de sesiones, centros y clima diario.
- `meteo_diaria.csv`: Registro limpio del clima por ciudad y día.
- `resumen_centros.csv`: Total de visitas acumuladas por centro deportivo.
- `ocupacion_por_turno.csv`: Porcentaje medio de ocupación por actividad y turno.
- `visitas_diarias.png` y `.csv`: Gráfico y datos de la evolución de visitas diarias por ciudad.
- `ocupacion_actividad.png`: Comparativa visual de ocupación (turno mañana vs. tarde) por deporte.

## 🤖 Decisiones de Revisión con IA

| Decisión | Consulta y sugerencia | Qué se aceptó o cambió | Comprobación y resultado |
| :--- | :--- | :--- | :--- |
| **1. Validación de Uniones (Merge)** | Se consultó sobre la propuesta de unir la meteorología únicamente por la columna `ciudad`. La IA advirtió que esto generaba un producto cartesiano (multiplicación de filas), duplicando las sesiones por cada uno de los 14 días. | Se rechazó la sugerencia de unión simple y se implementó la unión compuesta por `['ciudad', 'fecha']`. | La comprobación de filas final mantuvo estrictamente las 504 sesiones originales sin duplicaciones indeseadas. |
| **2. Clasificación de ocupación eficiente** | Se solicitó una alternativa optimizada para clasificar los niveles de ocupación de forma vectorizada en pandas. | Se evaluó el uso de `pd.cut` frente a `.apply()`. Finalmente se optó por mantener la legibilidad de `.apply(clasificar_ocupacion)` por fines didácticos. | Se verificó visualmente en la cabecera que los umbrales de clasificación (Baja, Media, Alta) se asignaron correctamente. |

---
**Autores:** Iván Pérez y Carlos Baena
