# Versión 3.22 — Auditoría de canon y plan de desarrollo de la facción militar R4

## Estado
**Etapa de preparación narrativa.** Esta entrega no modifica el juego ejecutable, la geografía, las coordenadas ni los guardados. La implementación jugable queda pendiente de resolver los vacíos expresamente identificados abajo.

## Fuentes rectoras
- Guion Maestro y Biblia Narrativa — Fase 4, especialmente secciones 2, 3 (Acto IV), 5, 6, 8, 9 y 10.
- Documento Maestro de Reconstrucción 3.19.
- Atlas de Organización del Mundo 3.19 Integrado.
- Plano Detallado de Coordenadas 3.19 Integrado y CSV maestro 3.21.
- Guion de Continuidad y Consecuencias 3.19.
- Implementación geográfica R4 de la versión 3.21.

En caso de diferencia, el Guion Maestro Fase 4 gobierna los hechos narrativos; el Plano/CSV gobierna las coordenadas; el estado ejecutable 3.21 gobierna la implementación existente.

## 1. Canon confirmado para el Acto IV

La ruta principal del Acto IV es:
**Puerto Militar → Campo de Trincheras → Hangar Oxidado → Muelle de Carga → Puente Blindado → Aeródromo → Fortaleza del General.**

Elementos y hechos que sí están establecidos:
- La **Mecánica** y el **Piloto** revelan la logística del ejército: lanchas artilladas, evacuaciones selectivas y el Vuelo 9.
- El **Aeródromo** contiene la evidencia más clara del transporte de la cápsula de Fiebre Gris y de la cadena de mando que permitió ocultarlo.
- El **recetario de Don Aurelio** conecta el pasado del General con la petición de clemencia por los robots.
- La **llave inglesa** permite que la Mecánica sabotee las lanchas para evitar un ataque, si el jugador la ayudó.
- El **General Acorazado** mantuvo el orden mediante fuerza y ocultó información sobre el Vuelo 9. No creó por sí solo todos los males, pero eligió obedecer y encubrir.
- El General está agotado y teme que, sin una orden central, el mundo vuelva a la guerra. Esto explica su temor, pero no absuelve sus decisiones.
- En el enfrentamiento final, las salidas posibles son destruir su autoridad, exponer la verdad o permitir que se rinda si se reunieron pruebas y vínculos suficientes.

La instalación militar vinculada al Vuelo 9 conserva pruebas del origen y de la transmisión que manipuló a numerosas unidades. No debe atribuirse al ejército la creación de todos los males ni afirmarse que el General originó la señal.

## 2. Correspondencia espacial con R4 existente

Se conserva la geografía de 3.21 sin desplazar centros, huellas ni accesos:

| Sector del plano 3.21 | Centro | Relación con la ruta del Acto IV |
|---|---:|---|
| Puerto | (65,225) | Puerto Militar |
| Trincheras norte | (91,185) | Campo de Trincheras |
| Hangar | (145,230) | Hangar Oxidado |
| Muelle | (44,247) | Muelle de Carga |
| Control del puente | (112,160) | Puente Blindado |
| Aeródromo | (180,250) | Aeródromo |
| Fortaleza | (133,276) | Fortaleza del General |
| Cuartel avanzado | (139,188) | Hito logístico auxiliar ya cartografiado |
| Puesto de radio | (192,192) | Hito auxiliar; su función narrativa no está definida |

Los nombres del Guion Maestro y del plano se relacionan por función geográfica, no como autorización para inventar nuevos sectores o cambiar coordenadas. La secuencia de ruta del Guion Maestro tiene prioridad narrativa.

## 3. Matriz de contenido que puede implementarse sin alterar el canon

| Hito | Contenido respaldado por el Guion Maestro | Dependencia o consecuencia confirmada |
|---|---|---|
| Puerto Militar | Logística militar y presencia de lanchas artilladas | La Mecánica y el Piloto revelan la logística |
| Campo de Trincheras | Tramo de aproximación del Acto IV | No se especifica encuentro ni combate obligatorio |
| Hangar Oxidado | Parte de la ruta militar | No se especifica qué archivo u objeto contiene |
| Muelle de Carga | Lanchas artilladas y posibilidad de sabotaje | Llave inglesa + ayuda previa a la Mecánica permiten sabotearlas |
| Puente Blindado | Parte de la ruta hacia el Aeródromo y la Fortaleza | No se especifica mecanismo de control ni guardia |
| Aeródromo | Evidencia de la cápsula del Vuelo 9 y de la cadena de mando que ocultó el transporte | Reunir pruebas contribuye a las resoluciones del General y a la verdad del Vuelo 9 |
| Fortaleza del General | Confrontación con el General Acorazado | Destruir autoridad, exponer verdad o rendición condicionada por pruebas y vínculos |
| Recetario de Don Aurelio | Conexión entre el pasado del General y la petición de clemencia por los robots | Se debe preservar su peso emocional; el contenido exacto de esa conexión aún no está detallado |

## 4. Variables y persistencia previstas

El Guion Maestro propone el registro narrativo central:
- `faction.military`: pruebas reunidas y estado de rendición o resistencia.
- `truth.flight9`: pruebas sobre la cápsula y la cadena de mando.
- `truth.siesta`: fragmentos que explican la orden y su manipulación.
- `relationships`: afinidad y decisiones individuales de compañeros.
- `star.community`: quién vive en La Estrella, quién confía en Siete y qué espacios están activos.

Cada decisión importante deberá tener una bandera explícita y estable; no debe inferirse exclusivamente de `G.m`. La migración de partidas antiguas será aditiva y conservará `mesero30save`.

**No se implementan todavía estas variables en 3.22.** Antes deben definirse los eventos concretos que las activan y su relación con los campos ya existentes, evitando duplicar o sobrescribir estado guardado.

## 5. Vacíos que el material fuente no resuelve

No se completarán por inferencia. Se necesita definición o aprobación antes de escribir diálogos, misiones o escenas:
1. Nombre oficial de la facción militar y denominación interna de sus miembros.
2. Nombres propios de la Mecánica y el Piloto, y si corresponden a alguno de los ocho contactos existentes.
3. Coordenadas exactas de encuentro y condiciones de aparición de ambos personajes.
4. Qué acción concreta significa “ayudar” a la Mecánica y cuándo se entrega/obtiene la llave inglesa.
5. Contenido exacto, ubicación y secuencia de lectura de las pruebas del Aeródromo.
6. Qué revela exactamente el recetario sobre el pasado del General y cómo se vincula con la petición de Don Aurelio.
7. Qué pruebas y vínculos son suficientes para habilitar la rendición; no hay umbrales numéricos definidos.
8. Qué implica exactamente “destruir su autoridad” frente a “exponer la verdad” en términos de escenas y consecuencias.
9. Función narrativa del Cuartel avanzado y del Puesto de radio dentro del Acto IV.
10. Orden de desbloqueo de interiores, puertas, retorno y progresión entre los siete hitos de la ruta.

## 6. Secuencia técnica propuesta para la siguiente implementación jugable

Una vez resueltos los vacíos anteriores:
1. Diseñar el registro narrativo militar con migración aditiva y pruebas de compatibilidad con `mesero30save`.
2. Integrar los encuentros de Mecánica y Piloto usando sus roles y hechos canónicos.
3. Implementar la cadena de evidencia del Vuelo 9 en el Aeródromo.
4. Implementar la condición de ayuda a la Mecánica, la llave inglesa y el sabotaje de lanchas.
5. Integrar el recetario de Don Aurelio como evidencia/vínculo, sin convertirlo en una revelación distinta.
6. Implementar el enfrentamiento y sus tres resoluciones, condicionadas por pruebas y vínculos.
7. Reflejar consecuencias en La Estrella, diario y estado de facción.
8. Validar sintaxis, regresión, colisiones, accesos, transiciones, guardado/carga y rutas alternativas.

## 7. Límites de esta entrega

- R4 conserva el bloqueo de ingreso desde otras regiones hasta que la progresión narrativa y sus accesos estén preparados.
- No se añaden soldados, enemigos, emblemas, rangos, doctrinas, mensajes, archivos legibles ni diálogos.
- No se modifica `index.html`, `saveVersion:49`, `mesero30save`, el CSV ni las coordenadas.
- No se declaran implementadas ni probadas las escenas del Acto IV.
- Esta versión es una auditoría de canon y un plan de producción, no una versión jugable 3.22.
