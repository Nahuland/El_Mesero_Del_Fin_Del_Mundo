# Catálogo inicial de producción visual — 3.28
## El Mesero del Fin del Mundo

**Fuente técnica:** `index.html` de la rama `release/3.27-pulido-tecnico`, SHA `8d10cafa4f9c63876cc3ef4ac3de7644a91e7d69`.  
**Naturaleza:** inventario inicial derivado del código actual; no es una lista cerrada del canon ni una aprobación de estilo.

## Estados utilizados
- **PLACEHOLDER ACTUAL — REEMPLAZAR:** hay representación funcional, pero no arte final.
- **PENDIENTE — PRODUCIR:** no se identificó recurso visual final.
- **PENDIENTE — AUDITAR:** requiere revisar el conjunto de escenas y documentos antes de definir cantidad/variantes.
- **VALIDADO:** solo cuando el usuario aprueba el resultado y se comprueba integrado en el juego. En esta primera pasada no se marca ningún arte como VALIDADO.

## 1. Protagonista y personajes

| Elemento | Representación actual observada | Estado visual | Trabajo requerido |
|---|---|---|---|
| S-07 / Siete | Silueta geométrica dibujada con rectángulos | PLACEHOLDER ACTUAL — REEMPLAZAR | Diseño reconocible, proporciones, materiales, rostro/visor, silueta, ocho direcciones, idle, caminar, interactuar, daño y combate |
| Desertor | Emoji de robot | PLACEHOLDER ACTUAL — REEMPLAZAR | Diseño individual, ropa/piezas, postura, retrato y animaciones |
| Superviviente | Emoji humano | PLACEHOLDER ACTUAL — REEMPLAZAR | Diseño individual, retrato, estados y animación |
| Robot refugiado | Emoji de robot | PLACEHOLDER ACTUAL — REEMPLAZAR | Variante visual diferenciada y animaciones |
| Mara, Tomás y doctora Ibarra | Representación emoji en el render actual | PLACEHOLDER ACTUAL — REEMPLAZAR | Tres diseños distinguibles, retratos/expresiones y animaciones |
| Elba Roldán, Nerea Vidal, Ramiro Funes, Celina Borda y Damián Ferreyra | Personajes/interacciones presentes en la lógica; visual final no acreditado | PENDIENTE — PRODUCIR | Fichas visuales fieles a sus roles aprobados, siluetas, retratos y estados |
| Richars Octavio | Jefe y personaje de combate implementado en lógica | PENDIENTE — PRODUCIR | Modelo/sprite de jefe, fases, ataques telegrafiados, daño y derrota |
| Mira, Iván, Lía, Teo, Noa, Dante, Kai y Eva | Contactos del Acto V; arte final no acreditado | PENDIENTE — PRODUCIR | Diseños individuales, retratos, expresiones y animaciones |
| Sacerdote del Eclipse | Personaje/encuentro de R5 | PENDIENTE — PRODUCIR | Diseño visual que no invente símbolos/doctrinas fuera del canon aprobado |
| NPC de relleno y población ambiental | No existe un catálogo visual completo confirmado | PENDIENTE — AUDITAR | Determinar cantidades por región, variedad, rutinas y estados sin añadir biografías no aprobadas |

## 2. Enemigos y jefes

| Elemento | Estado visual | Trabajo requerido |
|---|---|---|
| Infectados comunes | PLACEHOLDER ACTUAL — REEMPLAZAR | Siluetas/variantes, locomoción, alerta, ataque, daño y neutralización |
| El Coro / núcleo del Nido | PLACEHOLDER ACTUAL — REEMPLAZAR | Forma legible, estados de pulso, ataque, vulnerabilidad y resolución |
| Capataz | PLACEHOLDER ACTUAL — REEMPLAZAR | Diseño de jefe, piezas mecánicas, fases y feedback de combate |
| Ramiro Funes / encuentro de seguridad | PENDIENTE — PRODUCIR | Diseño de personaje/combate según implementación y canon |
| Richars Octavio | PENDIENTE — PRODUCIR | Jefe final del tramo militar, tres fases visualmente diferenciadas |
| Otros enemigos y variantes | PENDIENTE — AUDITAR | Inventario contra el Guion Maestro, atlas y HTML; no inventar tipos nuevos |

## 3. Escenarios, texturas y utilería

| Familia | Estado actual | Trabajo requerido |
|---|---|---|
| Terrenos R1–R5 | PLACEHOLDER ACTUAL — REEMPLAZAR | Texturas/materiales por bioma, transiciones y variaciones sin costuras |
| Caminos, barro, ruinas, costa y agua | PLACEHOLDER ACTUAL — REEMPLAZAR | Materiales, bordes, huellas y lectura topográfica |
| La Estrella exterior e interior | PLACEHOLDER ACTUAL — REEMPLAZAR | Escenario completo, mobiliario, barra, mesas, cocina, objetos de memoria y luz |
| Calle Oxidada / territorio de máquinas | PLACEHOLDER ACTUAL — REEMPLAZAR | Metal, óxido, chatarra, maquinaria, cercas, señalización y props |
| Ciudad Enferma | PLACEHOLDER ACTUAL — REEMPLAZAR | Viviendas, parque, Metro, Centro Comercial, Hospital, Cementerio y Nido |
| Territorio del Culto | PLACEHOLDER ACTUAL — REEMPLAZAR | Aldea, bosque, mercado, Catacumbas, Templo y Santuario; respetar reserva narrativa |
| Territorio Militar | PLACEHOLDER ACTUAL — REEMPLAZAR | Puerto, trincheras, hangar, muelle, puente, aeródromo y fortaleza |
| Interiores instanciados | PLACEHOLDER ACTUAL — REEMPLAZAR | Paredes, suelos, techos/capas, mobiliario, iluminación y props únicos por interior |
| Props interactivos y coleccionables | PLACEHOLDER ACTUAL — REEMPLAZAR | Campanilla, fotografía, terminales, puertas, consolas, registros, herramientas, cajas, bancos, braseros y objetos del mundo |
| Props ambientales y puntos de interés | PLACEHOLDER ACTUAL — REEMPLAZAR | Árboles, troncos, ruinas, puentes, vehículos, antenas, contenedores, refugios y señalización |

## 4. Animación, efectos y ambientación

- **PENDIENTE — PRODUCIR:** ciclo de movimiento del protagonista y personajes.
- **PENDIENTE — PRODUCIR:** animaciones de interacción, gestos, daño, caída, ataques, fases y muerte/derrota de enemigos.
- **PENDIENTE — PRODUCIR:** animación ambiental de agua, vegetación, fuego, luces, polvo, humo, lluvia y partículas según región.
- **PENDIENTE — PRODUCIR:** iluminación por hora/ambiente y efectos de zonas interiores.
- **PENDIENTE — AUDITAR:** feedback visual de decisiones, estados de facción, objetos usados y cambios persistentes del mundo.

## 5. Interfaz

La estructura HTML/CSS actual es funcional, pero no se considera arte final. Deben diseñarse y validar:
- Pantalla de título, comenzar, continuar y confirmaciones.
- HUD, integridad, recursos, amenazas y avisos.
- Diálogos, retratos, expresiones, elecciones y transiciones.
- Diario, inventario, mapa/ayudas si forman parte del diseño aprobado.
- Pausa, configuración, accesibilidad y controles móviles.
- Pantallas de carga y estados de progreso cuando la estrategia técnica las requiera.

## 6. Reglas para producir los assets
1. Antes de dibujar/modelar en lote, aprobar una guía de estilo y una ficha técnica de escala, perspectiva, pivote, resolución, formatos, animaciones y nomenclatura.
2. Diseñar primero a Siete y La Estrella como vertical slice. El protagonista debe ser reconocible en el mapa y en los diálogos.
3. Priorizar siluetas y legibilidad en la vista isométrica 2.5D; no imponer 3D real si sprites o animación 2D cumplen mejor el diseño y rendimiento.
4. Los personajes principales deben tener identidad visual propia; los NPC de relleno pueden compartir bases/variantes solo si no se confunden con personajes importantes.
5. Todo asset debe indicar región, escena, estado, dependencias, variantes, animaciones y validación.
6. El arte puede reforzar el canon, pero no crear hechos o relaciones nuevas.
7. No se marca un asset como terminado por existir en un archivo: debe estar integrado, visible, probado y aprobado.

## 7. Próxima tanda recomendada
**Primero:** guía de dirección de arte + ficha técnica de assets.  
**Segundo:** Siete (protagonista) + set modular de La Estrella + un NPC existente.  
**Tercero:** integrar un primer atlas/paquete de recursos con carga y fallback.  
**Cuarto:** probar una escena real de La Estrella en escritorio y móvil, medir y ajustar antes de producir el resto.
