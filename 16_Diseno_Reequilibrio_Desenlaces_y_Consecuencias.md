# Diseño narrativo — Reequilibrio de desenlaces y consecuencias
## Documento de trabajo · Revisión posterior a 3.26

**Estado:** propuesta de diseño para aprobación narrativa.  
**Base técnica revisada:** `index.html`, `15_Implementacion_3.26_Ocho_Desenlaces.md`, `REPORTE_QA_3.26_Ocho_Desenlaces.txt` y `12_Plan_Produccion_PostMapa.md`.  
**No modifica todavía el HTML ni las partidas guardadas.**

## 1. Diagnóstico de 3.26

La lógica actual tiene cuatro problemas estructurales:

1. `support` y `negotiate` cuentan igual para el total de aliados. La negociación no registra condiciones cumplidas, incumplidas ni confianza.
2. Las decisiones pacíficas se suman como puntos intercambiables. No se mide el coste, la estabilidad ni quién paga las consecuencias.
3. La consola ofrece `Siesta Voluntaria` siempre que se completa el consejo, y `Mesero de Hierro` con solo haber elegido control compartido.
4. El sistema de combate limita la integridad de Siete a 1 en los encuentros revisados. No existe derrota real, herida persistente ni coste duradero por retirarse y volver.

Además:
- `La Mesa Larga` depende de `cultResolution === 'reconciled'`, bandera que no existe en la progresión actual. No debe habilitarse artificialmente.
- La petición de Teo consume/reserva el antídoto, pero no existe una escena que resuelva el intento de salvar al Carnicero.
- `La Señal se Apaga` se resuelve en una consola a partir de documentos; no existe una incursión física al transmisor.
- El final médico exige que Lía sea acompañada y que Teo no reciba apoyo, pero no modela el destino de Lía ni las consecuencias humanas de la elección.

## 2. Principios de rediseño

- Ninguna postura moral será una puntuación universal de bondad.
- Negociar no equivale a conseguir apoyo: exige concesiones verificables y puede fracasar.
- Toda resolución de una facción debe tener coste, riesgo, consecuencias y supervivientes afectados.
- Los combates importantes deben poder dejar a Siete fuera de combate, obligar a retiradas y consumir recursos; la dificultad debe ser justa y telegráfica, no arbitraria.
- Los jefes no cambian de convicción por una conversación. Las salidas diplomáticas son treguas, intercambios, rendiciones limitadas o alianzas inestables, según el personaje.
- Algunas amenazas son irreconciliables. Richars Octavio permanece como canon: jefe obligatorio, sin rendición ni redención.
- Los finales expresan resultados mixtos: una victoria puede salvar a unos y condenar a otros.
- No se añadirá un contador global de moralidad ni se reducirá el desenlace a una ruta pacífica/violenta.

## 3. Propuesta de revisión de los ocho desenlaces

### 1. El Restaurante de Estrella
**Mantener el final, cambiar su significado de “ruta pacífica óptima” a “refugio ganado con sacrificios”.**

Requisitos de diseño:
- Siesta desconectada.
- Una coalición mínima, pero no basta con sumar respuestas favorables: deben existir compromisos cumplidos de varias comunidades.
- Resolver conflictos de La Estrella, máquinas y Ciudad Enferma sin exigir que todas las resoluciones sean no violentas.
- Al menos una pérdida o coste irreversible asumido por el grupo (recursos críticos, refugio, seguridad, relación rota o personaje ausente), determinado por decisiones ya existentes.
- La escena debe reconocer quién no regresó, quién desconfía y qué amenaza sigue afuera.

Evitar: convertir dos “resoluciones pacíficas” y dos misiones opcionales en una receta automática.

### 2. El Mesero Solitario
**Dejar de ser un simple resultado residual.**

Puede surgir de:
- desconectar Siesta y rechazar compromisos colectivos;
- salvar una comunidad sacrificando deliberadamente otra;
- perder aliados por decisiones concretas;
- conseguir una victoria militar que deje a Siete sin legitimidad ni red de apoyo.

El epílogo debe distinguir abandono voluntario, ruptura de confianza y supervivencia en aislamiento.

### 3. El Archivo del Eco
**La verdad debe tener consecuencias.**

- La publicación requiere preparar copias, elegir destinatarios y decidir qué pruebas exponer.
- Publicar puede provocar represalias, purgas, saqueos o fracturas internas; ocultar nombres puede proteger inocentes, pero debilitar la acusación.
- El final debe registrar qué comunidades creen la evidencia y cuáles la rechazan.
- Reunir documentos por sí solo no debe garantizar una publicación segura.

### 4. El Mesero de Hierro
**El control compartido no debe desbloquear automáticamente la tiranía.**

- Requiere una decisión posterior explícita de imponer obediencia, además de una crisis que Siete use como justificación.
- Debe existir resistencia, sabotaje o desobediencia dentro del sistema.
- El epílogo debe mostrar el precio: orden aparente, vigilancia, castigos y autonomía suprimida.
- La opción debe ser reconocible como autoritaria antes de confirmarla.

### 5. Siesta Voluntaria
**No estará disponible sin contexto emocional y consecuencias.**

- La decisión requiere haber comprendido qué significa apagar a Siete y qué deja sin resolver.
- Debe considerar vínculos reales, no solo el número de aliados.
- El jugador debe conocer el coste operativo de su ausencia y quién podrá continuar.
- No debe ser un “final bueno” automático ni una salida sin consecuencias.

### 6. La Mesa Larga
**Final excepcional de cooperación bajo tensión, no premio por acumular posturas pacíficas.**

- Implementar primero una ruta real del Sacerdote del Eclipse, sin dar por hecho que la reconciliación es posible.
- Mantener las condiciones tácticas de lanchas y puente como hechos independientes.
- Cada facción debe aceptar garantías verificables y entregar algo concreto.
- La mesa puede formarse, pero no implica paz definitiva: debe haber heridas, desacuerdos y riesgo de ruptura.
- No usar el total de aliados como sustituto de confianza política.

### 7. Un Amanecer sin Fiebre
**La medicina debe ser una decisión de supervivencia con capacidad limitada.**

- Resolver jugablemente el destino del antídoto: red médica o intento de Teo por salvar al Carnicero.
- El intento de Teo no garantiza curación; debe implicar riesgo, tiempo, recursos y resultado incierto.
- La ruta hospitalaria debe exigir una operación de abastecimiento/protección y consecuencias para quienes quedan atrás.
- La condición de Lía debe tener continuidad narrativa; acompañarla no puede ser solo una bandera.
- El final no debe prometer curación global: representa una posibilidad concreta, no una solución milagrosa.

### 8. La Señal se Apaga
**Convertir la documentación en preparación para una operación.**

- Las pruebas permiten localizar el origen/ruta, pero no desactivarlo por sí solas.
- Diseñar una incursión con acceso, defensa, recursos, peligro y una decisión final irreversible.
- Las decisiones sobre el transmisor deben afectar a las unidades y a las comunidades conectadas.
- No atribuir el origen de la Fiebre Gris ni de la señal a Richars: el canon actual lo descarta.

## 4. Cambios sistémicos necesarios antes de tocar los finales

1. Sustituir el contador único de aliados por estados individuales: confianza, compromiso, deuda, ruptura y presencia final, solo donde la narrativa lo justifique.
2. Diferenciar acompañar, negociar y rechazar por personaje. Cada negociación debe tener condiciones propias; no sumar automáticamente como aliado.
3. Revisar las tres resoluciones del Nido: destruir, desincronizar y sellar deben tener resultados y costes persistentes distintos. No presentar desincronizar como solución limpia.
4. Completar la resolución de la Secta y el destino del Carnicero antes de recalcular los finales que dependen de ellos.
5. Añadir consecuencias persistentes de combate solo tras auditar el sistema de integridad, reparación, retirada y guardado. No introducir muerte arbitraria ni corrupción de partidas.
6. Reescribir epílogos para que reflejen pérdidas, heridas, fracturas y amenazas pendientes.

## 5. Hallazgos técnicos confirmados en el HTML

- `finaleMetrics()` suma `support` y `negotiate` como aliados.
- `peaceful` cuenta Capataz, Nido desincronizado y Secta reconciliada como tres valores intercambiables.
- Restaurante exige 4 aliados, 2 resoluciones pacíficas y 2 misiones personales.
- La Mesa Larga exige 6 aliados y que Noa, Dante, Kai y Eva no hayan sido rechazados, además de condiciones tácticas y de facción.
- Siesta Voluntaria está marcada como disponible incondicionalmente.
- Mesero de Hierro depende únicamente de `siestaDecision === 'shared'`.
- El combate de Capataz, Funes, Richars y el Coro aplica `Math.max(1, player.hp - incoming)` en los fragmentos revisados: Siete no puede caer a 0 en esos encuentros.
- Richars no se rinde ni se redime, coherente con el plan de producción vigente.

## 6. Fuera de alcance de esta primera etapa

- No se cambian todavía las orientaciones ni relaciones de los personajes. Eso corresponde a la siguiente etapa, con fichas individuales basadas en el guion maestro.
- No se reescribe el origen de la Fiebre Gris, la señal, el Vuelo 9 ni el destino de Don Aurelio.
- No se altera `mesero30save` ni `saveVersion:49` en esta fase de diseño.
- No se implementa aún ningún cambio en `index.html`.

## 7. Pendientes de canon que requieren el documento maestro

Antes de cerrar el diseño definitivo se debe cotejar:
- texto original y motivaciones completas del Capataz, el Nido, el Sacerdote del Eclipse y el General;
- destino y papel narrativo de Mara, Tomás, Ibarra, Elba y los ocho contactos;
- condiciones originales de los ocho desenlaces, si difieren de la implementación 3.26;
- hechos concretos que el guion establece sobre las relaciones afectivas y familiares.

**Criterio de aprobación:** ningún final se considerará equilibrado hasta que sus requisitos sean alcanzables desde una partida normal, sus costes sean legibles antes de elegir y sus epílogos reconozcan las consecuencias reales de la ruta tomada.


## 8. Cotejo con el Guion Maestro — Fase 4

**Fuente de continuidad:** `Guion_Maestro_El_Mesero_del_Fin_del_Mundo_Fase4.md`, revisión de continuidad aportada por el usuario. Esta sección separa hechos establecidos de propuestas y conflictos pendientes.

### Hechos canónicos que deben conservarse

- Siete es la unidad S-07, nombrada por Don Aurelio. Estrella lo consideró familia, retiró manualmente su batería para protegerlo del Protocolo Siesta y lo escondió. Don Aurelio salió a pedir clemencia por los robots y nunca regresó.
- La señal externa manipuló órdenes de robots; la instalación militar vinculada al Vuelo 9 conserva pruebas de origen y transmisión. No confundir esta señal con el origen de la Fiebre Gris.
- La Fiebre Gris llegó en una cápsula transportada por el Vuelo 9 y afecta a humanos. El Hospital Abandonado y el Aeródromo permiten reconstruir la cadena de negligencia.
- El reflector oxidado sostuvo el rito de la Secta del Sol y la Luna. El Sacerdote convirtió el miedo en doctrina de odio, pero su historia incluye dolor y culpa.
- El ejército ocultó información del Vuelo 9 y sostuvo el orden mediante fuerza. El General no originó por sí solo todos los males: eligió obedecer y encubrir.
- El Carnicero fue cocinero de hospital; su violencia y su canción están ligadas a pérdida y deterioro. Teo cantaba con él en la cocina: el vínculo es significativo, pero el documento no lo define como romántico.
- La confesión de Noa se refiere a que dejó marchar a su hijo con su padre. La de Dante, al reflector y al rito del Sol. No convertir estos hechos en subtramas románticas.
- Las misiones de los ocho contactos deben seguir la secuencia encuentro, confianza, decisión (apoyar/rechazar/negociar) y consecuencia persistente.

### Rutas y consecuencias que el diseño debe respetar

- Capataz: puede ser derrotado o escuchado si se ganó la confianza del Desertor. Si es escuchado, los Rebeldes pueden dejar de atacar viajeros neutrales y facilitar rutas; si cae por la fuerza, el territorio queda más abierto pero hostil y desconfiado.
- Carnicero: la alternativa de reconocimiento depende de condiciones narrativas; el antídoto es un recurso disputado, no una cura garantizada.
- Secta: refugio, comida y sentido son parte de su función comunitaria. Exponer el engaño puede permitir la rendición del Sacerdote si existen confianza y prueba del reflector. Humillar o masacrar dispersa seguidores y mantiene hostilidad.
- Ejército: la Mecánica y el Piloto revelan logística, lanchas, evacuaciones y Vuelo 9. La llave inglesa permite sabotear las lanchas si se ayudó a la Mecánica. La rendición del General requiere pruebas y vínculos suficientes según el Guion Maestro.
- La Señal se Apaga debe incluir una operación física sobre el transmisor, no solo una decisión documental en consola.
- Un Amanecer sin Fiebre debe distinguir el destino del antídoto, la continuidad de Lía y la capacidad real de una red médica; no representa una cura global.
- La Estrella es centro emocional y mecánico persistente: compañeros, habitaciones, conversaciones, tablero de pistas, taller y diario deben reflejar hechos concretos, no solo contadores.

### Conflictos entre documentos que no se resolverán por suposición

1. **General / Richars:** el Guion Maestro permite que el General se rinda si se reúnen pruebas y vínculos; el plan técnico anterior caracteriza a Richars Octavio como irreconciliable, sin rendición ni redención. Antes de implementar hay que confirmar si Richars es el General y cuál de las dos versiones prevalece.
2. **Sacerdote / La Mesa Larga:** el Guion Maestro contempla la rendición del Sacerdote con confianza y prueba del reflector; la implementación 3.26 carece de una bandera funcional `cultResolution === 'reconciled'`. La ruta debe construirse explícitamente, sin concederla por coleccionables ni por un contador genérico.
3. **Antídoto / Carnicero:** el Guion Maestro plantea una elección de recursos y una resolución alternativa condicionada; no establece que el Carnicero pueda curarse con certeza. La escena debe preservar esa incertidumbre.
4. **Identidad afectiva del elenco:** el documento fija hechos familiares y vínculos emocionales, pero no define orientaciones sexuales o románticas. Las fichas posteriores deben marcar como “sin definir en canon” lo que no esté respaldado y proponer opciones por separado, para aprobación.

### Condiciones de calidad añadidas

- Las decisiones principales necesitan banderas explícitas y estables; no inferirlas exclusivamente de `G.m`.
- La migración de partidas antiguas debe asignar valores por defecto sin borrar progreso.
- Los finales pueden compartir escenas, pero sus epílogos deben reflejar compañeros presentes/ausentes, estado de refugios, consecuencias de facción y decisiones verificables.
- No se exige completar todos los coleccionables para finales principales, salvo la ruta de archivo/completismo.
- La exploración semiabierta y las ubicaciones existentes se conservan: exterior físico, interiores conectados con retorno al punto exacto y La Estrella persistente.
