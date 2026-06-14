

# CHANGELOG: Proyecto Urban Flow

Todos los cambios notables en este proyecto serán documentados en este archivo, siguiendo la progresión de los ejercicios del **Sprint 1**.

---

# Sprint 1

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

## Día 10 - Ejercicio 05: Correcciones y Ajustes Post-Entrega (Correcciones TP 1)

- **Corrección de Fechas**:
Actualización de la normalización de fechas utilizando `format="mixed"` para soportar múltiples formatos de entrada.

- **Trazabilidad Git**:
Incorporación explícita de bloques `git add`, `git commit` y `git push` luego de cada ejercicio, siguiendo las observaciones de la devolución.

- **Corrección de Visualizaciones**:
Incorporación del gráfico faltante correspondiente al análisis de excesos de velocidad para registros con fecha `1932-01-01`.

- **Ajuste de Análisis Mensual**:
Corrección del gráfico de infracciones por mes eliminando el filtrado de fechas imputadas, respetando la consigna original.

- **Documentación**:
Actualización de observaciones, conclusiones y descripciones de gráficos para mantener coherencia con los resultados obtenidos.

---

# Sprint 2

## Día 1 - Ejercicio 01: Inicialización y Preparación del Dataset de Imágenes

-   **Gestión de Repositorio**:
    *   Creación y configuración de la rama `Sprint_2` a partir de `Sprint_1`.

-   **Adquisición de Datos**:
    *   Descarga del dataset de imágenes provisto para el Sprint 2.
    *   Descompresión y almacenamiento de imágenes en `urban_flow/data/raw/imgs`.

-   **Estructura de Datos**:
    *   Preparación de directorios destinados al procesamiento y análisis de imágenes.

-   **Documentación**:
    *   Actualización del `README.md` y `CHANGELOG.md` para el nuevo sprint.

---

## Día 2 - Ejercicio 02: Verificación y Organización del Dataset de Imágenes

-   **Inspección de Imágenes**:
    *   Relevamiento de imágenes disponibles en `urban_flow/data/raw/imgs`.
    *   Obtención de nombre de archivo y tamaño en kilobytes.

-   **Agrupación de Imágenes**:
    *   Separación de imágenes en los grupos `plates` y `completes`.
    *   Conteo de imágenes por grupo.

-   **Metadatos de Imágenes**:
    *   Obtención de resolución (`width` y `height`) y cálculo de área.
    *   Cálculo de resolución promedio por grupo.

-   **Persistencia de Datos**:
    *   Construcción del diccionario `group_images`.
    *   Exportación de `group_images.json` en `urban_flow/data/interim`.

-   **Visualización**:
    *   Desarrollo de función reutilizable para mostrar imágenes aleatorias.
    *   Visualización de 4 imágenes por grupo en formato de tabla.

---

## Día 3 - Ejercicio 03: Procesamiento de Imágenes

-   **Escala de Grises**:
    *   Conversión de imágenes originales a escala de grises.
    *   Almacenamiento de resultados en `urban_flow/data/interim/imgs/03_01_gray_scale`.

-   **Suavizado de Imágenes**:
    *   Aplicación de filtro Gaussiano sobre imágenes en escala de grises.
    *   Almacenamiento de resultados en `urban_flow/data/interim/imgs/03_02_blur`.

-   **Detección de Bordes**:
    *   Aplicación del algoritmo Canny sobre imágenes suavizadas.
    *   Almacenamiento de resultados en `urban_flow/data/interim/imgs/03_03_canny`.

-   **Visualización**:
    *   Reutilización de función para mostrar imágenes procesadas de ambos grupos.

---

## Día 4 - Ejercicio 04: Extracción y Relación de Patentes

-   **Extracción OCR**:
    *   Aplicación de la función `extraer_patente` sobre imágenes del grupo `plates`.
    *   Almacenamiento de la patente detectada en la clave `patent` del diccionario `group_images`.

-   **Relación con Dataset**:
    *   Carga del dataset limpio generado en el Sprint 1.
    *   Comparación entre patentes detectadas por OCR y patentes del dataset procesado.

-   **Validación de Coincidencias**:
    *   Cálculo del porcentaje de coincidencia mediante `ratio`.
    *   Consideración de coincidencias válidas a partir del 80%.

-   **Persistencia**:
    *   Incorporación de las columnas `imagen`, `patente_imagen` y `ratio`.
    *   Exportación del dataset final en `urban_flow/data/processed/speeding_fines_image.csv`.

---

## Día 5 - Ejercicio 05: Métricas del Dataset Final

-   **Métricas de Evidencia Visual**:
    *   Cálculo de multas con imágenes relacionadas.
    *   Cálculo de multas sin imágenes asociadas.

-   **Control de Coincidencias**:
    *   Identificación de imágenes sin match con el dataset procesado.

-   **Estado de Multas**:
    *   Cálculo de multas pendientes de pago.
    *   Cálculo de multas pendientes de pago con imágenes relacionadas.

---

## Día 6 - Ejercicio 06: Conclusión sobre Imágenes y Datos

*   **Análisis Final**:
    *   Evaluación de la relación entre el dataset administrativo y las imágenes procesadas.
    *   Interpretación de multas con y sin evidencia visual asociada.

*   **Resultados Obtenidos**:
    *   Identificación de 754 multas con imágenes relacionadas.
    *   Identificación de 959 multas sin evidencia visual asociada.
    *   Detección de 66 imágenes sin coincidencia con el dataset.

*   **Evaluación OCR**:
    *   Análisis de ratios de coincidencia entre patentes detectadas y patentes registradas.
    *   Reconocimiento de un promedio de coincidencia aproximado del 94.6%.

*   **Conclusión**:
    *   Interpretación de las imágenes como evidencia visual complementaria.
    *   Reconocimiento de limitaciones asociadas a calidad de imagen, OCR y coincidencias parciales.

---

## Día 10 - Correcciones y Ajustes Post-Entrega (Sprint 2)
*   **Ejercicio 2 y 4**:
    *   Corrección de la ruta de guardado de `group_images.json`.
    *   Eliminación de la duplicación de `mostrar_imagenes_aleatorias()`.
    *   Incorporación de la carga de `group_images.json` antes del OCR.
    *   Ajuste de rutas relativas y validaciones de lectura de imágenes.

---

# Sprint 3

## Día 1 - Ejercicio 01: Inicialización y Verificación de Datasets

*   **Gestión de Repositorio**:
    *   Creación y configuración de la rama `Sprint_3` a partir de `Sprint_2`.

*   **Entorno de Trabajo**:
    *   Configuración del flujo de trabajo en Google Colab.
    *   Actualización de la rama personal desde `Sprint_3`.

*   **Verificación de Datos**:
    *   Validación de acceso al dataset limpio del Sprint 1.
    *   Validación de acceso al diccionario `group_images.json`.
    *   Validación de acceso al dataset final con evidencia visual del Sprint 2.

---

## Día 2 - Ejercicio 02: Migración de Archivos Binarios a DVC

*   **Configuración de DVC**:
    *   Instalación e inicialización de DVC.
    *   Creación del repositorio remoto local `/content/remote_dvc`.
    *   Configuración del remote por defecto.

*   **Migración de Datos**:
    *   Migración de imágenes originales a DVC.
    *   Migración de imágenes procesadas a DVC.
    *   Publicación de archivos en el remote local.

*   **Validación**:
    *   Verificación del estado del repositorio DVC.

---

## Día 3 - Ejercicio 03: Diseño del Modelo Lógico

*   **Modelado de Entidades**:
    *   Definición de la clase `Vehiculo`.
    *   Definición de la clase `Radar`.
    *   Definición de la clase `Evidencia`.
    *   Definición de la clase `Multa`.

*   **Diseño de Relaciones**:
    *   Representación de la relación entre Vehículo y Multa.
    *   Representación de la relación entre Radar y Multa.
    *   Representación de la relación entre Multa y Evidencia.

## Día 4 - Ejercicio 04: Mapeo de Datos CSV a Entidades

*   **Implementación del Procesamiento de Registros**:
    *   Desarrollo de la función `procesar_fila_csv`.
    *   Recepción de registros del archivo CSV mediante diccionarios.
    *   Extracción de atributos necesarios para cada entidad.

*   **Mapeo del Modelo Lógico**:
    *   Creación de instancias de la clase `Vehiculo`.
    *   Creación de instancias de la clase `Radar`.
    *   Creación de instancias de la clase `Evidencia`.
    *   Construcción de objetos `Multa` utilizando las entidades relacionadas.

*   **Validación**:
    *   Lectura de registros desde `speeding_fines_image.csv`.
    *   Conversión de una fila de prueba al modelo lógico.
    *   Verificación del correcto funcionamiento del proceso de mapeo.


---

## Día 5 - Ejercicio 05: Diseño del Modelo Relacional con SQLAlchemy ORM

* **Definición de Entidades y Mapeo**:
    * Creación de la clase base declarativa `Base` para el mapeo relacional.
    * Implementación de los modelos de datos fundamentales: `Vehiculo`, `Radar`, `Multa` y `Evidencia`.
    * Configuración de tipos de datos (`String`, `Integer`, `Float`), restricciones y claves primarias (`primary_key=True`).

* **Establecimiento de Relaciones y Claves Foráneas**:
    * Configuración de relaciones uno a muchos (`back_populates`) entre `Vehiculo`-`Multa` y `Radar`-`Multa`.
    * Implementación de una relación uno a uno (`uselist=False`, `unique=True`) entre `Multa` y `Evidencia`.
    * Definición de claves foráneas (`ForeignKey`) para vincular tablas mediante patentes y identificadores.

* **Visualización y Legibilidad**:
    * Sobrescritura del método `__repr__` en todas las entidades para facilitar la depuración y mejorar la legibilidad del código en consola.
