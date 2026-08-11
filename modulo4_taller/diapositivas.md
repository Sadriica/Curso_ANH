# Diapositivas clave. Módulo 4: Taller
### Curso: Data & GIS para Energía

Guía de apoyo. El taller se hace en el notebook
[`modulo4_taller.ipynb`](modulo4_taller.ipynb) (Colab), corriéndolo en clase.

---

## Portada
- Objetivo: producir un mapa de idoneidad para un proyecto eólico en el norte de Colombia.
- Reúne todo lo anterior: datos, unificación, malla y decisión multicriterio.
- Los datos llegan como en la vida real: distintos formatos y sistemas de coordenadas.

---

## Paso 1. Las fuentes
- Fuente A (viento y vías): puntos en EPSG:9377 (metros).
- Fuente B (radiación): tabla en EPSG:4326 (grados).
- Vienen en sistemas distintos, así que no se pueden cruzar directamente.

## Paso 2. Unificar
- Llevar todo al mismo sistema de coordenadas (EPSG:4326) con `to_crs`.
- Sin este paso, los puntos no coinciden.

## Paso 3. Generar la malla
- Malla H3 sobre la zona de estudio (`geo_to_cells`). Celdas iguales y con código único.

## Paso 4. Mapear
- Cada sitio a su celda H3; se resume por celda y se unen las dos fuentes en una tabla por celda.

## Paso 5. Visualizar
- Mapa de las celdas con dato para verificar que la unificación y el mapeo quedaron bien.

## Paso 6. Decidir (AHP)
- Normalizar criterios, pesos por comparación por pares y puntaje de idoneidad por celda.
- Mapa final coloreado (rojo = más idóneo).

---

## Cierre
- Es el mismo flujo del proyecto real, a pequeña escala.
- Para llevarlo más lejos: más criterios, más resolución, exclusiones y datos reales por municipio.
- Actividad: cambiar los pesos AHP y observar cómo cambia el mapa.

---

### Notas para el instructor
- Tiempo sugerido: 60 min, ejecutando el notebook en clase y discutiendo cada paso.
- Autocontenido: genera las fuentes y no depende de los otros notebooks.
- En `recursos/` están las fuentes crudas (una en 9377, otra en 4326) y el resultado ya calculado
  en el formato de trabajo (`resultado_idoneidad.h3.parquet`, `mapa_idoneidad.png`) por si falla algún render en vivo.
- Actividad (cambiar pesos AHP): al subir el peso de la cercanía a vías, los sitios bien conectados
  (Riohacha, Barranquilla) escalan y los de la alta Guajira (Uribia, Manaure) bajan. Sirve para
  discutir por qué justificar los pesos es parte de la decisión.
