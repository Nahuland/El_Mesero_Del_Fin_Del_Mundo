# Versión 3.21 — Geografía exterior de R4

## Objetivo
Completar la primera capa física del Territorio Militar utilizando los hitos y coordenadas ya existentes en los documentos maestros, sin desarrollar todavía la facción.

## Sectores representados
- Control del puente (112,160)
- Trincheras norte (91,185)
- Cuartel avanzado (139,188)
- Puerto (65,225)
- Muelle (44,247)
- Hangar (145,230)
- Aeródromo (180,250)
- Fortaleza (133,276)
- Puesto de radio (192,192)

## Implementación
- Estructuras exteriores, parapetos, almacén de carga, muelle visual, pista vacía, perímetro de Fortaleza y mástil de radio.
- Etiquetas de zona y colisiones exteriores en edificios.
- Los accesos del plano permanecen libres para futuras puertas e interiores.
- El agua suroeste existente no se convierte en ruta navegable.

## Restricciones de continuidad
No se introducen NPC, soldados, bandos, emblemas, jerarquías, órdenes, transmisiones, misiones, documentos legibles ni historia militar. R4 sigue bloqueado para entradas desde otras regiones. Los interiores y la progresión de facción se desarrollarán más adelante.

## Guardado
Se conserva `mesero30save` y `saveVersion:49`; no se agregan datos persistentes en esta etapa.

## QA
Ver `REPORTE_QA_3.21_R4_Geografia.txt`. Validación estática aprobada; revisión visual y móvil pendientes.
