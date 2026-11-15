# Auditoría 3.27 — Progresión y combate del Acto IV

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo inspeccionado:** `index.html`  
**Método:** inspección estática del código y contraste con el plan de producción y la implementación 3.23.  
**Estado:** auditoría estática; no equivale a una partida manual ni a una prueba de navegador.

## 1. Cadena de cierre del Acto IV

La mesa de revisión (`militaryAct4Review`) exige 13 condiciones:

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
13. Decisión persistente de Siesta.

La revisión solo marca `act4ReviewComplete` cuando las trece condiciones están registradas. El flujo es coherente con la documentación: el archivo, el recetario y Siesta quedan detrás de la derrota de Richars; la Fortaleza no abre antes.

**Consecuencia:** el Acto IV no se considera cerrado solo por derrotar al jefe. Hay que completar las pruebas y los testimonios, leer el archivo y tomar una de las tres decisiones de Siesta.

## 2. Contenido opcional y consecuencias tácticas

- Elba puede ser ayudada para sabotear las lanchas; requiere la llave inglesa del Cuartel.
- Ramiro Funes puede ser neutralizado en el Control del puente.
- Ninguna de estas dos acciones es requisito de la mesa de revisión. Esto coincide con el plan: son consecuencias tácticas, no sustitutos de las pruebas.
- El combate de Richars reduce el daño recibido si las lanchas fueron saboteadas (-6), Funes fue derrotado (-4) y se obtuvo la orden de ocultamiento (-2).

**Observación:** el código conserva la opcionalidad de Elba y Funes y aplica sus efectos al combate. Falta validar en una partida que las rutas opcionales sean alcanzables y que sus consecuencias se perciban con claridad.

## 3. Combate de Richars Octavio

La implementación actual contiene:

- Tres fases según la integridad restante: más de 174, entre 88 y 174, y 87 o menos.
- Ataque pesado: 46 de daño.
- Esquiva y contraataque: 30 de daño.
- Exposición de la cadena de órdenes: 58 de daño, una sola vez, si están reunidas las tres pruebas principales del Vuelo 9.
- Reparación: consume dos piezas, recupera 25 puntos y puede usarse una vez.
- Daño base entrante por fase: 15, 20 y 25, con reducciones por sabotaje, Funes y orden de ocultamiento.
- Richars es obligatorio, no se rinde y su derrota no apaga Siesta ni resuelve la señal externa.

### Hallazgo de diseño

Las fases cambian el texto y el daño entrante, pero todavía no ejecutan patrones de ataque claramente diferenciados ni un aviso visual previo a cada golpe. La frase de fase 2 describe una embestida y la fase 3 un ataque de área, pero el sistema resuelve ambas como daño numérico inmediato. La preparación artillera también está representada como reducción de daño, no como un evento de apoyo visible.

**Prioridad recomendada:** antes de alterar valores, diseñar una señal telegráfica por fase y hacer que el tipo de ataque anunciado determine el daño. Mantener las opciones actuales de ataque, exposición y reparación; no convertir la preparación opcional en requisito.

## 4. Accesos y espacios a comprobar

La inspección del código confirma condiciones de acceso para Hangar y Fortaleza y perímetros de colisión específicos para ambos interiores. También confirma que la salida de la Fortaleza y sus objetos interiores se filtran por `currentInterior`.

Quedan pendientes de prueba real:

- Ruta completa Puerto → Trincheras → Hangar → Muelle → Puente → Aeródromo → Fortaleza.
- Aproximación al acceso del Hangar y retorno al exterior.
- Entrada a la Fortaleza tras derrotar a Richars y salida desde el interior.
- Accesibilidad de los puntos de inspección del Puerto, Aeródromo y Puesto de radio.
- Colisiones alrededor del perímetro de la Fortaleza y del punto de combate de Richars.
- Guardado/carga en Hangar y Fortaleza, y persistencia de cada condición de cierre.

## 5. Estado y siguientes pasos

| Área | Estado de auditoría |
|---|---|
| Requisitos de cierre 13/13 | Confirmados estáticamente |
| Opcionalidad Elba/Funes | Confirmada en código; recorrido pendiente |
| Condición de acceso a Richars | Confirmada estáticamente |
| Tres fases de combate | Implementadas como umbrales de daño/texto |
| Patrones telegráficos por fase | Pendientes |
| Apoyo artillado visible | Pendiente |
| Ruta geográfica completa | Pendiente de recorrido |
| Guardado/carga y regresión | Pendientes |
| Prueba visual y móvil | No ejecutadas |

**Conclusión:** la estructura de progresión del Acto IV existe y su cierre está protegido por trece requisitos persistentes. El mayor pendiente de diseño identificado es hacer que las fases de Richars se distingan mecánicamente y que el apoyo opcional se comunique visualmente. No se modificó el HTML, la historia, el canon ni los guardados durante esta auditoría.
