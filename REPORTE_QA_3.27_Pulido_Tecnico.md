# REPORTE QA 3.27 — Pulido técnico

## Identificación
- Versión objetivo: 3.27 — Pulido técnico.
- Rama: `release/3.27-pulido-tecnico`.
- Base: `main` / 3.26.
- Archivo modificado: `index.html`.
- Guardado: `mesero30save`, marcador 50.

## Pruebas ejecutadas
| Prueba | Resultado | Alcance |
|---|---|---|
| Parseo sintáctico del JavaScript embebido | APROBADO | Compilación con el parser JavaScript del entorno |
| IDs HTML duplicados | APROBADO | No se detectaron duplicados |
| Botones sin nombre accesible explícito | APROBADO | 0 botones sin `id`, `aria-label` o `aria-labelledby` |
| Marcador de guardado | APROBADO | `saveVersion: 50` |
| Metadatos de versión | APROBADO | Título, HUD y menú en 3.27 |
| Foco y semántica del diálogo | REVISIÓN ESTÁTICA | Atributos ARIA, foco inicial y restauración implementados |

## No ejecutado
- No se realizó prueba visual manual en navegador.
- No se probó en dispositivo móvil físico.
- No se ejecutó una batería de partidas reales para verificar guardados históricos.
- No se midió rendimiento con perfilador del navegador.
- No se certificaron rutas completas ni colisiones mediante recorrido automatizado.

## Dictamen
**APROBADO CON ALCANCE LIMITADO.** La primera pasada de accesibilidad y controles está implementada y supera las comprobaciones estáticas indicadas. No equivale a una certificación integral de 3.27. Las pruebas visuales, táctiles, de regresión y rendimiento permanecen pendientes.

## Protección narrativa
Las propuestas de orientación y fichas afectivas permanecen intactas y fuera del canon; no se incorporaron cambios narrativos en esta rama.
