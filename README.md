Detección de Anomalías IoT en Tiempo Real con Databricks


Descripción y Objetivos

Este proyecto construye un pipeline de datos end-to-end para la detección de anomalías en dispositivos IoT utilizando procesamiento en tiempo real sobre Databricks. La solución ingiere eventos generados por sensores, procesa flujos de datos mediante una arquitectura Medallion (Bronze → Silver → Gold) y aplica reglas de negocio y modelos analíticos para identificar comportamientos anómalos, generar alertas y habilitar monitoreo operativo en tiempo real.

El objetivo es proporcionar una plataforma escalable que permita detectar fallas potenciales, degradación de equipos y eventos atípicos antes de que impacten la operación.



Arquitectura


Capa Bronze: Ingesta de datos crudos provenientes de dispositivos IoT mediante streaming. Los eventos son almacenados en formato Delta Lake conservando el histórico completo.
Capa Silver: Limpieza, normalización, validación de calidad de datos, manejo de valores nulos y enriquecimiento de eventos con métricas derivadas.
Capa Gold: Construcción de modelos analíticos para detección de anomalías, agregaciones operativas y datasets optimizados para visualización y monitoreo.


Tecnologías
Motor de Procesamiento: Databricks / Apache Spark
Streaming: Spark Structured Streaming
Lenguaje: SQL (Spark SQL) y PySpark
Almacenamiento: Delta Lake
Orquestación: Databricks Workflows
Machine Learning: MLflow y modelos de detección de anomalías
Control de Versiones: Git / GitHub


Modelado de Datos

Para la capa de consumo analítico (Gold) se implementó un modelo dimensional orientado a monitoreo operacional y análisis de anomalías.




Tabla de hechos (fact_sensor_readings): Diseñada con granularidad a nivel de evento generado por sensor. Contiene métricas como temperatura, humedad, presión, consumo energético y score de anomalía.

Tablas de dimensiones:

dim_devices: Información de dispositivos IoT.
dim_locations: Ubicación física de los sensores.
dim_timestamp: Dimensión temporal para análisis histórico.
dim_alerts: Catálogo de alertas y niveles de criticidad.


Dashboard Analítico


KPIs
Total de eventos procesados por minuto.
Cantidad de anomalías detectadas.
Tasa de anomalías por dispositivo.
Dispositivos con mayor criticidad.
Disponibilidad operativa de sensores.


Visualizaciones
Monitoreo en Tiempo Real: Flujo de eventos procesados y anomalías detectadas.
Mapa de Dispositivos: Visualización geográfica de sensores y nivel de riesgo.
Tendencia de Métricas: Evolución histórica de temperatura, humedad y otras variables monitorizadas.
Ranking de Dispositivos Críticos: Equipos con mayor frecuencia de eventos anómalos.


Origen de los Datos

Los datos provienen de dispositivos IoT simulados o reales conectados mediante eventos de streaming.

Sensores IoT: Telemetría de temperatura, humedad, presión, vibración o consumo energético.
Eventos en Tiempo Real: Generados continuamente y procesados mediante Spark Structured Streaming.
Datos de Referencia: Catálogos de dispositivos, ubicaciones y umbrales operativos.


Detección de Anomalías

El proyecto implementa múltiples estrategias para identificar comportamientos anormales:

Reglas de negocio basadas en umbrales configurables.
Detección estadística utilizando percentiles y desviación estándar.
Machine Learning para identificar patrones fuera del comportamiento normal.
Generación automática de alertas clasificadas por severidad.


Estructura del Repositorio

El repositorio sigue mejores prácticas de Data Engineering y procesamiento en tiempo real:

notebooks/00_EDA/: Análisis exploratorio de datos históricos y definición de reglas de anomalía.
notebooks/01_DDL/: Creación de esquemas, tablas Delta y configuración del entorno.
notebooks/02_Bronze/: Ingesta de eventos IoT mediante Structured Streaming.
notebooks/03_Silver/: Limpieza, validación y enriquecimiento de datos.
notebooks/04_Gold/: Construcción de métricas, agregaciones y datasets analíticos.
notebooks/05_ML/: Entrenamiento y registro de modelos de detección de anomalías con MLflow.
workflows/: Definición de pipelines y orquestación.
docs/: Documentación técnica, diagramas de arquitectura y decisiones de diseño.
dashboards/: Dashboards de monitoreo y visualización en tiempo real.


Caso de Uso

La solución puede aplicarse en escenarios de manufactura, logística, transporte, energía y ciudades inteligentes, donde la detección temprana de anomalías permite reducir tiempos de inactividad, optimizar mantenimiento preventivo y mejorar la eficiencia operativa. 🚀

Esta descripción se ve muy sólida para un repositorio de portafolio de Data Engineer con Databricks, porque muestra claramente:

Medallion Architecture.
Structured Streaming.
Delta Lake.
MLflow.
IoT Analytics.
Dashboarding.
Data Modeling (Gold).
Orquestación con Workflows.
