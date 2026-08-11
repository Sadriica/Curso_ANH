# Guía rápida de Google Colab

Los notebooks del curso corren en Google Colab, un entorno gratuito que ejecuta Python en la nube,
desde el navegador y sin instalar nada. Solo hace falta una cuenta de Google.

## 1. Abrir un notebook

Cada módulo tiene un botón "Open in Colab" al inicio de su notebook. Al hacer clic, el notebook se
abre en Colab listo para usar. Las otras dos formas de abrirlo son:

- Ir a [colab.research.google.com](https://colab.research.google.com), pestaña GitHub, y pegar la
  URL del repositorio.
- Subir el archivo `.ipynb` desde Archivo > Subir notebook.

La primera vez, Colab pide iniciar sesión con la cuenta de Google.

## 2. Ejecutar el notebook

Un notebook es una lista de celdas: de texto (explicaciones) y de código (Python).

- Para ejecutar una celda: clic en ella y Shift + Enter, o el botón de play a la izquierda.
- Conviene ejecutar en orden, de arriba hacia abajo: cada celda suele depender de las anteriores.
- La primera celda de código instala las librerías (`!pip install ...`). Puede tardar un minuto;
  es normal y solo pasa una vez por sesión.
- Para ejecutar todo de una vez: menú Entorno de ejecución > Ejecutar todas.

## 3. Cosas que pueden pasar

- **El entorno se desconectó o se reinició:** Colab cierra la sesión tras un rato de inactividad.
  No se pierde el notebook, pero sí las variables en memoria. Solución: Entorno de ejecución >
  Ejecutar todas, para reconstruir todo desde cero.
- **Error en una celda:** casi siempre es porque no se ejecutó una celda anterior. Vuelva arriba y
  ejecute en orden.
- **Cambios:** se puede editar y volver a ejecutar cuantas veces haga falta. Para guardar una copia
  propia: Archivo > Guardar una copia en Drive.

## 4. Sin conexión o sin cuenta de Google

Todos los notebooks son autocontenidos: generan sus propios datos y no dependen de archivos
externos. Si no se puede usar Colab, corren igual en Jupyter local. Además, en la carpeta
`recursos/` de cada módulo están los archivos de respaldo (datos de entrada y resultados ya
calculados) por si algún paso falla durante la sesión.
