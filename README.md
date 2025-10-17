# 📊 Proyecto Lakehouse: Optimización del Proceso de Pagos a Proveedores

## 📝 Descripción
Este proyecto implementa una **arquitectura Lakehouse** en **Databricks** basada en **Delta Lake**, con el objetivo de optimizar y analizar el proceso de pagos a proveedores del área de Finanzas.  
Se estructura bajo el enfoque **Medallón (Bronze, Silver, Gold)** y concluye con la creación de **dashboards interactivos en Power BI** para facilitar la toma de decisiones.

---

## 🧩 Objetivo General
Desarrollar un **flujo ETL automatizado** y un **modelo analítico dimensional** que permita consolidar información de pedidos y pagos, mejorando la trazabilidad, calidad de datos y eficiencia en el análisis financiero.

---

## 🔁 Flujo General de Datos

### 1️⃣ Bronze Layer
- Ingesta de archivos crudos (CSV/Excel) a formato Delta.  
- Mantiene los datos originales para trazabilidad.

### 2️⃣ Silver Layer
- Limpieza, transformación y enriquecimiento con PySpark.  
- Cálculo de métricas clave (`total_pago`, `tipo de cambio`).  
- Eliminación de duplicados con `dropDuplicates()`.

### 3️⃣ Gold Layer
- Construcción del **modelo dimensional (esquema estrella)**:  
  - **Tabla de hechos:** `fact_pedidos_pago`  
  - **Dimensiones:** `dim_proveedor`, `dim_area`, `dim_pedido`  
- Optimización para análisis temporal y conexión con Power BI.

---

## 🛠️ Tecnologías Utilizadas
- **Databricks Notebooks**  
- **PySpark (Apache Spark)**  
- **Delta Lake**  
- **Power BI**

---

## ✅ Resultados Clave
- Reducción de duplicidades y errores en datos financieros.  
- Estandarización de procesos de transformación (ETL).  
- Dashboards dinámicos con métricas de pagos y pedidos.  
- Preparado para automatización con **Jobs o Workflows de Databricks**.

---

## 📤 Exportación a Power BI
Las tablas de la capa **Gold** pueden exportarse a `.csv` para conexión directa con Power BI:

```sql
SELECT id_proveedor, codigo_proveedor, nombre_proveedor 
FROM default.dim_proveedor
ORDER BY id_proveedor;
