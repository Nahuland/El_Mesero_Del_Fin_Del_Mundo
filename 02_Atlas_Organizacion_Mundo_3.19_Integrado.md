# El Mesero del Fin del Mundo

## Atlas de organización territorial --- propuesta 3.1

**Estado:** propuesta de diseño para revisión antes de modificar el
HTML.\
**Base conservada:** 3.0 Beta --- Estabilización 01.\
**Objetivo:** fijar la geografía, la distribución de puntos de interés,
las conexiones y la progresión espacial antes de construir la expansión.

------------------------------------------------------------------------

## 1. Decisión general

No reconstruir el Capítulo I ni desplazar sus puntos ya probados en esta
primera etapa. Se conserva como núcleo inicial:

-   La Estrella y su salida física.
-   Calle Oxidada.
-   Depósito de Chatarra y sus interiores.
-   Patio de Máquinas, fábrica del Capataz, Línea de Montaje y Túnel de
    Servicio.
-   Puente derrumbado, torre de agua, autobús, antena, campamento y
    cráter como hitos existentes.

La expansión se realiza principalmente hacia el este y el sur, ampliando
el terreno. Los interiores pueden seguir usando instancias visuales
separadas, siempre que las puertas de entrada y salida mantengan la
continuidad física y el punto de retorno.

## 2. Diagnóstico técnico-geográfico

1.  El HTML declara `world.w = 205` y `world.h = 145`; el documento
    anterior menciona 120 × 96 como escala de prototipo. La cifra 120 ×
    96 no debe tratarse como límite definitivo.
2.  La lista `areas` solo define tres rectángulos parcialmente
    superpuestos y no representa las cinco regiones finales.
3.  La función de identificación de zona (`zoneAt`) clasifica
    principalmente por coordenada X. Esto provoca etiquetas incorrectas
    cuando el jugador se mueve al norte o al sur de una misma franja.
4.  Los puntos de interés actuales se concentran en el eje X y el mapa
    todavía tiene grandes áreas sin estructura territorial.
5.  Algunos hitos son decorativos o narrativos, pero aún no están
    conectados a caminos, cruces, rutas secundarias ni límites legibles.
6.  Las instancias interiores del Depósito y del Patio están colocadas
    lejos del exterior en coordenadas de mapa, pero el sistema las
    presenta mediante puertas y conserva el punto de retorno. Se pueden
    mantener como interiores instanciados; no deben confundirse con
    regiones exteriores.

**Conclusión:** primero se fija un atlas de regiones y conexiones;
después se asignan coordenadas definitivas a los nuevos lugares y se
implementa la expansión.

## 3. Propuesta de escala

Reservar un mapa exterior de planificación de aproximadamente **420 ×
300 unidades**. Es una dimensión de diseño, no una escala física ni una
obligación de llenar todo el terreno.

-   Mantener las coordenadas actuales del Capítulo I durante la primera
    reorganización.
-   Ampliar el terreno hacia el este y el sur.
-   Dejar márgenes vacíos intencionales para futuras misiones, caminos,
    ruinas y encuentros.
-   No dibujar todo el terreno como una cuadrícula uniforme de puntos de
    interés.
-   Construir caminos principales, secundarios y senderos de exploración
    con anchuras y materiales visualmente distintos.

## 4. Distribución macro del mundo

La orientación es de diseño: norte arriba, este a la derecha. Las
regiones se conectan mediante corredores geográficos; no son pantallas
ni niveles separados.

``` text
                         NORTE
                           ↑

  OESTE                                                ESTE
  ┌──────────────────────┬───────────────────────────────┐
  │ LA ESTRELLA          │ CIUDAD ENFERMA                │
  │ + cinturón exterior  │ Barrio · Parque · Metro       │
  │                      │ Centro Comercial · Hospital   │
  │ Calle Oxidada        │ Cementerio · Nido              │
  │ Depósito / máquinas  ├───────────────┬───────────────┤
  │ Fábrica / montaje    │                │ TERRITORIO    │
  │ Túnel de Servicio ───┘                │ DEL CULTO     │
  ├──────────────────────┐                │ Aldea · Bosque│
  │ TERRITORIO MILITAR   │                │ Mercado       │
  │ Puerto · Muelle      │                │ Catacumbas    │
  │ Trincheras · Puente  │                │ Templo        │
  │ Hangar · Aeródromo   │                │ Santuario     │
  │ Fortaleza            │                └───────────────┘
  └──────────────────────┘

                           ↓
                           SUR
```

La distribución final debe respetar estas relaciones:

-   **La Estrella** está en el borde occidental del territorio conocido
    y funciona como primer refugio y referencia emocional.
-   **El cinturón exterior** rodea La Estrella y conecta con la Calle
    Oxidada. Incluye ruinas, caminos secundarios, pequeños campamentos y
    señales de la guerra.
-   **El territorio de las máquinas** ocupa el corredor
    central-occidental. Es la región ya iniciada y el primer gran bloque
    explorable.
-   **La Ciudad Enferma** se desarrolla al este/noreste del territorio
    de las máquinas. La transición debe mostrar un cambio gradual de
    vegetación, residuos, contaminación y presencia de infectados.
-   **El territorio militar** se extiende al sur/suroeste, con costa o
    infraestructura portuaria en su borde exterior y defensas
    escalonadas hacia el interior.
-   **El territorio del culto** se sitúa al este/sureste, en una zona de
    bosque, elevaciones y construcciones rituales. Debe sentirse aislado
    por el terreno, no por una pantalla de carga.

## 5. Regiones y ubicación de sus puntos de interés

### Región 1 --- La Estrella y cinturón exterior

**Función:** punto de origen, refugio, memoria y primera lectura del
mundo.

-   La Estrella: conservar su ubicación y su salida hacia el este.
-   Calle Oxidada: conservarla como primer camino reconocible, con
    restos de vehículos, señales y fachadas bajas.
-   Depósito de Chatarra: conservar el acceso actual y ampliar sus
    patios exteriores alrededor de la nave.
-   Torre de agua: hito visible desde varios tramos del cinturón.
-   Autobús abandonado: junto a un desvío de la ruta principal; puede
    contener pistas o recursos.
-   Antena de radio: en una elevación o estructura despejada que
    anticipe la red de señales.
-   Campamento vacío: fuera del camino principal, con rastros de
    evacuación.
-   Puente derrumbado: límite físico visible y futura conexión hacia el
    territorio militar.
-   Cráter: zona de exploración opcional con restos del impacto y pistas
    del pasado.

No convertir todos estos hitos en misiones obligatorias. Algunos deben
funcionar como orientación, ambiente o recompensa de exploración.

### Región 2 --- Territorio de las máquinas

**Función:** explorar la autonomía, la obediencia y el miedo a repetir
la opresión.

Orden espacial sugerido, conservando el recorrido actual:

1.  Calle Oxidada y borde del depósito.
2.  Depósito de Chatarra: clasificación, contenedores, grúas y patios de
    carga.
3.  Patio de Máquinas: mantenimiento, reparación y consolas.
4.  Fábrica del Capataz: sala de control y arena del conflicto.
5.  Línea de Montaje: producción, registros y vestigios de las unidades.
6.  Túnel de Servicio: corredor de comunicaciones hacia el exterior.

Añadir ramales, no solo una línea recta: - Un patio de vehículos y
chatarra al sur del Depósito. - Un área de almacenamiento bloqueada que
se abra desde el Patio. - Una ruta de mantenimiento que conecte el Patio
con la Línea de Montaje. - Una salida secundaria del túnel que pueda
convertirse en atajo al descubrir el repetidor.

### Región 3 --- Ciudad Enferma

**Función:** mostrar el coste humano de la Fiebre Gris y la diferencia
entre supervivencia, aislamiento y comunidad.

Orden sugerido desde la entrada occidental:

1.  **Barrio:** acceso urbano, viviendas abandonadas y primeros indicios
    de la enfermedad.
2.  **Parque:** espacio abierto que permite orientarse y ofrece rutas
    alternativas.
3.  **Centro Comercial:** refugio improvisado, recursos y conflictos
    entre supervivientes.
4.  **Metro:** conexión subterránea que cruza varios sectores y puede
    habilitar atajos.
5.  **Cementerio:** memoria de las víctimas y pistas sobre los primeros
    días.
6.  **Hospital:** núcleo de investigación, tratamiento y decisiones
    difíciles.
7.  **Nido:** zona más peligrosa y concentrada; debe quedar al fondo de
    la progresión urbana, no junto a la entrada.

El Nido no debe ser simplemente una arena de combate: su ubicación debe
explicar cómo se propagó o concentró la amenaza.

### Región 4 --- Territorio del culto

**Función:** explorar fe, comunidad, manipulación, protección y
responsabilidad moral.

Orden sugerido desde el acceso occidental/norte:

1.  **Bosque:** transición natural, senderos que se bifurcan y señales
    del culto.
2.  **Aldea:** vida cotidiana, habitantes y primera lectura de sus
    normas.
3.  **Mercado:** intercambio, rumores, tensiones y acceso a misiones.
4.  **Catacumbas:** capa histórica bajo la aldea y rutas ocultas.
5.  **Escalinata:** ascenso físico y visual hacia el centro ceremonial.
6.  **Templo:** centro público del poder religioso.
7.  **Santuario:** enclave más reservado, con revelaciones y decisiones
    de alto impacto.

La aldea y el mercado deben tener habitantes y actividades; no conviene
que toda la región sea un conjunto de pasillos de combate.

### Región 5 --- Territorio militar

**Función:** mostrar la supervivencia organizada mediante jerarquía,
logística, defensa y control territorial.

Orden sugerido desde el acceso norte/este:

1.  **Puente:** cruce estratégico y primer cuello de botella.
2.  **Trincheras:** primera línea defensiva y restos de distintos
    bandos.
3.  **Puerto y Muelle:** logística, comercio, evacuaciones y acceso por
    agua.
4.  **Hangar:** vehículos, aeronaves y archivos de operaciones.
5.  **Aeródromo:** espacio abierto de tránsito y posible ruta de gran
    alcance.
6.  **Fortaleza:** centro de mando, defensa y resolución de la trama
    militar.

El Puerto y el Muelle deben sentirse conectados al agua; el Hangar y el
Aeródromo necesitan espacio libre suficiente para que su escala sea
creíble.

## 6. Red de caminos y conexiones

La geografía debe formar un grafo con rutas principales, secundarias y
atajos persistentes.

  -----------------------------------------------------------------------
  Conexión                Tipo inicial            Evolución
  ----------------------- ----------------------- -----------------------
  La Estrella ↔ Calle     Camino abierto tras la  Ruta segura hacia el
  Oxidada                 salida                  refugio

  Calle Oxidada ↔         Camino industrial       Accesos secundarios por
  Depósito                                        patios

  Depósito ↔ Patio de     Portón/camino de        Atajo tras restaurar
  Máquinas                servicio                mecanismos

  Patio ↔ Fábrica         Compuerta industrial    Se abre con las tres
                                                  consolas

  Fábrica ↔ Línea de      Puerta física           Se abre tras resolver
  Montaje                                         al Capataz

  Línea de Montaje ↔      Acceso de mantenimiento Se habilita con el
  Túnel                                           registro Siesta

  Túnel ↔ Ciudad Enferma  Salida remota bloqueada Conexión principal a la
                                                  segunda gran región

  Ciudad ↔ Territorio     Puente o corredor       Cruce reparable o
  militar                 fluvial                 controlado

  Ciudad ↔ Territorio del Camino de bosque /      Ruta alternativa según
  culto                   línea de metro          decisiones

  Culto ↔ Militar         Paso de montaña         Conexión tardía
                          secundario              opcional
  -----------------------------------------------------------------------

Regla esencial: las regiones importantes deberían tener, con el tiempo,
más de una forma de entrar o salir. Así el jugador puede crear circuitos
y atajos, en lugar de recorrer siempre el mismo pasillo.

## 7. Cómo colocar edificios, caminos y puntos de interés

-   Los caminos principales deben conectar puertas y cruces reales, no
    terminar frente a paredes decorativas.
-   Cada edificio importante necesita fachada, entrada visible, espacio
    de aproximación y una salida coherente.
-   Los puntos de interés no deben quedar pegados entre sí: reservar
    espacio para leer el entorno y para encuentros.
-   Los hitos altos ---torres, antenas, grúas, templos, hangares---
    deben servir como referencias visuales desde lejos.
-   Los edificios grandes deben tener patios, accesos de carga, zonas de
    servicio y al menos un lado no accesible que cierre su volumen.
-   Las rutas secundarias deben recompensar exploración con recursos,
    información, vistas o atajos.
-   Las barreras deben ser visibles desde antes de alcanzarlas y tener
    una explicación física o narrativa.
-   Las regiones deben cambiar gradualmente de suelo, vegetación,
    iluminación, arquitectura, sonido y densidad de objetos.

## 8. Reglas técnicas para implementar el atlas

Antes de añadir muchos objetos:

1.  Sustituir la clasificación de zonas basada solo en X por sectores
    definidos mediante polígonos o regiones con límites en X/Y.
2.  Mantener un identificador estable para cada región y subzona.
3.  Separar los datos de mapa de la lógica narrativa: posición, tipo,
    región, colisión, acceso y condición de aparición deben ser
    propiedades explícitas.
4.  Definir caminos como trazados navegables y colisiones como geometría
    independiente; no inferir que todo objeto dibujado bloquea el paso.
5.  Añadir puntos de acceso como entidades con entrada, salida,
    condición y destino de retorno.
6.  Mantener los interiores instanciados, pero guardar siempre el punto
    exterior de entrada y el estado del interior.
7.  Registrar cada atajo desbloqueado en el estado persistente del
    mundo.
8.  Evitar que un cambio de región teletransporte al jugador: las
    transiciones deben ocurrir al cruzar el acceso físico.
9.  Diseñar primero el terreno y las rutas; colocar props y misiones
    después.
10. Probar navegación y cámara con geometría provisional antes de
    producir decoración detallada.

## 9. Orden de producción recomendado

**Etapa 1 --- Atlas y coordenadas** - Aprobar la distribución de las
cinco regiones. - Definir límites y conexiones. - Resolver qué hitos
actuales se conservan y cuáles cambian de función.

**Etapa 2 --- Esqueleto navegable** - Ampliar dimensiones del mundo. -
Dibujar suelo, caminos, barreras, cruces y salidas. - Implementar
identificación de región por geometría real. - Verificar que se puede
recorrer el mapa sin quedar atrapado.

**Etapa 3 --- Puntos de interés** - Colocar edificios grandes y hitos de
orientación. - Incorporar interiores y accesos físicos. - Añadir rutas
secundarias y zonas opcionales.

**Etapa 4 --- Contenido** - Distribuir NPC, facciones, misiones,
recursos, documentos y encuentros. - Conectar las decisiones con cambios
persistentes del mundo.

**Etapa 5 --- Expansión jugable** - Desarrollar primero la salida del
Túnel hacia la Ciudad Enferma. - Luego construir la Ciudad como la
siguiente región jugable completa. - Incorporar después las conexiones
al Culto y al Territorio Militar.

## 10. Decisiones que deben quedar fijadas antes de programar

-   Confirmar si el atlas de 420 × 300 unidades es suficiente o si se
    prefiere una reserva mayor.
-   Aprobar la orientación macro propuesta: máquinas al oeste/centro,
    ciudad al este/noreste, militar al sur/suroeste y culto al
    este/sureste.
-   Decidir si el acceso inicial a la Ciudad Enferma será por el Túnel
    de Servicio o si habrá también una ruta exterior visible desde el
    principio.
-   Definir si Puerto/Muelle forman una costa real o un complejo
    fluvial.
-   Mantener el Guion Maestro Fase 4 como autoridad para nombres, hechos
    y relaciones narrativas.

**Recomendación:** aprobar primero la geografía y el grafo de
conexiones. No empezar todavía a poblar la Ciudad, el Culto o el
Territorio Militar con NPC y misiones hasta que el esqueleto navegable
esté definido y probado.


---

## Addendum de integración — Versión 3.1

### Correspondencia regional adoptada
Para evitar una contradicción de numeración, la implementación utiliza:
- **R1:** La Estrella y cinturón exterior.
- **R2:** Territorio de las máquinas.
- **R3:** Ciudad Enferma.
- **R4:** Territorio militar.
- **R5:** Territorio del culto.

Esta correspondencia sigue el diagrama macro del propio Atlas, el Plano Detallado de Coordenadas y el CSV maestro. Los apartados descriptivos del Atlas que titulan R4 como Culto y R5 como Militar deben leerse como un intercambio de rótulos, no como un cambio de coordenadas.

### Estado de integración
El HTML 3.1 ya contiene el terreno exterior 420 × 300, la red inicial de caminos, los hitos propuestos del CSV y la identificación territorial en dos dimensiones. La geografía está preparada como esqueleto; los interiores, edificios sólidos, NPC, misiones y contenido narrativo de las nuevas regiones siguen pendientes.


---

## Addendum 3.2 — R3 Ciudad Enferma: primera implementación jugable

La organización macro del Atlas se mantiene. La Ciudad Enferma conserva sus puntos principales del plano 3.1 y ahora tiene una primera capa de contenido físico y narrativo.

- **Barrio:** cuatro bloques residenciales y un local; Mara ofrece la primera misión de suministros.
- **Plaza del tranvía:** distribuidor de los caminos principales.
- **Parque municipal:** espacio abierto, árboles fuera de los corredores y Tomás como testigo de la evacuación.
- **Centro Comercial:** edificio con colisión y acceso sur; interior de refugio, depósito de suministros y radio de emergencias.
- **Metro norte:** acceso separado del hito cartográfico para evitar dos interacciones en la misma coordenada. Su panel habilita un atajo al sur urbano.
- **Cementerio:** sector de memoria y pistas, conectado con Hospital y corredor hacia el bosque.
- **Hospital:** edificio con acceso norte y salida de emergencia sur; interior con archivo epidemiológico y muestra sellada. La evidencia abre el acceso al Nido, en cualquier orden de obtención.
- **Nido:** estructura orgánica al fondo del recorrido; acceso bloqueado hasta reunir ambas evidencias. Su interior contiene el núcleo y el registro de evacuación.

La región se construye como continuidad exterior, no como selección de pantallas. Los cuatro interiores usan instancias separadas y retornan al punto exacto desde el que se ingresó, salvo el atajo del Metro que devuelve a la salida sur (218,139).

**Criterio editorial:** el Nido no se presenta como una arena aislada. La documentación recuperada lo vincula con el antiguo intercambiador subterráneo y con una señal rítmica que precedió a los episodios de desorientación. Esta es una primera pista, no la explicación final de la Fiebre Gris.


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


## Addendum 3.7 — Catacumbas: interior de exploración

La entrada de Catacumbas deja de ser un hito meramente descriptivo y abre una instancia interior. Su distribución se limita a un corredor principal y cámaras laterales con arquitectura de piedra, humedad y objetos sin identificación. La salida conserva la coordenada exterior de entrada. No se establece todavía el uso histórico o doctrinal del lugar. El Templo y el Santuario continúan sin interiores.


## Addendum 3.8 — Templo: interior de exploración

El acceso norte del Templo (352,247) abre una instancia interior propia. El diseño se limita a una nave de piedra, columnas, bancos laterales, una plataforma vacía y tres puntos de inspección ambiental. No se agregan símbolos interpretables, doctrinas, habitantes, misiones ni revelaciones. El Santuario permanece sin interior y el territorio militar no recibe contenido.


## Addendum 3.9 — hitos visibles y continuidad de rutas

Se añaden al exterior marcadores arquitectónicos/ambientales para nueve puntos R1/R2 ya definidos en el CSV maestro. Se dibujan solo dentro del área cercana a cámara para mantener el coste de renderizado acotado. La ruta desde el Puente Viejo se representa como corredor de aproximación y termina antes de entrar al territorio militar.

La clasificación de región ahora utiliza ambos ejes. Se respeta la correspondencia adoptada: R1 La Estrella/cinturón, R2 máquinas, R3 Ciudad Enferma, R4 militar y R5 culto. El solapamiento R1/R2 se resuelve priorizando el cinturón occidental hasta X=45 y el núcleo industrial desde X=45.

No se habilitan todavía interiores, NPC ni misiones en estos hitos. La región militar permanece como geografía reservada.


## Addendum 3.10 — lectura física de R1/R2

Los hitos R1/R2 dejan de ser únicamente visuales: sus estructuras y elementos principales bloquean el paso. Los caminos se ajustan a los accesos ya fijados en el Plano Detallado, sin crear rutas que atraviesen edificios. El almacén incorpora un pasillo central condicionado por la restauración de las tres consolas industriales.

La frontera de R4 queda sellada para el ingreso desde otras regiones. El corredor del Puente Viejo se conserva como aproximación visible y no abre el territorio militar. No se incorpora contenido narrativo, facciones ni misiones nuevas.


## Addendum 3.12 — Santuario explorable

El acceso occidental del Santuario (384,276) abre una sala interior de exploración ambiental. La salida devuelve al punto exacto de entrada. La sala contiene piedra expuesta, columnas periféricas, bancos bajos y una plataforma vacía. Las inspecciones describen desgaste, polvo y filtración de luz sin interpretar su origen ni función. El Santuario queda habilitado como espacio físico, pero su contenido histórico y doctrinal continúa sin definir.

El territorio militar R4 permanece cerrado a nuevos ingresos. No se crea una conexión militar ni se anticipa contenido de esa región.


## Addendum 3.12 — hitos interactivos R1/R2

Los diez hitos R1/R2 definidos en el Plano y CSV reciben interacciones de inspección o servicio. Las descripciones se mantienen en el nivel funcional del Atlas: distribuidor de rutas, recursos, pista ambiental, observación, corredor futuro, encuentro opcional, ramal sur, reparación, atajo condicionado y energía.

Las interacciones no alteran la geografía ni habilitan el Territorio Militar. Los dos puntos de recursos (Patio de vehículos y Taller de desguace) entregan dos piezas una sola vez cada uno. El taller permite reparar con dos piezas.


## Addendum 3.13 — exploración de R3

Se incorpora una capa de inspección ambiental en siete hitos ya cartografiados: Puerta de la ciudad (184,34), Barrio residencial (211,38), Plaza del tranvía (232,58), Parque municipal (205,91), Cementerio (278,88), Salida sur urbana (218,139) y Paso del bosque (309,133). Las inspecciones registran la visita en el diario y no alteran rutas ni recompensas.

Se mantiene el orden funcional de la región: Barrio, Parque, Centro Comercial, Metro, Cementerio, Hospital y Nido. Los interiores del Centro Comercial, Metro, Hospital y Nido conservan sus accesos y condiciones existentes. La salida sur sigue siendo un límite, no un enlace abierto a R4.


## Addendum 3.15 — corredor urbano sur

El extremo sur de Ciudad Enferma incorpora tres referencias civiles de orientación y mantenimiento. Su función es ayudar a cartografiar la ruta tras resolver el Nido. No son puestos militares ni instalaciones de una facción. El reconocimiento completo registra el corredor en el diario, pero la frontera de R4 permanece cerrada.


## Addendum 3.15 — preparativos civiles de frontera

La salida sur urbana puede prepararse únicamente después de resolver el Nido y registrar los tres hitos civiles del corredor. La acción despeja escombros menores y deja señalización de orientación. No abre R4, no establece contacto, no añade soldados, mandos, instalaciones, órdenes ni información sobre la facción militar. El paso fronterizo permanece cerrado y el contenido militar sigue reservado para su tramo narrativo.


## Addendum 3.16 — recursos civiles secundarios en Ciudad Enferma

Se incorporan tres puntos opcionales de recuperación de equipo: una caja de mantenimiento junto a la Plaza del tranvía (237,61), un armario de servicio en el Parque municipal (214,100) y una caja de herramientas en el Cementerio (285,96). Cada punto entrega una pieza reutilizable una sola vez. Al reunir las tres piezas, el banco de reparación civil del Barrio (225,53) queda habilitado: consume dos piezas para restaurar 30 puntos de integridad. La actividad amplía la exploración y no modifica la progresión narrativa, los desenlaces del Nido ni el acceso a R4.


## Actualización 3.17 — contenido sin expansión territorial
Las tres tareas posteriores al Nido se desarrollan en los NPC existentes de Barrio, Parque y Hospital. No agregan puntos geográficos ni modifican rutas, límites o accesos. R4 permanece cerrado.


## Addendum 3.18 — lectura de conectores R3/R5

El corredor desde Ciudad Enferma se lee en dos tramos consecutivos: el **Paso del bosque** es la subzona terminal de R3 y el **Umbral del bosque** es el acceso regional de R5 en (309,139). El HUD diferencia el Umbral del bosque y el Sendero de los símbolos antes de llegar a la Aldea. Se mantienen los ramales existentes hacia Mercado y Catacumbas.

La Escalinata (380,245) se reconoce como subzona propia entre Catacumbas y el Templo. El corredor hacia el Templo concluye en su puerta norte (352,247); no se considera un camino que atraviese la huella del edificio. La vereda al Santuario conserva su aproximación occidental (384,276).

Esta actualización aclara la navegación y la lectura de subzonas; no introduce rutas nuevas ni altera la geografía aprobada.


## Addendum 3.19 — frontera lógica y progresión de interiores

La frontera regional del corredor se resuelve en Y=135: el Paso del bosque (R3) ocupa Y=110–134 y el acceso del Umbral (R5) está en (309,139). El hito cartográfico Umbral del bosque conserva su centro en (316,145); su acceso operativo es el punto de entrada (309,139). Son referencias relacionadas, pero no deben confundirse como dos puertas.

La secuencia de interiores R5 queda documentada así: acceso exterior Catacumbas (354,220) → instancia (329–361,91–125) → salida al punto de entrada; acceso norte del Templo (352,247) → instancia (329–361,132–166) → retorno al punto de entrada; acceso occidental del Santuario (384,276) → instancia (365–397,190–224) → retorno al punto de entrada. La aparición interior del Santuario se separa del marcador de salida.

La continuación de partidas restaura el estado activo y conserva `currentInterior`/`returnPoint`. La clasificación regional de los interiores se mantiene vinculada a su región exterior de origen.


## Addendum 3.20 — R5, exploración ambiental

Se agregan seis puntos de observación sin función narrativa nueva: Tronco caído (316,168), Claro pedregoso (326,163), Muro derrumbado (329,190), Fuente seca (321,222), Patio de puestos (342,218) y Descanso de la escalinata (372,239). Los ramales son senderos de lectura visual; no habilitan accesos ni modifican la organización regional. La Aldea, Mercado, Catacumbas, Templo y Santuario conservan su distribución. R4 continúa reservado.


## Addendum 3.21 — R4 Territorio Militar: capa geográfica

La numeración regional de implementación se mantiene: R4 es Territorio Militar y R5 es Territorio del Culto, según diagrama macro, Plano Detallado y CSV maestro. El apartado descriptivo antiguo que llama al Culto R4 y al Militar R5 contiene un intercambio de rótulos y no altera esta correspondencia.

La secuencia cartográfica militar conserva el acceso por el norte/este hacia Control del puente (112,160), Trincheras norte (91,185), Cuartel avanzado (139,188), y los sectores logísticos del sur: Puerto (65,225), Muelle (44,247), Hangar (145,230), Aeródromo (180,250) y Fortaleza (133,276). El Puesto de radio (192,192) permanece como hito auxiliar.

La costa suroeste se representa con el agua existente y una estructura de muelle conectada visualmente a la orilla. El Hangar y el Aeródromo conservan áreas despejadas acordes a sus huellas. Esta capa es geográfica, no narrativa: no identifica fuerzas, bandos, rangos ni responsables.


## Addendum 3.22 — preparación narrativa de R4

El Guion Maestro Fase 4 establece la ruta del Acto IV y sus contenidos narrativos: logística de lanchas artilladas y evacuaciones selectivas, revelaciones de Mecánica y Piloto, pruebas del Vuelo 9 en el Aeródromo, conexión del recetario de Don Aurelio con el pasado del General y sabotaje condicionado de las lanchas mediante llave inglesa y ayuda previa a la Mecánica. La Fortaleza contiene la confrontación con el General Acorazado.

La correspondencia espacial utiliza los hitos R4 ya cartografiados en 3.21; no se cambian centros, huellas ni accesos. El Cuartel avanzado y el Puesto de radio continúan sin función narrativa definida. Esta addenda es de planificación: no abre R4 ni añade puertas, interiores, personajes o misiones.
