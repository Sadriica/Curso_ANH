# Glosario

Términos que aparecen en el curso, en lenguaje sencillo.

## Datos geográficos

- **SIG (Sistema de Información Geográfica):** conjunto de herramientas para guardar, analizar y
  visualizar datos que tienen una ubicación.
- **Capa:** un conjunto de datos de un mismo tipo puesto sobre el mapa (una capa de vías, otra de
  ríos, otra de viento).
- **Geometría:** la parte que dice *dónde* está un dato: un punto, una línea o un polígono.
- **Atributo:** la parte que dice *qué* o *cuánto*: nombre, población, velocidad de viento.
- **Vector:** datos como geometrías discretas (puntos, líneas, polígonos). Formatos: Shapefile,
  GeoJSON, GeoPackage.
- **Raster:** datos como una grilla de celdas, cada una con un valor. Sirve para variables
  continuas (elevación, viento, radiación). Formato típico: GeoTIFF (`.tif`).

## Coordenadas

- **Coordenadas:** los números que ubican un punto (por ejemplo, latitud y longitud).
- **CRS (Sistema de Referencia de Coordenadas):** las reglas que dan sentido a esas coordenadas.
  Sin CRS, un par de números no ubica nada.
- **EPSG:** un catálogo de CRS, cada uno con un número. Los dos que más se usan aquí:
  - **EPSG:4326:** latitud/longitud en **grados**. Estándar de GPS y de la mayoría de datos.
  - **EPSG:9377:** coordenadas planas en **metros**, oficial de Colombia. Se usa para medir
    distancias y áreas.
- **Reproyectar:** convertir datos de un CRS a otro (por ejemplo, de grados a metros para poder
  medir).

## Malla y celdas

- **Malla:** una cuadrícula (aquí, de hexágonos) que cubre la zona de estudio y sobre la cual se
  ponen los datos. Permite comparar y cruzar fuentes en una unidad común.
- **H3:** un sistema de malla hexagonal (creado por Uber). Divide el mundo en hexágonos de tamaño
  casi igual, cada uno con un **código único** (`h3_index`).
- **Resolución (H3):** el tamaño del hexágono. Mayor resolución, celdas más pequeñas.

## Toma de decisiones (multicriterio)

- **Criterio:** una variable que pesa en la decisión (viento, distancia a vías, radiación).
- **Beneficio / costo:** sentido de un criterio. *Beneficio* = más es mejor (viento). *Costo* =
  menos es mejor (distancia a una vía).
- **Normalización:** llevar criterios en unidades distintas a una escala común (0 a 1) para poder
  combinarlos.
- **Peso:** cuánto importa cada criterio en el puntaje final. Los pesos suman 1.
- **Suma ponderada:** combinar los criterios normalizados multiplicando cada uno por su peso y
  sumando.
- **AHP (Analytic Hierarchy Process):** método que deriva los pesos a partir de **comparaciones
  por pares** entre criterios, y permite chequear si los juicios fueron **consistentes** (razón de
  consistencia CR; se acepta CR < 0.1).
- **TOPSIS:** método que puntúa cada alternativa por su **cercanía a la solución ideal** y lejanía
  de la peor.
- **Exclusión:** zona donde el proyecto no va (área protegida, restricción). En el modelo del
  proyecto se marca y no recibe puntaje.
- **Idoneidad:** el puntaje final que resume qué tan apta es una zona para el proyecto.
