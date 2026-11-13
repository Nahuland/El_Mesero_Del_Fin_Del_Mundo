# Versión 3.24 — Cierre jugable del Acto IV

## Base y compatibilidad
Continuación directa de 3.23 sobre el HTML principal de `main`. Se conservan movimiento, colisiones, interiores, diálogos, combate, inventario y el guardado `mesero30save` con `saveVersion:49`. No se fuerza una migración ni se reinician partidas existentes.

## Mesa de revisión en la Fortaleza
Se añade el punto interactivo **Mesa de revisión del Acto IV**, dentro de la Fortaleza y accesible tras derrotar a Richars Octavio. El tablero consolida en una sola revisión los elementos que ya estaban distribuidos por R4 y el Hangar.

Requisitos para cerrar la revisión (13/13):
1. Manifiesto de evacuación.
2. Órdenes de las trincheras.
3. Orden de carga del Vuelo 9.
4. Discrepancia del Vuelo 9.
5. Orden de ocultamiento.
6. Recetario de Don Aurelio.
7. Testimonio de Nerea Vidal.
8. Testimonio de Celina Borda.
9. Testimonio de Damián Ferreyra.
10. Libro de operaciones del Hangar.
11. Archivo de mando.
12. Derrota de Richars Octavio.
13. Decisión persistente sobre Siesta.

Si faltan elementos, el tablero informa cuáles son y no marca el acto como cerrado. Al completar el expediente, registra `military.act4ReviewComplete` y `state.flags.act4Complete`, actualiza el objetivo hacia la deliberación de Mira, Iván, Lía, Teo, Noa, Dante, Kai y Eva y guarda la partida.

## Consecuencias preservadas
- El sabotaje de las lanchas sigue siendo una consecuencia táctica opcional.
- La neutralización de Ramiro Funes sigue registrada por separado.
- El tablero informa ambos estados sin convertirlos en requisitos del expediente ni borrar sus consecuencias.
- Richars Octavio continúa siendo un jefe obligatorio, sin rendición ni redención.
- La decisión de Siesta no determina por sí sola el destino de las unidades ni selecciona uno de los ocho finales.
- No se adelanta contenido del Acto V ni se inventan escenas para los ocho contactos.

## Corrección adicional
Al comenzar una partida nueva, el bloque de estado militar se reinicializa con los valores por defecto. Esto evita arrastrar decisiones militares de una partida anterior si el jugador inicia una nueva partida en la misma sesión del navegador. La carga de partidas existentes conserva sus datos.

## Validación realizada
- Compilación sintáctica del JavaScript inline con `new Function`: aprobada.
- Aserciones estáticas de presencia del tablero, checklist, persistencia y compatibilidad: aprobadas.
- Se conserva `saveVersion:49` y la clave `mesero30save`.

## Pendiente de validación
No se declara todavía una partida manual completa, prueba visual en navegador, prueba en móvil físico ni validación real de guardado/carga con navegador. El recorrido integral de R4, el balance de Richars y la progresión de las rutas opcionales siguen requiriendo QA dinámico.
