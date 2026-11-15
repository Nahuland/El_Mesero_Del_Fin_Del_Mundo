# Matriz de regresión manual 3.27 — Colisiones y transiciones

**Rama:** `release/3.27-pulido-tecnico`  
**Versión del juego:** 3.27  
**Archivo bajo prueba:** `index.html`  
**Tipo de validación:** manual en navegador  
**Estado inicial:** pendiente de ejecución  
**Regla:** no marcar un caso como aprobado sin ejecutarlo. Registrar navegador, dispositivo, método de control y evidencia cuando falle.

## 1. Preparación de la sesión

- [ ] Abrir la versión de `index.html` de esta rama en un navegador.
- [ ] Registrar navegador y versión.
- [ ] Registrar dispositivo, resolución y si se usa teclado, ratón o controles táctiles.
- [ ] Iniciar una partida de prueba o cargar un guardado preparado.
- [ ] Confirmar que el personaje responde a las ocho direcciones.
- [ ] Anotar si la prueba usa partida nueva, guardado actual o guardado antiguo.

**Datos de sesión**

| Campo | Registro |
|---|---|
| Fecha y hora | |
| Navegador / versión | |
| Sistema / dispositivo | |
| Resolución / escala | |
| Controles | |
| Tipo de partida / guardado | |
| Probador | |

## 2. Criterios de resultado

- **APROBADO:** se ejecutaron todos los pasos y el resultado esperado ocurrió.
- **FALLIDO:** se reprodujo un comportamiento distinto al esperado.
- **BLOQUEADO:** no se pudo llegar al escenario o faltan condiciones previas.
- **NO EJECUTADO:** todavía no se probó.

En cada fallo, anotar pasos exactos, ubicación aproximada, controles usados y adjuntar captura o vídeo si es posible. No cambiar coordenadas, diálogos, historia ni lógica durante la ejecución de esta matriz.

## 3. Casos de prueba

### A. H1 — Perímetros de interiores urbanos

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| A01 | Centro Comercial: entrar y caminar contra cada uno de los cuatro bordes; intentar cruzar el borde inferior sin interactuar con la salida. | El personaje permanece dentro; no queda fuera con `currentInterior` activo. | NO EJECUTADO |
| A02 | Centro Comercial: interactuar con la salida normal, volver a entrar y repetir. | Sale al punto exterior correcto y puede reentrar. | NO EJECUTADO |
| A03 | Metro: repetir A01 en los cuatro bordes. | No se atraviesa el perímetro ni se abandona el estado interior. | NO EJECUTADO |
| A04 | Metro: usar la salida normal. | Regresa al punto exterior de retorno correcto. | NO EJECUTADO |
| A05 | Metro: activar y usar el atajo/salida sur especial. | La transición termina en el destino especial previsto (218,139). | NO EJECUTADO |
| A06 | Hospital: repetir A01 en los cuatro bordes. | No se atraviesa el perímetro ni se abandona el estado interior. | NO EJECUTADO |
| A07 | Hospital: usar la salida normal y reentrar. | Retorno correcto y reentrada funcional. | NO EJECUTADO |
| A08 | Nido: repetir A01 en los cuatro bordes. | No se atraviesa el perímetro ni se abandona el estado interior. | NO EJECUTADO |
| A09 | Nido: usar la salida normal y reentrar. | Retorno correcto y reentrada funcional. | NO EJECUTADO |
| A10 | Guardar dentro de cada uno de los cuatro interiores, recargar y probar movimiento y salida. | Conserva interior, posición válida y salida funcional. | NO EJECUTADO |
| A11 | Cargar un guardado antiguo preparado con `currentInterior` válido y posición fuera del área transitable. | Reubica al punto de entrada de esa sala sin perder `returnPoint` ni progreso. | NO EJECUTADO |

### B. H3 — Puertas y aberturas estrechas

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| B01 | Catacumbas: cruzar la abertura desde dentro y desde fuera, acercándose en horizontal, vertical y diagonal. | Cruza sin quedar pegado al borde; transición correcta en ambos sentidos. | NO EJECUTADO |
| B02 | Templo: repetir B01. | Corredor de salida funcional; no atraviesa muros fuera de la abertura. | NO EJECUTADO |
| B03 | Santuario: cruzar la abertura occidental desde ambos lados y distintos ángulos. | Transición correcta sin atasco ni salida por zonas bloqueadas. | NO EJECUTADO |
| B04 | Repetir B01–B03 con teclado y controles táctiles, si están disponibles. | Comportamiento equivalente; sin pérdida de respuesta. | NO EJECUTADO |

### C. H4 — Hangar y Fortaleza

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| C01 | Acceder al Hangar, recorrer su perímetro, salir y volver a entrar. | Entrada, movimiento y retorno funcionales. | NO EJECUTADO |
| C02 | Guardar dentro del Hangar, recargar y salir. | Conserva ubicación interior válida y permite salir. | NO EJECUTADO |
| C03 | Cumplir la condición narrativa ya existente para acceder a la Fortaleza; entrar, recorrer y salir. | Entrada y retorno funcionales; no se altera la condición de acceso. | NO EJECUTADO |
| C04 | Guardar dentro de la Fortaleza, recargar y salir. | Conserva ubicación interior válida y permite salir. | NO EJECUTADO |

### D. H5 — Movimiento, diagonales y esquinas

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| D01 | En zona despejada, mantener cada una de las ocho direcciones durante el mismo intervalo. | Movimiento consistente; diagonal no es notablemente más rápida que cardinal. | NO EJECUTADO |
| D02 | Aproximarse en diagonal a una esquina de edificio y deslizarse por cada lado. | El personaje se desliza cuando un eje está libre, sin vibración ni bloqueo permanente. | NO EJECUTADO |
| D03 | Repetir D02 junto a vehículo, contenedor, árbol y muro. | Colisión estable; no atraviesa el objeto ni queda atrapado. | NO EJECUTADO |
| D04 | Probar esquinas interiores y los bordes de las puertas de B01–B03. | Sin microavances, vibración o atascos persistentes. | NO EJECUTADO |
| D05 | Repetir pruebas de esquina con teclado y controles táctiles, si están disponibles. | Respuesta estable con ambos métodos. | NO EJECUTADO |

### E. Transiciones de control de regresión

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| E01 | La Estrella ↔ Calle Oxidada: abrir puerta, cruzar y volver. | Interacción y transición en ambos sentidos. | NO EJECUTADO |
| E02 | Exterior ↔ Depósito / Patio: entrar, tocar límites, salir y reentrar. | Límites y retorno consistentes. | NO EJECUTADO |
| E03 | Fábrica ↔ Línea de Montaje ↔ Túnel: probar antes y después de desbloquear las puertas mediante el progreso normal. | Bloqueos y aperturas respetan las condiciones existentes. | NO EJECUTADO |
| E04 | Túnel ↔ Ciudad Enferma: abrir compuerta y cruzar en ambos sentidos. | Transición correcta al habilitarse. | NO EJECUTADO |

## 4. Registro de incidencias

Duplicar este bloque por cada caso FALLIDO:

- **ID del caso:**
- **Estado:** FALLIDO
- **Partida / guardado:**
- **Ubicación aproximada:**
- **Controles y dirección de aproximación:**
- **Pasos exactos para reproducir:**
- **Resultado observado:**
- **Resultado esperado:**
- **Frecuencia:** siempre / intermitente / una vez
- **Evidencia:** captura, vídeo o descripción
- **Notas:**

## 5. Cierre de la regresión

| Grupo | Aprobados | Fallidos | Bloqueados | No ejecutados |
|---|---:|---:|---:|---:|
| A — H1 perímetros urbanos | | | | |
| B — H3 puertas estrechas | | | | |
| C — H4 accesos militares | | | | |
| D — H5 movimiento y esquinas | | | | |
| E — transiciones generales | | | | |

**Conclusión de la sesión:** pendiente.

**Importante:** esta matriz es un instrumento de prueba, no evidencia de que el juego haya sido probado. La auditoría 3.27 permanece estática hasta registrar la ejecución de los casos.

### F. La Estrella — coherencia visual del acceso

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| F01 | Iniciar partida nueva y observar La Estrella desde dentro y desde el exterior. Recorrer el pasillo hacia la puerta este y seguir el camino hacia el este. | La senda interior se lee como pasillo de salida; el camino exterior comienza después de la fachada y no parece atravesar el edificio. | NO EJECUTADO |
| F02 | Observar y rodear la farola situada junto al camino exterior. | La farola queda fuera de la huella del restaurante, no invade el vano de la puerta ni bloquea el paso. | NO EJECUTADO |
| F03 | Acercarse a la puerta este desde el interior y desde el exterior, en diagonal y de frente. | La puerta sigue visible y la interacción/transición se mantiene funcional. | NO EJECUTADO |


### G. Richars Octavio — combate telegráfico y preparación

| ID | Escenario y pasos | Resultado esperado | Estado |
|---|---|---|---|
| G01 | Iniciar el combate con Richars sin sabotear las lanchas ni neutralizar a Funes. Leer el anuncio y alternar ataque pesado y esquiva durante tres turnos de la fase 1. | Cada turno anuncia uno de los tres patrones de fase 1 antes de elegir; el patrón rota y el daño aplicado coincide con el anunciado. | NO EJECUTADO |
| G02 | Reducir la integridad de Richars hasta la fase 2 y repetir tres turnos. | Se anuncian Embestida blindada, Onda de choque y Ráfaga perforante; el cambio de fase se comunica. | NO EJECUTADO |
| G03 | Reducir la integridad de Richars hasta la fase 3 y repetir tres turnos. | Se anuncian Descarga de área, Salva final y Presión directa; el daño coincide con el aviso. | NO EJECUTADO |
| G04 | Repetir el combate tras sabotear las lanchas con Elba. | El diálogo informa que el apoyo artillado fue impedido y el daño entrante refleja la reducción de 6 puntos. | NO EJECUTADO |
| G05 | Repetir tras neutralizar a Funes, sin sabotear las lanchas. | El diálogo informa que Richars perdió la coordinación desde el puente y el daño refleja la reducción de 4 puntos. | NO EJECUTADO |
| G06 | Obtener la orden de ocultamiento y combatir. | El diálogo informa que la información permite anticipar movimientos y el daño refleja la reducción de 2 puntos. | NO EJECUTADO |
| G07 | Reunir las tres pruebas del Vuelo 9 y usar Exponer la cadena de órdenes. | La opción aparece una sola vez, causa el daño previsto y no cambia los hechos narrativos establecidos. | NO EJECUTADO |
| G08 | Repararse durante un ataque anunciado. | El coste de 2 piezas y la recuperación de 25 se aplican una sola vez; Richars ejecuta el ataque anunciado y el daño coincide con el mostrado. | NO EJECUTADO |
| G09 | Retirarse del combate y volver después. | Richars conserva integridad, fase y continuidad del contador de patrones; el jugador puede reanudar el combate. | NO EJECUTADO |
| G10 | Guardar durante el combate, recargar y continuar. | Se conservan integridad, turno/patrón, piezas, reparación usada y progreso; no se reinicia ni duplica una acción. | NO EJECUTADO |
| G11 | Derrotar a Richars. | No hay rendición; se abre el acceso narrativo existente a la Fortaleza y Siesta permanece pendiente de decisión. | NO EJECUTADO |
| G12 | Repetir una sesión en escritorio y otra en móvil. | Los avisos y opciones son legibles, los botones responden y no se solapan con el diálogo. | NO EJECUTADO |
