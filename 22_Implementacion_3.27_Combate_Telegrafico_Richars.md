# Implementación 3.27 — Combate telegráfico de Richars Octavio

**Rama:** `release/3.27-pulido-tecnico`  
**Archivo:** `index.html`  
**Estado:** implementado en código; validación estática satisfactoria; prueba manual pendiente.

## Objetivo

Diferenciar las tres fases del combate mediante ataques anunciados antes de resolver el turno, y comunicar en pantalla el efecto de la preparación opcional del jugador. Se conserva a Richars como jefe obligatorio: no se rinde, no se redime y su derrota no resuelve Siesta ni la señal externa.

## Cambios implementados

### 1. Ataques telegrafiados por fase

Cada turno anuncia nombre, icono, descripción y daño previsto antes de que el jugador elija su acción. El patrón rota entre tres ataques por fase usando el contador de turnos ya existente.

| Fase | Patrones anunciados |
|---|---|
| 1 — Control del campo | Ráfaga de cobertura, Disparo de precisión, Fuego de supresión |
| 2 — Blindaje de asalto | Embestida blindada, Onda de choque, Ráfaga perforante |
| 3 — Última orden | Descarga de área, Salva final, Presión directa |

Los patrones modifican el daño base de cada fase. El diálogo muestra el daño previsto tanto para ataque pesado como para esquiva y contraataque.

### 2. Preparación y apoyo opcional visibles

El informe de combate explica los efectos que ya estaban codificados:

- **Lanchas saboteadas por Elba:** reducción de 6 puntos al daño recibido; se informa que el apoyo artillado queda impedido.
- **Control del puente neutralizado por Funes:** reducción de 4 puntos; se informa que Richars pierde esa coordinación.
- **Orden de ocultamiento obtenida:** reducción de 2 puntos; se comunica como información que permite anticipar movimientos.

No se convierten en requisitos para acceder al jefe ni para completar el Acto IV.

### 3. Acciones y equilibrio

- Ataque pesado: 46 de daño.
- Esquivar y contraatacar: 30 de daño y reducción de 7 puntos al daño entrante respecto al ataque pesado.
- Exponer la cadena de órdenes: 58 de daño, una vez, si están reunidas las tres pruebas del Vuelo 9.
- Reparación: consume 2 piezas y recupera 25 puntos una vez. Ahora consume el turno y recibe el ataque que Richars ya había anunciado; el daño se muestra antes de confirmar la reparación.
- Retirada: mantiene la posibilidad de abandonar el combate y volver preparado.

La resolución del golpe informa qué ataque impactó, cuánto daño recibió Siete y su integridad restante. Al cambiar de fase, el texto lo comunica.

## Compatibilidad y alcance

- Se reutiliza `bossTurnCount` ya existente para rotar los patrones.
- Cada turno resuelto persiste silenciosamente el estado para conservar integridad, turno/patrón y reparación usada al recargar.
- No se añade una nueva bandera narrativa ni se altera el esquema de guardado.
- Se conserva `saveVersion: 50` y la clave `mesero30save`.
- No se modifican diálogos de historia, condiciones de acceso, desenlaces, personajes ni coordenadas.
- No se modificó `main`; los cambios están en la rama 3.27.

## QA estático realizado

Se volvió a leer el archivo tras los commits y se comprobaron estas condiciones:

| Comprobación | Resultado |
|---|---|
| Una única definición de `militaryBossTurn` | OK |
| Una única definición de `militaryBossAction` con parámetro de ataque | OK |
| Presencia de anuncio previo del ataque | OK |
| Patrones de las tres fases presentes | OK |
| Mensajes de apoyo artillado y preparación | OK |
| Reparación consume el turno y recibe el golpe anunciado | OK |
| Versión y clave de guardado sin cambios | OK |
| Persistencia silenciosa tras cada turno | OK |
| Richars conserva su condición de no rendirse | OK |

También se verificó que las funciones usan el contador persistente existente y que la opción de reparación muestra el daño entrante antes de seleccionarla.

## Pruebas manuales pendientes

No se ejecutó el juego en navegador. Quedan pendientes:

1. Recorrer las tres fases y comprobar el ciclo de patrones.
2. Verificar que el daño mostrado coincide con el daño aplicado.
3. Repetir con lanchas intactas y saboteadas.
4. Repetir con Funes activo y neutralizado.
5. Comprobar el modificador de la orden de ocultamiento.
6. Probar reparación, esquiva, exposición y retirada.
7. Guardar y cargar durante el combate y comprobar que el ciclo de patrones continúa coherentemente.
8. Repetir en móvil y escritorio.

**Conclusión:** la mejora está integrada y supera las comprobaciones estáticas enumeradas. No se declara el combate validado hasta ejecutar la matriz manual en navegador.
