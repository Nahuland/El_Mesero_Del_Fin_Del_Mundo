# Versión 3.25 — Acto V: La última orden

## Base
Continuación directa del HTML principal 3.24 en `main`. Se mantienen el motor, mapa, interiores, diálogos, combate, inventario y guardado `mesero30save` con `saveVersion:49`. Los datos nuevos del Acto V son aditivos y reciben valores por defecto al cargar partidas antiguas.

## Mesa de los ocho contactos
Al completar el expediente del Acto IV, la Mesa de revisión permite convocar la deliberación del Acto V. Se presentan los ocho contactos y las confesiones/peticiones registradas en el guion maestro:

| Contacto | Rol | Conflicto tratado |
|---|---|---|
| Mira | Superviviente | Su silencio durante el apagado de Siete |
| Iván | Desertor | Su participación en la barricada y el Capataz |
| Lía | Enfermera | Su infección oculta y el acompañamiento |
| Teo | Cazador | Su vínculo con el Carnicero y el antídoto |
| Noa | Acólita | La pérdida de su hijo y su salida del culto |
| Dante | Exacólito | El reflector y la verdad del rito |
| Kai | Mecánica | El expediente de Siete y las lanchas |
| Eva | Piloto | Su responsabilidad en el Vuelo 9 |

Cada contacto plantea su petición y permite tres posturas independientes: acompañar, negociar condiciones o rechazar. Cada elección se guarda en `state.act5.contacts` y genera una bandera explícita `state.flags.act5_<contacto>_<postura>`. No se usa un contador de karma ni una afinidad agregada para borrar responsabilidades.

## Persistencia y reanudación
- El progreso se guarda después de cada respuesta.
- Si el jugador sale de la conversación, la siguiente interacción continúa desde el primer contacto pendiente.
- Las ocho posturas se conservan en partidas guardadas.
- Al completar 8/8, se registra `state.act5.councilComplete` y `state.flags.act5CouncilComplete`.
- La mesa permite consultar el resumen sin volver a sobrescribir elecciones ya tomadas.

## Límite de alcance
Esta versión reúne las voces y registra las posturas, pero no elige uno de los ocho finales ni cambia la decisión técnica de Siesta tomada en el Acto IV. La consola queda preparada para la fase 3.26, que implementará las condiciones y epílogos finales a partir de estas banderas y de las consecuencias de las cuatro facciones.

## Validación realizada
- Compilación sintáctica del JavaScript inline: aprobada.
- Simulación aislada del flujo de ocho contactos: 8/8 respuestas, guardado tras cada una y cierre del consejo aprobados.
- Se conserva `saveVersion:49` y `mesero30save`.
- Compatibilidad por defecto de partidas antiguas: verificada estáticamente.

## Pendiente
No se declara recorrido manual completo, inspección visual en navegador, prueba móvil física ni validación real de guardado/carga en navegador. Esas pruebas siguen pendientes.
