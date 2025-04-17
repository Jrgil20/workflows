# Validación de Conventional Commits

Este workflow valida que los mensajes de commit en las Pull Requests cumplan con el formato de [Conventional Commits](https://www.conventionalcommits.org/).

## Características

- Valida que los mensajes de commit sigan la estructura de Conventional Commits
- Soporta mensajes en inglés y español
- Verifica tipos de commit estándar (feat, fix, docs, etc.)
- Valida que el primer carácter del mensaje esté en minúscula
- Permite configurar la rama objetivo para la validación

## Cómo usar este workflow

1. Crea un archivo `.github/workflows/validate-commits.yml` en tu repositorio con el siguiente contenido:

```yaml
name: Validar Conventional Commits

on:
  pull_request:
    branches: [ main, master, develop ]
    types: [ opened, synchronize, reopened, ready_for_review ]

jobs:
  validate:
    name: Validar Formato de Commits
    if: github.event.pull_request.draft == false
    uses: jrgil20/workflows/.github/workflows/conventional-commits-validation.yml@main
    with:
      language: "es"  # Opciones: "es" o "en" (predeterminado: "en")
      # target-branch: "main"  # Opcional: rama objetivo personalizada
    secrets: inherit
```


## Parámetros disponibles

| Parámetro | Descripción | Requerido | Valor predeterminado |
|-----------|-------------|-----------|---------------------|
| `language` | Idioma para los mensajes de commit (es/en) | No | `en` |
| `target-branch` | Rama objetivo para validar los commits | No | Rama predeterminada del repositorio |

## Tipos de commit validados

- `feat`: Nuevas características
- `fix`: Correcciones de errores
- `docs`: Cambios en documentación
- `style`: Cambios de estilo (formato, espacios en blanco, etc.)
- `refactor`: Refactorizaciones que no agregan características ni corrigen errores
- `perf`: Mejoras de rendimiento
- `test`: Adición o corrección de pruebas
- `build`: Cambios en el sistema de construcción
- `ci`: Cambios en la configuración de CI
- `chore`: Tareas rutinarias y mantenimiento
- `revert`: Revierte un commit anterior

## Ejemplos de Conventional Commits válidos

```
feat: añadir login con autenticación de dos factores
fix: corregir error en el cálculo de impuestos
docs(readme): actualizar instrucciones de instalación
refactor!: cambiar API de procesamiento de pagos
```

## Pruebas

Para probar este workflow en un entorno local:

1. Clona este repositorio
2. Crea un repositorio de prueba
3. Configura el workflow en el repositorio de prueba
4. Crea algunos commits con diferentes formatos
5. Verifica si la acción de validación detecta correctamente los formatos inválidos

Para probar en GitHub:

1. Sube este repositorio a tu cuenta de GitHub
2. Crea un nuevo repositorio que utilice este workflow reutilizable
3. Crea una pull request con commits que sigan y no sigan el formato de Conventional Commits
4. Verifica que la validación funcione como se espera