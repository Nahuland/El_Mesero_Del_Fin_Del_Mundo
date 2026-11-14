# Auditoría 3.27 — Colisiones y transiciones

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo auditado:** `index.html`  
**Alcance:** revisión estática del código de movimiento, colisiones, límites, interiores y cambios de zona.  
**Estado:** auditoría estática completada; validación jugable pendiente.

## Resultado ejecutivo

No se encontró en esta revisión estática un bloqueo de progresión que pueda declararse reproducible con certeza. Los accesos y salidas examinados tienen manejadores de interacción y las coordenadas de aparición están dentro de los límites globales del mundo.

Esto no equivale a una aprobación funcional: no se ejecutó una sesión de juego en navegador ni se recorrieron físicamente todas las rutas. Las conclusiones sobre transitabilidad son inferencias del código.

## Comprobaciones realizadas

- Se localizó una única función central `blocked()`; el movimiento comprueba los ejes X e Y por separado.
- Se revisaron los límites globales del mundo (420 × 300), la barrera de acceso a R4, la costa, el perímetro del Capataz, la Línea de Montaje y el Túnel.
- Se inspeccionaron colisionadores de hitos, estructuras urbanas, edificios de R5, árboles, muros militares y obstáculos interiores.
- Se revisaron los interiores del Depósito, Patio, Centro Comercial, Metro, Hospital, Nido, Catacumbas, Templo, Santuario, Hangar y Fortaleza.
- Se verificó que los 23 identificadores de acceso/salida seleccionados tienen un `case` de interacción.
- Se confirmó que `enterInterior()` conserva la posición exterior y `exitInterior()` restaura esa posición; los accesos especiales pueden definir un destino explícito.
- Se revisó la recuperación de partidas guardadas: los interiores permitidos y los puntos de retorno se validan antes de continuar.

## Hallazgos y riesgos

### H1 — Riesgo de mantenimiento: colisionadores globales aplicados también dentro de interiores
**Severidad:** baja, preventiva.

La función `blocked()` evalúa `explorationColliders` y `obstacles` antes de terminar las comprobaciones específicas del interior. Las coordenadas actuales de esos objetos no muestran una intersección evidente con los interiores revisados, pero una futura sala situada sobre esas coordenadas heredaría colisiones exteriores.

**Recomendación:** separar colisiones exteriores e interiores, o condicionar los colisionadores por región/interior.

### H2 — Puertas con aperturas geométricas estrechas
**Severidad:** media, pendiente de prueba manual.

Catacumbas y Templo dependen de un corredor de salida de aproximadamente cuatro unidades de ancho lógico; el Santuario usa una abertura occidental estrecha. El código contempla esos huecos y las posiciones de salida están cerca de ellos, pero falta comprobar el recorrido real con teclado, diagonales y controles táctiles.

**Recomendación:** probar cada puerta desde ambos lados, acercándose en horizontal, vertical y diagonal; comprobar que el personaje no queda pegado al borde.

### H3 — Accesos militares dependen de aperturas coordinadas entre dos sistemas
**Severidad:** media, pendiente de prueba manual.

Los accesos al Hangar y a la Fortaleza dependen de las aperturas de `militaryWalls`, de los límites de cada interior y de las zonas especiales de salida. Las coordenadas parecen coordinadas en el código, pero requieren recorrido real para descartar una salida demasiado ajustada.

**Recomendación:** probar entrada, recorrido interior, salida y reentrada en ambos edificios, incluyendo una partida cargada dentro de cada interior.

### H4 — Movimiento diagonal y deslizamiento en esquinas
**Severidad:** media, pendiente de prueba manual.

El movimiento normaliza las diagonales y comprueba X/Y por separado. Este patrón suele permitir deslizarse junto a paredes, pero también puede producir esquinas pegajosas o pequeños avances junto a colisionadores.

**Recomendación:** probar las esquinas de edificios, vehículos, contenedores, árboles, muros y puertas con las ocho direcciones.

## Matriz mínima de regresión manual

| Zona / transición | Prueba |
|---|---|
| La Estrella → Calle Oxidada | Abrir puerta, cruzar y volver |
| Exterior → Depósito / Patio | Entrar, tocar límites, salir y reentrar |
| Fábrica → Línea de Montaje → Túnel | Probar puertas antes y después de desbloquearlas |
| Túnel → Ciudad Enferma | Abrir compuerta y cruzar en ambos sentidos |
| Centro Comercial / Metro / Hospital / Nido | Entrar y salir por cada acceso |
| Metro → salida sur especial | Activar atajo, salir al destino alternativo y regresar |
| Umbral R5 → Catacumbas / Templo / Santuario | Probar accesos y salidas en ambos sentidos |
| R4 → Hangar / Fortaleza | Probar puertas, perímetros y retorno |
| Guardado dentro de interiores | Guardar, recargar y comprobar posición y salida |

## Conclusión

**Resultado estático: sin bloqueo confirmado; pruebas de movimiento real pendientes.** No se modificó el código del juego en esta fase. La siguiente corrección debe basarse en los resultados de la matriz manual, evitando cambiar coordenadas o colisiones por intuición.
