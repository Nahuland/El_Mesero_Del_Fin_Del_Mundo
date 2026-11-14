# Implementación 3.27 — Corrección H1 de perímetros interiores

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo modificado:** `index.html`  
**Alcance:** corrección del escape accidental de los interiores Centro Comercial, Metro, Hospital y Nido.

## Cambio aplicado

1. `blocked()` aplica ahora el límite interior de forma estricta en los cuatro interiores urbanos. El personaje ya no puede salir del rectángulo por el umbral inferior manteniendo `state.currentInterior` activo.
2. La salida ordinaria continúa dependiendo de interactuar con `mallReturn`, `metroReturn`, `hospitalReturn` o `nestReturn`.
3. La conexión sur especial del Metro sigue llamando a `exitInterior({x:218,y:139})` cuando el atajo está desbloqueado.
4. Al cargar una partida antigua, si el estado interior es válido pero la posición guardada está fuera de la zona transitable de una de estas cuatro salas, el personaje se coloca en el punto de entrada interior correspondiente. Se conserva `returnPoint` y el resto del estado narrativo.
5. Se mantienen `saveVersion:50` y la clave `mesero30save`; no se fuerza una migración ni se reinician partidas.

## Verificaciones estáticas

- La regla de perímetro cubre mall, metro, hospital y nest.
- Los cuatro puntos de recuperación coinciden con los puntos de entrada usados por `enterInterior()`.
- Las salidas ordinarias continúan conectadas a `exitInterior()`.
- El atajo sur del Metro conserva su destino especial.
- La versión y clave de guardado no cambiaron.
- No se alteraron diálogos, personajes, decisiones, mapas ni desenlaces.

## Pendiente de QA manual

- Probar movimiento contra los cuatro bordes de cada sala.
- Interactuar con las cuatro salidas ordinarias.
- Probar la conexión sur del Metro con el atajo bloqueado y desbloqueado.
- Guardar y cargar dentro de cada sala.
- Cargar un guardado antiguo que conserve `currentInterior` pero tenga al jugador fuera del perímetro.
- Comprobar teclado, diagonales y controles táctiles.

**Limitación:** la validación realizada en esta implementación es estática. No se ejecutó el juego en un navegador ni se simuló movimiento real; por tanto, la corrección queda implementada pero no certificada como jugable hasta completar la matriz manual.
