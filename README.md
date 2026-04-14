# Sistema de analítica y predicción de stock en un market mediante arquitectura Lakehouse

Este proyecto implementa una arquitectura Lakehouse para centralizar y transformar datos de ventas, productos y usuarios de un market. El sistema convierte datos crudos en conocimiento estratégico, facilitando la toma de decisiones basada en tendencias de consumo y rendimiento de productos. Además, establece los cimientos para capacidades avanzadas de IA, como la optimización de inventarios y personalización de ofertas
---

## Componentes del sistema

- **Scripts de procesamiento**: Flujos automatizados de ingesta, limpieza y transformación siguiendo el paradigma de capas (Bronze, Silver, Gold).
- **PostgreSQL**: Data Warehouse donde se almacenan los datos de la capa Gold para consumo analítico.
- **Modelo de IA (scikit-learn)**: Algoritmo de clasificación binaria entrenado para predecir el riesgo de agotamiento de productos.
- **visualizacion (metabase/powerBI)**: dashboard de visualización de resultados.
- **Documentación**: Diseño técnico detallado y planificación de gestión (enfoque mixto).

---

## Tecnologías utilizadas

-Git
-Docker
-Python 3.9 o superior
-Apache Spark
-PostgreSQL (opcional)
-Power BI o herramienta de visualización equivalente

---

## Pipeline implementado

| Etapa | Descripción |
|-------|-------------|
| 1. Diseño e instalación | Configuración de arquitectura Lakehouse en Docker y estructura de carpetas del proyecto. |
| 2. Ingesta (Capa Bronze) | Lectura de fuentes (CSV/Mockaroo) y almacenamiento persistente en Delta Lake / Parquet. |
| 3. Limpieza (Capa Silver) | Procesamiento con Spark para eliminación de duplicados, manejo de nulos y tipado de datos. |
| 4. Transformación (Capa Gold) | Creación de variables de negocio (días sin reposición, tasa de ventas) y tablas agregadas. |
| 5. Validación | Control de calidad mediante Spark SQL para asegurar coherencia y rangos válidos. |
| 6. Carga en PostgreSQL | Migración de datos refinados (Capa Gold) a la base de datos para consumo de analítica. |
| 7. Entrenamiento IA | Implementación de clasificación binaria con scikit-learn para predecir agotamiento de stock. |
| 8. Evaluación | Análisis de métricas (Accuracy, Recall) y validación de resultados del modelo predictivo. |
| 9. Visualización | Despliegue de Dashboards en Power BI o Metabase con alertas de stock y KPIs de ventas. |

---

## 📂 Estructura del repositorio

```
iamarket-bearpAI/
├── .gitignore
├── LICENSE
├── README.md
├── docker-compose.yml
├── dashboards/
│   └── imagen_referencial_powerBI.jfif
├── data/
│   ├── .gitkeep
│   └── productos_ventas.csv
├── docker/
│   ├── .gitkeep
│   └── Dockerfile
├── docs/
│   ├── Diagrama_flujo_datos.png
│   ├── Diagrama_wbs(edt).png
│   └── README_docs.md
├── notebooks/
│   ├── .gitkeep
│   └── exploracion_inventario.ipynb
└── scripts/
    ├── .gitkeep
    └── procesamiento.py
```

---

## Cómo ejecutar el sistema (entorno ya instalado)

1. Clonar el repositorio  
   `git clone https://github.com/bearpRetamales/Proyecto_gestion_BearpAI.git`

2. Entrar a la carpeta del proyecto  
   `cd Proyecto_gestion_BearpAI`

3. Levantar la base de datos y dependencias  
   `docker-compose up -d`  
   `pip install -r requirements.txt`

4. Ejecutar el pipeline de procesamiento  
   `python scripts/procesamiento.py`

5. Visualizar los resultados y métricas  
   Revisar la carpeta `dashboards/` para ver las alertas y `notebooks/` para el análisis experimental.

---

## Documentación técnica

Los documentos de planificación y diseño del Lakehouse están disponibles en:

* **Diagrama de Flujo de Datos:** [`docs/Diagrama_flujo_datos.png`](docs/Diagrama_flujo_datos.png)
* **Diagrama WBS (EDT):** [`docs/Diagrama_wbs(edt).png`](docs/Diagrama_wbs(edt).png)
* **Guía de Documentación:** [`docs/DOCUMENTO_DISEÑO_TECNICO_completo(1).docx`](docs/docs/DOCUMENTO_DISEÑO_TECNICO_completo(1).docx)

---

## Equipo

- **Benjamín Retamales** – Responsable del ciclo completo:
  - Ingesta, procesamiento y limpieza de datos.
  - Modelado predictivo y lógica de negocio.
  - Visualización (Dashboards) y documentación técnica.


