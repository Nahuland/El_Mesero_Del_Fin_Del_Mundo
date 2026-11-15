# Plan de producción posterior a la geografía — El Mesero del Fin del Mundo

## Estado de partida
- Versión de referencia inicial: 3.26 — ocho desenlaces con dos bloqueos narrativos heredados.
- Estado actualizado en rama 3.27: cierres de los finales 6 y 7 implementados; QA automatizado de progresión 13/13 del Acto IV, condiciones de los ocho finales, secuencia de la Secta y tratamiento del Carnicero aprobado en GitHub Actions.
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
- Final 6: la resolución de la Secta se completó en 3.27 con prueba del reflector, braseros Sol → Luna y rendición limitada del Sacerdote, condicionada por la confianza de Noa y Dante.
- Final 7: la red médica del Hospital conserva su ruta y límites; la alternativa de Teo ahora incluye una escena jugable de tratamiento del Carnicero, con lucidez temporal y sin prometer cura.
- Final 8: desactivación del enlace externo desde la consola con registros de fábrica, Vuelo 9 y mando.
- Se conserva `mesero30save` y `saveVersion:49`.

**QA 3.26:** scripts compilados, aserciones estáticas y simulación aislada de las ocho condiciones aprobadas. En 3.27 se amplió la automatización: Chromium simula las ocho condiciones y las rutas críticas descritas en el informe 24. Se aprobó en Chromium el guardado de las nuevas banderas en localStorage, la recarga y la recuperación mediante Continuar. Siguen pendientes el recorrido manual, la migración de guardados antiguos y la prueba física en móvil.

### 3.27 — Pulido sistémico y experiencia
**Estado parcial:** accesibilidad, perímetros interiores H1, corrección visual de La Estrella, combate telegráfico de Richars, arco jugable de Noa y Dante, registro de doctrina, resolución limitada del Sacerdote y tratamiento del Carnicero implementados. GitHub Actions valida coordenadas y retornos de los 11 interiores, el contrato 13/13 del Acto IV, modificadores tácticos, los ocho finales controles táctiles y arranque de partida en viewport móvil. Siguen pendientes recorrido manual, guardado/carga real, prueba física y perfilado en dispositivo.
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

---

## Revisión de hoja de ruta — producción integral posterior a 3.27

**Corrección de alcance:** 3.27 es una base funcional de sistemas y progresión, no el 95% del videojuego. No equivale a versión final ni a candidata de lanzamiento. El porcentaje global queda sin asignar hasta disponer de inventario y validación de todas las áreas.

### Inventario vivo de producción

| Área | Estado actual | Qué falta para poder cerrarla |
|---|---|---|
| Lógica y sistemas | IMPLEMENTADA EN PARTE / QA AUTOMÁTICO PARCIAL | Recorrido manual, regresiones completas, guardados heredados, balance y cierre de pendientes |
| Contenido y narrativa | IMPLEMENTADA EN PARTE | Auditoría contra Guion Maestro, escenas/interacciones pendientes y comprobación de continuidad en partida completa |
| Dirección de arte | PENDIENTE | Definir y aprobar lenguaje visual, paleta, escala, composición y guía de estilo |
| Texturas y materiales | PENDIENTE | Crear e integrar texturas definitivas de terreno, caminos, edificios, interiores, objetos y superficies |
| Personajes y criaturas | PENDIENTE / PLACEHOLDERS POR AUDITAR | Diseño final de Siete, elenco, NPC de relleno, enemigos, élites y jefes; sprites/modelos, siluetas, estados y animaciones |
| Mapas y ambientación | PARCIAL | Sustituir geometría provisional y completar decoración, vegetación, mobiliario, iluminación, clima y efectos por región/interior |
| Interfaz y experiencia | PARCIAL | Arte final de inicio, menús, HUD, diario, inventario, diálogos, pausa, opciones y accesibilidad |
| Carga y rendimiento | PENDIENTE DE AUDITORÍA | Medición, carga asíncrona, precarga por zona, caché, liberación de recursos, atlas y pantallas de carga justificadas |
| Audio | PENDIENTE DE AUDITORÍA | Inventario y producción/integración de música, ambiente y efectos |
| Pruebas y estabilización | PARCIAL | 53 casos manuales, recorrido integral, inspección visual, dispositivos reales, rendimiento y migración de guardados |

Los estados se actualizarán tarea por tarea. No se marcará como terminado ningún elemento hasta tener evidencia de aceptación.

### Nueva secuencia de trabajo

#### 3.28 — Auditoría técnica y pipeline visual (SIGUIENTE)
- Auditar el HTML 3.27: renderizado, canvas, cámara, capas, dibujo de entidades, placeholders, CSS/UI y puntos de carga de recursos.
- Inventariar qué elementos actuales son geometría provisional, qué recursos ya existen y qué falta producir.
- Medir coste de renderizado y memoria en escenas representativas; no inventar cifras antes de medir.
- Definir guía de dirección de arte y especificaciones de assets compatibles con la vista isométrica 2.5D.
- Diseñar un gestor de recursos con manifiesto, carga asíncrona, precarga, caché y liberación; definir umbrales para pantallas de carga frente a transiciones continuas.
- No alterar canon, coordenadas ni progresión narrativa durante esta fase salvo correcciones aprobadas.
- Entregables: auditoría, inventario de assets, guía técnica/visual inicial, plan de rendimiento y pruebas.

#### 3.29 — Vertical slice visual de La Estrella
- Producir escenario completo del restaurante y su entorno inmediato con materiales definitivos.
- Diseñar y animar visualmente a Siete, al menos un NPC existente y elementos interactivos representativos.
- Completar iluminación, ambientación, efectos, UI y transiciones de esa zona.
- Integrar los recursos mediante el pipeline aprobado y validar rendimiento en escritorio/móvil.
- No expandir a todas las regiones hasta aprobar este estándar visual.

#### 3.30 — Producción de arte por regiones
- Extender el estándar aprobado a R1–R5 y todos los interiores.
- Crear personajes principales, NPC de relleno, enemigos, variantes, jefes y animaciones.
- Completar texturas, props, iluminación, vegetación, partículas y ambientación contextual.
- Mantener un registro de assets por región, escena y estado de validación.

#### 3.31 — Interfaz, audio y pulido de experiencia
- Terminar menús, HUD, diario, inventario, diálogos, pausa, configuración y accesibilidad.
- Integrar música, efectos y ambientes.
- Revisar transiciones, feedback, legibilidad y consistencia audiovisual.

#### 3.32 — Optimización y QA integral
- Optimizar atlas, tamaño y formato de texturas, carga y descarga de recursos, memoria y renderizado.
- Probar pantallas de carga y transiciones con escenarios de mayor complejidad.
- Ejecutar matriz manual completa, revisión visual y pruebas en dispositivos reales.
- Corregir errores y regresiones sin alterar canon.

#### 3.33 — Candidato final y publicación
- Solo iniciar cuando todas las áreas obligatorias estén validadas.
- Empaquetar HTML y recursos, ZIP, checksums y documentación final.
- Verificar publicación y versión servida, únicamente con autorización explícita.

### Regla de descarte de pendientes
Una tarea se quita de la lista activa solo cuando su estado pasa a VALIDADA. Las listas de trabajo deben conservar las tareas PENDIENTES, EN CURSO, IMPLEMENTADAS — SIN VALIDAR y BLOQUEADAS. Cada actualización de versión debe indicar cambios visibles, pruebas realizadas, limitaciones y pendientes restantes.

### Regla de evaluación global
No usar una cifra única como sustituto del inventario. Informar progreso por área y separar implementación lógica, producción visual, optimización y validación. El proyecto no se declarará terminado mientras haya placeholders relevantes, personajes/escenarios sin arte final, sistemas de carga sin validar o pruebas integrales pendientes.

### Auditoría inicial 3.28
- [Auditoría del renderizado y pipeline visual](26_Auditoria_3.28_Renderizado_y_Pipeline_Visual.md)

La inspección estática confirma que el prototipo actual dibuja el mundo con primitivas Canvas y emojis: no utiliza texturas de imagen, spritesheets ni gestor de recursos. El informe separa estos hallazgos de las métricas de rendimiento, que todavía deben medirse.
- [Catálogo inicial de producción visual y placeholders](27_Catalogo_Visual_Assets_3.28.md)

El catálogo separa las representaciones provisionales actuales del arte definitivo pendiente. Ningún recurso visual se considera validado todavía.
