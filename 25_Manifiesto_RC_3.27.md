# Manifiesto de candidato — 3.27 Pulido Técnico RC

**Rama:** `release/3.27-pulido-tecnico`  
**Estado estimado:** candidato funcional cercano al 95 % del alcance previsto; no es un cierre de QA manual.  
**Base:** `main` permanece intacta. No se creó PR ni se hizo merge.

## HTML de referencia

- Principal: `index.html`
- Copia numerada: `El_Mesero_del_Fin_Del_Mundo_3.27_Pulido_Tecnico_RC.html`
- SHA de contenido de ambos: `8d10cafa4f9c63876cc3ef4ac3de7644a91e7d69`
- Verificación: ambos archivos tienen el mismo SHA y 211.065 caracteres.

## QA automatizado

<https://github.com/Nahuland/El_Mesero_Del_Fin_Del_Mundo/actions/runs/43744324561>

Aprobado:
- Sintaxis JavaScript y carga inicial.
- Estructura de props, coordenadas, referencias y retornos de los 11 interiores.
- Cierre 13/13 del Acto IV, bloqueo si falta evidencia y opcionalidad de Elba/Funes.
- Modificadores tácticos y nueve patrones de Richars.
- Arco de Noa y Dante, registro de doctrina, prueba del reflector, braseros Sol → Luna y rendición limitada.
- Condiciones de los ocho desenlaces, incluidos bloqueos de finales 6 y 7.
- Escena de tratamiento del Carnicero con resultado de lucidez temporal.
- Guardado en `localStorage`, recarga y recuperación con Continuar de las nuevas banderas.
- Inicio de partida en escritorio y viewport táctil 390×844; ocho direcciones y objetivos de al menos 44×44 px.
- Sin excepciones JavaScript ni IDs DOM duplicados en la carga comprobada.

## Archivos de seguimiento

- `12_Plan_Produccion_PostMapa.md`
- `18_Matriz_Regresion_Manual_3.27.md`
- `21_Auditoria_3.27_Acto_IV_Progresion_y_Combate.md`
- `22_Implementacion_3.27_Combate_Telegrafico_Richars.md`
- `23_Auditoria_3.27_Finales_6_y_7.md`
- `24_Implementacion_3.27_Finales_6_y_7.md`
- `REPORTE_QA_3.27_Pulido_Tecnico.md`
- `.github/workflows/qa-3.27.yml`

## Paquete candidato

El workflow de QA genera, tras aprobar todas las pruebas, un ZIP de la rama con HTML principal y numerado, informes y matriz de regresión. Se excluye el archivo legado `index.html.html` para evitar distribuir una copia antigua como entrada del juego.

## Límites conocidos y siguiente etapa

- Los 42 casos anteriores y los 11 casos H de la matriz manual siguen `NO EJECUTADO`; la automatización simula estados e interacciones, no recorre físicamente toda la aventura.
- La prueba de persistencia cubre las nuevas banderas con `saveVersion:50`; aún falta una regresión manual con guardados históricos de distintas versiones.
- El viewport móvil es Chromium emulado, no un teléfono físico.
- Falta revisar rendimiento y composición visual en dispositivos reales.
- No se inventa el paradero del hijo de Noa: la escena deja asentada su decisión de buscarlo.
- El tratamiento del Carnicero ofrece lucidez temporal, no cura ni recuperación garantizada.
- La rendición del Sacerdote es limitada: no borra el daño ni fuerza a todos los fieles a reconciliarse.
- El empaquetado ZIP completo y la publicación de Pages pertenecen a la etapa 3.28 y quedan pendientes.

**Criterio de entrega:** este RC es apto para iniciar una revisión de juego completa cuando se decida, pero no se declara 100 % terminado ni se publica en `main`.
