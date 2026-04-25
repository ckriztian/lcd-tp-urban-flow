
# CHANGELOG: Proyecto Urban Flow

Todos los cambios notables en este proyecto serán documentados en este archivo, siguiendo la progresión de los ejercicios del **Sprint 1**.

---

## Día 1 - Ejercicio 01: Inicialización y Configuración
*   **Gestión de Repositorio**: Creación del repositorio en GitHub y definición del flujo colaborativo.
*   **Entorno de Trabajo**: Configuración inicial en Google Colab y organización de ramas (`main`, `Sprint_1` y ramas individuales).
*   **Estructura de Datos**: Implementación de la jerarquía de directorios del proyecto.
*   **Documentación Base**: 
    *   Actualización del `README.md` con objetivos, introducción y contexto.
    *   Inicialización del `CHANGELOG.md` para el registro de avances.
*   **Maquetación**: Organización inicial del notebook principal siguiendo los criterios de evaluación establecidos.

---

## Día 2 - Ejercicio 02: Carga y Exploración Inicial
*   **Adquisición de Datos**: Descarga del dataset original y almacenamiento en la ruta estructurada `urban_flow/data/raw`.
*   **Ingesta**: Carga del dataset utilizando la librería `pandas`.
*   **Inspección Técnica**: 
    *   Visualización de registros iniciales mediante el método `head()`.
    *   Análisis de tipos de datos (`dtypes`) por columna.
*   **Diagnóstico de Calidad**: 
    *   Cuantificación de valores nulos mediante `isna()` y `sum()`.
    *   Detección de inconsistencias críticas en fechas, horas y valores faltantes.

---

## Día 3 - Ejercicio 03: Limpieza y Normalización
*   **Normalización Temporal**: 
    *   Estandarización de fechas al formato `YYYY-MM-DD` (valor base `1932-01-01` para inválidos).
    *   Ajuste de horas al formato de 24hs (valor base `00:00` para errores).
*   **Saneamiento de Texto**: 
    *   Limpieza de `ubicacion` eliminando caracteres especiales y normalizando a mayúsculas.
    *   Normalización de `patente` (mayúsculas y remoción de símbolos) utilizando `pd.NA` para datos no disponibles.
*   **Depuración de Registros**: 
    *   Eliminación de filas con nulos en columnas relevantes (`patente`, `velocidad_registrada`).
    *   Tratamiento de outliers mediante el método de rango intercuartílico (IQR).
*   **Ingeniería de Características**: 
    *   Cálculo de `exceso_velocidad_real`.
    *   Cálculo de `exceso_velocidad` (incluyendo tolerancia del 5% sobre el límite).
*   **Persistencia**: Eliminación de registros sin infracción y exportación a `urban_flow/data/interim/speeding_fines.csv`.

---

## Día 4 - Ejercicio 04: Análisis Avanzado (Clase FineAnalyzer)
*   **Arquitectura de Software**: Definición de la clase `FineAnalyzer` con encapsulamiento de datos mediante el atributo privado `__data`.
*   **Ranking y Reportes**: 
    *   Desarrollo del método para el **Top 5 de patentes** con índice base 1.
    *   Desarrollo del método para el **Top 5 de horarios** con mayor siniestralidad.
*   **Métricas Estadísticas**: Implementación de métodos para calcular el exceso promedio (real y con tolerancia).
*   **Contabilización Geográfica**: Método para contabilizar multas por ubicación con ordenamiento alfabético.
*   **Validación**: Creación de celdas independientes para la instanciación del objeto y la invocación de todos los métodos de análisis.


---

## Día 5 - Ejercicio 05: Visualización de Datos

- **Análisis Gráfico**:
Generación de visualizaciones para responder a cada punto de la consigna utilizando gráficos adecuados según el tipo de análisis.

- **Ranking de Reincidencia**:
Construcción de gráfico de barras con el Top 10 de patentes más infractoras, ordenado de mayor a menor.

- **Distribución Horaria**:
Representación del porcentaje de infracciones por hora mediante gráfico de torta para identificar franjas de mayor incidencia.

- **Análisis Temporal Mensual**:
Visualización de la cantidad de infracciones por mes utilizando gráfico de barras horizontal ordenado.

- **Comportamiento Horario**:
Análisis del exceso de velocidad promedio agrupado por hora completa (HH:00) mediante gráfico de líneas.

- **Análisis de Datos Atípicos**:
Visualización del exceso de velocidad correspondiente a registros con fecha inválida (1932-01-01) para evaluar su comportamiento.

- **Persistencia de Resultados**:
Exportación de todos los gráficos generados en formato .jpg dentro de la ruta `urban_flow/data/interim/plots`.


---

## Día 6 - Ejercicio 06: Análisis de Datos Imputados

- **Evaluación de Fechas Inválidas**:
Cálculo del porcentaje de infracciones registradas con la fecha 1932-01-01, utilizada como valor por defecto para datos incorrectos o faltantes.

- **Resultado de Fechas**:
Presentación del porcentaje obtenido para dimensionar el impacto de los datos inválidos en la variable temporal.

El porcentaje de infracciones en la fecha 1932-01-01 es XX.XX%

- **Evaluación de Horas Inválidas**:
Cálculo del porcentaje de infracciones registradas a la hora 00:00, asignada a valores no interpretables durante la normalización.

- **Resultado de Horas**:
Presentación del porcentaje obtenido para identificar la proporción de datos horarios incorrectos.

El porcentaje de infracciones a la hora 00:00 es XX.XX%

- **Análisis de Impacto**:
Interpretación de cómo estos valores imputados afectan los análisis temporales y la distribución de los datos.

---

## Día 7 - Ejercicio 07: Conclusión del Dataset

- **Análisis General**:
Evaluación integral del dataset luego del proceso de limpieza, normalización y transformación de los datos.

- **Calidad de los Datos**:
Identificación de inconsistencias en variables clave como fecha, hora, patente y velocidad, que requirieron corrección para su análisis.

- **Patrones Observados**:
Detección de comportamientos relevantes como la reincidencia de patentes y la distribución no uniforme de las infracciones.

- **Impacto de Datos Imputados**:
Reconocimiento de la influencia de valores como 1932-01-01 y 00:00 en los resultados, los cuales deben interpretarse como datos inválidos.

- **Conclusión Final**:
El dataset permite analizar el comportamiento de las infracciones de tránsito de manera efectiva una vez procesado, aunque los resultados deben considerarse teniendo en cuenta las limitaciones derivadas de la calidad de los datos originales.


---

## Día 6 - Ejercicio 06: Análisis de Datos Imputados

- **Evaluación de Fechas Inválidas**:
Cálculo del porcentaje de infracciones registradas con la fecha 1932-01-01, utilizada como valor por defecto para datos incorrectos o faltantes.

- **Resultado de Fechas**:
Presentación del porcentaje obtenido para dimensionar el impacto de los datos inválidos en la variable temporal.

El porcentaje de infracciones en la fecha 1932-01-01 es XX.XX%

- **Evaluación de Horas Inválidas**:
Cálculo del porcentaje de infracciones registradas a la hora 00:00, asignada a valores no interpretables durante la normalización.

- **Resultado de Horas**:
Presentación del porcentaje obtenido para identificar la proporción de datos horarios incorrectos.

El porcentaje de infracciones a la hora 00:00 es XX.XX%

- **Análisis de Impacto**:
Interpretación de cómo estos valores imputados afectan los análisis temporales y la distribución de los datos.

---

## Día 7 - Ejercicio 07: Conclusión del Dataset

- **Análisis General**:
Evaluación integral del dataset luego del proceso de limpieza, normalización y transformación de los datos.

- **Calidad de los Datos**:
Identificación de inconsistencias en variables clave como fecha, hora, patente y velocidad, que requirieron corrección para su análisis.

- **Patrones Observados**:
Detección de comportamientos relevantes como la reincidencia de patentes y la distribución no uniforme de las infracciones.

- **Impacto de Datos Imputados**:
Reconocimiento de la influencia de valores como 1932-01-01 y 00:00 en los resultados, los cuales deben interpretarse como datos inválidos.

- **Conclusión Final**:
El dataset permite analizar el comportamiento de las infracciones de tránsito de manera efectiva una vez procesado, aunque los resultados deben considerarse teniendo en cuenta las limitaciones derivadas de la calidad de los datos originales.
