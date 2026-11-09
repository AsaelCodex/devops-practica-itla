# Práctica 3: Pipeline CI/CD con GitHub Actions

![CI/CD Pipeline](https://github.com/<TU_USUARIO>/<TU_REPO>/actions/workflows/ci.yml/badge.svg)

## Descripción del Proyecto
Aplicación web desarrollada con Node.js y Express que incluye pruebas automatizadas con Jest, contenedorización con Docker y un pipeline de Integración y Despliegue Continuo (CI/CD) mediante GitHub Actions hacia GitHub Pages.

## Requisitos e Instalación Local
1. Clonar el repositorio:
   `git clone https://github.com/<TU_USUARIO>/<TU_REPO>.git`
2. Instalar dependencias:
   `npm install`
3. Ejecutar servidor local:
   `npm start`
4. Ejecutar pruebas y reporte de cobertura:
   `npm test`

## Documentación del Pipeline CI/CD
El archivo `.github/workflows/ci.yml` se dispara en cada `push` o `pull_request` hacia la rama `main` y consta de dos etapas (jobs):
1. **build-and-test**: Descarga el código, configura Node.js 20, instala las dependencias (`npm install`), ejecuta las pruebas unitarias y de integración generando el reporte de cobertura (`npm test`), y empaqueta los archivos estáticos de `public/` junto con el reporte de cobertura como artefacto.
2. **deploy**: Depende de que `build-and-test` finalice con éxito (`needs: build-and-test`). Toma el artefacto generado y lo publica automáticamente en GitHub Pages usando `actions/deploy-pages@v4`.

## Instrucciones de Despliegue
1. En el repositorio de GitHub, ir a **Settings > Pages**.
2. Cambiar **Source** a **GitHub Actions**.
3. Realizar un `push` a la rama `main`. El despliegue se ejecutará automáticamente y la URL pública aparecerá en la pestaña **Actions** y en **Settings > Pages**.

## Guía de Contribución
1. Crea un fork del repositorio o una rama descriptiva (`git checkout -b feature/nueva-funcionalidad`).
2. Agrega tus cambios en `src/` y sus respectivas pruebas en `tests/app.test.js`.
3. Verifica que todas las pruebas pasen localmente con `npm test`.
4. Haz commit siguiendo buenas prácticas (`git commit -m "feat: descripción del cambio"`) y abre un Pull Request hacia `main`.

## Informe de Implementación
- **Cambios realizados**: Se configuraron pruebas unitarias y de integración en `tests/app.test.js` con cobertura de código mediante Jest, y se extendió el workflow `.github/workflows/ci.yml` para automatizar el despliegue continuo en GitHub Pages.
- **Retos y soluciones**: Configuración de permisos (`pages: write`, `id-token: write`) en el workflow de GitHub Actions para permitir el despliegue automático sin tokens manuales.
- **URL de despliegue**: `https://<TU_USUARIO>.github.io/<TU_REPO>/`