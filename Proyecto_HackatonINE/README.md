# Predicción y Escenarios de Riesgo de Abstención Electoral en México (2009 - 2024)

**Hackatón: "Hackea la participación: Datos que construyen democracia" - INE 2026**
**Reto 2:** Predicción y escenarios de riesgo de abstención.
**Equipo:** Las Queens (Itzel Cruz Del Moral y Daniela Cruz Del Moral).

## Descripción del Proyecto
Este repositorio contiene una propuesta desarrollada para identificar territorios con alta vulnerabilidad de abstención electoral en México. A través de la integración de datos históricos de los Conteos Censales del INE (2009-2024), el Censo de Población y Vivienda 2020, y la cartografía geoestadística, construimos un **Modelo Predictivo de Regresión Logística** y un **Semáforo de Riesgo Territorial**.

El proyecto permite anticipar escenarios y focalizar recursos institucionales, ofreciendo al INE una herramienta de alerta temprana basada en ciencia de datos.

##  Estructura del Repositorio

El código está dividido en un *pipeline* secuencial de 10 scripts para garantizar su reproducibilidad:

*   `01_procesamiento_base_nacional.py`: Carga y unificación masiva de los archivos históricos del INE (2009-2024) a nivel seccional.
*   `02_perfil_riesgo_seccional.py`: Cálculo de tendencias, volatilidad y promedios históricos por sección electoral.
*   `03_cruce_censo_sociodemografico.py`: Enriquecimiento de la base seccional mediante el cruce con el Censo 2020 (variables de edad, género, marginación, etc.).
*   `04_exportacion_resultados.py`: Generación de la base anonimizada final y la tabla "Top 10" de estados con más secciones en riesgo.
*   `05_union_geografica.py`: Cruce de los datos con el shapefile seccional del INE; exportación a formatos GIS (GeoJSON y GPKG).
*   `06_visualizacion_mapa_seccional.py`: Renderizado del Mapa 1 (Semáforo Nacional por Sección Electoral).
*   `07_simulacion_escenarios.py`: Cálculo del Escenario Base vs. Escenario de Intervención Hipotética (+10% participación).
*   `08_tabla_escenarios.py`: Generación de la Tabla 2 (Comparativa de escenarios de riesgo).
*   `09_modelo_estatal.py`: Entrenamiento del modelo de Regresión Logística, cálculo de Accuracy y generación de la Tabla 1 (Semáforo Estatal).
*   `10_mapa_municipal.py`: Renderizado del Mapa 2 (Proyección del riesgo estatal sobre la cartografía municipal).

##  Entregables Visuales (Generados por los scripts)
1.  **Tabla 1:** Semáforo de riesgo de abstención por entidad federativa.
2.  **Tabla 2:** Simulación de escenarios (sin intervención vs. con intervención).
3.  **Mapa 1:** Semáforo de riesgo por sección electoral (Nacional).
4.  **Mapa 2:** Semáforo de riesgo proyectado por municipio.
5.  **Datos Abiertos:** Archivos `.csv`, `.geojson` y `.gpkg` listos para consulta.

##  Requisitos y Ejecución
Para replicar este proyecto, instala las dependencias necesarias:
```bash
pip install pandas numpy scikit-learn matplotlib geopandas