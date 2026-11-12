# EL MESERO DEL FIN DEL MUNDO

## Plano detallado de mundo --- coordenadas maestras 3.1

**Estado:** plano de producción propuesto.\
**Referencia:** Atlas de Organización del Mundo 3.1 + HTML 3.0 Beta
Capítulo I.\
**Revisión espacial:** se auditaron las posiciones del Capítulo I. Se
conservan sus coordenadas probadas; se corrige la lectura de la compuerta
del patio y se añade una red de caminos para conectar la progresión. Las
coordenadas nuevas siguen siendo propuestas para expansión.

------------------------------------------------------------------------

## 1. Sistema de coordenadas

-   Tamaño objetivo del mapa exterior: **420 × 300 unidades**.
-   Origen `(0,0)`: esquina noroeste del mapa lógico.
-   `X` aumenta hacia el este; `Y` aumenta hacia el sur.
-   Las coordenadas son unidades lógicas del mundo, no píxeles.
-   Proyección isométrica actual: `screenX = (X - Y) × 32`,
    `screenY = (X + Y) × 16`, antes de aplicar cámara.
-   Norte corresponde a valores Y menores; sur a valores Y mayores.
-   Las posiciones de edificios son centros aproximados; las huellas se
    expresan como ancho × fondo en unidades lógicas.
-   Las puertas se colocan en el borde de la huella, no en su centro.
-   Los caminos son corredores navegables; no deben convertirse en una
    tira de puntos decorativos.

**Importante:** las coordenadas nuevas deben considerarse una cuadrícula
de diseño. Antes de integrarlas en el HTML, se debe validar la escala
visual con el tamaño actual de los personajes, edificios, cámara y
colisiones.

## 2. Qué queda bloqueado y qué se puede mover

### Se conserva exactamente en esta etapa

  Elemento                                              X      Y Tratamiento
  ------------------------------- ----------------------- ------ -------------
  La Estrella / punto de inicio                       8.2   11.2 No mover
  Campanilla                                          5.7    5.7 No mover
  Fotografía                                         11.3    5.5 No mover
  Terminal                                           11.5    9.5 No mover
  Puerta de La Estrella                             19.35   10.2 No mover
  Acceso al Depósito                                 34.2   22.5 No mover
  Desertor                                           30.2   13.2 No mover
  Compuerta de fábrica                               36.2   17.5 No mover
  Superviviente                                      42.5   25.5 No mover
  Consolas I / II / III             49,19 / 57,30 / 69,20    --- No mover
  Capataz                                              87     33 No mover
  Acceso Línea de Montaje                            97.8     33 No mover
  Registro Siesta                                   108.5   30.2 No mover
  Registro de órdenes                               114.5   30.2 No mover
  Acceso Túnel                                      121.8   30.2 No mover
  Núcleo de comunicaciones                          145.5   30.2 No mover
  Torre de agua                                        53     22 No mover
  Autobús                                              69     38 No mover
  Antena                                               91     18 No mover
  Campamento vacío                                     82     67 No mover
  Puente derrumbado                                    42     73 No mover
  Cráter                                              108     78 No mover

Los interiores del Depósito y del Patio usan coordenadas de instancia
(`x≈158–198`). Se conservan como interiores instanciados y **no** se
interpretan como ubicaciones exteriores del mapa.

## 3. Auditoría espacial del Capítulo I

**Decisión: no desplazar los puntos narrativos ni los puntos de interacción.**
La progresión actual está bien escalonada: La Estrella queda al oeste; el
Desertor y la compuerta introducen el patio; el Superviviente y las tres
consolas ocupan el área de máquinas; la fábrica del Capataz queda al este;
Línea de Montaje y Túnel prolongan el recorrido hacia la futura Ciudad Enferma.

Los hitos secundarios también pueden conservarse: la torre de agua y el
autobús sirven como referencias del patio; la antena domina el borde norte
de la fábrica; el campamento, el puente derrumbado y el cráter quedan como
exploración lateral al sur. No se detecta una razón narrativa suficiente
para moverlos ahora.

**Ajustes de coherencia aplicados:**
- La posición `(36.2,17.5)` se denomina **Compuerta del patio industrial**;
  no es la puerta física de la sala del Capataz.
- Se incorpora un camino principal continuo desde Calle Oxidada, pasando
  por las consolas, hasta la entrada sur de la fábrica `(87,46)`.
- Se añaden ramales al Depósito `(34.2,22.5)`, Consola I `(49,19)`,
  Taller del Patio `(52.5,39.5)`, Consola III `(69,20)` y autobús `(69,38)`.
- Se mantiene la entrada sur de la fábrica como acceso a la arena; la
  salida lateral este conecta con Línea de Montaje y luego con el Túnel.
- Los interiores del Depósito y Patio continúan siendo instancias separadas;
  sus coordenadas interiores no son posiciones del mapa exterior.

La ampliación a 420 × 300 se reserva para la expansión posterior. El HTML
actual sigue usando 205 × 145; no se debe cambiar esa escala hasta integrar
el terreno ampliado y revisar cámara, límites y colisiones en conjunto.

## 4. Regiones maestras y límites de planificación

Los límites siguientes son rectángulos de planificación inicial. En la
implementación final, los límites visuales deben seguir el relieve, las
carreteras, ríos, muros y cambios de terreno; no dibujar bordes
rectangulares visibles.

  -----------------------------------------------------------------------
  Código            Región            Rectángulo lógico Núcleo
                                      (X1--X2, Y1--Y2)  
  ----------------- ----------------- ----------------- -----------------
  R1                La Estrella y     X 0--75, Y 0--125 X 10--55, Y
                    cinturón exterior                   10--75

  R2                Territorio de las X 24--170, Y      X 45--150, Y
                    máquinas          0--125            15--95

  R3                Ciudad Enferma    X 170--315, Y     X 195--295, Y
                                      0--150            25--125

  R4                Territorio        X 35--225, Y      X 65--200, Y
                    militar           145--295          165--270

  R5                Territorio del    X 235--415, Y     X 265--395, Y
                    culto             135--295          155--275
  -----------------------------------------------------------------------

Los rectángulos R1 y R2 se solapan deliberadamente: el cinturón exterior
es una zona de transición alrededor del núcleo de máquinas. Las regiones
R3, R4 y R5 se conectan mediante corredores, no por superposición
indiscriminada.

## 5. Plano de referencia (vista lógica, no a escala)

``` text
NORTE / Y=0
┌──────────────────────────┬──────────────────────────────┐
│ R1 LA ESTRELLA           │ R3 CIUDAD ENFERMA            │
│ Restaurante              │ Barrio                       │
│ Calle Oxidada            │ Parque                       │
│ Depósito / Patio         │ Centro Comercial             │
│ Fábrica / Montaje        │ Metro / Cementerio            │
│ Túnel ──────────────────►│ Hospital / Nido               │
├──────────────────────┐  └───────────────────┬───────────┤
│ R4 TERRITORIO MILITAR │                      │ R5 CULTO  │
│ Trincheras            │ Corredor de conexión │ Bosque    │
│ Puerto / Muelle       │ y paso de montaña   │ Aldea     │
│ Hangar / Aeródromo    │                      │ Mercado   │
│ Fortaleza            │                      │ Templo    │
└──────────────────────┘                      └───────────┘
SUR / Y=300
OESTE / X=0                                     ESTE / X=420
```

## 6. Coordenadas propuestas de nuevos lugares

Las huellas son reservas iniciales de espacio, no geometría final.
`Acceso` es el punto sugerido para la puerta o entrada principal.

### R1 --- La Estrella y cinturón exterior

Los puntos actuales se mantienen. Se añaden espacios de conexión y
exploración:

  --------------------------------------------------------------------------
  Lugar nuevo        Centro X,Y           Huella Acceso /     Función
                                                 conexión     
  ------------ ---------------- ---------------- ------------ --------------
  Cruce del              54, 52            12×10 54,52        Distribuye
  cinturón                                                    ruta norte/sur

  Patio de               72, 42            20×16 63,42        Chatarra y
  vehículos                                                   vehículos
                                                              desmontados

  Estación de            25, 61            12×10 31,61        Recurso y
  bombeo                                                      pista
                                                              ambiental

  Puesto de              18, 88              8×8 22,84        Vista hacia la
  vigía                                                       zona militar
  derruido                                                    

  Paso del               52, 96            18×12 52,90        Futuro
  puente viejo                                                corredor al
                                                              sur;
                                                              inicialmente
                                                              bloqueado

  Refugio de             75, 82            12×10 69,82        Encuentro
  caminantes                                                  opcional y
                                                              descanso
  --------------------------------------------------------------------------

### R2 --- Territorio de las máquinas

Se conserva el contenido existente hasta el núcleo de comunicaciones. Se
añaden ramales alrededor de la zona ya construida:

  --------------------------------------------------------------------------
  Lugar nuevo          Centro X,Y           Huella Acceso /     Función
                                                   conexión     
  -------------- ---------------- ---------------- ------------ ------------
  Patio de                 58, 53            24×18 58,44        Ramal sur
  contenedores                                                  del Patio

  Taller de                82, 83            18×14 82,76        Reparación y
  desguace                                                      piezas

  Almacén                 112, 62            20×16 112,54       Atajo/loot
  bloqueado                                                     tras
                                                                restaurar
                                                                energía

  Subestación             139, 59            14×12 132,59       Alimenta un
                                                                acceso
                                                                lateral

  Salida                  164, 31            12×12 170,31       Conecta con
  exterior del                                                  la Ciudad
  túnel                                                         Enferma

  Camino de              corredor    6--8 de ancho X 150--178,  Ruta entre
  servicio                                         Y 31--48     túnel y
  oriental                                                      ciudad
  --------------------------------------------------------------------------

### R3 --- Ciudad Enferma

La entrada desde el túnel queda al oeste. La ciudad se despliega hacia
el este y el sur, con un bulevar principal y ramales.

  ----------------------------------------------------------------------------
  Lugar               Centro X,Y           Huella Acceso /     Función
                                                  conexión     
  ------------- ---------------- ---------------- ------------ ---------------
  Puerta de la           184, 34            12×10 178,34       Entrada desde
  ciudad                                                       el túnel

  Barrio                 211, 38            34×26 198,42       Primera zona
  residencial                                                  urbana

  Plaza del              232, 58            18×16 232,58       Cruce y
  tranvía                                                      orientación

  Parque                 205, 91            30×24 205,79       Zona abierta y
  municipal                                                    rutas
                                                               alternativas

  Centro                 258, 43            28×22 245,50       Refugio y
  Comercial                                                    recursos

  Estación de            244, 76            16×12 244,76       Acceso
  Metro norte                                                  subterráneo

  Cementerio             278, 88            24×18 267,88       Memoria y
                                                               pistas de la
                                                               epidemia

  Hospital              279, 119            30×24 279,107      Investigación y
                                                               decisiones

  Nido                   300, 68            24×22 288,68       Núcleo de
                                                               amenaza

  Salida sur            218, 139            12×10 218,145      Corredor hacia
  urbana                                                       zona militar

  Paso del              309, 133            12×10 309,139      Conexión futura
  bosque                                                       al culto
  ----------------------------------------------------------------------------

**Estructura urbana:** bulevar oeste--este desde la Puerta hasta la
Plaza; ramal norte al Centro Comercial; ramal sur al Parque, Cementerio
y Hospital. El Nido se sitúa en un sector aislado del tejido urbano, no
en medio de la ruta principal.

### R4 --- Territorio militar

El acceso norte se aproxima desde la salida sur de la Ciudad y desde el
corredor del puente. El Puerto/Muelle se coloca al oeste/suroeste para
que tenga relación clara con el agua.

  ---------------------------------------------------------------------------
  Lugar              Centro X,Y           Huella Acceso /     Función
                                                 conexión     
  ------------ ---------------- ---------------- ------------ ---------------
  Control del          112, 160            18×12 112,153      Puesto de
  puente                                                      control

  Trincheras            91, 185            34×18 91,174       Primera línea
  norte                                                       

  Cuartel              139, 188            24×18 139,179      NPC y logística
  avanzado                                                    

  Puerto                65, 225            34×24 82,225       Zona de carga

  Muelle                44, 247            28×12 55,247       Embarcaciones y
                                                              comercio

  Hangar               145, 230            32×24 145,218      Vehículos y
                                                              archivos

  Aeródromo            180, 250            38×26 180,236      Pista y espacio
                                                              abierto

  Fortaleza            133, 276            34×20 133,265      Centro de mando

  Puesto de            192, 192            12×12 186,192      Comunicación y
  radio                                                       vigilancia
  ---------------------------------------------------------------------------

El agua debe ocupar una franja continua al oeste/suroeste del Puerto y
del Muelle. El Aeródromo requiere una pista despejada; no llenar ese
espacio con edificios pequeños.

### R5 --- Territorio del culto

La entrada desde la ciudad llega por el paso del bosque. La progresión
gana altura y densidad arquitectónica hacia el este/sureste.

  -------------------------------------------------------------------------
  Lugar              Centro X,Y           Huella Acceso /     Función
                                                 conexión     
  ------------ ---------------- ---------------- ------------ -------------
  Umbral del           316, 145            14×12 309,139      Entrada
  bosque                                                      regional

  Sendero de           333, 164    corredor 5--7 322,150      Ruta de
  los símbolos                                                bosque

  Aldea                350, 183            30×24 337,183      Comunidad y
                                                              vida diaria

  Mercado              325, 211            24×18 325,201      Intercambio y
                                                              rumores

  Catacumbas           365, 220            22×18 354,220      Red
                                                              subterránea

  Escalinata           380, 245       corredor 8 380,232      Ascenso
                                                              ceremonial

  Templo               352, 259            30×22 352,247      Centro
                                                              público

  Santuario            395, 276            22×18 384,276      Enclave final
  -------------------------------------------------------------------------

El Santuario debe quedar en una elevación o terraza. La escalinata tiene
que ser visible desde el acceso al Templo y funcionar como hito de
orientación.

## 6. Corredores principales y puntos de conexión

  ------------------------------------------------------------------------
  Ruta             Trazado lógico                   Ancho Estado inicial
                   aproximado                             
  ---------------- ---------------- --------------------- ----------------
  La Estrella →    (19,10) →                         5--7 Abierta por
  Calle → Depósito (34,22) →                              progresión
                   (54,52)                                

  Depósito → Patio (34,22) →                         6--8 Accesos del
  → Fábrica        (52,40) →                              capítulo
                   (76,33)                                

  Fábrica →        (98,33) →                         7--9 Según progreso
  Montaje → Túnel  (110,31) →                             del Capítulo I
                   (122,31) →                             
                   (151,31)                               

  Túnel → Ciudad   (151,31) →                       8--10 Cerrada hasta
                   (170,31) →                             expansión
                   (184,34)                               

  Ciudad principal (184,34) →                       7--10 Abierta al
                   (232,58) →                             entrar
                   (258,43)                               

  Ciudad sur       (232,58) →                        6--8 Alternativa
                   (205,91) →                             
                   (218,139)                              

  Ciudad → Militar (218,139) →                      8--10 Puente
                   (112,160)                              controlado

  Ciudad → Culto   (309,139) →                       6--8 Sendero
                   (316,145) →                            inicialmente
                   (350,183)                              bloqueado

  Militar → Culto  (192,192) →                       5--7 Paso tardío
                   (260,205) →                            
                   (316,190)                              
  ------------------------------------------------------------------------

Los trazados son ejes de camino. Para dibujar el camino real, construir
un corredor alrededor de cada eje con el ancho indicado y suavizar las
curvas; no unir puntos con líneas rectas que atraviesen edificios.

## 7. Orden de dibujo y colisiones

-   El suelo y los caminos se dibujan primero.
-   Las huellas de edificios y obstáculos se definen en coordenadas
    lógicas.
-   Las colisiones se separan del arte: una pared puede ser alta y tener
    una huella de colisión más estrecha.
-   Puertas y accesos deben tener un punto de activación delante de la
    puerta, no dentro de la pared.
-   Los objetos interactivos conservan identificadores estables para no
    romper misiones y guardados.
-   El orden de profundidad se calcula por la coordenada lógica del
    pie/base del objeto, no por el centro del sprite.
-   Los hitos altos se dibujan con anclaje al suelo; la altura visual no
    altera su coordenada de navegación.

## 8. Cambios técnicos necesarios antes de poblar las regiones

1.  Cambiar `world.w/h` a 420/300 solo después de ampliar el renderizado
    y validar cámara y límites.
2.  Reemplazar la función `zoneAt(x,y)` actual ---basada principalmente
    en X--- por polígonos o zonas con límites X/Y.
3.  Separar `regions`, `paths`, `buildings`, `props`, `interactables`,
    `portals` y `collisionShapes` en datos distintos.
4.  Definir cada portal con `id`, `x`, `y`, `radius`, `destination`,
    `returnPoint` y `unlockCondition`.
5.  Mantener los interiores actuales como mapas-instancia separados del
    exterior.
6.  Guardar el estado de puertas, atajos, región y coordenada de
    retorno.
7.  Actualizar el render de terreno: la lógica actual colorea
    principalmente por X y no será suficiente para cinco biomas.
8.  Evitar dibujar el mapa entero cada frame; conservar el culling por
    cámara y extenderlo al nuevo tamaño.
9.  Probar primero con polígonos de color y marcadores numerados, sin
    arte final.
10. No mover ni renombrar los IDs actuales sin migración de guardado.

## 9. Secuencia de implementación

**Paso A --- Validación del plano:** revisar que las posiciones
propuestas y los corredores tengan sentido.\
**Paso B --- Esqueleto 420×300:** ampliar límites, cámara, terreno,
biomas y caminos.\
**Paso C --- Conexión de túnel-ciudad:** primera expansión jugable, con
puerta y retorno persistente.\
**Paso D --- Ciudad gris:** colocar los siete núcleos urbanos y probar
navegación antes de crear misiones.\
**Paso E --- Militar y culto:** incorporar sus accesos y rutas,
manteniéndolos inicialmente bloqueados.\
**Paso F --- Poblar contenido:** NPC, facciones, misiones, recursos,
documentos y consecuencias.

## 10. Decisiones pendientes de aprobación

-   ¿Se aprueba 420×300 como dimensión de trabajo?
-   ¿Se aprueba la ubicación relativa de las regiones y los nuevos
    centros de interés?
-   ¿La costa del Puerto/Muelle será borde marítimo o ribera de un gran
    río?
-   ¿La primera salida del Túnel a la Ciudad se abre al completar el
    Capítulo I o requiere una misión posterior?

**Recomendación de producción:** aprobar o corregir este plano antes de
modificar las coordenadas del HTML. La distribución actual del Capítulo
I queda protegida; las nuevas coordenadas se incorporan por etapas.


---

## Addendum de implementación — HTML 3.1

- El mapa exterior ahora utiliza la reserva de diseño de **420 × 300** unidades.
- Las coordenadas conservadas del Capítulo I no se desplazaron.
- Los 39 lugares marcados como `Propuesto` en el CSV se añadieron como hitos visuales de referencia.
- Se trazaron corredores de conexión entre R1, R2, R3, R4 y R5, respetando el trazado lógico del plano.
- Se incorporó una compuerta física en la salida oriental del Túnel (posición de implementación: X 149.7, Y 31), que no sustituye al punto de la Puerta de la Ciudad del CSV. Se abre al recuperar la traza del Núcleo de comunicaciones.
- La costa suroeste se representa como agua no transitable; el muelle permanece al este de la orilla.
- Las coordenadas propuestas siguen siendo referencias de diseño y requieren una pasada de ajuste visual con prueba manual.

**No incluido todavía:** colisiones individuales para cada edificio nuevo, contenido de misiones, NPC y transiciones interiores de las regiones 3, 4 y 5.


---

## Addendum 3.2 — coordenadas implementadas de Ciudad Enferma

### Exterior R3
| Elemento | Coordenada | Observación |
|---|---:|---|
| Mara | (218,47) | NPC del Barrio; misión de suministros |
| Tomás | (238,88) | NPC del Parque; pista sobre evacuados |
| Doctora Ibarra | (279,103) | NPC en el acceso norte del Hospital |
| Infectado errante | (286,82) | Encuentro al oeste del Nido, fuera de su colisión |
| Entrada Centro Comercial | (252,44) | Umbral sur del edificio |
| Entrada Metro norte | (245.3,77.1) | Separada del hito del Metro (244,76) para que ambas interacciones no se solapen |
| Entrada norte Hospital | (279,107) | Acceso al interior |
| Salida de emergencia Hospital | (279,122) | Acceso sur hacia corredor militar |
| Acceso al Nido | (288,68) | Umbral oeste; requiere archivo y muestra |

### Huellas urbanas principales
- Residencias: A (196,26), 8×7; B (207,25), 7×8; C (218,29), 8×7; D (195,49), 9×7.
- Local: (228,35), 7×8.
- Centro Comercial: (249,31), 17×13; acceso al sur.
- Hospital: (269,107), 19×15; accesos norte y sur.
- Nido: (290,57), 19×21; acceso al oeste.

### Instancias interiores (coordenadas técnicas, no geografía exterior)
- Centro Comercial: recinto X=329–361, Y=9–41; entrada interior en (332,25); salida en (345,39).
- Metro: X=364–397, Y=9–42; entrada interior en (367,25); salida norte en (380,39); panel (374,24); atajo sur desde (390,22) a exterior (218,139).
- Hospital: X=329–361, Y=49–86; entrada interior en (332,65); archivo (337,62); muestra (350,72); salida (345,84).
- Nido: X=364–397, Y=49–86; entrada interior en (367,65); núcleo (379,63); registro (390,76); retirada (380,84).

### Correcciones de coherencia heredada
Los interiores del Depósito y Patio mantienen sus coordenadas de instancia, pero sus muros, suelo y colisiones solo se activan dentro del interior correspondiente. Así dejan de ocupar visual y físicamente el corredor exterior que pasa por X≈158–198. El banco de reparación se reubica a (180,103), y la estantería oriental del Depósito a X=187 para despejar la grúa.


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


## Addendum 3.7 — coordenadas del interior de Catacumbas

| Elemento | Coordenada | Función |
|---|---:|---|
| Acceso exterior | (354, 220) | Entrada a Catacumbas desde el corredor sur |
| Sala interior | (329–361, 91–125) | Instancia explorable independiente |
| Entrada/salida interior | (345, 122.2) | Umbral sur y retorno al exterior |
| Inscripción erosionada | (338.5, 112) | Inspección ambiental |
| Canal de filtración | (351.5, 108) | Inspección ambiental |
| Nicho de piedra | (345, 96.5) | Inspección ambiental |
| Caja de herramientas | (352, 116.5) | Recurso menor, una sola vez |

El perímetro interior tiene una única abertura al sur. El eje central entre la entrada y la cámara norte queda libre de obstáculos. Estas coordenadas pertenecen a la instancia de interior y no modifican la geografía exterior R5.


## Addendum 3.8 — coordenadas del interior del Templo

| Elemento | Coordenada | Función |
|---|---:|---|
| Acceso exterior del Templo | (352,247) | Puerta norte en la huella exterior existente |
| Huella exterior del Templo | (337–367, 248–270) | Se conserva sin desplazar |
| Sala interior | (329–361, 132–166) | Instancia explorable independiente |
| Entrada interior | (345,161.5) | Llegada desde el acceso exterior |
| Salida interior | (345,164.2) | Umbral sur y retorno a la posición guardada |
| Marcas del pavimento | (345,150) | Inspección ambiental |
| Grieta de filtración | (345,158) | Inspección ambiental |
| Nicho vacío | (345,141.5) | Inspección ambiental |

El perímetro interior tiene una única abertura al sur. Las columnas, los bancos laterales y la plataforma se mantienen fuera del corredor central. La geometría interior reutiliza coordenadas de instancia y no modifica la geografía exterior de R5.


## Addendum 3.9 — actualización del mapa exterior

### Hitos ambientales integrados

| Región | Hito | Coordenada | Estado 3.9 |
|---|---|---:|---|
| R1 | Estación de bombeo | (25,61) | Geometría visual ambiental |
| R1 | Puesto de vigía | (18,88) | Geometría visual ambiental |
| R1 | Puente viejo | (52,96) | Paso derrumbado y corredor de aproximación |
| R1 | Refugio de caminantes | (75,82) | Geometría visual ambiental |
| R1 | Patio de vehículos | (72,42) | Geometría visual ambiental |
| R2 | Patio de contenedores | (58,53) | Geometría visual ambiental |
| R2 | Taller de desguace | (82,83) | Geometría visual ambiental |
| R2 | Almacén bloqueado | (112,62) | Geometría visual ambiental, sin desbloqueo |
| R2 | Subestación | (139,59) | Geometría visual ambiental, sin sistema eléctrico nuevo |

Se incorpora una ruta de aproximación desde el Puente Viejo hacia el borde sur, sin abrir el territorio militar. Los nuevos hitos no son todavía interactivos ni tienen colisión propia; se priorizó completar la lectura espacial sin introducir bloqueos involuntarios.

### Estado de los pendientes

- Clasificación territorial X/Y: implementada en 3.9.
- Hitos visuales R1/R2: implementados en 3.9.
- Caminos principales entre R1/R2/R3/R5 y corredor de aproximación sur: presentes.
- Colisiones dedicadas de los nuevos hitos: pendientes.
- Atajos con condiciones narrativas: pendientes.
- R4 militar: permanece reservado; solo se conserva la geografía de planificación.
- Interior del Santuario: pendiente de etapa posterior.


## Addendum 3.10 — geometría de colisión y caminos secundarios

| Hito | Acceso del plano | Colisión / regla 3.10 |
|---|---:|---|
| Estación de bombeo | (31,61) | Estructura bloqueante; entrada este despejada |
| Puesto de vigía | (22,84) | Colisión circular del puesto; acceso este despejado |
| Puente viejo | (52,90) | Restos del paso bloquean el cruce; aproximación norte libre |
| Refugio de caminantes | (69,82) | Tienda bloqueante; acceso oeste despejado |
| Patio de vehículos | (63,42) | Vehículos bloqueantes; ruta por el sur |
| Patio de contenedores | (58,44) | Cuatro pilas bloqueantes; acceso norte libre |
| Taller de desguace | (82,76) | Nave bloqueante; acceso norte libre |
| Almacén bloqueado | (112,54) | Nave sólida; pasillo central tras activar las tres consolas |
| Subestación | (132,59) | Edificio bloqueante; acceso oeste libre |

Los trazados secundarios se verificaron por muestreo de colisión desde sus nodos de acceso. El corredor R2–R3 por el Túnel y las conexiones R3–R5 hacia Bosque, Mercado y Catacumbas también se revisaron con sus puertas en estado habilitado.

**Frontera R4:** se conserva la región y su representación cartográfica, pero el ingreso desde fuera queda bloqueado. Las partidas que ya estuvieran dentro no se reubican: pueden recorrer el área y salir. El Puente Viejo no se convierte en acceso al territorio militar.

**Atajo del Almacén:** puerta en (112,54), habilitada únicamente después de restaurar las tres consolas industriales. La bandera `state.flags.warehouseShortcut` persiste en el guardado. No se incorpora loot ni contenido narrativo no definido.


## Addendum 3.12 — interior del Santuario

| Elemento | Coordenada / huella | Estado |
|---|---|---|
| Acceso exterior occidental | (384,276) | Puerta interactiva |
| Edificio exterior | Centro aprox. (395,276), 18×18 | Huella conservada; umbral occidental libre |
| Sala interior | (365–397, 190–224) | Instancia explorable independiente |
| Entrada/salida interior | (367,207) | Abertura occidental; retorno al punto exterior de ingreso |
| Plataforma vacía | (382,204), 4×3 | Elemento arquitectónico bloqueante |
| Columnas | (370,194), (393,194), (370,219), (393,219) | Perímetro interior |
| Inspecciones | (374,207), (389,198), (389,216) | Umbral, repisa y filtración de luz |

La sala mantiene un corredor occidental despejado. La geometría interior no abre el territorio R4 ni modifica las conexiones regionales existentes.


## Addendum 3.12 — estado de interacción de hitos

| Región | Hito | Coordenada | Interacción | Condición / límite |
|---|---|---:|---|---|
| R1 | Cruce del cinturón | (54,52) | Inspección de distribución de rutas | Sin cambio de trazado |
| R1 | Patio de vehículos | (72,42) | Recuperar 2 piezas una vez | Huellas y acceso conservados |
| R1 | Estación de bombeo | (25,61) | Inspección de tablero y válvulas | No activa sistemas |
| R1 | Puesto de vigía derruido | (18,88) | Observación del corredor sur | No habilita R4 |
| R1 | Paso del puente viejo | (52,96) | Inspección del derrumbe | Cruce cerrado |
| R1 | Refugio de caminantes | (75,82) | Inspección ambiental | Sin NPC ni misión |
| R2 | Patio de contenedores | (58,53) | Inspección de ramal de carga | Pasillos existentes conservados |
| R2 | Taller de desguace | (82,83) | 2 piezas una vez y reparación | Reparar 30 puntos por 2 piezas |
| R2 | Almacén bloqueado | (112,62) | Consultar estado del atajo | Depende de las tres consolas |
| R2 | Subestación | (139,59) | Consultar estado energético | No sustituye las consolas |

Las coordenadas, huellas y accesos maestros no se modifican.


## Addendum 3.13 — puntos de inspección R3 (coordenadas conservadas)

| Hito | Coordenada | Interacción |
|---|---:|---|
| Puerta de la ciudad | (184, 34) | Inspección del umbral urbano |
| Barrio residencial | (211, 38) | Inspección de viviendas y evacuación visible |
| Plaza del tranvía | (232, 58) | Inspección del distribuidor vial |
| Parque municipal | (205, 91) | Inspección del corredor abierto |
| Cementerio | (278, 88) | Inspección de caminos y memoria |
| Salida sur urbana | (218, 139) | Inspección del límite cerrado |
| Paso del bosque | (309, 133) | Inspección de transición geográfica |

No se modifican posiciones, colisiones, caminos, huellas ni accesos existentes.


## Addendum 3.15 — referencias de reconocimiento R3

| Hito | Coordenada | Acceso / condición |
|---|---:|---|
| Señal urbana caída | (221,128) | Inspección tras resolver el Nido |
| Canal de desagüe | (233,131) | Inspección tras resolver el Nido |
| Mojón de evacuación | (214,136) | Inspección tras resolver el Nido |

Los tres puntos se ubican sobre el corredor civil ya trazado. No crean caminos nuevos, colisiones de estructura ni entrada a R4.


## Addendum 3.15 — preparativos civiles de frontera

La salida sur urbana puede prepararse únicamente después de resolver el Nido y registrar los tres hitos civiles del corredor. La acción despeja escombros menores y deja señalización de orientación. No abre R4, no establece contacto, no añade soldados, mandos, instalaciones, órdenes ni información sobre la facción militar. El paso fronterizo permanece cerrado y el contenido militar sigue reservado para su tramo narrativo.


## Addendum 3.16 — coordenadas de recursos civiles opcionales R3

| Hito | Coordenada | Interacción | Persistencia |
|---|---:|---|---|
| Caja de mantenimiento del tranvía | (237,61) | Recuperar 1 pieza una sola vez | `state.city.civicCaches.cityCachePlaza` |
| Armario de servicio del parque | (214,100) | Recuperar 1 pieza una sola vez | `state.city.civicCaches.cityCachePark` |
| Caja de herramientas del cementerio | (285,96) | Recuperar 1 pieza una sola vez | `state.city.civicCaches.cityCacheCemetery` |

Los puntos se ubican fuera de las huellas de edificios y de los árboles existentes. No agregan colisiones ni desplazan coordenadas maestras. La interacción requiere que la compuerta de acceso a Ciudad Enferma esté habilitada. La recompensa total máxima es de tres piezas.

| Servicio | Coordenada | Condición | Efecto |
|---|---:|---|---|
| Banco de reparación civil | (225,53) | Inventario civil 3/3 y 2 piezas disponibles | Consume 2 piezas y restaura 30 puntos de integridad; reutilizable |


## Actualización 3.17 — coordenadas
No se agregan ni desplazan puntos. Mara (218,47), Tomás (238,88) e Ibarra (279,103) conservan sus coordenadas. Las tareas de seguimiento se activan al interactuar con esos NPC existentes después de resolver el Nido.


## Addendum 3.18 — auditoría de corredores R3/R5 (geometría conservada)

| Tramo | Eje / acceso | Resultado de revisión |
|---|---|---|
| R3 → Umbral | (278,88) → (292,95) → (309,133) → (309,139) | Aproximación despejada; el cruce regional está en el Umbral |
| Umbral → Aldea | (309,139) → (316,145) → (322,150) → (329,160) → (334,170) → (337,183) | Corredor despejado |
| Aldea → Mercado | (350,183) → (337,183) → (325,201) → (325,211) | Pasa entre los puestos; acceso conservado |
| Aldea → Catacumbas | (350,183) → (352,198) → (353,210) → (354,220) | Aproximación sur despejada |
| Catacumbas → Escalinata → Templo | (354,220) → (366,224) → (380,232) → (380,245) → (352,247) | Termina en el umbral norte; no atraviesa la huella del Templo |
| Escalinata → Santuario | (380,245) → (381,257) → (382,268) → (384,276) | Vereda occidental despejada |

Las etiquetas de subzona se ajustan para que (309,133)–(309,139) se lea como Paso del bosque/Umbral del bosque y (380,245) como Escalinata. Esta tabla documenta ejes de camino y accesos ya existentes; no autoriza desplazamientos de coordenadas.


## Addendum 3.19 — prueba de progresión y retornos (coordenadas conservadas)

| Acceso exterior | Aparición interior | Salida interior | Retorno exterior | Resultado de revisión |
|---|---:|---:|---:|---|
| Catacumbas (354,220) | (345,120.5) | (345,122.2) | Punto de entrada guardado | Corredor sur disponible; salida diferenciada de la aparición |
| Templo (352,247) | (345,161.5) | (345,164.2) | Punto de entrada guardado | Corredor central disponible; salida sur alcanzable |
| Santuario (384,276) | (369,207) | (367,207) | Punto de entrada guardado | Aparición separada 2 unidades del marcador de salida; acceso occidental despejado |

La coordenada exterior de retorno se captura al entrar y no se sustituye por un punto fijo. Se corrige además la clasificación de los interiores para que sus metadatos de guardado indiquen R2/R3/R5 según la región de origen, no según el rectángulo artificial de la instancia. No se mueven coordenadas del CSV maestro.


## Addendum 3.20 — puntos ambientales R5

| Hito | Coordenada | Interacción | Restricción |
|---|---:|---|---|
| Tronco caído | (316,168) | Inspección ambiental | Sin colisión; fuera del eje de acceso |
| Claro pedregoso | (326,163) | Inspección ambiental | Sin colisión; ramal corto desde el sendero |
| Muro derrumbado | (329,190) | Inspección ambiental | Sin colisión; no modifica huellas de Aldea |
| Fuente seca | (321,222) | Inspección ambiental | Sin colisión; no altera el corredor del Mercado |
| Patio de puestos | (342,218) | Inspección ambiental | Sin colisión; no modifica puestos existentes |
| Descanso de la escalinata | (372,239) | Inspección ambiental | Sin colisión; no cambia el acceso al Templo |

Los seis puntos son adiciones 3.20; no desplazan coordenadas 3.19. Los accesos Catacumbas (354,220), Templo (352,247) y Santuario (384,276), sus apariciones y retornos permanecen intactos. No se modifica el límite de R4.


## Addendum 3.21 — implementación física exterior de R4

| Sector | Centro | Huella | Acceso del plano | Estado 3.21 |
|---|---:|---:|---:|---|
| Control del puente | (112,160) | 18×12 | (112,153) | Puestos laterales y barrera visual; acceso regional cerrado |
| Trincheras norte | (91,185) | 34×18 | (91,174) | Parapetos y zanjas ambientales; corredor libre |
| Cuartel avanzado | (139,188) | 24×18 | (139,179) | Estructura exterior cerrada; acceso reservado |
| Puerto | (65,225) | 34×24 | (82,225) | Zona de carga, almacén y contenedores ambientales |
| Muelle | (44,247) | 28×12 | (55,247) | Pasarela visual sobre la costa existente; sin navegación |
| Hangar | (145,230) | 32×24 | (145,218) | Nave exterior cerrada; sin aeronaves ni interior |
| Aeródromo | (180,250) | 38×26 | (180,236) | Pista vacía y marcas de orientación |
| Fortaleza | (133,276) | 34×20 | (133,265) | Perímetro y edificio exterior cerrados |
| Puesto de radio | (192,192) | 12×12 | (186,192) | Mástil sin transmisión ni mensajes |

Las coordenadas, huellas y accesos se conservan sin desplazamientos. Los muros nuevos dejan libre la aproximación a los puntos de inspección. El límite físico de R4 en Y=145 y el bloqueo de entrada desde otras regiones siguen vigentes.


## Addendum 3.22 — correspondencia de ruta militar (sin cambios geométricos)

| Ruta del Guion Maestro Fase 4 | Hito cartográfico 3.21 | Centro |
|---|---|---:|
| Puerto Militar | Puerto | (65,225) |
| Campo de Trincheras | Trincheras norte | (91,185) |
| Hangar Oxidado | Hangar | (145,230) |
| Muelle de Carga | Muelle | (44,247) |
| Puente Blindado | Control del puente | (112,160) |
| Aeródromo | Aeródromo | (180,250) |
| Fortaleza del General | Fortaleza | (133,276) |

Esta tabla relaciona nombres de ruta del Guion Maestro con sectores ya existentes; no crea hitos, no desplaza coordenadas y no fija todavía la secuencia de puertas ni interiores. Cuartel avanzado (139,188) y Puesto de radio (192,192) permanecen como hitos auxiliares sin función narrativa especificada. La implementación de personajes, pruebas, sabotaje y decisiones queda pendiente de la auditoría de canon 3.22.
