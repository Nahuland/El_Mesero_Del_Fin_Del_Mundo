# Versión 3.23 — Interiores militares y puente hacia el Acto V

## Alcance
Continuación directa de 3.22. Se conservan los nueve hitos exteriores de R4, el sistema de movimiento, la interacción, los interiores existentes y el guardado `mesero30save` con `saveVersion:49`.

## Hangar Oxidado
- Puerta interior lateral vinculada al hito exterior Hangar.
- Sala explorable con perímetro, salida física, avión inmovilizado, bancos de mantenimiento y puntos de inspección.
- Celina Borda, Mayor de Logística, aporta testimonio limitado a la asignación de plazas y a las planillas que administró.
- Libro de operaciones del Vuelo 9 corrobora número de serie y corrección del peso declarado.
- Banco de mantenimiento consume dos piezas y recupera 30 puntos de integridad.
- Nerea Vidal y las pruebas exteriores conservan su funcionamiento.

## Control del puente
- Damián Ferreyra, Coronel de Operaciones, aparece como encuentro de diálogo.
- Su testimonio se limita a coordinación de puestos y transmisión de órdenes; el jugador puede contrastarlo con trincheras y radio.
- No se añade combate ni una absolución automática.

## Fortaleza
- El acceso interior se habilita solo después de derrotar a Richars Octavio.
- Sala explorable con salida física, archivo de mando y consola Siesta.
- El archivo confirma la recepción y retirada de la discrepancia del Vuelo 9; no atribuye al General el origen de la Fiebre Gris ni de la señal.
- El recetario de Don Aurelio sigue disponible tras la derrota, sin resolver su destino posterior.

## Consola Siesta — decisión inicial
Se registra una única decisión persistente:
1. Desconectar el núcleo de órdenes.
2. Aislarlo con autorización compartida.
3. Conservar una copia de solo lectura.

La decisión no apaga la señal externa, no resuelve la libertad de las unidades y no selecciona todavía uno de los ocho finales. Es el primer nodo del Acto V y debe conectarse con los contactos y estados de mundo en la siguiente fase.

## Corrección técnica
- Los props militares se registran fuera de `resize()`; así no se duplican al cambiar el tamaño de ventana.
- La evidencia ya no revierte `faction='weakened'` a `exposed` si las lanchas fueron saboteadas o Funes fue derrotado.
- Los interiores `milHangar` y `milFortress` se agregan a la lista de interiores válidos para restauración de partidas.
- Se conserva la versión de guardado 49; los nuevos campos se inicializan de forma aditiva.

## Pendiente de validación
La sintaxis y comprobaciones estáticas pasan. Faltan recorrido automatizado real de entradas/salidas, colisiones, guardado/carga en navegador, combate balanceado, prueba visual manual y móvil físico. No se declara cerrado el Acto IV ni el Acto V.
