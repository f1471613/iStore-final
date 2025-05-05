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


# Solución de Negocio Cloud con Microsoft Fabric, Power Platform y Power BI

Este proyecto implementa una solución de negocio moderna utilizando:

- 🧱 **Microsoft Fabric Warehouse** y **Data Factory** para gestión de datos.
- ⚙️ **Azure SQL** para almacenamiento estructurado.
- ⚡ **Power Apps** para el desarrollo de aplicaciones low-code.
- 📊 **Power BI** para análisis de datos e inteligencia de negocios de autoservicio.

---

## 🚀 Diagrama de la arquitectura del proyecto

![Diagrama de la Arquitectura del Proyecto](carpeta-img/Diagrama.jpg)

1. Data Sources: Los datos provienen de archivos Excel y de un sistema de escritorio con estructura propia. Ambos se integran inicialmente a través de procesos manuales o semi-automatizados.

2. Data Layer: Centraliza la información recopilada en una base de datos relacional en Azure SQL, permitiendo un almacenamiento seguro y estructurado en la nube. También registra datos desde PowerApps.

3. Application Layer: Utiliza Microsoft Power Apps como interfaz gráfica para el ingreso y edición de datos, directamente conectada al entorno de Azure.

4. ETL Layer: Implementada con Pipelines y Dataflows de Microsoft Fabric, automatiza el flujo de datos hacia el Data Warehouse, e incorpora Notebooks en Python para validación y notificación por correo.

5. Data Warehouse Layer: Almacena los datos ya transformados en un Fabric Data Warehouse, optimizado para análisis avanzado y consolidación de información.

6. Presentation Layer: Brinda acceso a reportes interactivos mediante Power BI Service y en Excel, facilitando la toma de decisiones basada en datos.

7. User Access : Permite gestionar accesos según roles definidos en Azure, Power Apps y Power BI. Los usuarios reciben correos automáticos tras cada actualización, garantizando trazabilidad y comunicación.

---

## Data Layer (Capa de Datos)

Descripción de la Base de Datos – Proyecto iStore

La base de datos del sistema de ventas de iStore ha sido diseñada para gestionar de forma eficiente las operaciones relacionadas con la comercialización de dispositivos Apple, incluyendo el modelo de negocio tipo buyback, donde los clientes pueden entregar su equipo usado como parte de pago en todas nuestras sedes.

Esta base de datos está normalizada y distribuida en seis tablas principales:

🛒 Ventas

Registra las transacciones realizadas. Cada venta incluye información del cliente, modelo de equipo vendido, precio, forma de pago y, si aplica, los detalles del proceso buyback. Se registran también descuentos aplicados por el valor del equipo entregado.

👤 Clientes

Contiene los datos personales de los compradores: tipo y número de documento, nombre, apellidos, contacto, fecha de nacimiento y estado de suscripción a correos. Permite segmentar y personalizar la atención al cliente.

🏬 Sede

Representa las tiendas físicas de iStore. Se almacena información como nombre, ubicación, departamento, fecha de apertura y si la sede se encuentra activa. Esto permite análisis geográficos y operativos.

📱 Modelo

Almacena la información de los modelos disponibles: familia del producto (iPhone, iPad, etc.), capacidad, color y precio de lista. Esta tabla se relaciona directamente con ventas y buybacks.

🔁 Buyback

Gestiona el inventario de equipos usados entregados por los clientes. Incluye el ID del modelo, estado físico del equipo (representado por un código) y su valor de recompra, que se descuenta del precio final de la venta.

💳 Metodo_pago

Lista los métodos de pago aceptados (efectivo, tarjeta, transferencia, entre otros), estandarizando la forma de registrar cada transacción.


Azure SQL: Base de datos en la nube donde se almacenan los datos procesados desde múltiples orígenes.
![Base de datos relacional](carpeta-img/BD-relacional.jpg)

---

## Application Layer (Capa de aplicación)

Pantalla de Inicio/Bienvenida

![Inicio - Bienvenida](carpeta-img/PPrincipal.jpg)

Propósito:

Servir como punto de entrada principal para los usuarios, centralizando el acceso a todas las funcionalidades del sistema mediante una interfaz clara, visual y fácil de usar.

Funcionalidades:

Presentación visual con logotipo de la empresa o nombre de la aplicación.

Contenedor con botones o íconos de navegación para acceder a cada una de las pantallas del sistema:

🛒 Ventas  👤 Cliente   🏬 Sede   📱 Modelo   🔁 Buyback   💳 Método de Pago

Diseño responsive y moderno, con botones representados por íconos e imágenes que mejoran la experiencia de usuario.

Posible mensaje de bienvenida personalizado.

Estructura centralizada para mantener la usabilidad y consistencia en la navegación.



Pantalla de Ventas

Propósito: Registrar y visualizar las ventas realizadas, incluyendo el detalle del proceso de buyback.

Funcionalidades:

- Generación automática del ID de venta con formato estructurado (ej. F002-00001).

- Formulario con selección de cliente, modelo, método de pago y sede.

- Gestión del valor del equipo entregado (buyback), cálculo automático del precio final.

- Soporte para ventas tradicionales y con canje de equipo (bit de buyback).

- Botones de guardar, editar, eliminar y crear nueva venta.

![Ventas](carpeta-img/PVentas.jpg)

Pantalla de Clientes

![Clientes](carpeta-img/PClientes.jpg)

Pantalla de Sedes

![Sedes](carpeta-img/PSedes.jpg)

Pantalla de Metodo de Pago

![PMetodoPago](carpeta-img/PMetodoPago.jpg)

Pantalla de Buyback

![PBuyback](carpeta-img/Buyback.jpg)

---

## ETL Layer (Capa de extracción, transformación y carga)

El pipeline llamado "pl_update_table" se ejecuta todos los días a las 6:00 a.m.

![Pipeline: pl-update-table](carpeta-img/Pipeline.jpg)


Notebook: NotificarExitoPipeline

![Notebook: NotificarExitoPipeline](carpeta-img/Notebook.jpg)


Correo electrónico de notificación del éxito del pipeline

![Notebook: NotificarExitoPipeline](carpeta-img/Correo.jpg)


---

## Data Warehouse Layer (Capa de almacén de datos)

Vista del Data Warehouse en Microsoft Fabric

![Warehouse](carpeta-img/DataWarehouse.jpg)

---

## Presentation Layer (Capa de presentación)

Reportes con Microsoft Power BI Service.

Informe 1
![Power BI](carpeta-img/informe1.jpg)

Informe 2
![Power BI](carpeta-img/informe2.jpg)

Informe 3
![Power BI](carpeta-img/informe3.jpg)

Informe 4
![Power BI](carpeta-img/informe4.jpg)

Informe 5
![Power BI](carpeta-img/informe5.jpg)

---

# Conclución
Este proyecto evidencia el poder de integrar el ecosistema Microsoft —incluyendo Power Apps, Azure SQL, Microsoft Fabric y Power BI— para construir una solución empresarial robusta, escalable y centrada en el usuario. La arquitectura desarrollada no solo optimiza el flujo de datos y la toma de decisiones, sino que también reduce significativamente los tiempos de desarrollo, mejora la trazabilidad y garantiza una operación eficiente con una experiencia de usuario intuitiva y segura.

Además, permite:

✅ Centralizar y gobernar datos de múltiples orígenes en un entorno confiable y accesible.

✅ Automatizar procesos ETL mediante pipelines y notebooks en Fabric, asegurando precisión y agilidad.

✅ Notificar a los usuarios con correos automáticos que refuerzan la trazabilidad y el control operativo.

✅ Facilitar el ingreso de datos con Power Apps, eliminando barreras técnicas para los usuarios finales.

✅ Visualizar y analizar la información con Power BI y Excel, promoviendo la inteligencia de negocio en todos los niveles.

✅ Proteger el acceso a la información, gracias a la gestión de roles y permisos definidos en Azure.

En conjunto, esta solución representa un modelo eficaz de transformación digital con herramientas Microsoft, alineado con los objetivos de eficiencia, crecimiento y experiencia de usuario que exige el entorno empresarial actual.
