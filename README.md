# Building Cloud Business Applications for iStore

📌 Descripción General del Proyecto - Arquitectura de Datos para iStore

El presente proyecto tiene como objetivo implementar una arquitectura moderna de datos para la empresa iStore, permitiendo una gestión eficiente, automatizada y escalable de la información proveniente de diversas fuentes internas.

Esta arquitectura está diseñada para centralizar los datos operativos y analíticos, optimizar su procesamiento mediante herramientas de ETL, y ofrecer acceso flexible y seguro a través de interfaces como Power BI, Excel y PowerApps.

Se emplean tecnologías en la nube como Azure SQL y Microsoft Fabric, permitiendo a iStore una solución robusta, integrada y lista para el análisis avanzado y la toma de decisiones en tiempo real.


🎯 Objetivos Principales

- Centralizar datos de diversas fuentes (Excel, SQL).
- Automatizar flujos ETL con Microsoft Fabric.
- Integrar PowerApps como capa de entrada y edición de datos.
- Consolidar un Data Warehouse para reportes confiables.
- Facilitar el análisis con Power BI y distribución por correo.


# 🌐 Solución de Negocio Cloud con Microsoft Fabric, Power Platform y Power BI

Este proyecto implementa una solución de negocio moderna utilizando:

- 🧱 **Microsoft Fabric Warehouse** y **Data Factory** para gestión de datos.
- ⚙️ **Azure SQL** para almacenamiento estructurado.
- ⚡ **Power Apps** para el desarrollo de aplicaciones low-code.
- 📊 **Power BI** para análisis de datos e inteligencia de negocios de autoservicio.

---

## 🚀 Diagrama de la arquitectura del proyecto

![Diagrama de la Arquitectura del Proyecto](carpeta-img/Diagrama-arquitectura.png)

1. Data Sources: Los datos provienen de archivos Excel y de un sistema de escritorio con estructura propia. Ambos se integran inicialmente a través de procesos manuales o semi-automatizados.

2. Data Layer: Centraliza la información recopilada en una base de datos relacional en Azure SQL, permitiendo un almacenamiento seguro y estructurado en la nube. También registra datos desde PowerApps.

3. Application Layer: Utiliza Microsoft Power Apps como interfaz gráfica para el ingreso y edición de datos, directamente conectada al entorno de Azure.

4. ETL Layer: Implementada con Pipelines y Dataflows de Microsoft Fabric, automatiza el flujo de datos hacia el Data Warehouse, e incorpora Notebooks en Python para validación y notificación por correo.

5. Data Warehouse Layer: Almacena los datos ya transformados en un Fabric Data Warehouse, optimizado para análisis avanzado y consolidación de información.

6. Presentation Layer: Brinda acceso a reportes interactivos mediante Power BI Service y en Excel, facilitando la toma de decisiones basada en datos.

7. User Access : Permite gestionar accesos según roles definidos en Azure, Power Apps y Power BI. Los usuarios reciben correos automáticos tras cada actualización, garantizando trazabilidad y comunicación.


## Data Layer (Capa de Datos)

Azure SQL: Base de datos en la nube donde se almacenan los datos procesados desde múltiples orígenes.
![Base de datos relacional](carpeta-img/BD-relacional.jpg)

## Application Layer (Capa de aplicación)

Pantalla de bienvenida
![Inicio - Bienvenida](carpeta-img/PPrincipal.jpg)

Pantalla de Ventas
![Ventas](carpeta-img/PVentas.jpg)

## ETL Layer (Capa de extracción, transformación y carga)

Pipeline: pl_update_table
![Pipeline: pl-update-table](carpeta-img/Pipeline.jpg)


Notebook: NotificarExitoPipeline
![Notebook: NotificarExitoPipeline](carpeta-img/Notebook.jpg)

## Vista del Warehouse en Microsoft Fabric
![Warehouse](capturas/fabric-warehouse.png)

## Dashboard en Power BI
![Power BI](capturas/powerbi-dashboard.png)

---

# Conclución
Esta solución demuestra cómo integrar plataformas Microsoft para crear sistemas empresariales escalables, accesibles y potentes, con bajo tiempo de desarrollo y alta eficiencia operativa.
