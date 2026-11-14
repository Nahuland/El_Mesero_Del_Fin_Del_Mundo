# 15 · Implementación 3.27 — Pulido técnico

## Base
- Rama: `release/3.27-pulido-tecnico`
- Base de código: `main`, versión 3.26 — Los ocho desenlaces.
- Archivo principal: `index.html`
- Guardado: clave histórica `mesero30save`; formato actualizado a `saveVersion: 50`.

## Alcance aplicado
1. Accesibilidad de controles: botones de dirección móvil con nombres accesibles y tipo explícito; área táctil mínima de 44 px.
2. Navegación por teclado: indicador visible de foco para controles interactivos.
3. Diálogo: semántica de diálogo modal, asociación con hablante y texto, anuncio del texto actualizado y foco inicial en la primera opción (o en el diálogo cuando no hay opciones).
4. Gestión de foco: se conserva el elemento que abrió el diálogo y se devuelve el foco al cerrarlo.
5. Estado visual: se activa y desactiva `body.dialogue-open` al abrir/cerrar, habilitando el oscurecimiento ya definido en CSS.
6. Metadatos: título, HUD y menú identifican 3.27 — Pulido técnico.
7. Guardado: se incrementa el marcador a 50; se conserva la clave de almacenamiento y la lectura tolerante de estructuras previas.

## Conservación
- No se alteran mapas, coordenadas, personajes, decisiones, diálogos narrativos ni los ocho desenlaces.
- No se modifican las propuestas de orientación ni las fichas afectivas; quedan reservadas para revisión narrativa.
- Se mantienen movimiento, colisiones, transiciones, interiores y progreso de historia de la versión 3.26.

## Siguiente pasada técnica
- Revisión de colisiones y límites de movimiento por región/interior.
- Perfilado de renderizado y coste de ordenamiento de objetos.
- Pruebas de regresión de guardados antiguos, cambios de región e interiores.
- Verificación visual en navegador de escritorio y dispositivo táctil real.
