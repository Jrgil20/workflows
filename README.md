# Workflows Reutilizables para GitHub Actions

Colección de workflows reutilizables para GitHub Actions que pueden ser utilizados en múltiples repositorios. Esta colección está diseñada para estandarizar procesos comunes de CI/CD y validación de código a través de varios proyectos.

## Índice de Contenidos

- [Introducción](#introducción)
- [Cómo usar los Workflows Reutilizables](#cómo-usar-los-workflows-reutilizables)
- [Workflows Disponibles](#workflows-disponibles)
  - [Validación de Conventional Commits](#validación-de-conventional-commits)
- [Contribuir](#contribuir)
- [Licencia](#licencia)

## Introducción

Este repositorio contiene workflows reutilizables de GitHub Actions que implementan buenas prácticas para:

- Validación de formato de commits
- (Espacio reservado para futuros workflows como: pruebas automatizadas, despliegues, análisis de calidad, etc.)

Estos workflows están diseñados para ser:
- **Fáciles de integrar** en proyectos existentes
- **Configurables** según las necesidades específicas de cada proyecto
- **Mantenibles** con actualizaciones centralizadas que se propagan a todos los repositorios que los utilizan

## Cómo usar los Workflows Reutilizables

Para utilizar cualquier workflow de este repositorio en tu propio proyecto:

1. Crea un archivo YAML en el directorio `.github/workflows/` de tu repositorio
2. Referencia el workflow reutilizable con la sintaxis `uses: usuario/workflows/.github/workflows/nombre-del-workflow.yml@version`
3. Proporciona los parámetros requeridos y opcionales según la documentación específica de cada workflow

Ejemplo básico:

```yaml
name: Mi Workflow

on:
  push:
    branches: [ main ]

jobs:
  mi-job:
    uses: usuario/workflows/.github/workflows/workflow-ejemplo.yml@main
    with:
      parametro1: valor1
    secrets: inherit
```

## Workflows Disponibles

### Validación de Conventional Commits

Este workflow valida que los mensajes de commit en las Pull Requests cumplan con el formato de [Conventional Commits](https://www.conventionalcommits.org/).

**Características principales:**
- Valida mensajes de commit según el estándar de Conventional Commits
- Soporta mensajes en inglés y español
- Configurable para diferentes necesidades de proyecto

[**Ver documentación completa**](./docs/conventional-commits-validation.md)

<!-- 
### Futuro Workflow: Análisis de Calidad de Código

Este workflow ejecutará herramientas de análisis de calidad de código como SonarQube o ESLint.

[**Ver documentación completa**](./docs/code-quality-analysis.md)
-->

## Contribuir

Si deseas contribuir a esta colección de workflows, por favor:

1. Haz fork del repositorio
2. Crea una rama para tu contribución
3. Añade o modifica el workflow siguiendo las mejores prácticas
4. Asegúrate de documentar adecuadamente el workflow:
   - Archivo YAML en `.github/workflows/`
   - Documentación detallada en `docs/nombre-workflow.md`
   - Referencia en este README
5. Envía un pull request con una descripción detallada de los cambios

## Licencia

Este proyecto está licenciado bajo [INSERTAR TIPO DE LICENCIA]. Ver el archivo [LICENSE](LICENSE) para más detalles.