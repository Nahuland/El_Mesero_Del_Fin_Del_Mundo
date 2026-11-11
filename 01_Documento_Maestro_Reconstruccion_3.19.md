# EL MESERO DEL FIN DEL MUNDO
## Documento Maestro de Reconstrucción y Producción 3.12

**Estado:** reconstrucción iniciada — prototipo alfa jugable  
**Principio rector:** conservar la identidad narrativa y reconstruir la experiencia jugable, no seguir acumulando parches sobre la arquitectura anterior.

---

## 1. Decisión de producción

La versión 3.0 se desarrolla como una base nueva e independiente. Las versiones 2.5D, 2.6 y 2.7 quedan archivadas como referencias de contenido y continuidad, no como arquitectura obligatoria.

Se conserva el Guion Maestro Fase 4 como fuente narrativa. Este documento no lo reemplaza: establece cómo convertirlo en una experiencia jugable comprobable.

## 2. Pilares no negociables

1. **Mundo semiabierto real:** la exploración sucede en un espacio conectado. Las zonas son regiones de un mismo mundo, no una secuencia de pantallas que se cargan al derrotar jefes.
2. **Vista isométrica 2.5D:** movimiento en ocho direcciones de pantalla (cardinales y diagonales), cámara que sigue al jugador, profundidad por orden de dibujo, colisiones y puntos de acceso visibles.
3. **Narrativa superpuesta:** los diálogos son escenas de novela visual encima del escenario, con retrato, nombre, texto, decisiones y bloqueo del movimiento.
4. **Consecuencias visibles:** las decisiones modifican rutas, personajes, presencia de facciones, refugios y estado de las regiones.
5. **PC y móvil diferenciados:** teclado en PC; controles táctiles solo en dispositivos con puntero táctil.
6. **Progreso persistente:** guardar posición, decisiones, objetos, misiones y cambios del mundo. Migración de partidas antiguas solo cuando sea segura y explícita.
7. **Entrega verificable:** no se declara terminada una fase por tener funciones escritas; debe poder jugarse y comprobarse.

## 3. Continuidad narrativa

Se conserva la premisa y continuidad del Guion Maestro Fase 4:

- S-07, llamado Siete por Don Aurelio, despierta 26 años después de la guerra en La Estrella.
- Estrella retiró manualmente su batería para protegerlo del Protocolo Siesta.
- La señal externa manipuló unidades robóticas.
- La Fiebre Gris procede de una cápsula transportada por el Vuelo 9.
- La Secta del Sol y la Luna y el ejército tienen historias y responsabilidades complejas; no son facciones planas.
- El eje temático es construir un mundo libre sin repetir la violencia que lo destruyó.

No se alteran nombres, hechos ni relaciones establecidos por el guion sin una decisión editorial expresa.

## 4. Arquitectura de mundo

### Escala y reserva de expansión

Las regiones se diseñan como grandes espacios continuos, no como habitaciones compactas ni niveles cerrados. El terreno explorable debe tener margen libre alrededor de las zonas de contenido para incorporar misiones, encuentros, secretos, edificios e historias secundarias sin tener que rediseñar el mapa base. La escala se amplía por exploración útil y puntos de interés, no por rellenar con límites artificiales.

El primer prototipo ampliado utiliza un terreno de 120 × 96 unidades de mapa como reserva espacial inicial. Es una escala de prototipo, no un límite definitivo del mundo. La cámara renderiza el entorno cercano al jugador para conservar rendimiento.


### Regiones y progresión

La geografía final mantiene las cinco grandes áreas narrativas:

1. La Estrella y el cinturón exterior.
2. Territorio de las máquinas — Calle Oxidada, Depósito, Línea de Montaje, Túnel, Patio y Fábrica.
3. Ciudad enferma — Barrio, Parque, Metro, Centro Comercial, Cementerio, Hospital y Nido.
4. Territorio del culto — Aldea, Bosque, Mercado, Catacumbas, Escalinata, Templo y Santuario.
5. Territorio militar — Puerto, Trincheras, Hangar, Muelle, Puente, Aeródromo y Fortaleza.

La geografía se organiza como un grafo de regiones y accesos. Los sectores no se convierten en niveles independientes. Las fronteras pueden tener puertas, derrumbes, puentes, túneles y atajos desbloqueables.

### Reglas de acceso

- El jugador debe ver el camino, puerta o bloqueo que limita su avance.
- Los bloqueos deben tener una causa narrativa o física legible.
- Al desbloquear un atajo, el cambio queda en el mundo y permanece después de guardar.
- No se debe teletransportar al jugador a otro escenario por derrotar a un jefe.
- Los interiores pueden tener una instancia visual propia, pero se entra y sale por puertas físicas sin perder continuidad.

## 5. Interfaz y presentación

### Diálogo de novela visual

El panel se superpone al canvas y contiene:
- Retrato grande del personaje.
- Nombre y, cuando corresponda, emoción.
- Texto con avance controlado.
- Opciones de decisión claramente diferenciadas.
- Oscurecimiento del escenario y pausa de movimiento mientras la escena está activa.

No se permite que el diálogo empuje el canvas ni se comporte como un panel normal debajo del juego.

### Dispositivos

- PC: ocho direcciones mediante WASD/flechas combinadas, diagonales Q/R/Z/C o teclado numérico; E para interactuar, J para diario, F5 para guardar.
- Móvil: controles táctiles visibles solo en dispositivos táctiles.
- El cambio de dispositivo no debe dejar controles superpuestos en PC.
- Respetar `prefers-reduced-motion`.

## 6. Vertical slice obligatorio

La primera entrega reconstruida debe completar un recorrido pequeño, pero coherente:

**La Estrella → Calle Oxidada → Depósito de Chatarra → encuentro con el Desertor.**

Debe incluir:
- Pantalla de inicio y despertar de Siete.
- Restaurante explorable, con objetos de memoria.
- Puerta que se abre y permite salir físicamente.
- Calle conectada con el depósito, sin pantalla de selección de nivel.
- Cámara isométrica, movimiento y colisiones.
- Interacciones con objetos y un NPC.
- Diálogo de novela visual superpuesto.
- Diario con objetivo actualizado.
- Guardado y carga de posición y progreso.

El prototipo 3.0 Alfa implementa la primera versión de este recorrido y sirve para probar el nuevo enfoque. La revisión de movimiento y escala amplía el terreno a 120 × 96 unidades, incorpora movimiento en ocho direcciones y añade hitos distantes como reserva de expansión. Aún no representa el juego completo ni contiene el combate final del Capitán Oxidado.

## 7. Fases de producción

### Fase A — Fundamentos jugables
- Validar cámara, escala, colisiones y profundidad.
- Ajustar la puerta de La Estrella y el recorrido exterior.
- Confirmar que no hay carga de niveles al avanzar.
- Verificar controles de PC y móvil.

### Fase B — Narrativa integrada
- Sistema de escenas y retratos.
- Retratos y expresiones consistentes.
- Árbol de decisiones y banderas.
- Diario y objetivos.

### Fase C — Primer capítulo completo
- Depósito y Línea de Montaje.
- Desertor y Superviviente.
- Consolas del Capataz.
- Encuentro y jefe Capataz.
- Resolución alternativa si se cumplen las condiciones narrativas.
- Secuencia posterior sin diálogos heredados o duplicados.

### Fase D — Expansión semiabierta
- Añadir ciudad, culto y territorio militar.
- Rutas y atajos persistentes.
- Facciones y cambios ambientales.
- Compañeros y misiones personales.

### Fase E — Pulido
- Combate, animaciones y jefes.
- Accesibilidad, rendimiento y configuración.
- Pruebas de guardado, carga y compatibilidad.
- Prueba de regresión en PC y móvil.

## 8. Criterios de aceptación

Una fase no se considera terminada hasta cumplir todos sus criterios:

- Se puede jugar de principio a fin sin errores bloqueantes.
- Las transiciones son físicas y coherentes.
- No aparecen niveles descartados ni cargas automáticas no justificadas.
- Los diálogos aparecen sobre el mundo, no dentro del flujo de página.
- Los controles táctiles no aparecen en PC.
- Las escenas de jefes no llaman dos veces a la resolución ni muestran diálogos de versiones antiguas.
- El guardado restaura posición, estado del mundo y decisiones.
- La entrega incluye una lista de cambios visibles y limitaciones conocidas.

## 9. Política de versiones

- **3.0 Alfa:** prueba de arquitectura y primera zona conectada.
- **3.0 Beta:** vertical slice completo del primer capítulo.
- **3.1+:** expansión del mundo y sistemas una vez validada la base.

No se incrementa la versión por sumar código invisible. Cada versión debe aportar un cambio observable y verificable en la experiencia.


---

## 10. Actualización de producción — Versión 3.1: expansión espacial inicial

**Estado:** esqueleto territorial integrado en HTML; contenido completo de las nuevas regiones pendiente.

### Cambios implementados
- Se amplió el mapa exterior de `205 × 145` a `420 × 300` unidades lógicas.
- Se conservaron las coordenadas de los puntos preexistentes del Capítulo I.
- Se reemplazó la clasificación de zona basada principalmente en X por una clasificación que considera X e Y.
- Se incorporaron caminos principales y ramales de exploración según el plano de coordenadas 3.1.
- Se añadieron los 39 puntos propuestos del CSV como hitos visibles de referencia.
- Se incorporó una compuerta física en la boca oriental del Túnel de Servicio. Se desbloquea al recuperar la traza del Núcleo de comunicaciones y queda registrada en el estado persistente.
- Se diferenció visualmente el terreno de ciudad, territorio militar y territorio del culto.
- Se definió una franja de agua en la costa suroeste y una colisión específica para impedir caminar sobre ella.
- Se mantuvieron las instancias interiores del Depósito y del Patio.

### Decisión de nomenclatura regional
Hay una discrepancia entre documentos: el Atlas intercambia los números de las regiones 4 y 5 en sus apartados descriptivos, mientras que el diagrama macro, el Plano Detallado y el CSV asignan **R4 al Territorio Militar** y **R5 al Territorio del Culto**. Esta implementación sigue el Plano Detallado y el CSV, por ser las referencias de coordenadas concretas.

### Alcance y límites de esta entrega
Esta versión incorpora el esqueleto geográfico y de navegación, no el contenido completo de las cinco regiones. Los nuevos hitos son referencias explorables con una ficha breve derivada de su función en el atlas; todavía no tienen misiones, NPC, diálogos narrativos extensos ni edificios con colisión individual. La Ciudad Enferma, el Culto y el Territorio Militar quedan preparados para producción de contenido posterior.

### Validación realizada
- Sintaxis JavaScript comprobada con `node --check`: sin errores.
- Comparación de los puntos originales del HTML: 39 identificadores conservados, sin cambios de coordenadas.
- Se verificó la incorporación de los 39 puntos propuestos del CSV y de la nueva compuerta del Túnel.
- No se declara superada una partida manual en navegador ni una prueba física en móvil. La ejecución de Chromium headless no pudo completarse en este entorno; por eso esas pruebas quedan pendientes.

### Próximo trabajo recomendado
1. Probar manualmente el recorrido del Capítulo I y la salida oriental del Túnel.
2. Probar el guardado y la restauración de `cityGateOpen` después de cerrar y volver a abrir el navegador.
3. Añadir colisiones selectivas a edificios y barreras de las nuevas regiones, sin bloquear los corredores.
4. Desarrollar la Ciudad Enferma como siguiente región jugable, comenzando por Puerta de la Ciudad, Barrio y Plaza del Tranvía.


---

## 11. Actualización de producción — Versión 3.2: Ciudad Enferma jugable y auditoría abierta del Capítulo I

**Estado:** primera porción jugable de R3 integrada. El Capítulo I queda sujeto a revisión espacial continua; no se considera una zona congelada.

### Ciudad Enferma — contenido incorporado
- Manzanas residenciales y local de barrio con huellas de colisión.
- Centro Comercial, Hospital y Nido con edificios reconocibles y umbrales físicos.
- Parque municipal con árboles colocados fuera de los corredores; Cementerio con lápidas y recorrido de acceso.
- NPC Mara (Barrio), Tomás (Parque) y doctora Ibarra (Hospital), además de un encuentro con un infectado errante.
- Interiores instanciados para Centro Comercial, Metro, Hospital y Nido. Cada uno conserva su punto de retorno.
- Primera cadena de objetivos: ayudar a Mara con suministros; reunir el archivo epidemiológico y la muestra; habilitar el acceso al Nido; investigar su núcleo y el registro de evacuación.
- Panel del Metro que habilita un atajo persistente a la salida sur urbana (218,139).
- El acceso al Nido requiere las dos evidencias hospitalarias; pueden obtenerse en cualquier orden.

### Auditoría del Capítulo I — correcciones aplicadas
- Los interiores del Depósito y del Patio ya no dibujan paredes ni aplican colisiones cuando el personaje está en el exterior. Esto elimina la superposición que afectaba al corredor oriental hacia Ciudad Enferma (aprox. X 158–198).
- Se desplazó el banco de reparación del Patio de (175,101) a (180,103) para separarlo del banco/plataforma contiguo.
- Se movió la estantería oriental del Depósito de X=184 a X=187 para despejar el punto de interacción de la grúa.
- Se conservaron 38 de los 39 puntos originales con sus coordenadas; el único cambio de posición es `patioworkbench`. Los interiores continúan instanciados y no son geografía exterior.
- Se ajustaron trazados urbanos para que no terminen dentro de las huellas del Centro Comercial, Hospital o Nido. El Hospital suma una entrada norte y una salida de emergencia al sur.

### Guardado y compatibilidad
Se conserva la clave `mesero30save`. El nuevo estado `state.city` se incluye en el objeto de estado ya serializado por el guardado existente. Las partidas anteriores inicializan `state.city` vacío al cargarse; no se reemplazan automáticamente las decisiones ni el progreso del Capítulo I.

### Alcance y pendientes
Esta versión es una primera entrega jugable de Ciudad Enferma, no el cierre de toda la región. Quedan pendientes el desarrollo de encuentros y combate avanzados, misiones secundarias, más supervivientes, diálogos ramificados, interiores adicionales y consecuencias regionales de mayor alcance.

### Próximo trabajo
1. Prueba manual de la ruta completa desde el Túnel hasta el Barrio y los interiores urbanos.
2. Probar guardado/carga real con una partida 3.1 y una partida nueva 3.2.
3. Profundizar la historia del Metro y el origen del foco del Nido.
4. Continuar la auditoría del Capítulo I con pruebas de recorrido, no con una regla de conservación absoluta de coordenadas.


---

## 11. Actualización de producción — Versión 3.3: decisiones, consecuencias y jefes

**Estado:** nueva capa narrativa y de combate implementada sobre la versión 3.2.

### Objetivo de diseño
La progresión hacia un jefe no debe depender solo de caminar hasta su ubicación. Debe exigir preparación, lectura de pistas, gestión de recursos y comprensión parcial de los conflictos. Las decisiones no se presentan como una opción correcta y otra incorrecta: cada una protege algo y pone otra cosa en riesgo.

### Ciudad Enferma — decisiones y consecuencias
- **Mara:** después de recuperar suministros, elegir entre estabilizar el Barrio o enviar parte al Hospital. La primera opción habilita un recurso de emergencia para el enfrentamiento; la segunda permite a Ibarra preparar un inhibidor.
- **Tomás:** decidir si acusarlo, pedirle detalles o no juzgarlo todavía. En todos los casos puede aportar su testimonio, pero la relación y la lectura moral del jugador cambian.
- **Radio municipal:** transmitir públicamente la advertencia sobre las voces sintéticas o guardar el registro para evitar el pánico. La elección queda persistida y no se puede revertir al volver a interactuar.
- **Infectado errante:** inmovilizarlo sin destruirlo o neutralizarlo. La elección registra si Siete prioriza preservar una posible conciencia o eliminar una amenaza inmediata.
- **El Coro (jefe del Nido):** no puede enfrentarse de manera responsable hasta reunir archivo y muestra del Hospital, restaurar el panel del Metro, escuchar el registro de la radio y obtener el testimonio de Tomás. El combate ofrece lectura de patrón, aplicación de muestra, corte del retorno, inhibidor y ataque directo.
- **Resolución del Nido:** destruir el núcleo, desincronizarlo (la señal puede escapar) o sellarlo (protege el Barrio, pero abandona a los conectados). La decisión queda fija y cambia los diálogos posteriores de Mara e Ibarra.

### Capítulo I — Capataz
- Integridad elevada a 180 puntos.
- Opciones tácticas diferenciadas: golpe pesado, esquiva, sobrecarga de consolas a cambio de piezas y reparación de emergencia.
- La resolución pacífica ya no se activa solo por hablar con el Desertor: requiere además el manifiesto del Depósito y el cuaderno de mantenimiento del Patio.
- La propuesta de paz es una asamblea provisional, no una rendición instantánea. Exigir que el Capataz entregue todo el control provoca el rechazo y abre el conflicto.

### Persistencia y compatibilidad
- Se mantienen el identificador de guardado `mesero30save` y la estructura de estado existente.
- Los nuevos flags se agregan dentro de `state.city` y `state.flags`.
- La carga de una partida 3.2 inicializa los nuevos estados sin exigir empezar una partida nueva.
- Un guardado heredado con el valor inicial de 100 puntos de Capataz se migra a la nueva integridad de 180, salvo que el jefe ya haya sido derrotado o que exista un combate guardado en curso.

### Límite de validación
La lógica se comprobó con 18 pruebas automatizadas en un entorno DOM simulado y `node --check`. Esto no sustituye una partida manual visual completa, la comprobación real de localStorage al cerrar/reabrir ni las pruebas en móvil físico.


---

## 12. Actualización de producción — Versión 3.4: continuidad y memoria de decisiones

**Estado:** pasada de continuidad narrativa y persistencia integrada sobre 3.3. La historia central y sus hechos establecidos permanecen sin cambios.

### Criterio de continuidad
Se mantiene la continuidad de S-07/Siete, La Estrella, Don Aurelio y Estrella, el Protocolo Siesta, la señal externa y la Fiebre Gris asociada al Vuelo 9. Las facciones siguen siendo complejas y no se convierten en bandos simples de buenos y malos. No se agregan revelaciones que contradigan el Guion Maestro Fase 4.

### Cambios jugables y narrativos
- Mara ahora recuerda en su conversación posterior al Nido el reparto de suministros, la decisión sobre la radio y el destino incierto de Julián.
- Tomás reacciona al desenlace según el trato recibido, la decisión del Nido y si la advertencia se transmitió o se mantuvo privada. La confesión no lo absuelve ni lo convierte en villano plano.
- Ibarra explica qué permitió o impidió la decisión de suministros y distingue inhibición, contención y cura.
- El registro de evacuación cambia su lectura posterior según el desenlace, sin afirmar que todas las personas conectadas sobrevivieron.
- El diario resume varias consecuencias recordadas, no solamente el último desenlace.
- Se centralizó la escritura de guardados manuales y automáticos, se añadió `saveVersion: 34` y se corrigió la carga: las partidas guardadas con `started:false` ahora vuelven a habilitar el movimiento tras continuar.
- Se mantiene la clave `mesero30save` para compatibilidad con las partidas anteriores.

### Validación
- Sintaxis JavaScript: aprobada con `node --check`.
- Regresión de sistemas 3.3: 18/18 pruebas aprobadas.
- Continuidad, consecuencias y guardado 3.4: 16/16 pruebas aprobadas.
- La suite verificó carga de un guardado legado 3.3, decisiones de Mara/Tomás/radio, reacciones de supervivientes para los desenlaces y persistencia del interior activo.
- No se completó una prueba visual manual en navegador: el entorno bloqueó la navegación automatizada. Tampoco se realizó prueba en teléfono físico.

### Pendientes reales
1. Partida visual completa de Capítulo I y Ciudad Enferma en navegador normal.
2. Cerrar y reabrir el navegador para validar el guardado real, además de probar migración desde partidas de versiones anteriores.
3. Prueba en teléfono físico y ajuste de legibilidad/controles.
4. Continuar el contenido de Ciudad Enferma con misiones secundarias, personajes y amenazas, sin expandir todavía a otra región.


## Addendum 3.5 — incorporación geográfica del territorio de la Secta del Sol y la Luna

Se incorporó la primera capa física exterior de R5 siguiendo las coordenadas y el orden del Plano Detallado: Umbral del bosque, Sendero de los símbolos, Aldea, Mercado, Catacumbas, Escalinata, Templo y Santuario. Se añadieron huellas de edificios, puestos, arcos, hitos de piedra, vegetación y colisiones independientes. Los caminos conservan el trazado previsto y se agregaron puntos de inspección en los accesos.

**Alcance deliberadamente limitado:** esta etapa no agrega NPC, misiones, diálogos de facción, interiores jugables, revelaciones ni decisiones del culto. Las descripciones son observaciones ambientales y no establecen hechos nuevos del Guion Maestro. Los interiores de Catacumbas, Templo y Santuario quedan pendientes.

**Territorio militar:** permanece como reserva geográfica del plano. No se añadieron instalaciones funcionales, enemigos, misiones ni contenido narrativo militar. Su desarrollo se posterga expresamente para el tramo final de la historia.

La clave de guardado continúa siendo `mesero30save`; se incrementa el identificador de formato a 35 sin alterar los datos existentes de decisiones o progreso.


## Addendum 3.6 — revisión de conectividad y accesos de R5

Se revisó la red exterior de la Secta del Sol y la Luna con una comprobación de transitabilidad basada en la función real de colisiones del juego. Se reorganizaron árboles y una vivienda de la Aldea para despejar el corredor Umbral–Sendero–Aldea. Se ajustó la fachada de Catacumbas para que no invada el paso hacia la Escalinata y se desplazó el edificio del Santuario hacia el este para preservar su acceso occidental.

La red queda organizada en siete tramos: Umbral–Sendero, Sendero–Aldea, Aldea–Mercado, Aldea–Catacumbas, Catacumbas–Escalinata, Escalinata–Templo y Escalinata–Santuario. Se corrigieron las subzonas del HUD para distinguir Bosque, Aldea, Mercado, Catacumbas, Templo y Santuario con mayor precisión.

No se agregaron NPC, misiones, doctrinas, interiores ni revelaciones de la Secta. El territorio militar continúa reservado para el final de la historia.

La clave `mesero30save` se conserva y el formato de guardado pasa a la versión 36.


## Actualización de producción — Versión 3.7: interior de Catacumbas

Se incorpora una instancia subterránea explorable conectada físicamente al acceso exterior de R5. El interior contiene un corredor central, cámaras laterales, pilares, sarcófagos vacíos, filtraciones y tres puntos de inspección ambiental. Una caja de herramientas entrega dos piezas menores una sola vez. No se incorporan NPC, misiones, doctrinas, símbolos interpretables ni revelaciones de la Secta.

El acceso exterior se encuentra en (354,220). El interior ocupa la instancia lógica (329–361, 91–125), con entrada/salida al sur en torno a (345,123). La posición exterior se guarda como `returnPoint` y se restaura al salir. El estado del interior y su posición se conserva en `mesero30save`; `saveVersion` pasa a 37.

El Templo y el Santuario siguen pendientes. El territorio militar no recibe contenido.


## Actualización de producción — Versión 3.8: interior del Templo

Se habilita el acceso norte del Templo en R5, conservando su coordenada exterior (352,247) y su huella arquitectónica (30×22) en el mapa maestro. La puerta abre una instancia interior independiente, ubicada en (329–361, 132–166), con nave principal, columnas, bancos laterales y una plataforma vacía. El corredor central queda despejado y la salida sur devuelve al jugador a la posición exterior exacta desde la que ingresó.

Se incorporan tres inspecciones ambientales: marcas de desgaste en el pavimento, una grieta de filtración y un nicho vacío. Sus descripciones no identifican responsables, no reconstruyen doctrinas y no agregan revelaciones, NPC ni misiones. El Santuario continúa pendiente y el territorio militar permanece reservado.

La clave `mesero30save` se conserva; `saveVersion` pasa a 38. Las partidas 3.7 mantienen sus campos existentes y el nuevo interior no exige reiniciar la partida.


## Addendum 3.9 — expansión geográfica R1/R2 y clasificación territorial

La versión 3.9 continúa sobre el HTML 3.8 sin reconstruir los sistemas existentes. Se implementa:

- Clasificación de región mediante X e Y, usando los límites maestros 420×300 y el solapamiento R1/R2.
- Etiquetas de subzona más precisas para La Estrella, cinturón exterior, máquinas, Ciudad Enferma, corredor sur, territorio militar y R5.
- Hitos ambientales visibles en R1/R2: estación de bombeo, puesto de vigía, puente viejo, refugio de caminantes, patio de vehículos, patio de contenedores, taller de desguace, almacén bloqueado y subestación.
- Un corredor visual desde el paso del puente viejo que termina antes de abrir la región militar.
- El guardado pasa a saveVersion 39 y añade el identificador de región, conservando la clave `mesero30save` y los datos anteriores.

Los hitos nuevos son ambientales y no interactivos: no añaden NPC, misiones, botín, doctrinas ni contenido militar. No se han cambiado coordenadas existentes del Capítulo I, Ciudad Enferma, Catacumbas o Templo.

**Pendiente:** colisiones específicas para los nuevos hitos, atajos condicionados por decisiones, interior del Santuario, prueba funcional/visual en navegador y prueba en móvil físico.


## Addendum 3.10 — colisiones, accesos y caminos R1/R2

La capa ambiental incorporada en 3.9 recibe colisiones físicas en los nueve hitos nuevos. Se conservan los puntos de acceso del plano maestro: Estación de bombeo (31,61), Puesto de vigía (22,84), Puente viejo (52,90), Refugio (69,82), Patio de vehículos (63,42), Patio de contenedores (58,44), Taller de desguace (82,76), Almacén (112,54) y Subestación (132,59).

Los caminos secundarios se reordenan para llegar a esos accesos sin atravesar las huellas de los hitos. El paso del Puente Viejo sigue derrumbado: el corredor al sur permanece visible como aproximación, pero no constituye un cruce abierto.

El Almacén recibe una puerta física en (112,54). Las tres consolas industriales, que ya habilitan la compuerta de fábrica, permiten liberar el pasillo central de mantenimiento. El estado persistente se guarda en `state.flags.warehouseShortcut`; no se agregan objetos, NPC ni misiones nuevas.

R4 permanece como región cartográfica, pero el jugador no puede ingresar desde otra región en esta etapa. Una partida anterior que ya estuviera dentro puede desplazarse y salir, preservando su posición guardada. No se añade contenido militar.

La clave `localStorage` `mesero30save` se conserva y `saveVersion` pasa a 40. Las partidas anteriores siguen usando la estructura existente; las nuevas banderas se inicializan dentro de `state.flags`.


## Actualización de producción — Versión 3.13: interior del Santuario

Se habilita la entrada occidental del Santuario en (384,276), respetando la huella exterior definida por el Plano Detallado (18×18, centro aproximado 395,276). La puerta abre una instancia interior independiente en (365–397, 190–224), con acceso/salida occidental. La posición exterior exacta desde la que se ingresa se conserva mediante `returnPoint`.

La sala incorpora arquitectura de piedra, cuatro columnas periféricas, bancos bajos, una plataforma vacía y tres puntos de inspección ambiental: umbral de piedra, repisa cubierta de polvo y filtración de luz. No se añaden NPC, doctrinas, misiones, decisiones, objetos de culto ni revelaciones sobre lo que se guarda en el Santuario. Su función narrativa permanece deliberadamente sin resolver.

La colisión exterior mantiene sólida la huella del edificio salvo el umbral occidental. El interior tiene perímetro propio, salida abierta y obstáculos internos que dejan libre el corredor de entrada. El Santuario queda explorable sin habilitar el territorio militar ni alterar el paso tardío entre R4 y R5.

La clave `mesero30save` se conserva y `saveVersion` pasa a 41. La nueva instancia no requiere reiniciar la partida; el punto de retorno se guarda con el mismo mecanismo de interiores existente.

### Validación 3.12
- Sintaxis JavaScript: aprobada con `node --check`.
- Integridad HTML: estructura de etiquetas y bloques script verificada.
- Geometría: perímetro, salida occidental, plataforma, bancos y columnas contrastados con los límites de la sala.
- Prueba de navegador, inspección visual manual y prueba móvil: pendientes; no se declaran aprobadas.


## Addendum 3.12 — exploración e interacciones R1/R2

Se añade una primera capa de interacción a los diez hitos exteriores ya definidos en el CSV maestro de R1/R2: Cruce del cinturón, Patio de vehículos, Estación de bombeo, Puesto de vigía derruido, Paso del puente viejo, Refugio de caminantes, Patio de contenedores, Taller de desguace, Almacén bloqueado y Subestación.

Las interacciones se limitan a inspección ambiental, registro de exploración y servicios de recursos/reparación que corresponden a las funciones ya asignadas en el Atlas. Patio de vehículos y Taller de desguace permiten recuperar dos piezas una sola vez; el banco del taller repara 30 puntos de integridad por dos piezas. El diario registra el progreso de hitos revisados.

No se agregan NPC, misiones, doctrinas, revelaciones ni hechos nuevos de canon. El Puente Viejo sigue siendo un límite infranqueable; R4 permanece cerrado. El Almacén continúa sujeto a la activación de las tres consolas industriales. La Subestación no reemplaza ni altera el sistema de consolas.

El guardado conserva la clave `mesero30save`, migra los indicadores de exploración de forma aditiva y actualiza `saveVersion` a 42.


## 13. Actualización de producción — Versión 3.13: exploración de Ciudad Enferma

Se amplía la exploración exterior de R3 con siete puntos de inspección: Puerta de la ciudad, Barrio residencial, Plaza del tranvía, Parque municipal, Cementerio, Salida sur urbana y Paso del bosque. Cada punto registra su primera inspección en un indicador persistente del diario (0–7). Las visitas repetidas informan que el lugar ya fue registrado, sin duplicar recompensas ni alterar el mundo.

Los textos se limitan a condiciones observables y orientación geográfica. No identifican responsables, no resuelven el origen de la Fiebre Gris, no confirman el destino de Julián y no habilitan el corredor militar ni nuevas entradas a R4. Las misiones, personajes, interiores y decisiones preexistentes de la Ciudad Enferma se conservan.

### Persistencia y compatibilidad
- Se conserva `localStorage` bajo la clave `mesero30save`.
- `saveVersion` pasa de 42 a 43.
- El nuevo objeto `flags.cityPoiExplored` se inicializa de forma aditiva; no sustituye ni borra `poiExplored`, `state.city`, decisiones, inventario, interiores ni coordenadas previas.
- No se cambian coordenadas maestras ni huellas físicas.

### Pendientes de validación
La sintaxis y las comprobaciones estáticas se ejecutan en esta entrega. La partida visual completa, la restauración real desde navegador y la prueba en móvil físico siguen pendientes y no se declaran aprobadas.


## 14. Actualización de producción — Versión 3.15: reconocimiento del corredor sur

Tras resolver el Nido, se habilita una tarea de reconocimiento civil en el extremo sur de R3. El jugador inspecciona tres referencias ya situadas sobre el corredor urbano: Señal urbana caída (221,128), Canal de desagüe (233,131) y Mojón de evacuación (214,136). Cada inspección queda guardada y el diario muestra el progreso 0/3–3/3.

Al completar los tres puntos, el trazado civil queda cartografiado y se actualiza el objetivo. Esto prepara la continuidad hacia el sur, pero no abre R4, no crea un acceso alternativo, no revela instalaciones, unidades ni responsables militares y no altera el mapa maestro ni sus huellas. Las diferencias de texto dependen únicamente del desenlace del Nido: destruido, desincronizado o sellado.

### Persistencia
- Se conserva `mesero30save`; `saveVersion` pasa de 43 a 44.
- `state.city.southSurvey` se inicializa de forma aditiva durante la carga.
- Las tres inspecciones son persistentes y no entregan recursos repetibles.
- No se alteran decisiones de suministros, radio, Tomás, infectado ni resolución del Nido.

### Validación
Se verifica sintaxis JavaScript, presencia de los tres hitos, condición de acceso posterior al Nido, contador y persistencia. La prueba visual manual y el recorrido en móvil siguen pendientes.


## Addendum 3.15 — preparativos civiles de frontera

La salida sur urbana puede prepararse únicamente después de resolver el Nido y registrar los tres hitos civiles del corredor. La acción despeja escombros menores y deja señalización de orientación. No abre R4, no establece contacto, no añade soldados, mandos, instalaciones, órdenes ni información sobre la facción militar. El paso fronterizo permanece cerrado y el contenido militar sigue reservado para su tramo narrativo.


## 15. Cierre de validación — Versión 3.15

La validación técnica, estática, de sintaxis y de empaquetado de 3.15 queda cerrada y la versión se acepta como base de continuidad. La prueba visual manual en navegador y la prueba física en móvil permanecen pendientes y se mantienen identificadas como limitaciones; no se declaran aprobadas. El detalle queda en `04_REPORTE_QA_3.15_Cierre.txt`.

## 16. Actualización de producción — Versión 3.16: recursos civiles opcionales de R3

Se añade una capa secundaria de exploración en Ciudad Enferma mediante tres depósitos de mantenimiento ya fuera de las rutas narrativas principales: Plaza del tranvía (237,61), Parque municipal (214,100) y Cementerio (285,96). Cada punto permite recuperar una pieza reutilizable una sola vez. Al completar el inventario 3/3 queda disponible un banco de reparación civil en el Barrio (225,53), que consume dos piezas para restaurar 30 puntos de integridad. El diario registra el progreso 1/3–3/3.

La actividad es opcional, no altera las decisiones de Mara, Tomás, Ibarra ni el desenlace del Nido, y no modifica los accesos regionales. Los objetos no activan sistemas urbanos ni establecen nuevos hechos sobre la Fiebre Gris. La persistencia se guarda en `state.city.civicCaches`; la migración es aditiva y `saveVersion` pasa a 46. R4 permanece cerrado.


---

## Actualización de producción — Versión 3.17: consecuencias y seguimiento civil de R3

**Estado:** tareas opcionales posteriores al Nido integradas para Mara, Tomás e Ibarra. No se amplía el mapa ni se abre una región nueva.

### Contenido incorporado
- **Mara — Acta comunitaria:** después de resolver el Nido, puede dejar constancia de la distribución de suministros, la decisión sobre la radio y el desenlace. El acta no convierte la elección en una absolución ni resuelve el destino de Julián.
- **Tomás — Protocolo manual:** después de entregar su testimonio y resolver el Nido, puede registrar un procedimiento que exige verificación local y dos personas para operar compuertas. No borra su responsabilidad pasada.
- **Doctora Ibarra — Informe de seguimiento:** después de resolver el Nido, puede archivar observaciones diferenciando muestra, intervención y límites. No se declara una cura.
- Cada tarea es opcional, persistente y puede dejarse pendiente. El diario registra el avance 0/3–3/3 y los personajes muestran una marca visual al completar su registro.

### Continuidad y límites
- Las tareas solo se habilitan tras el desenlace del Nido; Tomás requiere además su confesión y la doctora conserva las condiciones de evidencia ya existentes.
- No se alteran las decisiones previas, los recursos, las coordenadas, las colisiones, los interiores ni los accesos regionales.
- No se introduce información nueva sobre el origen de la Fiebre Gris, la fuente remota de la señal ni el destino de Julián.
- R4 continúa cerrado y el arco militar permanece reservado.

### Persistencia
Se conserva `mesero30save`. La versión de guardado sube a 47. Los tres indicadores se inicializan de forma aditiva al cargar partidas 3.16 o anteriores; no se reinician las decisiones ya guardadas.

### Validación
Se comprueban sintaxis, presencia de ramas, condiciones de desbloqueo, marcas visuales, contador de seguimiento, versión de guardado y ausencia de cambios de coordenadas. La prueba visual manual y móvil físico siguen pendientes.


## 17. Actualización de producción — Versión 3.18: auditoría de conectividad R3/R5

**Alcance:** revisión de los corredores entre Ciudad Enferma (R3) y el Territorio del Culto (R5), sin expansión narrativa ni desplazamiento de geometría maestra.

### Ajustes implementados
- El camino de la Escalinata al Templo termina ahora en el acceso norte (352,247). Se elimina el tramo visual que continuaba dentro de la huella sólida del Templo y no era transitable.
- El HUD distingue la subzona **Paso del bosque** en el tramo final de R3 (X≥300, Y=110–134), antes del cruce regional situado en (309,139).
- El HUD distingue **Umbral del bosque**, **Sendero de los símbolos** y **Escalinata** en R5, además del **Paso del bosque** en R3.
- Se conserva la ruta R3 Cementerio/Hospital → Paso del bosque → Umbral del bosque → Sendero → Aldea y los ramales de Mercado, Catacumbas, Templo y Santuario.

### Límites preservados
- No se añaden ni desplazan puntos, huellas, edificios, puertas, interiores o colisiones.
- No se crea una segunda entrada a R5 ni se cambia la condición de acceso a Ciudad Enferma.
- R4 continúa cerrado; no se modifica el corredor militar ni se añade contenido de la Secta.
- No cambia el estado serializado ni el formato `saveVersion:47`; la actualización es compatible porque solo corrige trazado visual y etiquetas de subzona.

### Validación
Se ejecutó una auditoría geométrica estática de los ejes de los cinco tramos R3–R5: conexión al Umbral, Mercado, Catacumbas, Escalinata–Templo y Santuario. Los cuatro primeros accesos y la vereda al Santuario quedan libres en sus aproximaciones; el camino del Templo ahora termina en su umbral y no atraviesa el edificio. Se comprobó que las coordenadas del CSV 3.18 son idénticas a las de 3.17.

La sintaxis JavaScript y la integridad del ZIP se verifican en esta entrega. La prueba visual manual en navegador y la prueba en móvil físico siguen pendientes.


## 18. Actualización de producción — Versión 3.19: QA integral y correcciones de progresión

**Alcance:** auditoría de progresión desde el Túnel de Servicio hasta los interiores de R5, incluyendo conectividad, colisiones cartografiadas, retornos, guardado/carga y consistencia entre HTML, Atlas, Plano y CSV.

### Defectos detectados y corregidos
- **Carga de partidas bloqueada:** `savePayload()` serializaba `state.started:false`; `startGame(true)` mezclaba ese valor después de activar el juego. Al continuar una partida, el movimiento quedaba deshabilitado. Ahora `state.started=true` se restablece después de restaurar el estado.
- **Retorno inmediato del Santuario:** el punto de aparición interior coincidía con `sanctuaryReturn` en (367,207). Ahora la aparición es (369,207), dentro del corredor, separada del umbral de salida. La coordenada exterior de retorno (384,276) no cambia.
- **Metadato de región en interiores:** la clasificación del guardado dependía solo de las coordenadas artificiales de la instancia. Ahora las instancias se asignan a su región de origen: Depósito/Patio→R2; interiores urbanos→R3; Catacumbas/Templo/Santuario→R5.
- **Límite de subzona R3:** el Paso del bosque se limita a Y=110–134, coherente con la frontera lógica R5 que comienza en Y=135. El acceso del Umbral en (309,139) queda clasificado como R5.
- **Versión visible:** el menú identifica ahora 3.19. El guardado pasa a `saveVersion:48`.
- **Carga defensiva:** se validan el nombre del interior, el punto exterior de retorno y las coordenadas del jugador; un guardado inválido devuelve al punto seguro inicial en lugar de dejar al personaje dentro de una instancia sin salida.

### Compatibilidad
Se conserva la clave `mesero30save` y se acepta el estado previo 3.18/`saveVersion:47`. No se borran banderas narrativas ni inventarios. La corrección de carga restituye el estado activo después de la mezcla del objeto guardado. El formato nuevo se escribe como `saveVersion:48`.

### Límites de validación
La sintaxis, referencias, metadatos, tablas de coordenadas y geometría de corredores se verifican de forma automatizada/estática. El navegador de pruebas de esta sesión bloqueó la navegación local por política del entorno; por ello no se declara una partida manual completa ni una prueba visual real. La prueba en móvil físico sigue pendiente.
