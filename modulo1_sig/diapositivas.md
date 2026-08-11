# Diapositivas clave. Módulo 1: SIG
### Curso: Data & GIS para Energía

Guía de 2 o 3 diapositivas por tema. La práctica va en el notebook
[`modulo1_sig.ipynb`](modulo1_sig.ipynb) (Colab). Nivel básico, público ANH y ministerios.

---

## Portada
- ¿Qué es un SIG y por qué importa en energía?
- Módulo introductorio: conceptos y dos temas técnicos base (geodesia y estructuras de datos).

---

## Tema 1. ¿Qué es un SIG?

**1.1 Datos con ubicación**
- Un SIG guarda, analiza y visualiza datos que tienen un lugar.
- Cada dato es un valor en una posición, no solo un número.

**1.2 Capas, geometría y atributos**
- La información se organiza en capas (vías, ríos, viento).
- Cada elemento tiene geometría (dónde) y atributos (qué / cuánto).

---

## Tema 2. Casos de aplicación

**2.1 En el sector energético**
- Ubicación de proyectos (eólico, solar).
- Redes e infraestructura (transmisión, subestaciones, vías, puertos).
- Riesgo y ambiente (amenazas, áreas protegidas, comunidades).

**2.2 El hilo del curso**
- Decidir dónde conviene un proyecto combinando varias capas. Se construye módulo a módulo.

---

## Tema 3. Geodesia

**3.1 Coordenadas y CRS**
- La Tierra no es plana; para ubicar se usan coordenadas y un sistema de referencia (CRS).
- EPSG:4326: grados (lat/lon), estándar GPS. EPSG:9377: metros, oficial de Colombia.

**3.2 Grados vs metros**
- En grados no se mide distancia directamente.
- Para medir hay que reproyectar a metros. Ejemplo en el notebook, con la misma pareja de puntos.

---

## Tema 4. Fuentes y estructuras de datos

**4.1 Dos estructuras**
- Vector: puntos, líneas, polígonos (Shapefile, GeoJSON, GeoPackage).
- Raster: una grilla de valores, para variables continuas (GeoTIFF).

**4.2 Fuentes**
- DANE (división administrativa, censo), IDEAM (clima), geoportales de entidades.

---

## Cierre. Puente al Módulo 2
- Con las bases cubiertas (SIG, geodesia, estructuras), el Módulo 2 maneja los datos con Python:
  leer, unificar y llevar a una malla común.

---

### Notas para el instructor
- Tiempo sugerido: 45 min. Es el módulo más conceptual; apoyarlo con el mapa y los dos ejemplos
  del notebook.
- Autocontenido; en `recursos/` hay un vector de ejemplo (`puntos_ciudades.geojson`) y un raster (`elevacion.tif`).
