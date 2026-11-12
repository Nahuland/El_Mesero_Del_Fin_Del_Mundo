# Actualización 3.20 — expansión ambiental de R5

## Alcance
Continuación de la base 3.19 con ampliación de exploración ambiental del Territorio del Culto. No se agregan personajes, misiones, doctrinas, facciones activas ni revelaciones.

## Nuevos puntos de inspección
| Punto | Coordenada | Lectura ambiental |
|---|---:|---|
| Tronco caído | (316,168) | Madera húmeda y musgo; sin marcas legibles |
| Claro pedregoso | (326,163) | Suelo irregular y piedras dispersas |
| Muro derrumbado | (329,190) | Mampostería erosionada sin inscripción legible |
| Fuente seca | (321,222) | Pileta agrietada y sin agua |
| Patio de puestos | (342,218) | Tablones, soportes y lona deteriorada |
| Descanso de la escalinata | (372,239) | Rellano lateral y peldaños rotos |

## Navegación y geometría
- Se agregan seis ramales gráficos cortos que conectan los puntos con los caminos existentes.
- No se alteran las coordenadas maestras 3.19 ni las huellas de edificios.
- No se añaden colisiones nuevas.
- Se conservan los accesos y retornos de Catacumbas, Templo y Santuario.
- R4 continúa bloqueado.

## Persistencia
- Los seis puntos registran inspección en `state.flags.cultPoiExplored`.
- El diario muestra el avance R5 (n/6).
- `mesero30save` se conserva.
- `saveVersion` pasa de 48 a 49 mediante migración aditiva.

## Continuidad narrativa
Los textos describen exclusivamente condiciones físicas observables. No permiten reconstruir prácticas, identificar responsables, explicar símbolos ni atribuir función a las ruinas. La historia interna de la Secta y el arco militar siguen pendientes.

## Validación
Ver `REPORTE_QA_3.20_R5.txt`. La sintaxis y los controles estáticos se aprobaron. La validación visual/manual y móvil debe repetirse sobre 3.20; la validación visual/móvil cerrada por el usuario corresponde a 3.19.
