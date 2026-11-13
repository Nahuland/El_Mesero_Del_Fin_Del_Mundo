# Versión 3.22 — Implementación inicial del Ejército de Salvación

## Alcance de esta entrega

La primera capa jugable del Acto IV queda integrada en el HTML principal y en la copia versionada. Se parte de la geografía R4 de 3.21 y se preservan las coordenadas de los nueve hitos ya existentes.

## Progresión y acceso a R4

R4 se abre al completar:
1. La resolución del Nido.
2. El reconocimiento de los tres puntos del corredor sur.
3. La preparación de la salida urbana.

La bandera nueva es `state.flags.militaryAccessOpen`. Las partidas anteriores que ya tenían `state.city.southApproachPrepared` reciben esa bandera durante la carga.

## Personajes y encuentros

- **Elba Roldán, Mecánica:** se encuentra en el Puerto. Puede aceptar ayudarla y conseguir la llave inglesa en el Cuartel avanzado. El sabotaje se realiza en el Muelle.
- **Nerea Vidal, Piloto:** se encuentra junto al Hangar. Su testimonio se limita a lo que vio y a las órdenes que recibió sobre el Vuelo 9.
- **Ramiro Funes, Jefe de Seguridad:** encuentro opcional de combate en el Control del puente.
- **Richars Octavio, General Acorazado:** jefe final obligatorio frente a la Fortaleza.

Damián Ferreyra y Celina Borda quedan definidos en el canon aprobado, pero sus escenas y encuentros aún no están implementados.

## Cadena de pruebas

- Manifiesto de evacuación: Puerto.
- Orden de carga del Vuelo 9: Hangar.
- Registro de discrepancia de carga: Aeródromo.
- Orden de ocultamiento: Puesto de radio.
- Testimonio de Nerea: Hangar.
- Testimonio/logística de Elba: Puerto y Muelle.
- Orden de represión: Trincheras norte.
- Recetario de Don Aurelio: disponible dentro de la Fortaleza después de derrotar a Richars Octavio.

La cadena principal de acceso al jefe requiere tres documentos: orden de carga, discrepancia y ocultamiento. No se afirma que el Ejército creara la Fiebre Gris o la señal externa.

## Combate de Richars Octavio

Combate por turnos adaptado al sistema de diálogo y decisiones ya existente:
- Fase 1: Control del campo.
- Fase 2: Blindaje de asalto.
- Fase 3: Última orden.

Las pruebas completas permiten una acción de exposición que abre una oportunidad de daño. El sabotaje de lanchas, la derrota de Funes y la orden de ocultamiento reducen la presión recibida. El combate sigue siendo obligatorio y ganable sin completar todos los preparativos.

Richars Octavio no se rinde, no se redime y no puede ser perdonado. Su derrota abre el paso de la Fortaleza, el recetario y la consola Siesta.

## Persistencia y compatibilidad

- Clave de guardado: `mesero30save`.
- `saveVersion:49` se mantiene.
- Nuevas variables se guardan en `state.military` y `state.flags.militaryAccessOpen`.
- Migración aditiva: no se elimina ni renombra estado anterior.

## Archivos

- `index.html`: entrada principal 3.22.
- `El_Mesero_del_Fin_del_Mundo_3.22_Ejercito_Salvacion.html`: copia versionada.
- `Coordenadas_Maestro_El_Mesero_3.21.csv`: filas adicionales de los nuevos elementos.
- Documento Maestro, Atlas, Plano y Guion de Continuidad: addendas 3.22.
- `REPORTE_QA_3.22_Plan.txt`: validaciones y pendientes.

## Validación y límites

Aprobado:
- Compilación estática del JavaScript inline.
- Verificación estática de funciones, bandera de acceso y migración.
- Conservación de las coordenadas originales.
- Conservación de la clave y versión del guardado.

Pendiente:
- Recorrido automatizado de la progresión completa.
- Prueba automatizada de combate y balance.
- Guardado/carga real desde una partida 3.21.
- Inspección visual manual en navegador.
- Prueba en móvil físico.
- Interiores militares, escenas de Ferreyra y Borda y decisiones completas del Acto V.

Esta entrega es una primera implementación jugable; no certifica aún el Acto IV completo.
