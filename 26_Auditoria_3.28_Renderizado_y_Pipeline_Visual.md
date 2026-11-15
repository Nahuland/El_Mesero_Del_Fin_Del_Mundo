# Auditoría inicial 3.28 — renderizado y pipeline visual
## El Mesero del Fin del Mundo

**Base inspeccionada:** `index.html` de la rama `release/3.27-pulido-tecnico`  
**SHA del HTML inspeccionado:** `8d10cafa4f9c63876cc3ef4ac3de7644a91e7d69`  
**Alcance:** inspección estática del código fuente. No es un perfil de rendimiento ni una revisión visual manual.

## Hallazgos confirmados

### 1. Renderizado actual
- El juego utiliza un único elemento `<canvas>` con contexto `2d`.
- El escenario se dibuja proceduralmente mediante primitivas Canvas: polígonos, rectángulos, líneas, elipses, texto y bloques de color.
- No se encontraron llamadas `drawImage()` ni instancias `new Image()` en el HTML inspeccionado.
- No se encontraron manifiestos de recursos, atlas de texturas, precargas ni gestor de assets.
- El terreno utiliza diamantes isométricos con variaciones de color deterministas y patrones alternados; no son texturas de imagen.
- Edificios, interiores, utilería y buena parte de la ambientación se construyen con funciones de dibujo y volúmenes geométricos.
- Los personajes y criaturas visibles se representan en varios casos mediante emojis; el protagonista Siete es una silueta construida con rectángulos y formas simples.
- La interfaz DOM tiene estilo CSS propio, pero todavía corresponde a una presentación funcional, no a un paquete visual final aprobado.

### 2. Bucle y coste potencial
- El bucle usa `requestAnimationFrame` y ejecuta movimiento, búsqueda de interacción y renderizado de forma continua.
- En cada frame, `drawGround()` recorre una ventana aproximada de hasta 54 × 54 celdas alrededor del jugador (un máximo teórico cercano a 2.916 celdas por frame, antes de recortes por límites del mapa).
- En cada render se filtra la colección global de props, se crea una copia, se ordena por profundidad y se dibuja.
- `drawAtmosphere()` calcula y dibuja 18 partículas simples en cada frame.
- El canvas limita el DPR a 2 y redimensiona su buffer con el tamaño CSS.
- Los interiores se activan mediante cambio síncrono de `state.currentInterior`, posición y cámara; se informa mediante un toast. No hay todavía carga de paquetes de recursos ni pantalla de carga.
- El código guarda al ocultar la pestaña y antes de salir, pero no implementa un ciclo explícito de pausa/reanudación de recursos gráficos.

**Importante:** estos puntos identifican trabajo que conviene medir; no demuestran por sí solos que haya caídas de FPS. No se ejecutó un perfilador ni una prueba en dispositivo físico durante esta auditoría.

### 3. Conclusión de producción
La presentación actual es un prototipo visual procedural. Sirve para comprobar geografía, movimiento, colisiones, interacción y progresión, pero no constituye el apartado artístico definitivo. La ausencia de texturas de imagen, sprites/modelos finales y un sistema de recursos confirma que el trabajo visual y el pipeline de carga siguen siendo una fase de producción pendiente.

## Backlog 3.28 — estado inicial

| Tarea | Estado | Criterio para cerrar |
|---|---|---|
| Inventariar funciones de dibujo y capas | IMPLEMENTADA — SIN VALIDAR | Revisión visual de cada región e interior y mapa de dependencias |
| Inventariar entidades y placeholders | EN CURSO | Catálogo completo de protagonista, elenco, NPC, enemigos, jefes y props |
| Definir dirección de arte | PENDIENTE | Guía visual aprobada antes de producir lotes de assets |
| Definir especificaciones de sprites/texturas | PENDIENTE | Tamaños, escala, perspectiva, pivotes, animaciones, formatos y nomenclatura documentados |
| Diseñar manifiesto/gestor de recursos | PENDIENTE | Carga, errores, caché, precarga, liberación y compatibilidad demostrados |
| Definir estrategia de carga por zona | PENDIENTE | Decisión medida entre transición continua y pantalla de carga por tipo de zona |
| Medir rendimiento base | PENDIENTE | FPS, frame time, memoria y tiempo de entrada en escenas representativas |
| Producir vertical slice visual de La Estrella | BLOQUEADA | Depende de aprobar dirección de arte y especificaciones técnicas |

## Próximo orden recomendado

1. Completar el inventario de entidades y placeholders a partir del código y los documentos de mundo.
2. Aprobar una guía de dirección de arte que mantenga la identidad del proyecto y no introduzca canon nuevo.
3. Especificar assets de Siete y La Estrella como primer lote de prueba.
4. Diseñar e implementar el gestor de recursos y su integración con las escenas, con métricas de carga.
5. Producir el vertical slice visual de La Estrella y medirlo en escritorio y móvil.
6. Solo después extender el pipeline y la producción artística al resto del mundo.

## Restricciones
- No alterar el Guion Maestro Fase 4, diálogos, nombres, decisiones, coordenadas ni desenlaces.
- No sustituir la arquitectura jugable completa ni romper `mesero30save`.
- No introducir pantallas de carga en todas las puertas por defecto: justificar cada una con volumen de recursos, medición y experiencia de usuario.
- No afirmar rendimiento validado hasta medirlo en navegadores y dispositivos objetivo.
- Mantener separado el estado IMPLEMENTADA del estado VALIDADA.
