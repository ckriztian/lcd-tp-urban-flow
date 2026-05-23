
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

