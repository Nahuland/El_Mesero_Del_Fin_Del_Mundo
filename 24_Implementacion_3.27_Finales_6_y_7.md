# Implementación 3.27 — Resolución de la Secta y escena del Carnicero

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo:** `index.html`  
**Estado:** implementado en código; QA automatizado aprobado en GitHub Actions.

## Final 6 — La Mesa Larga

Se añadió el núcleo jugable de R5 y se completó la secuencia del Templo/Santuario:
- Noa, Acólita, en la Aldea: el jugador puede acompañarla a preparar su salida y su búsqueda de su hijo, sin prometer un reencuentro.
- Dante, Exacólito, en el Mercado: confiesa que fabricó el rito del reflector y ofrece testimonio sin quedar absuelto.
- Registro de doctrina en las Catacumbas: distingue las decisiones del Sacerdote de las familias que buscaban refugio.
- Refugio de la Aldea: contextualiza la comida y el amparo que la comunidad sí ofrecía.
- Registro del reflector, que aporta la prueba del eclipse artificial.
- Brasero del Sol y brasero de la Luna. La secuencia válida es Sol → Luna; intentar Luna primero no completa ni altera la secuencia.
- Sacerdote del Eclipse en el Santuario.

La rendición limitada del Sacerdote exige:
1. Prueba del reflector registrada.
2. Secuencia Sol → Luna completada.
3. Confianza de Noa y Dante ganada mediante sus interacciones de R5.
4. Noa y Dante dispuestos a apoyar o negociar en la deliberación del Acto V para que el Final 6 siga disponible.

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

## QA automatizado realizado

**Resultado:** APROBADO · GitHub Actions

Ejecución: [QA 3.27 — GitHub Actions](https://github.com/Nahuland/El_Mesero_Del_Fin_Del_Mundo/actions/runs/43742725807)

- Sintaxis del JavaScript principal: aprobada.
- Estructura del mapa: IDs de props únicos, coordenadas dentro de 420×300, referencias de interiores válidas y puerta de retorno presente en los 11 interiores.
- Simulación del cierre 13/13 del Acto IV: bloquea la revisión si falta una prueba y la completa al reunirlas todas; las acciones opcionales de Elba y Funes no son requisito.
- Nueve patrones de Richars y persistencia por turno: comprobados.
- Chromium carga el menú inicial sin excepciones JavaScript y sin IDs duplicados.
- Viewport táctil 390×844: controles visibles, 8 direcciones y objetivos direccionales de al menos 44×44 px; sin excepciones JavaScript.
- Simulación de las condiciones de los ocho desenlaces: los ocho quedan alcanzables con estados preparados; se verifican los bloqueos específicos de Final 6 y Final 7.
- Simulación real en Chromium de la secuencia Sol → Luna; Luna antes que Sol no completa el ritual.
- El Sacerdote no acepta la rendición sin la confianza de Noa y Dante; con la prueba y el orden correctos, registra la rendición limitada.
- Final 6 se habilita con `cultResolution` y se bloquea cuando falta.
- Final 7 médico se habilita con el antídoto reservado al Hospital y se bloquea cuando se destina al Carnicero.
- La escena de Teo/Carnicero se ejecuta y persiste el resultado de lucidez temporal.
- Las nuevas banderas se conservan en la estructura generada por `savePayload()`.

La instrumentación de prueba expone el estado encapsulado solo dentro de una copia HTML en memoria durante Chromium; no se incorpora al juego. La simulación ejecuta las funciones reales de interacción y cierre de expedientes con estados preparados; no recorre físicamente el mapa ni sustituye la partida manual.

## Validación manual pendiente

- Recorrer físicamente los puntos del Templo y Santuario, y comprobar distancias de interacción y legibilidad.
- Probar guardado/carga cerrando y reabriendo el navegador.
- Ejecutar la ruta médica y la alternativa del Carnicero en una partida completa.
- Recorrido manual completo y revisión en móvil físico.

**Importante:** el QA automatizado sí ejecutó las interacciones y las condiciones en Chromium con estado simulado. No equivale a una partida completa ni a validación manual.
