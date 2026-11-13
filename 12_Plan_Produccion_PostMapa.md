# Plan de producción posterior a la geografía — El Mesero del Fin del Mundo

## Estado de partida
- Versión de referencia en el repositorio: 3.26 — ocho desenlaces implementados con dos bloqueos narrativos heredados.
- Versión 3.25 implementada: deliberación persistente de los ocho contactos.
- R1–R5 existen como mapa explorable con distintos niveles de desarrollo narrativo.
- R4 conserva la geografía de 3.21 y la primera capa narrativa 3.22.
- Richars Octavio es el jefe final obligatorio del tramo militar: malvado e irredimible; no hay rendición, alianza, clemencia ni redención.
- `mesero30save` y `saveVersion:49` se conservan.

## Qué existe para seguir implementando o mejorar

### Sistemas ya disponibles
1. Movimiento isométrico 2.5D, teclado y controles táctiles.
2. Mapa regional de 420×300, subzonas, terreno, estructuras y colisiones.
3. Interacción contextual, diálogos y elecciones.
4. Interiores instanciados con entrada, salida y retorno a la coordenada exterior.
5. Guardado/carga local con restauración de posición e interior activo.
6. Diario/HUD y persistencia de decisiones.
7. Combate por turnos para Capataz, Coro, Funes y Richars.
8. Inventario de chatarra, reparación y recursos consumibles.
9. Progresión narrativa de La Estrella, máquinas, Ciudad Enferma y R5 ambiental.
10. Evidencias, testimonios y consecuencias parciales del Ejército de Salvación.

### Contenido que ya está implementado
- R4 exterior, Puerto, Muelle, Trincheras, Control del puente, Cuartel, Hangar, Aeródromo, Fortaleza y Puesto de radio.
- Elba Roldán, Nerea Vidal, Ramiro Funes y Richars Octavio.
- Cadena de evidencias del Vuelo 9, evacuaciones y ocultamiento.
- Sabotaje opcional de lanchas y jefe de tres fases.
- Interiores de Hangar y Fortaleza, Celina Borda, Damián Ferreyra, libro de operaciones y archivo de mando.
- Tres tratamientos iniciales persistentes para el núcleo de Siesta.

## Hoja de ruta recomendada

### 3.24 — Cierre jugable del Acto IV
- Recorrer y corregir la ruta completa Puerto → Trincheras → Hangar → Muelle → Puente → Aeródromo → Fortaleza.
- Dar continuidad a los testimonios de Elba, Nerea, Celina y Damián sin ampliar sus conocimientos más allá de lo aprobado.
- Integrar evidencia de evacuación, represión, Vuelo 9, ocultamiento y recetario en un tablero de pruebas legible.
- Revisar la secuencia de acceso al jefe, estados de facción y consecuencias de sabotaje/Funes.
- Ajustar combate de Richars: fases, patrones, apoyo artillado según preparación y opciones de reparación; debe seguir siendo obligatorio y ganable.
- Pruebas de progresión, guardado/carga y regresión.

### 3.25 — Acto V: mesa de comunidades y consecuencias — IMPLEMENTADO
- Reunión secuencial de Mira, Iván, Lía, Teo, Noa, Dante, Kai y Eva en la mesa de la Fortaleza.
- Cada contacto presenta su confesión y petición del guion maestro.
- Tres posturas por contacto: acompañar, negociar condiciones o rechazar.
- Registro explícito y persistente por contacto; reanudación desde el primero pendiente.
- El consejo completado deja la consola preparada, sin seleccionar todavía un final.
- La conexión detallada de las banderas con condiciones y epílogos queda para 3.26.

**QA 3.25:** compilación y simulación aislada 8/8 aprobadas. Pruebas manuales, visuales, guardado/carga real y móvil pendientes.

### 3.26 — Ocho finales y epílogos — IMPLEMENTADO CON BLOQUEOS NARRATIVOS
- Consola final conectada a la deliberación 8/8 y a la decisión técnica previa de Siesta.
- Ocho desenlaces, condiciones explícitas, epílogos y persistencia de una elección definitiva.
- Final 1: cuatro vínculos, dos resoluciones pacíficas y dos misiones personales.
- Final 2: Siesta desconectada sin cumplir el umbral comunitario.
- Final 3: copia de solo lectura, advertencia pública y seis o más registros.
- Final 4: acceso compartido y elección de imponer paz mediante Siesta.
- Final 5: apagado voluntario con epílogo variable según los vínculos.
- Final 6: requiere resolución reconciliada de la Secta; queda bloqueado porque la base 3.25 aún no implementa la resolución del Sacerdote del Eclipse.
- Final 7: añade el frasco de antídoto al Hospital y conecta la elección de Lía/Teo con la red médica; el tratamiento del Carnicero aún carece de escena jugable.
- Final 8: desactivación del enlace externo desde la consola con registros de fábrica, Vuelo 9 y mando.
- Se conserva `mesero30save` y `saveVersion:49`.

**QA 3.26:** scripts compilados, aserciones estáticas y simulación aislada de las ocho condiciones aprobadas. No se declara QA manual, guardado/carga real, móvil ni despliegue.

### 3.27 — Pulido sistémico y experiencia
- Auditoría de colisiones y rutas de todas las regiones e interiores.
- Balance de combates, recuperación, chatarra y dificultad.
- Revisión de textos, objetivos, diario y consistencia de nombres.
- Mejoras de accesibilidad: tamaño de texto, foco de botones, contraste, controles y pausa.
- Rendimiento del render isométrico y escalado de canvas en móviles.
- Revisión visual en navegador de escritorio y móvil; prueba física en dispositivo real.

### 3.28 — Empaquetado y cierre de producción
- HTML principal y versión numerada sincronizados.
- ZIP completo del repositorio, con integridad verificada.
- QA automático de sintaxis, estructuras, coordenadas, migración, finales y archivos.
- Informe separado de pruebas automatizadas, manuales y físicas.
- Publicación Pages y comprobación de la versión servida.

## Prioridades de mejora transversales
1. **Guardado:** probar migración real de partidas antiguas; mantener escritura aditiva y no reutilizar flags con significado distinto.
2. **Mapa:** crear una matriz de accesos, puertas, interiores y retornos para detectar callejones sin salida.
3. **Narrativa:** separar hechos comprobados, testimonios e inferencias en el diario.
4. **Combate:** añadir telegráficos visuales/patrones y balance sin sustituir la interfaz existente.
5. **Contenido opcional:** que recursos y conversaciones amplíen preparación y comprensión, sin bloquear la historia principal.
6. **Pruebas:** no llamar “completo” a un acto por compilar; exigir recorrido de principio a fin y guardado/carga.

## Criterio de cierre por versión
- Compilación JavaScript.
- Aserciones estáticas de contenido y compatibilidad.
- Prueba de progresión automatizada.
- Entradas/salidas y colisiones de interiores.
- Guardado/carga y migración.
- Recorrido de combate y condiciones de victoria.
- QA visual/manual y móvil reportados por separado.

## Límites de canon
- Richars Octavio no se rinde ni se redime; su derrota es obligatoria.
- El General no creó la Fiebre Gris ni la señal externa.
- El destino de Don Aurelio sigue sin determinarse por el recetario.
- La derrota del General no apaga Siesta ni resuelve la señal.
- Mantener los ocho contactos y ocho finales existentes.
