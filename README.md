# Estructuras de Datos Geoespaciales

---

## SECCIÓN EN ESPAÑOL

### Título del Proyecto

**Estructuras de Datos Geoespaciales: Creación y Manipulación de Geometrías Espaciales**

### Descripción General

Este proyecto es un conjunto integral de ejercicios prácticos diseñados para enseñar la creación, manipulación y conversión de estructuras de datos geoespaciales utilizando múltiples lenguajes de programación: R, Python y Julia. El objetivo principal es comprender los fundamentos del análisis vectorial geoespacial, incluyendo la construcción de objetos geométricos básicos (puntos, líneas y polígonos), la conversión de datos tabulares tradicionales a tablas espaciales con sistemas de referencia de coordenadas, y la importancia crítica de mantener coherencia en el orden de las coordenadas (Longitud, Latitud) en operaciones geoespaciales.

El proyecto enfatiza la diferencia fundamental entre sistemas de coordenadas geográficas (EPSG:4326, medidas en grados) y sistemas de coordenadas proyectadas (EPSG:9377, medidas en metros), demostrando por qué es imprescindible usar sistemas proyectados para cálculos precisos de áreas y distancias en aplicaciones de ingeniería territorial y planeamiento urbano.

### Análisis Técnico

Este proyecto se enfoca principalmente en **análisis vectorial geoespacial**. Los ejercicios cubren:

- **Creación de Geometrías Vectoriales**: Construcción de objetos geométricos primitivos (Point, LineString, Polygon) utilizando las coordenadas de referencia estándar del orden cartesiano (X, Y).
- **Análisis de Topología**: Estudio de la topología del Río Cauca mediante la creación de puntos que representan estaciones de monitoreo y líneas que conectan estas estaciones.
- **Conversión de Datos**: Transformación de estructuras de datos tabulares (DataFrames) en estructuras de datos espaciales (GeoDataFrames, GeoTables) con sistemas de referencia de coordenadas explícitos.
- **Gestión de Sistemas de Referencia de Coordenadas (CRS)**: Comprensión de EPSG:4326 (WGS84 - coordenadas geográficas) y EPSG:9377 (Magna-Sirgas - sistema de coordenadas proyectado nacional).

### Estructura del Repositorio

#### **datos_geoespaciales.qmd**
Archivo principal del proyecto en formato Quarto que contiene:
- Documentación teórica e instructiva sobre estructuras de datos geoespaciales
- **Ejercicio 1 - Topología del Río Cauca**: Creación de objetos Point y LineString para representar estaciones de monitoreo de calidad del agua en el Río Cauca. Incluye ejemplos de implementación en Python, R y Julia.
- **Ejercicio 2 - Conversión de Datos Tabulares a Espaciales**: Transformación de un DataFrame tradicional con información de barrios en riesgo de inundación a una tabla espacial con sistema de referencia de coordenadas WGS84 (EPSG:4326). También con implementaciones multilenguaje.
- Explicaciones sobre la importancia del orden de coordenadas (Longitud, Latitud) en operaciones geoespaciales
- Análisis de por qué es inapropiado utilizar EPSG:4326 para cálculos de áreas y la solución que proporciona EPSG:9377

#### **j_eval_j_plot.r**
Motor de interoperabilidad geomática que actúa como puente entre R y Julia. Este script proporciona:
- `j_eval()`: Función que ejecuta código Julia desde R, con análisis léxico avanzado para manejo de strings, comentarios multilínea y bloques de código.
- `j_plot()`: Función especializada para generar visualizaciones geoespaciales en Julia y renderizarlas en formato PNG desde R.
- `.j_render_output()`: Función auxiliar que formatea la salida de Julia para presentación en diferentes formatos (HTML, PDF, consola).
- Soporte completo para integración transparente entre ecosistemas de R y Julia

### Dependencias

#### **Dependencias en R**
- **sf**: Librería principal para manipulación de datos vectoriales y geometrías espaciales. Proporciona funciones como `st_point()`, `st_linestring()`, `st_as_sf()`, y `st_as_text()`.
- **sfheaders**: Utilidades para facilitar la creación de estructuras sf a partir de datos simples.
- **JuliaConnectoR**: Conexión bidireccional entre R y Julia, permitiendo ejecutar código Julia desde R.
- **png**: Lectura y procesamiento de imágenes PNG generadas por Julia.
- **grid**: Sistema gráfico de bajo nivel de R para la visualización de imágenes.
- **knitr**: Motor de procesamiento dinámico para documentos Quarto, utilizado en la renderización.

#### **Dependencias en Python**
- **geopandas**: DataFrames con soporte geoespacial, extiende pandas para incluir geometrías.
- **shapely**: Geometrías euclidanas (Point, LineString, Polygon) con operaciones topológicas.
- **pandas**: Manipulación y análisis de datos tabulares.

#### **Dependencias en Julia**
- **LibGEOS**: Bindings a la librería GEOS (Geometry Engine Open Source) para operaciones geométricas.
- **DataFrames**: Tablas tabulares en Julia análogas a las de R y Python.
- **GeoTables**: DataFrames con soporte para datos geoespaciales en Julia.
- **Meshes**: Tipos de geometrías y operaciones geométricas primitivas.
- **Printf**: Utilidades de formateo de texto (estándar de Julia).

### Instrucciones de Ejecución

#### **Requisitos Previos**
Asegúrate de tener instalados:
- R (versión 4.0 o superior)
- RStudio o un IDE compatible con Quarto
- Python 3.8 o superior (para ejemplos en Python)
- Julia 1.8 o superior (para ejemplos en Julia)
- Quarto CLI

#### **Instalación de Dependencias en R**

```r
# Instalar dependencias de CRAN
install.packages(c("sf", "sfheaders", "knitr", "png", "grid"))

# Instalar JuliaConnectoR desde GitHub
remotes::install_github("stefan-m-lenz/JuliaConnectoR")
```

#### **Instalación de Dependencias en Python**

```bash
pip install geopandas shapely pandas
```

#### **Instalación de Dependencias en Julia**

```julia
using Pkg
Pkg.add(["LibGEOS", "DataFrames", "GeoTables", "Meshes"])
```

#### **Ejecución del Flujo de Trabajo**

1. **Visualizar el documento Quarto**:
   ```bash
   quarto preview datos_geoespaciales.qmd
   ```
   Esto renderizará el documento interactivo en HTML con la capacidad de visualizar todos los ejercicios.

2. **Renderizar a HTML**:
   ```bash
   quarto render datos_geoespaciales.qmd --to html
   ```
   Genera un archivo `datos_geoespaciales.html` autocontenido.

3. **Renderizar a PDF**:
   ```bash
   quarto render datos_geoespaciales.qmd --to pdf
   ```
   Genera un documento PDF profesional con toda la documentación y ejercicios.

4. **Ejecutar desde RStudio**:
   - Abrir `datos_geoespaciales.qmd` en RStudio
   - Presionar `Ctrl+Shift+K` (Windows/Linux) o `Cmd+Shift+K` (Mac) para renderizar
   - Usar el botón "Render" en la barra de herramientas

#### **Notas Importantes**

- El archivo `j_eval_j_plot.r` se carga automáticamente mediante `source()` al inicio del documento Quarto.
- Los ejemplos de Julia se ejecutan dinámicamente mediante las funciones `j_eval()` y `j_plot()` desde dentro de R.
- La configuración de WGS84 (EPSG:4326) es la predeterminada para sistemas de referencia en ejemplos de conversión de datos.
- Para proyectos que requieran cálculos de áreas y distancias precisos en Colombia, considera cambiar a EPSG:9377 (Magna-Sirgas/Origen Nacional).

### Contexto Educativo

Este material forma parte del curso **"Programación en SIG: R, Python y Julia"** de la Maestría en Geomática de la Universidad Nacional de Colombia, bajo la dirección del docente Alexys Rodríguez-Avellaneda (2026).

---

## ENGLISH SECTION

### Project Title

**Geospatial Data Structures: Creation and Manipulation of Spatial Geometries**

### General Description

This project is a comprehensive set of practical exercises designed to teach the creation, manipulation, and conversion of geospatial data structures using multiple programming languages: R, Python, and Julia. The main objective is to understand the fundamentals of geospatial vector analysis, including the construction of basic geometric objects (points, lines, and polygons), the conversion of traditional tabular data into spatial tables with coordinate reference systems, and the critical importance of maintaining consistency in the order of coordinates (Longitude, Latitude) in geospatial operations.

The project emphasizes the fundamental difference between geographic coordinate systems (EPSG:4326, measured in degrees) and projected coordinate systems (EPSG:9377, measured in meters), demonstrating why it is essential to use projected systems for precise area and distance calculations in territorial engineering and urban planning applications.

### Technical Analysis

This project focuses primarily on **geospatial vector analysis**. The exercises cover:

- **Creation of Vector Geometries**: Construction of primitive geometric objects (Point, LineString, Polygon) using standard Cartesian coordinate order reference (X, Y).
- **Topology Analysis**: Study of the topology of the Cauca River through the creation of points representing monitoring stations and lines connecting these stations.
- **Data Conversion**: Transformation of tabular data structures (DataFrames) into spatial data structures (GeoDataFrames, GeoTables) with explicit coordinate reference systems.
- **Coordinate Reference System (CRS) Management**: Understanding EPSG:4326 (WGS84 - geographic coordinates) and EPSG:9377 (Magna-Sirgas - national projected coordinate system).

### Repository Structure

#### **datos_geoespaciales.qmd**
Main project file in Quarto format that contains:
- Theoretical and instructive documentation on geospatial data structures
- **Exercise 1 - Cauca River Topology**: Creation of Point and LineString objects to represent water quality monitoring stations on the Cauca River. Includes implementation examples in Python, R, and Julia.
- **Exercise 2 - Converting Tabular Data to Spatial**: Transformation of a traditional DataFrame with information about neighborhoods at flood risk into a spatial table with WGS84 coordinate reference system (EPSG:4326). Also with multilingual implementations.
- Explanations on the importance of coordinate order (Longitude, Latitude) in geospatial operations
- Analysis of why it is inappropriate to use EPSG:4326 for area calculations and the solution provided by EPSG:9377

#### **j_eval_j_plot.r**
Geospatial interoperability engine that acts as a bridge between R and Julia. This script provides:
- `j_eval()`: Function that executes Julia code from R, with advanced lexical analysis for handling strings, multiline comments, and code blocks.
- `j_plot()`: Specialized function for generating geospatial visualizations in Julia and rendering them in PNG format from R.
- `.j_render_output()`: Auxiliary function that formats Julia output for presentation in different formats (HTML, PDF, console).
- Full support for seamless integration between R and Julia ecosystems

### Dependencies

#### **R Dependencies**
- **sf**: Primary library for spatial vector data manipulation and geometries. Provides functions such as `st_point()`, `st_linestring()`, `st_as_sf()`, and `st_as_text()`.
- **sfheaders**: Utilities to facilitate the creation of sf structures from simple data.
- **JuliaConnectoR**: Bidirectional connection between R and Julia, allowing Julia code execution from R.
- **png**: Reading and processing of PNG images generated by Julia.
- **grid**: Low-level graphic system in R for image visualization.
- **knitr**: Dynamic document processing engine for Quarto rendering.

#### **Python Dependencies**
- **geopandas**: DataFrames with geospatial support, extending pandas to include geometries.
- **shapely**: Euclidean geometries (Point, LineString, Polygon) with topological operations.
- **pandas**: Manipulation and analysis of tabular data.

#### **Julia Dependencies**
- **LibGEOS**: Bindings to the GEOS library (Geometry Engine Open Source) for geometric operations.
- **DataFrames**: Tabular tables in Julia analogous to those in R and Python.
- **GeoTables**: DataFrames with support for geospatial data in Julia.
- **Meshes**: Primitive geometry types and geometric operations.
- **Printf**: Text formatting utilities (Julia standard library).

### Execution Instructions

#### **Prerequisites**
Make sure you have installed:
- R (version 4.0 or higher)
- RStudio or an IDE compatible with Quarto
- Python 3.8 or higher (for Python examples)
- Julia 1.8 or higher (for Julia examples)
- Quarto CLI

#### **Installation of R Dependencies**

```r
# Install CRAN dependencies
install.packages(c("sf", "sfheaders", "knitr", "png", "grid"))

# Install JuliaConnectoR from GitHub
remotes::install_github("stefan-m-lenz/JuliaConnectoR")
```

#### **Installation of Python Dependencies**

```bash
pip install geopandas shapely pandas
```

#### **Installation of Julia Dependencies**

```julia
using Pkg
Pkg.add(["LibGEOS", "DataFrames", "GeoTables", "Meshes"])
```

#### **Workflow Execution**

1. **View the Quarto document**:
   ```bash
   quarto preview datos_geoespaciales.qmd
   ```
   This will render the interactive document in HTML with the ability to view all exercises.

2. **Render to HTML**:
   ```bash
   quarto render datos_geoespaciales.qmd --to html
   ```
   Generates a self-contained `datos_geoespaciales.html` file.

3. **Render to PDF**:
   ```bash
   quarto render datos_geoespaciales.qmd --to pdf
   ```
   Generates a professional PDF document with all documentation and exercises.

4. **Execute from RStudio**:
   - Open `datos_geoespaciales.qmd` in RStudio
   - Press `Ctrl+Shift+K` (Windows/Linux) or `Cmd+Shift+K` (Mac) to render
   - Use the "Render" button in the toolbar

#### **Important Notes**

- The `j_eval_j_plot.r` file is automatically loaded via `source()` at the beginning of the Quarto document.
- Julia examples are executed dynamically through the `j_eval()` and `j_plot()` functions from within R.
- WGS84 configuration (EPSG:4326) is the default for coordinate reference systems in data conversion examples.
- For projects requiring precise area and distance calculations in Colombia, consider switching to EPSG:9377 (Magna-Sirgas/National Origin).

### Educational Context

This material is part of the course **"Programming in GIS: R, Python, and Julia"** of the Master's in Geomatics at the National University of Colombia, under the direction of Professor Alexys Rodríguez-Avellaneda (2026).
