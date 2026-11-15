# Auditoría 3.27 — Desenlaces 6 y 7

**Rama:** `release/3.27-pulido-tecnico`  
**Archivos inspeccionados:** `index.html`, `17_Guion_Maestro_Fase4_1_Continuidad.md`, `12_Plan_Produccion_PostMapa.md`  
**Método:** contraste estático del código con el guion maestro y el plan de producción.  
**Estado:** auditoría estática; no equivale a una partida manual.

## Resultado

### Final 6 — La Mesa Larga

El cálculo de condiciones ya exige:
- Siesta desconectada.
- Resolución pacífica del Capataz y del conflicto de Ciudad Enferma.
- `state.flags.cultResolution === 'reconciled'`.
- Sabotaje de lanchas y neutralización de Funes.
- Seis o más contactos aliados, con apoyo o negociación de Noa, Dante, Kai y Eva.

**Bloqueo confirmado:** `cultResolution` solo se consulta en `finaleMetrics()`; no existe en el HTML una escena, función o interacción que la establezca. Tampoco están implementados el Sacerdote del Eclipse, la prueba del reflector ni el orden de braseros Sol → Luna descritos por el guion.

**Criterio de implementación:** incorporar la secuencia del Santuario respetando el guion: confianza y prueba del reflector como condiciones para exponer el engaño; braseros en orden Sol antes que Luna; la rendición limitada del Sacerdote no borra el daño ni garantiza que toda la Secta abandone la doctrina. No convertir a todos los fieles en responsables equivalentes ni vincular esta resolución con Richars.

### Final 7 — Un Amanecer sin Fiebre

El código ya contiene:
- Archivo epidemiológico y muestra del Hospital.
- Elección de suministros al Hospital.
- Ayuda clínica de Ibarra.
- Recuperación del antídoto.
- Decisión de Teo de reservarlo para el Carnicero.
- Condiciones para el final médico, incluida la decisión de Lía y que Teo no haya elegido reservar el frasco para el Carnicero.

**Bloqueo confirmado:** cuando el antídoto se destina al Carnicero, el propio diálogo indica que no existe escena jugable de tratamiento. No hay una entidad o interacción jugable del Carnicero ni un resultado persistente que represente el intento. La alternativa médica del Hospital sí tiene condiciones, pero debe conservar sus límites.

**Criterio de implementación:** añadir la escena de reconocimiento/tratamiento vinculada a Teo y al antídoto, sin prometer cura global. El guion define al Carnicero como antiguo cocinero de hospital, vincula su canción con Teo y la Fiebre Gris, y permite una resolución de reconocimiento si se reúnen condiciones narrativas. El resultado debe expresar posibilidad de recuperación y riesgo, no una curación garantizada.

## Restricciones de continuidad

- Mantener los ocho nombres de desenlaces.
- No cambiar la condición de Richars: no se rinde, no se redime.
- No alterar el significado de las decisiones de Siesta.
- No convertir el tratamiento del Carnicero en cura global ni eliminar los costes de recursos.
- Preservar `mesero30save` y `saveVersion:50`, salvo que una nueva bandera persistente requiera una migración justificada.
- Añadir pruebas automáticas de disponibilidad/bloqueo de ambos finales y persistencia de las nuevas decisiones.
- No marcar la partida manual como aprobada.

## Referencias internas

- `17_Guion_Maestro_Fase4_1_Continuidad.md`: Actos II y III, y definiciones de los finales 6 y 7.
- `12_Plan_Produccion_PostMapa.md`: pendientes registrados para los finales 6 y 7.
- `index.html`: `finaleMetrics()`, `chooseEnding()`, `act5Choose()`, interacciones del Hospital y del antídoto.

**Conclusión:** los dos finales existen en el catálogo y tienen parte de sus condiciones preparadas, pero sus escenas de resolución están incompletas. La siguiente implementación debe cerrar primero la secuencia de la Secta y la escena del Carnicero, con persistencia y pruebas de regresión.
