# Diapositivas clave. Módulo 3: Multicriterio (AHP)
### Curso: Data & GIS para Energía

Guía de 2 o 3 diapositivas por tema. La práctica va en el notebook
[`modulo3_multicriterio.ipynb`](modulo3_multicriterio.ipynb) (Colab). Nivel básico.

---

## Portada
- ¿Cómo decidir dónde conviene un proyecto de energía?
- No basta una variable: pesan el viento, el acceso, la infraestructura y lo social.
- Los métodos multicriterio dan un único puntaje de idoneidad a partir de varios criterios con pesos.

---

## Tema 1. Punto de partida

**1.1 De los datos a la decisión**
- Retomamos la tabla del Módulo 2: cada municipio es una alternativa, cada variable un criterio.
- Criterios de ejemplo: viento (beneficio), distancia a vías (costo), radiación (beneficio).

**1.2 Beneficio vs costo**
- Beneficio: más es mejor (viento, radiación).
- Costo: menos es mejor (distancia a una vía).

---

## Tema 2. Normalización

**2.1 El problema de las unidades**
- Los criterios están en m/s, km, kWh. No se pueden sumar directamente.

**2.2 Escala común 0 a 1**
- Se normaliza cada criterio a 0 a 1, donde 1 es siempre lo mejor.
- En los criterios de costo se invierte (menos = más cerca de 1).

---

## Tema 3. Suma ponderada

**3.1 En qué consiste**
- A cada criterio se le da un peso, los pesos suman 1, y el puntaje es la suma ponderada.
- Es simple y transparente; la dificultad está en justificar los pesos.

**3.2 Resultado**
- Un puntaje por alternativa y un ranking. Ejemplo en el notebook.

---

## Tema 4. AHP

**4.1 Pesos por comparación por pares**
- En vez de fijar los pesos directamente, se compara criterio contra criterio en una escala de 1 a 9.
- De esa matriz salen los pesos.

**4.2 Consistencia**
- AHP mide si los juicios fueron coherentes (razón de consistencia CR).
- Regla práctica: CR menor a 0.1 es aceptable.

---

## Tema 5. TOPSIS

**5.1 Cercanía a la solución ideal**
- La mejor alternativa es la más cerca de lo ideal (lo mejor en cada criterio) y más lejos de lo peor.
- Es otra lógica de decisión sobre los mismos datos.

---

## Tema 6. Comparativa

**6.1 Mismos datos, distinto método**
- Se comparan los rankings de suma ponderada, AHP y TOPSIS.
- El resultado cambia según el método y los pesos: por eso hay que justificar la elección.

**6.2 Mapa de idoneidad**
- El puntaje se lleva a la malla H3 y se colorea (rojo = más idóneo).

---

## Cierre. Puente al taller
- Con los criterios combinados en un puntaje y llevados al mapa, queda el flujo completo.
- En el taller: datos crudos en distintos sistemas de coordenadas, unificación, malla y un método
  multicriterio para el mapa final.

---

### Notas para el instructor
- Tiempo sugerido: 60 min aprox. (10 partida/normalización, 15 suma ponderada, 20 AHP, 10 TOPSIS, 5 comparativa).
- El notebook recrea el resultado del Módulo 2, así que este módulo es independiente.
- En `recursos/` está la entrada en el formato de trabajo (`malla_h3.parquet`, viene del Módulo 2) y los resultados ya calculados (`resultado_idoneidad.h3.parquet`, `comparativa_metodos.png`) por si falla algún render en vivo.
