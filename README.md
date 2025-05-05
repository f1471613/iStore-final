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

#### Descripción de la Base de Datos - Proyecto iStore

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

#### Base de datos

[https://github.com/f1471613/iStore-final/tree/main/BaseDatos-iStore](https://github.com/f1471613/iStore-final/tree/main/BaseDatos-iStore)


---

## Application Layer (Capa de aplicación)

### Pantalla de Inicio/Bienvenida

#### Propósito:

Servir como punto de entrada principal para los usuarios, centralizando el acceso a todas las funcionalidades del sistema mediante una interfaz clara, visual y fácil de usar.

#### Funcionalidades:

- Presentación visual con logotipo de la empresa o nombre de la aplicación.

- Contenedor con botones o íconos de navegación para acceder a cada una de las pantallas del sistema:🛒 Ventas  👤 Cliente   🏬 Sede   📱 Modelo   🔁 Buyback   💳 Método de Pago

- Diseño responsive y moderno, con botones representados por íconos e imágenes que mejoran la experiencia de usuario.

- Estructura centralizada para mantener la usabilidad y consistencia en la navegación.

![Inicio - Bienvenida](carpeta-img/PPrincipal.jpg)


### Pantalla de Ventas

#### Propósito: 

Registrar y visualizar las ventas realizadas, incluyendo el detalle del proceso de buyback.

#### Funcionalidades:

- Generación automática del ID de venta con formato estructurado (ej. F002-00001).

- Formulario con selección de cliente, modelo, método de pago y sede.

- Gestión del valor del equipo entregado (buyback), cálculo automático del precio final.

- Soporte para ventas tradicionales y con canje de equipo (buyback).

- Botones de guardar, editar, eliminar y crear nueva venta.

- También cuenta con un botón de Inicio (Home) que permite al usuario regresar fácilmente a la pantalla principal.

![Ventas](carpeta-img/PVentas.jpg)

### Pantalla de Clientes

#### Propósito: 

Administrar el registro de clientes que realizan compras.

#### Funcionalidades:

- Tabla para visualizar la lista de clientes registrados.

- Formulario para ingresar datos personales: documento, nombre, apellidos, contacto, correo, fecha de nacimiento, suscripción.

- Cuadro de búsqueda por nombre o número de documento.
  
- Botones de guardar, editar, eliminar y crear nuevo cliente.

- También cuenta con un botón de Inicio (Home) que permite al usuario regresar fácilmente a la pantalla principal.
  

![Clientes](carpeta-img/PClientes.jpg)

### Pantalla de Sedes

#### Propósito: 

Gestionar la información de las tiendas físicas de iStore.

#### Funcionalidades:

- Visualización de todas las sedes.

- Formulario para agregar, editar o eliminar sedes.

- Campos: nombre, ubicación, departamento, fecha de apertura, estado (activo/inactivo).

- Cuadro de búsqueda para filtrar por nombre o ubicación.

- También cuenta con un botón de Inicio (Home) que permite al usuario regresar fácilmente a la pantalla principal.

![Sedes](carpeta-img/PSedes.jpg)


### Pantalla de Metodo de Pago

#### Propósito: 

Gestionar los métodos de pago que se ofrecen a los clientes.

#### Funcionalidades:

- Visualización y mantenimiento de métodos de pago disponibles.

- Permite agregar nuevos métodos y editar los existentes.

- También cuenta con un botón de Inicio (Home) que permite al usuario regresar fácilmente a la pantalla principal.

![PMetodoPago](carpeta-img/PMetodoPago.jpg)

### Pantalla de Buyback

#### Propósito: 

Administrar los equipos usados entregados por los clientes como parte de pago.

#### Funcionalidades:

- Registro de cada equipo entregado con su estado y valor asignado.

- Asociación con el modelo entregado.

- Tabla y formulario para búsqueda, edición y gestión de registros.

- También cuenta con un botón de Inicio (Home) que permite al usuario regresar fácilmente a la pantalla principal.

![PBuyback](carpeta-img/Buyback.jpg)

---

## ETL Layer (Capa de extracción, transformación y carga)

### Descripción General

El sistema de iStore emplea un flujo de datos automatizado y eficiente que conecta múltiples capas tecnológicas del ecosistema Microsoft. Este flujo asegura la correcta integración, transformación y disponibilidad de los datos para la toma de decisiones empresariales.

#### 1. Origen de Datos
Los datos se originan principalmente desde Power Apps, donde los usuarios registran operaciones de ventas, información de clientes, equipos entregados bajo modalidad buyback, sedes y métodos de pago. Esta información se guarda de forma estructurada en una base de datos relacional (Azure SQL Database).

#### 2. Pipeline (ETL con Data Factory)
Microsoft Fabric Data Factory se encarga de la orquestación del flujo ETL (Extracción, Transformación y Carga). Su función principal es extraer datos desde la base operativa en Azure SQL y trasladarlos al Data Warehouse para su posterior análisis.

El pipeline ejecuta los siguientes pasos:

- Extracción: Obtiene datos desde tablas transaccionales del sistema (Ventas, Clientes, Modelo, etc.).

- Transformación: Realiza limpieza, estandarización y enriquecimiento de los datos mediante Dataflows.

- Carga: Inserta los datos transformados en el Fabric Data Warehouse, donde se modelan para su análisis.

#### 3. Notebooks con Python (Automatización y Comunicación)

Al finalizar el pipeline, se ejecuta un Notebook desarrollado en Python. Este script tiene como propósito:

- Enviar correos electrónicos de confirmación a los usuarios o administradores.

- Confirmar el éxito del proceso ETL o notificar errores si los hubiera.

- Garantizar trazabilidad, comunicación efectiva y transparencia en las actualizaciones de datos.

#### 4. Seguridad y Automatización

Todo el proceso está diseñado para ejecutarse de forma automatizada y segura, utilizando credenciales protegidas y programaciones que aseguran su ejecución diaria o bajo demanda, reduciendo la intervención manual y errores operativos.


El pipeline llamado "pl_update_table" se ejecuta todos los días a las 6:00 a.m.

![Pipeline: pl-update-table](carpeta-img/Pipeline.jpg)


Notebook: NotificarExitoPipeline

![Notebook: NotificarExitoPipeline](carpeta-img/Notebook.jpg)


Correo electrónico de notificación del éxito del pipeline

![Notebook: NotificarExitoPipeline](carpeta-img/Correo.jpg)


---

## Data Warehouse Layer (Capa de almacén de datos)

### Descripción General

Esta capa constituye el centro estructurado del sistema analítico y recibe los datos procesados desde la capa de ETL mediante Pipelines y Dataflows. Una vez integrados, los datos se almacenan en Azure SQL Database, donde son normalizados y organizados para facilitar su consulta, análisis y visualización.

Dentro de esta capa se construyen las medidas calculadas, relaciones entre tablas clave (como ventas, clientes, modelos y buybacks) y se incorporan dimensiones fundamentales para el análisis empresarial. Destaca la implementación de una tabla calendario, esencial para habilitar análisis temporales precisos (por día, mes, trimestre, año), comparar periodos, y facilitar la segmentación dinámica de datos en Power BI. Esta estructura temporal permite un control detallado de la evolución de ventas, comportamiento del cliente y rendimiento por sede.

Gracias a este diseño optimizado, el Data Warehouse no solo ofrece una base sólida para la inteligencia de negocios, sino que también garantiza escalabilidad, trazabilidad y eficiencia operativa.

Vista del Data Warehouse en Microsoft Fabric

![Warehouse](carpeta-img/DataWarehouse.jpg)

---

## Presentation Layer (Capa de presentación)

### Descripción General

Los informes desarrollados en Power BI constituyen la capa de presentación de esta solución empresarial, permitiendo convertir datos complejos en información clara, visual y accionable. Estos informes fueron diseñados con enfoque ejecutivo y atención al detalle, priorizando la experiencia del usuario final mediante una interfaz intuitiva y moderna.

### Principales características:

- Storytelling con datos: Cada informe sigue una narrativa lógica que facilita la interpretación de los resultados, conectando visualmente las métricas con decisiones estratégicas.

- Análisis descriptivo y predictivo: Se incluyen indicadores clave de rendimiento (KPIs), tendencias de ventas, segmentación por sede, modelos y métodos de pago. Además, se incorporan atributos preatentivos y visualizaciones que permiten detectar patrones de comportamiento del cliente.

- Filtros dinámicos e interacción cruzada: Los usuarios pueden interactuar con los informes filtrando por fechas, sedes, estado de equipos buyback, entre otros, lo que enriquece el análisis.

- Actualización automatizada: Los informes se alimentan directamente desde el Data Warehouse, que a su vez es actualizado por los pipelines automatizados, garantizando información oportuna y confiable.

### Impacto:

Esta capa convierte el ecosistema de datos de iStore en una herramienta de toma de decisiones basada en evidencia. La visualización clara, predictiva y contextualizada potencia la eficiencia operativa y la identificación de oportunidades de mejora continua.

Reportes con Microsoft Power BI:

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

# Conclusión

Este proyecto evidencia el poder de integrar el ecosistema Microsoft —incluyendo Power Apps, Azure SQL, Microsoft Fabric y Power BI— para construir una solución empresarial robusta, escalable y centrada en el usuario. La arquitectura desarrollada no solo optimiza el flujo de datos y la toma de decisiones, sino que también reduce significativamente los tiempos de desarrollo, mejora la trazabilidad y garantiza una operación eficiente con una experiencia de usuario intuitiva y segura.

Además, permite:

✅ Centralizar y gobernar datos de múltiples orígenes en un entorno confiable y accesible.

✅ Automatizar procesos ETL mediante pipelines y notebooks en Fabric, asegurando precisión y agilidad.

✅ Notificar a los usuarios con correos automáticos que refuerzan la trazabilidad y el control operativo.

✅ Facilitar el ingreso de datos con Power Apps, eliminando barreras técnicas para los usuarios finales.

✅ Visualizar y analizar la información con Power BI y Excel, promoviendo la inteligencia de negocio en todos los niveles.

✅ Proteger el acceso a la información, gracias a la gestión de roles y permisos definidos en Azure.

En conjunto, esta solución representa un modelo eficaz de transformación digital con herramientas Microsoft, alineado con los objetivos de eficiencia, crecimiento y experiencia de usuario que exige el entorno empresarial actual.
