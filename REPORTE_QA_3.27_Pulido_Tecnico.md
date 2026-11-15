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


## QA automatizado ampliado — GitHub Actions

- Workflow: [QA 3.27](https://github.com/Nahuland/El_Mesero_Del_Fin_Del_Mundo/actions/runs/43744142112).
- Estado: **APROBADO**.
- Estructura del mapa: IDs únicos, coordenadas dentro de límites, referencias válidas y retornos en los 11 interiores.
- Simulación del cierre 13/13 del Acto IV y bloqueo cuando falta un requisito.
- Verificación de que Elba y Funes son consecuencias tácticas opcionales, no requisitos del expediente.
- Puerta de evidencia del Vuelo 9 y cálculo de daño con modificadores tácticos.
- R5: interacciones de Noa y Dante, registro de doctrina, refugio, ubicación interior de puntos, Sol → Luna, bloqueo sin confianza y rendición limitada.
- Simulación de las condiciones de los ocho finales y de los bloqueos específicos de los finales 6 y 7.
- Escena de Teo y el Carnicero, resultado de lucidez temporal y persistencia en `savePayload()`.
- Chromium escritorio: carga de menú, inicio de partida, HUD visible, IDs sin duplicados y sin excepciones JavaScript.
- Chromium táctil 390×844: controles visibles, inicio de partida, ocho direcciones y objetivos direccionales de al menos 44×44 px.
- Guardado/carga: escritura real en `localStorage`, recarga de página y recuperación de banderas con el botón Continuar.

**Límite:** el workflow simula estados y ejecuta funciones reales en Chromium, y sí prueba la persistencia en `localStorage` tras recargar y continuar. No realiza un recorrido físico completo por los mapas, no migra una colección de guardados antiguos ni certifica un dispositivo móvil real. Los casos manuales de la matriz 18 siguen pendientes.
