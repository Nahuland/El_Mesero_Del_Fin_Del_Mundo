# El Mesero del Fin del Mundo

Repositorio del juego y su documentación.

## Publicación web

El sitio se publica automáticamente en GitHub Pages mediante el flujo `.github/workflows/pages.yml`.

**Archivo de entrada requerido:** `index.html` en la raíz del repositorio.

Para publicar una versión:
1. Copiar el HTML principal del juego a la raíz y nombrarlo `index.html`.
2. Incluir junto a él cualquier carpeta de recursos que el juego necesite (por ejemplo, `assets/`).
3. Hacer commit en la rama `main`. El flujo de GitHub Actions realizará la publicación.

La primera vez, comprobar en **Settings → Pages** que la fuente de publicación esté configurada como **GitHub Actions**.

## Versión de trabajo

La versión de referencia preparada localmente es **3.19**. El informe de QA disponible indica validaciones estáticas aprobadas; no se registró una prueba manual/visual en navegador.
