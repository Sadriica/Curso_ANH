# Temario detallado. Módulo 2: Datos
### Curso: Data & GIS para Energía

Duración estimada: 55 a 60 minutos. Todo en Google Colab, con datos sintéticos autocontenidos.
Notebook: [`modulo2_datos.ipynb`](modulo2_datos.ipynb).

**Requisitos previos:** ninguno de programación. Solo una cuenta de Google para Colab.

**Tecnologías del módulo (visión general):**
- Lenguaje: Python 3.
- Entorno: Google Colab (notebooks en la web).
- Tablas: pandas, numpy.
- Datos geográficos: geopandas (usa shapely, pyproj, fiona/pyogrio por debajo).
- Malla hexagonal: h3 (versión 4).
- Visualización: matplotlib (estática), folium con branca (mapas interactivos).
- Formatos: CSV, Excel, GeoJSON, Shapefile, GeoTIFF, y sistemas de coordenadas EPSG (4326, 9377).

---

## 2.0 Preparación (5 min)
- Qué es un notebook y cómo se ejecutan las celdas (Shift+Enter, de arriba a abajo).
- Instalar librerías en Colab con `pip` (geopandas, h3, folium).
- Importar librerías (`import`).
- Tecnologías: Google Colab, pip.

## 2.1 Fundamentos de programación (15 min)
- Programar es dar instrucciones a la máquina, paso a paso.
- Variables y tipos básicos: número, texto, booleano.
- Listas y recorrerlas con un bucle `for` (y `zip` para ir en paralelo).
- Funciones y librerías: qué es `import` y para qué sirve.
- pandas y el DataFrame:
  - Crear una tabla.
  - Filtrar filas por una condición.
  - Ordenar.
  - Crear una columna derivada (ej. "apto eólico" si viento >= 7 m/s).
- Un gráfico de barras simple.
- Tecnologías: Python (variables, listas, `for`, funciones), pandas (DataFrame), matplotlib.

## 2.2 Transformación de archivos (15 min)
- Panorama de formatos y cuándo se usa cada uno:
  - CSV / Excel: tablas.
  - GeoJSON / Shapefile: geometrías (puntos, líneas, polígonos) con atributos.
  - GeoTIFF: raster, una grilla de valores (ej. un mapa de viento).
- Leer y escribir CSV (`read_csv`, `to_csv`).
- De tabla a mapa: construir un GeoDataFrame con `points_from_xy` y asignar el CRS.
- Guardar y volver a leer en GeoJSON y Shapefile (`to_file`, `read_file`).
- El shapefile son varios archivos juntos y recorta los nombres de columna a 10 caracteres.
- Un mapa estático de los puntos.
- Tecnologías: pandas (`read_csv`/`to_csv`), geopandas (`GeoDataFrame`, `points_from_xy`, `to_file`, `read_file`), shapely (geometría), matplotlib.

## 2.3 Unificación (10 min)
- El problema: fuentes distintas, en sistemas de coordenadas distintos, que no coinciden.
- Sistemas de coordenadas (CRS) y códigos EPSG:
  - EPSG:4326 (grados, latitud/longitud).
  - EPSG:9377 (metros, oficial de Colombia).
- Reproyectar: pasar de un CRS a otro con `to_crs`.
- Unir tablas por una llave común (ej. código de municipio) con `merge` (idea de join).
- Resultado: una sola tabla alineada y lista para analizar.
- Tecnologías: geopandas (`to_crs`) apoyado en pyproj, pandas (`merge`).

## 2.4 Mapeo en malla H3 (15 min)
- Por qué una malla: comparar unidades de tamaños distintos es difícil; las celdas iguales son comparables.
- Qué es H3: malla de hexágonos, cada celda con un código único, y el concepto de resolución.
- Asignar cada punto a su celda (`latlng_to_cell`).
- Agregar valores por celda (promedio) con `groupby`.
- Dibujar cada celda como polígono (`cell_to_boundary`) y colorearla por su valor.
- Mapa interactivo con folium y una escala de color (branca).
- Rellenar una zona completa con la malla (`geo_to_cells`).
- Tecnologías: h3 v4 (`latlng_to_cell`, `cell_to_boundary`, `geo_to_cells`), pandas (`groupby`), folium, branca (escala de color).

## 2.5 Cierre y puente (5 min)
- Repaso del flujo: datos, transformación, unificación, malla.
- Cómo esto alimenta el análisis multicriterio (módulo 3, AHP).
- Actividad en clase: cambiar la resolución H3 de 5 a 6 y observar el efecto en el tamaño y el número de celdas.

---

### Resultado de aprendizaje
Al terminar el módulo, la persona puede: cargar datos, convertirlos entre formatos, llevarlos
a un mismo sistema de coordenadas, unir varias fuentes y mapear todo en una malla H3 para
visualizarlo. Es el insumo del análisis de decisión que viene después.
