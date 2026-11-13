# Versión 3.26 — Los ocho desenlaces

## Base y compatibilidad
Continuación de 3.25 sobre el HTML principal. Se conservan motor, mapa, interiores, diálogos, combate y guardado `mesero30save` con `saveVersion:49`. Los campos nuevos se agregan dentro de `state.act5` y `state.city`; las partidas anteriores reciben valores por defecto mediante la inicialización existente.

## Acceso a los desenlaces
Después de completar el expediente del Acto IV y registrar las ocho posturas del Acto V, la consola Siesta muestra los desenlaces habilitados por la partida. Se registra un solo desenlace definitivo por guardado; volver a la consola permite consultar el desenlace ya elegido, no reemplazarlo.

## Condiciones implementadas

1. **El Restaurante de Estrella:** Siesta desconectada; al menos cuatro contactos acompañan o negocian; dos resoluciones pacíficas entre Capataz escuchado, Nido desincronizado y reconciliación de la Secta; y al menos dos misiones personales entre seguimientos de Mara, Tomás, Ibarra, ayuda clínica y ayuda a Elba.
2. **El Mesero Solitario:** Siesta desconectada sin cumplir los requisitos comunitarios del Restaurante.
3. **El Archivo del Eco:** Siesta preservada en solo lectura, advertencia pública de la señal y al menos seis registros entre archivos de fábrica, evidencias militares, hospital y transmisiones.
4. **El Mesero de Hierro:** Siesta bajo acceso compartido y elección explícita de convertir ese acceso en una orden permanente para imponer la paz.
5. **Siesta Voluntaria:** opción personal disponible al concluir el consejo. El epílogo distingue si hay cuatro o más contactos que permanecen junto a Siete.
6. **La Mesa Larga:** Siesta desconectada; Capataz escuchado; Nido desincronizado; reconciliación de la Secta; lanchas saboteadas; Funes neutralizado; seis o más contactos no rechazados y apoyo/negociación de Noa, Dante, Kai y Eva.
7. **Un Amanecer sin Fiebre:** registros y muestra del Hospital, evidencia epidemiológica, suministros enviados al Hospital, apoyo clínico, Nido desincronizado, Lía acompañada y antídoto conservado. Si se apoya la petición de Teo, el frasco se destina a su intento de salvar al Carnicero y deja de contar para este final.
8. **La Señal se Apaga:** registro de Siesta y de la señal externa, manifiesto y discrepancia del Vuelo 9, orden de ocultamiento, libro de operaciones del Hangar y archivo de mando. Al elegirlo, la partida registra la desactivación del enlace externo.

## Contenido nuevo
- Se añade el frasco de antídoto como punto interactivo del Hospital. Requiere haber recuperado el archivo epidemiológico y la muestra para comprobar su estabilidad.
- La elección de apoyar a Teo reserva o consume el antídoto para su petición; no se permite contabilizar el mismo frasco para la red médica.
- La consola muestra por separado desenlaces disponibles y requisitos todavía pendientes.
- El resultado final y la desactivación de la señal se guardan en `state.act5` y `state.flags`.

## Límites detectados en la base 3.25
- **La Mesa Larga queda bloqueada** hasta que el Acto III implemente y registre `state.flags.cultResolution === 'reconciled'`. El HTML 3.25 contiene geografía e interiores ambientales de la Secta, pero no la resolución del Sacerdote del Eclipse; no se inventa una reconciliación ni se concede este final por explorar coleccionables.
- La versión registra la asignación del antídoto a la petición de Teo, pero todavía no contiene la escena jugable del tratamiento del Carnicero.
- La desactivación de la señal se registra como acción final de consola a partir de las pruebas existentes; no se añadió un nuevo mapa físico del transmisor remoto.

## Validación realizada
- Compilación sintáctica de los scripts inline: aprobada.
- Aserciones estáticas de los ocho identificadores, consola, antídoto, guardado y compatibilidad: aprobadas.
- Simulación aislada de las ocho condiciones: cada condición devuelve disponible al suministrarle sus requisitos; La Mesa Larga requiere además la bandera explícita de reconciliación de la Secta.
- HTML principal y HTML versionado sincronizados (mismo SHA de contenido).

## Pendiente de QA
No se declara recorrido manual en navegador, prueba real de guardado/carga, inspección visual, prueba móvil física ni despliegue de GitHub Pages. La ruta del Acto III y la escena del Carnicero deben completarse para cerrar todos los desenlaces en una partida normal.
