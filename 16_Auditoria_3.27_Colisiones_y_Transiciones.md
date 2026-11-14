# Auditoría 3.27 — Colisiones y transiciones

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo auditado:** `index.html`  
**Alcance:** revisión estática del código de movimiento, colisiones, límites, interiores y cambios de zona.  
**Estado:** H1 corregido en código; validación jugable pendiente.

## Resultado ejecutivo

Se detectó un defecto lógico probable en los límites de cuatro interiores urbanos: Centro Comercial, Metro, Hospital y Nido. La comprobación de perímetro solo se aplica mientras el jugador permanece dentro del rectángulo de `roomBounds`; al cruzar el umbral de salida y superar el límite, la función deja de aplicar esa barrera aunque `state.currentInterior` siga activo. El jugador podría desplazarse fuera de la sala sin ejecutar `exitInterior()`.

Los 23 objetos `roomdoor` examinados tienen manejador de interacción. No se ha ejecutado una sesión real de navegador, por lo que el defecto se clasifica como hallazgo estático que requiere reproducción manual.

## Comprobaciones realizadas

- Se localizó una única función central `blocked()`; el movimiento comprueba los ejes X e Y por separado.
- Se revisaron los límites globales del mundo (420 × 300), la barrera de acceso a R4, la costa, el perímetro del Capataz, la Línea de Montaje y el Túnel.
- Se inspeccionaron colisionadores de hitos, estructuras urbanas, edificios de R5, árboles, muros militares y obstáculos interiores.
- Se revisaron los interiores del Depósito, Patio, Centro Comercial, Metro, Hospital, Nido, Catacumbas, Templo, Santuario, Hangar y Fortaleza.
- Se verificó que los 23 objetos de tipo `roomdoor` tienen un `case` de interacción.
- Se confirmó que `enterInterior()` conserva la posición exterior y `exitInterior()` restaura esa posición; los accesos especiales pueden definir un destino explícito.
- Se revisó la recuperación de partidas guardadas: los interiores permitidos y los puntos de retorno se validan antes de continuar.
- Se comprobó que no hay identificadores duplicados entre los 62 objetos de interacción inspeccionados.

## Hallazgos y riesgos

### H1 — Salida del rectángulo de cuatro interiores urbanos sin abandonar el estado interior
**Severidad:** alta, defecto estático probable.

En `blocked()`, `roomBounds` solo se evalúa cuando `x` e `y` están dentro del rectángulo definido. La puerta inferior permite avanzar hacia el exterior, pero una vez que el jugador supera el borde (`y > y2`) la condición deja de ejecutarse. No se exige que `state.currentInterior` cambie ni se llama automáticamente a `exitInterior()`. Esto afecta a Centro Comercial, Metro, Hospital y Nido, cuyos perímetros dependen de esa comprobación compartida.

**Recomendación:** mantener una barrera de perímetro activa mientras el jugador esté en esos interiores y permitir únicamente la interacción explícita con la salida. Como alternativa, convertir el cruce del umbral en una transición automática que llame a `exitInterior()`. No ampliar el hueco sin probarlo.

### H2 — Riesgo de mantenimiento: colisionadores globales aplicados también dentro de interiores
**Severidad:** baja, preventiva.

La función `blocked()` evalúa `explorationColliders` y `obstacles` antes de terminar las comprobaciones específicas del interior. Las coordenadas actuales de esos objetos no muestran una intersección evidente con los interiores revisados, pero una futura sala situada sobre esas coordenadas heredaría colisiones exteriores.

**Recomendación:** separar colisiones exteriores e interiores, o condicionar los colisionadores por región/interior.

### H3 — Puertas con aperturas geométricas estrechas
**Severidad:** media, pendiente de prueba manual.

Catacumbas y Templo dependen de un corredor de salida de aproximadamente cuatro unidades de ancho lógico; el Santuario usa una abertura occidental estrecha. El código contempla esos huecos y las posiciones de salida están cerca de ellos, pero falta comprobar el recorrido real con teclado, diagonales y controles táctiles.

**Recomendación:** probar cada puerta desde ambos lados, acercándose en horizontal, vertical y diagonal; comprobar que el personaje no queda pegado al borde.

### H4 — Accesos militares dependen de aperturas coordinadas entre dos sistemas
**Severidad:** media, pendiente de prueba manual.

Los accesos al Hangar y a la Fortaleza dependen de las aperturas de `militaryWalls`, de los límites de cada interior y de las zonas especiales de salida. Las coordenadas parecen coordinadas en el código, pero requieren recorrido real para descartar una salida demasiado ajustada.

**Recomendación:** probar entrada, recorrido interior, salida y reentrada en ambos edificios, incluyendo una partida cargada dentro de cada interior.

### H5 — Movimiento diagonal y deslizamiento en esquinas
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
| Centro Comercial / Metro / Hospital / Nido | Intentar cruzar el umbral sin interactuar; comprobar que no se abandona el estado interior |
| Centro Comercial / Metro / Hospital / Nido | Entrar, interactuar con salida, volver y reentrar |
| Metro → salida sur especial | Activar atajo, salir al destino alternativo y regresar |
| Umbral R5 → Catacumbas / Templo / Santuario | Probar accesos y salidas en ambos sentidos |
| R4 → Hangar / Fortaleza | Probar puertas, perímetros y retorno |
| Guardado dentro de interiores | Guardar, recargar y comprobar posición y salida |

## Conclusión

**Resultado estático: un defecto probable de perímetro en cuatro interiores urbanos; otros riesgos requieren pruebas de movimiento real.** La corrección estática de H1 se implementó en la rama de trabajo. La reproducción y regresión jugable de las cuatro salidas siguen pendientes; los hallazgos H2–H5 tampoco se consideran cerrados.


## Actualización posterior — corrección H1 (3.27)

**Estado:** implementada en `index.html`; pendiente de validación manual en navegador.

- Para `mall`, `metro`, `hospital` y `nest`, `blocked()` ahora mantiene activa la franja de colisión interior incluso cuando el movimiento intenta superar el borde inferior. La salida normal sigue siendo la interacción con el objeto `roomdoor`.
- Se conserva la transición especial `metroSouthExit`, que llama a `exitInterior({x:218,y:139})` cuando el atajo está habilitado.
- Al cargar una partida antigua, si `currentInterior` identifica uno de esos cuatro interiores pero la posición guardada quedó fuera de su zona transitable, Siete se reubica en el punto de entrada interior correspondiente. Se preservan `returnPoint`, progreso, decisiones y el formato de guardado.
- No se modificó `saveVersion:50` ni la clave `mesero30save`.
- El Templo conserva su corredor de salida anterior; no se amplió ni modificó su perímetro.

**Regresión estática comprobada:** presencia de la barrera estricta para los cuatro interiores, puntos de recuperación de guardados antiguos, conservación de versión/clave de guardado, interacción de salidas normales y destino especial del Metro.

**Pendiente:** recorrer en navegador cada sala, probar las cuatro salidas normales, el atajo sur del Metro y guardar/cargar partidas dentro y en posiciones heredadas. Esta actualización no afirma que esas pruebas manuales se hayan ejecutado.
