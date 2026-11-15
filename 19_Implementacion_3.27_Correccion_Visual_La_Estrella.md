# Implementación 3.27 · Corrección visual de La Estrella

## Problema observado
La senda principal se dibujaba con una franja continua desde x=10 hasta x=46. Como la huella de La Estrella ocupa aproximadamente x=1.3–20.2, el trazado se prolongaba a través del edificio y daba la impresión de que la calle lo atravesaba. Además, la farola estaba colocada en (18.3, 10.2), dentro de la huella del restaurante y junto al vano de la puerta este.

## Cambios aplicados
- El tramo de senda dentro del restaurante ahora mantiene un eje recto en y=10.2 y funciona visualmente como pasillo hacia la puerta este.
- El tramo exterior continúa desde el entorno de x=22 con una curva suave, evitando que el camino parezca atravesar el volumen del edificio.
- La farola se trasladó a (23.2, 13.0), fuera de la huella del restaurante y al costado del camino.
- Se conservaron la puerta este (19.35, 10.2), el punto inicial de Siete, los objetos interactivos, el interior, las colisiones, la historia y el sistema de guardado.

## Alcance y verificación
- Rama: `release/3.27-pulido-tecnico`.
- Archivo de juego modificado: `index.html`.
- Guardado: no se modificó `saveVersion:50` ni la clave `mesero30save`.
- Verificación realizada: lectura posterior del archivo en GitHub y comprobación de que el nuevo trazado y la nueva coordenada de la farola quedaron guardados, y de que la coordenada anterior ya no aparece.
- No se ejecutó el juego en navegador ni se realizó una comprobación visual en tiempo real. La integración visual y la transitabilidad deben confirmarse en la matriz de regresión manual.

## Nota de diseño
La senda interior queda interpretada como circulación del restaurante hacia su salida principal; el camino exterior comienza después de la fachada. Esto mantiene una continuidad espacial más coherente sin alterar el plano funcional del interior.
