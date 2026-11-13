# El Mesero del Fin del Mundo

Repositorio del juego y su documentación.

## Publicación web

El sitio se publica automáticamente en GitHub Pages mediante el flujo `.github/workflows/pages.yml`.

**Archivo de entrada requerido:** `index.html` en la raíz del repositorio.

Para publicar una versión:
1. Copiar el HTML principal del juego a la raíz y nombrarlo `index.html`.
2. Incluir junto a él cualquier carpeta de recursos que el juego necesite (por ejemplo, `assets/`).
3. Hacer commit en la rama `main`. El flujo de GitHub Actions realizará la publicación.

La primera vez, comprobar en **Settings → Pages** que la fuente de publicación esté configurada como **GitHub Actions**.

## Versión de trabajo

La versión de referencia preparada localmente es **3.19**. El informe de QA disponible indica validaciones estáticas aprobadas; no se registró una prueba manual/visual en navegador.


## Versión actual: 3.20 — Expansión ambiental de R5

- [Abrir el juego (GitHub Pages)](https://nahuland.github.io/El_Mesero_Del_Fin_Del_Mundo/)
- [HTML 3.20](El_Mesero_del_Fin_del_Mundo_3.20_R5_Expansion.html)
- [Actualización 3.20](06_Actualizacion_3.20_R5.md)
- [Coordenadas maestras 3.20](Coordenadas_Maestro_El_Mesero_3.20.csv)
- [Informe QA 3.20](REPORTE_QA_3.20_R5.txt)


## Versión actual: 3.21 — Geografía exterior de R4

- [Abrir juego 3.21](https://nahuland.github.io/El_Mesero_Del_Fin_Del_Mundo/)
- [HTML 3.21](El_Mesero_del_Fin_del_Mundo_3.21_R4_Geografia.html)
- [Actualización 3.21](07_Actualizacion_3.21_R4_Geografia.md)
- [Coordenadas maestras 3.21](Coordenadas_Maestro_El_Mesero_3.21.csv)
- [Informe QA 3.21](REPORTE_QA_3.21_R4_Geografia.txt)

R4 conserva el bloqueo de acceso. Esta entrega completa únicamente su primera capa geográfica exterior; la facción y la historia militar siguen pendientes.


## Versión 3.22 — auditoría y preparación documental del Acto IV

- [Plan de desarrollo de la facción militar R4](08_Plan_3.22_Desarrollo_Faccion_Militar.md)
- [Informe QA documental 3.22](REPORTE_QA_3.22_Plan.txt)

La auditoría documental fue completada y luego seguida por la implementación jugable inicial 3.22. El HTML principal ya integra la primera capa del Acto IV; quedan pendientes las pruebas visuales/manuales y la expansión de interiores y escenas secundarias.


### Diseño narrativo aprobado

- [Acto IV: facción, nombres, jerarquía y General como jefe final](09_Propuestas_3.22_Acto_IV_General_Jefe_Final.md)

El diseño narrativo fue aprobado por el usuario. La primera capa jugable está implementada; los interiores militares, las escenas de Damián Ferreyra y Celina Borda y las decisiones completas del Acto V siguen pendientes.


## Versión 3.22 — Ejército de Salvación (implementación inicial)

- [HTML principal 3.22](index.html)
- [HTML versionado 3.22](El_Mesero_del_Fin_Del_Mundo_3.22_Ejercito_Salvacion.html)
- [Plan y estado de implementación](08_Plan_3.22_Desarrollo_Faccion_Militar.md)
- [Detalle de implementación jugable 3.22](10_Implementacion_3.22_Ejercito_Salvacion.md)
- [Informe QA actualizado](REPORTE_QA_3.22_Plan.txt)
- [Propuesta narrativa aprobada](09_Propuestas_3.22_Acto_IV_General_Jefe_Final.md)

La versión incorpora la primera capa jugable del Acto IV: apertura de R4 tras la preparación civil, Elba, Nerea, evidencias, sabotaje, Funes, Richars Octavio y acceso posterior a la consola Siesta. saveVersion:49 y mesero30save se conservan. La prueba visual/manual y móvil queda pendiente.

## Versión 3.25 — Acto V: La última orden

- [Abrir juego (GitHub Pages)](https://nahuland.github.io/El_Mesero_Del_Fin_Del_Mundo/)
- [HTML principal 3.25](index.html)
- [HTML versionado 3.25](El_Mesero_del_Fin_del_Mundo_3.25_Acto_V_Ultima_Orden.html)
- [Implementación 3.25](14_Implementacion_3.25_Acto_V.md)
- [Informe QA 3.25](REPORTE_QA_3.25_Acto_V.txt)

La mesa de la Fortaleza convoca a Mira, Iván, Lía, Teo, Noa, Dante, Kai y Eva. Cada contacto plantea su confesión y petición; Siete registra una postura individual (acompañar, negociar o rechazar). Las elecciones se guardan una por una y la deliberación puede reanudarse. Se conserva `saveVersion:49`. No se elige todavía un final: esa etapa corresponde a 3.26.

## Versión 3.24 — cierre jugable del Acto IV

- [Abrir juego (GitHub Pages)](https://nahuland.github.io/El_Mesero_Del_Fin_Del_Mundo/)
- [HTML principal 3.24](index.html)
- [HTML versionado 3.24](El_Mesero_del_Fin_del_Mundo_3.24_Cierre_Acto_IV.html)
- [Implementación 3.24](13_Implementacion_3.24_Cierre_Acto_IV.md)
- [Informe QA 3.24](REPORTE_QA_3.24_Cierre_Acto_IV.txt)

La versión añade una mesa de revisión en la Fortaleza con 13 requisitos explícitos para consolidar las pruebas, testimonios, archivo de mando, derrota de Richars y decisión de Siesta. Se mantiene `mesero30save` y `saveVersion:49`. Validación estática aprobada; recorrido manual, guardado/carga real, visual y móvil siguen pendientes.

## Versión 3.23 — interiores militares y puente al Acto V

- [HTML principal](index.html)
- [HTML versionado 3.23](El_Mesero_del_Fin_Del_Mundo_3.23_Ejercito_Salvacion.html)
- [Implementación 3.23](11_Implementacion_3.23_Interiores_Acto_IV.md)
- [Plan posterior al mapa](12_Plan_Produccion_PostMapa.md)
- [Informe QA 3.23](REPORTE_QA_3.23_Interiores_Militares.txt)

La versión añade interiores del Hangar y Fortaleza, encuentros de Celina Borda y Damián Ferreyra, registros de operaciones y archivo de mando, y tres decisiones iniciales persistentes de Siesta. Se mantiene `mesero30save` y `saveVersion:49`. Validación estática aprobada; recorrido, visual y móvil pendientes.