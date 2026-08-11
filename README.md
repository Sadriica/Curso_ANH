# Data & GIS para Energía

Curso introductorio de 5 horas que va de archivos de datos sueltos a un mapa de idoneidad para un
proyecto de energía renovable. Nivel básico y autocontenido.

Todo corre en el navegador con Google Colab: no hay que instalar nada, solo hace falta una cuenta
de Google. También funciona en Jupyter local.

- Público: ANH y ministerios (MinCiencias, Energía, Departamento Nacional de Planeación).
- Duración: 5 horas, de 8:00 am a 1:00 pm, en 4 módulos.
- Requisitos previos: ninguno de programación.

## Antes de empezar

| Documento | Contenido |
|---|---|
| [Guía de Colab](guia_colab.md) | Cómo abrir y ejecutar los notebooks, y qué hacer si algo falla. |
| [Glosario](glosario.md) | Términos del curso en lenguaje sencillo: CRS, EPSG, H3, AHP, TOPSIS, idoneidad. |
| [Temario](temario.md) | Programa completo y notas de organización. |

## Módulos

Cada módulo tiene un notebook con la práctica, unas diapositivas de apoyo (2 o 3 por tema, con
notas y tiempos para el instructor) y una carpeta `recursos/` con los datos de entrada y los
resultados ya calculados, como respaldo por si algún paso falla durante la sesión. El Módulo 2
añade además un temario detallado.

### Módulo 1. SIG

Qué es un SIG y para qué sirve en energía. Geodesia básica (coordenadas y sistemas de referencia)
y las dos estructuras de datos que se usan en todo el curso: vector y raster.

[Notebook](modulo1_sig/modulo1_sig.ipynb) · [Diapositivas](modulo1_sig/diapositivas.md)

### Módulo 2. Datos

Fundamentos de Python y pandas. Transformación entre formatos (CSV, Excel, GeoJSON, Shapefile,
GeoTIFF), unificación de fuentes en un mismo CRS y mapeo sobre una malla hexagonal H3.

[Notebook](modulo2_datos/modulo2_datos.ipynb) · [Diapositivas](modulo2_datos/diapositivas.md) ·
[Temario detallado](modulo2_datos/temario.md)

### Módulo 3. Multicriterio

Normalización de criterios (beneficio y costo), suma ponderada, AHP con comparaciones por pares y
razón de consistencia, y TOPSIS. Cierra comparando los tres métodos sobre los mismos datos.

[Notebook](modulo3_multicriterio/modulo3_multicriterio.ipynb) ·
[Diapositivas](modulo3_multicriterio/diapositivas.md)

### Módulo 4. Taller

Integra los módulos anteriores: producir un mapa de idoneidad para un proyecto eólico en el norte
de Colombia, partiendo de fuentes en distintos formatos y sistemas de coordenadas (EPSG:9377 en
metros y EPSG:4326 en grados). Unificar, generar la malla, mapear, visualizar y decidir con AHP.

[Notebook](modulo4_taller/modulo4_taller.ipynb) · [Diapositivas](modulo4_taller/diapositivas.md)

## El hilo del curso

```
datos crudos  ->  mismo CRS  ->  malla H3  ->  criterios normalizados  ->  pesos (AHP)  ->  idoneidad
  (Mod. 2)        (Mod. 2)      (Mod. 2)           (Mod. 3)               (Mod. 3)        (Mod. 4)
```

El Módulo 1 aporta los conceptos, los módulos 2 y 3 construyen el flujo por partes y el Módulo 4
lo recorre entero.

## Tecnologías

- Lenguaje: Python 3.
- Entorno: Google Colab o Jupyter local.
- Tablas: pandas, numpy.
- Datos geográficos: geopandas (con shapely, pyproj y fiona/pyogrio por debajo), rasterio para
  GeoTIFF.
- Malla: h3 versión 4 (`h3>=4.1`).
- Visualización: matplotlib para gráficos estáticos, folium con branca y mapclassify para mapas
  interactivos.
- Formatos: CSV, Excel, GeoJSON, Shapefile, GeoTIFF, Parquet.
- CRS: EPSG:4326 (grados) y EPSG:9377 (metros, oficial de Colombia).

Cada notebook instala sus dependencias en la primera celda, por ejemplo:

```python
!pip install -q geopandas "h3>=4.1" folium mapclassify rasterio openpyxl
```

## Cómo usar el material

Como participante: abra el notebook del módulo con el botón "Open in Colab" que aparece en su
primera celda y ejecute las celdas en orden, de arriba hacia abajo (Shift + Enter). Hacia el final
de cada módulo hay una sección "Actividad individual" con un ejercicio corto: en los módulos 1, 2
y 3 la solución viene desplegable justo debajo, y en el 4 se describe el resultado esperado. Para
guardar los cambios: Archivo > Guardar una copia en Drive.

Como instructor: los archivos `diapositivas.md` de cada módulo son el guion de exposición, con
tiempos sugeridos en las notas finales; el notebook es la demostración. El taller del Módulo 4 se
ejecuta completo en clase.

Sin conexión o sin cuenta de Google: los notebooks son autocontenidos, generan sus propios datos
sintéticos y corren igual en Jupyter local. Los archivos de `recursos/` sirven de respaldo.

## Estructura del repositorio

```
.
├── README.md
├── temario.md                  Programa del curso
├── guia_colab.md               Cómo usar Colab
├── glosario.md                 Términos clave
├── modulo1_sig/
│   ├── modulo1_sig.ipynb
│   ├── diapositivas.md
│   └── recursos/               elevacion.tif, puntos_ciudades.geojson
├── modulo2_datos/
│   ├── modulo2_datos.ipynb
│   ├── diapositivas.md
│   ├── temario.md              Temario detallado del módulo
│   └── recursos/               municipios.{csv,xlsx,geojson}, municipios_shp/,
│                               radiacion_solar.csv, viento.tif, malla_h3.parquet
├── modulo3_multicriterio/
│   ├── modulo3_multicriterio.ipynb
│   ├── diapositivas.md
│   └── recursos/               malla_h3.parquet, resultado_idoneidad.h3.parquet,
│                               comparativa_metodos.png
└── modulo4_taller/
    ├── modulo4_taller.ipynb
    ├── diapositivas.md
    └── recursos/               fuente_viento_9377.geojson, fuente_radiacion_4326.csv,
                                resultado_idoneidad.h3.parquet, mapa_idoneidad.png
```
