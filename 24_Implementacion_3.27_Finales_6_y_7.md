# Implementación 3.27 — Resolución de la Secta y escena del Carnicero

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo:** `index.html`  
**Estado:** implementado en código; QA automatizado ampliado, resultado final pendiente.

## Final 6 — La Mesa Larga

Se añadieron al Templo y al Santuario:
- Registro del reflector, que aporta la prueba del eclipse artificial.
- Brasero del Sol y brasero de la Luna. La secuencia válida es Sol → Luna; intentar Luna primero no completa ni altera la secuencia.
- Sacerdote del Eclipse en el Santuario.

La rendición limitada del Sacerdote exige:
1. Prueba del reflector registrada.
2. Secuencia Sol → Luna completada.
3. Noa y Dante dispuestos a apoyar o negociar en la deliberación del Acto V.

Al aceptar la escena, se guarda `state.flags.cultResolution='reconciled'` y `cultPriestSurrendered=true`. El diálogo deja explícito que la rendición no borra el daño, no obliga a los fieles a perdonar y no significa que toda la Secta abandone la doctrina.

La condición de Final 6 que ya existía en `finaleMetrics()` queda ahora alcanzable por una ruta jugable. Se mantienen sus demás requisitos: Siesta desconectada, resolución pacífica del Capataz y de Ciudad Enferma, sabotaje de lanchas, Funes neutralizado y apoyo/negociación de seis contactos, incluidos Noa, Dante, Kai y Eva.

## Final 7 y alternativa del Carnicero

Se conserva la ruta médica del Hospital ya implementada: pruebas epidemiológicas, muestra, suministros al Hospital, ayuda clínica, antídoto reservado para la red médica, Lía apoyando y Teo sin reservar el frasco para el Carnicero. La red ofrece una posibilidad de tratamiento y recuperación; no una cura global.

Se añadió la escena que faltaba para la alternativa de Teo:
- Solo aparece tras apoyar a Teo, destinar el antídoto al Carnicero y resolver el encuentro del Nido.
- Desde el registro de evacuación del Nido se puede acompañar a Teo e intentar el tratamiento.
- El resultado persistente es `carniceroTreatmentResolved` con resultado `lucidez_temporal`.
- La escena expresa que el antídoto no elimina la Fiebre Gris: el Carnicero recupera lucidez por un momento y la recuperación posterior es incierta.
- La escena puede aplazarse y retomarse; si ya se resolvió, no se repite ni consume de nuevo el recurso.

Esta alternativa no cambia las condiciones del Final 7 médico: reservar el frasco para el Carnicero sigue impidiendo que ese mismo recurso se destine a la red del Hospital.

## Compatibilidad y alcance

- Las nuevas decisiones se guardan en `state.flags` y `state.city`, ya serializados por el sistema existente.
- No se cambió `saveVersion:50` ni la clave `mesero30save`.
- No se alteraron los ocho nombres de finales, la condición de Richars ni las decisiones de Siesta.
- Se añadió el control de estas rutas al workflow de GitHub Actions.
- La instrumentación de Playwright para simular estados se inserta solo en el HTML de prueba en memoria; no se incorpora al juego publicado.

## Validación pendiente

- Confirmar que GitHub Actions apruebe sintaxis, carga inicial y simulación de condiciones de Final 6 y Final 7.
- Comprobar la interacción física con los nuevos puntos del Templo y Santuario, el orden de braseros, la rendición limitada y la persistencia al recargar.
- Comprobar la escena del Carnicero y el guardado/carga del resultado.
- Recorrido manual completo y revisión en móvil siguen pendientes.

**Importante:** la aprobación del smoke test no equivale a haber jugado las rutas completas. No se declara validación manual.
