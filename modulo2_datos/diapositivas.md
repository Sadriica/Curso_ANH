# Diapositivas clave. Módulo 2: Datos
### Curso: Data & GIS para Energía

Guía de 2 o 3 diapositivas por tema. El detalle y la práctica van en el notebook
[`modulo2_datos.ipynb`](modulo2_datos.ipynb) (Colab). Nivel básico, público ANH y ministerios.

---

## Portada
- Data & GIS para Energía. Módulo 2: Datos.
- Objetivo: pasar de archivos sueltos a un mapa comparable para decidir dónde conviene un proyecto de energía.
- Herramienta: Google Colab. No se instala nada, corre en el navegador.

---

## Tema 1. Fundamentos de programación

**1.1 ¿Por qué programar?**
- Excel se queda corto con muchos datos y con mapas.
- Python son instrucciones simples, paso a paso. Es reproducible y gratuito.

**1.2 Las librerías clave**
- pandas para tablas, geopandas para tablas con geometría, h3 para la malla, folium para mapas.
- Son código ya hecho: se importan y se usan.

**1.3 Una tabla (DataFrame)**
- Filas y columnas como en una hoja de cálculo, pero programable: filtrar, ordenar, calcular.
- Ejemplo: viento por municipio y un gráfico de barras.

---

## Tema 2. Transformación de archivos

**2.1 Los formatos que se van a ver**
- CSV y Excel para tablas. GeoJSON y shapefile para geometrías. GeoTIFF para raster (una grilla de valores).
- Cada uno se abre con su librería; el contenido es el mismo tipo de dato.

**2.2 De tabla a mapa**
- Una tabla con lat/lon se convierte en puntos geográficos (GeoDataFrame).
- Guardar y leer entre formatos es una línea de código.
- Ejemplo: de CSV a GeoDataFrame a GeoJSON, y mapa de puntos.

---

## Tema 3. Unificación

**3.1 El problema**
- Los datos vienen de fuentes distintas y en sistemas de coordenadas distintos.
- Si se mezclan sistemas, los puntos no coinciden.

**3.2 Dos pasos**
1. Mismo sistema de coordenadas (reproyectar): metros (EPSG:9377) y grados (EPSG:4326).
2. Unir por una llave común (código de municipio) con merge.
- Ejemplo: reproyectar y unir viento con radiación solar.

**3.3 Resultado**
- Una sola tabla, alineada geográficamente, lista para analizar.

---

## Tema 4. Mapeo en malla (H3)

**4.1 ¿Por qué una malla?**
- Municipios de tamaños muy distintos son difíciles de comparar.
- Se divide el territorio en celdas iguales (hexágonos H3): comparables y con código único.

**4.2 Cómo funciona**
- Cada dato cae en una celda (`latlng_to_cell`). Se resume por celda (promedio).
- La resolución controla el tamaño del hexágono.

**4.3 Visualización**
- Cada celda es un polígono coloreado por su valor (azul a rojo, poco a mucho viento).
- Ejemplo: mapa interactivo con folium y relleno de una zona completa con la malla.

---

## Cierre. Puente al taller
- Con todo en la misma malla y comparable, el paso siguiente es combinar variables
  (viento, distancia a vías, población) para decidir dónde conviene. Ese es el módulo de multicriterio (AHP).
- Actividad en clase: cambiar la resolución H3 de 5 a 6 y observar el efecto.

---

### Notas para el instructor
- Tiempo sugerido: 55 min aprox. (15 fundamentos, 15 transformación, 10 unificación, 15 malla).
- Ejecutar el notebook en clase, celda por celda (Shift+Enter). Cada asistente con su copia en Colab.
- Todo es sintético y autocontenido: no depende de internet ni de archivos externos.
- La lógica es la misma del proyecto real (malla H3 y unificación), simplificada.
