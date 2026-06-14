
# Trabajo Práctico - Urban Flow

<p align="center">
  <img src="https://crup.org.ar/wp-content/uploads/2026/02/UGR-LOGO-1.png" alt="Logo Universidad" width="200"/>
</p>

---

## Materia

Herramientas de Software para el Análisis de Datos - 2026

---

## Integrantes

- Cristian Vera
- Darío Verdún
- Sergio Sánchez
- Eduardo Saldívia

---

## Introducción General

Urban Flow es un proyecto orientado al análisis de infracciones de velocidad registradas mediante radares urbanos y sistemas automáticos de captura de evidencia visual.

El trabajo práctico se desarrolla de manera incremental mediante distintos sprints, incorporando progresivamente nuevas etapas de procesamiento, análisis y validación de datos.

---

# Sprint 1 — Procesamiento y análisis de datos

## Objetivo

Durante el Sprint 1 se desarrolló un flujo de trabajo para el análisis de un dataset de infracciones de velocidad, aplicando procesos de limpieza, normalización, transformación y visualización de datos.

## Actividades realizadas

- Organización y configuración del repositorio en GitHub.
- Implementación de flujo colaborativo mediante Git y ramas.
- Creación de estructura de directorios del proyecto.
- Limpieza y normalización de datos.
- Tratamiento de valores nulos y outliers.
- Generación de métricas y visualizaciones estadísticas.
- Desarrollo de la clase `FineAnalyzer`.
- Exportación del dataset procesado.

El resultado de este sprint fue la generación de un dataset limpio y estructurado, utilizado posteriormente como base para el Sprint 2.

---

# Sprint 2 — Procesamiento de imágenes y evidencia visual

## Objetivo

El objetivo del Sprint 2 es desarrollar un sistema capaz de relacionar registros administrativos de infracciones con evidencia visual obtenida mediante cámaras urbanas.

## Introducción

Los radares urbanos generan automáticamente multas y, simultáneamente, cámaras asociadas capturan imágenes que actúan como evidencia visual de las infracciones detectadas.

Sin embargo:

- No todas las multas poseen imágenes asociadas.
- No todas las imágenes corresponden correctamente a una infracción.
- Pueden existir errores de detección o inconsistencias.

A partir del dataset procesado en el Sprint 1 y un dataset de imágenes, se busca determinar qué multas poseen evidencia visual válida.

## Actividades del Sprint 2

- Reutilización del dataset procesado en el Sprint 1.
- Creación de la rama `Sprint_2`.
- Descarga y organización del dataset de imágenes.
- Procesamiento y análisis de imágenes.
- Extracción automática de patentes mediante OCR.
- Relación entre imágenes y registros de infracciones.
- Validación de evidencia visual.

---

## Resultados obtenidos

Durante el Sprint 2 se logró relacionar información administrativa de multas con evidencia visual mediante procesamiento de imágenes y OCR.

### Métricas principales

| Métrica | Resultado |
|---|---:|
| Multas con imágenes relacionadas | 754 |
| Multas sin evidencia visual asociada | 959 |
| Imágenes sin coincidencia con el dataset | 66 |
| Multas pendientes de pago | 430 |
| Multas pendientes con imágenes relacionadas | 182 |
| Promedio de coincidencia OCR | 94.6% |

---

# Sprint 3 — Persistencia y explotación de datos

## Objetivo

El objetivo del Sprint 3 es integrar los datasets generados en los sprints anteriores dentro de una base de datos relacional, permitiendo centralizar la información, optimizar las consultas y facilitar futuros análisis.

## Introducción

Luego de completar las etapas de limpieza de datos, procesamiento de imágenes y validación de evidencia visual, el proyecto requiere una solución que permita almacenar y gestionar la información de manera estructurada y persistente.

Para ello, se utilizarán los datasets generados durante los Sprint 1 y Sprint 2 como fuente de datos para la construcción de un modelo relacional que facilite la consulta, análisis y explotación de la información.

## Actividades del Sprint 3

- Creación de la rama `Sprint_3`.
- Verificación y reutilización de datasets generados en los sprints anteriores.
- Diseño del modelo de datos relacional.
- Creación de la base de datos del proyecto.
- Definición de tablas, claves primarias y relaciones.
- Migración de datos desde archivos CSV y JSON.
- Validación de integridad y consistencia de la información.
- Desarrollo de consultas para análisis y explotación de datos.

---

## Resultados obtenidos

Durante el Sprint 3 se logró consolidar toda la información generada en los sprints anteriores mediante una arquitectura compuesta por una base de datos relacional y una base de datos vectorial.

### Métricas principales

| Métrica | Resultado |
|---|---:|
| Vehículos almacenados | 754 |
| Multas registradas | 754 |
| Evidencias visuales | 754 |
| Radares identificados | 3 |
| Vectores almacenados | 754 |
| Porcentaje de multas con evidencia | 100% |

### Consultas realizadas

- Top 10 de vehículos con mayor cantidad de multas.
- Identificación de radares con mayor volumen de infracciones.
- Consulta de vehículos reincidentes por período.
- Obtención de estadísticas de evidencia visual.
- Recuperación de información de vehículos mediante búsqueda por similitud de imágenes.

### Base de Datos Vectorial

Se implementó una base de datos vectorial denominada `patente_vectorial`, utilizando embeddings generados mediante OpenCLIP.

Cada imagen asociada a una evidencia fue transformada en un vector numérico y vinculada con la patente correspondiente, permitiendo búsquedas por similitud visual y recuperación automática de información desde la base relacional.

---

# Conclusión General

El proyecto Urban Flow permitió integrar distintas disciplinas vinculadas al análisis de datos, procesamiento de imágenes y gestión de bases de datos.

A lo largo de los tres sprints se desarrolló una solución capaz de:

- Procesar y depurar grandes volúmenes de datos.
- Analizar imágenes y extraer información mediante OCR.
- Relacionar evidencia visual con registros administrativos.
- Diseñar e implementar una base de datos relacional utilizando SQLAlchemy.
- Construir una base de datos vectorial para búsquedas por similitud visual.
- Recuperar información completa de un vehículo a partir de una imagen.

La integración entre datos estructurados y evidencia visual permitió construir una solución escalable que demuestra el potencial de combinar herramientas de Ciencia de Datos, Visión por Computadora y Bases de Datos Modernas para resolver problemas reales relacionados con la gestión y fiscalización del tránsito.
---
