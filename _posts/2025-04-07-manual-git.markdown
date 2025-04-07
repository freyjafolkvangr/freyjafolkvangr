---
layout: post
title: "Manual de git"
date: 2025-04-07
categories: [manual, git]
---

# Manual de Uso de Comandos Git

Git es un sistema de control de versiones distribuido que permite gestionar proyectos de manera eficiente. A continuación, se describen algunos de los comandos más utilizados:

## Configuración Inicial
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
```

## Crear un Repositorio
```bash
git init
```

## Clonar un Repositorio
```bash
git clone <url-del-repositorio>
```

## Ver el Estado del Repositorio
```bash
git status
```

## Añadir Cambios al Área de Staging
```bash
git add <archivo>
git add .
```

## Confirmar Cambios
```bash
git commit -m "Mensaje del commit"
```

## Ver el Historial de Cambios
```bash
git log
```

## Crear y Cambiar de Rama
```bash
git branch <nombre-rama>
git checkout <nombre-rama>
git switch <nombre-rama>
```

## Fusionar Ramas
```bash
git merge <nombre-rama>
```

## Subir Cambios al Repositorio Remoto
```bash
git push origin <nombre-rama>
```

## Actualizar el Repositorio Local
```bash
git pull
```

## Deshacer Cambios
- Deshacer cambios en el área de staging:
    ```bash
    git reset <archivo>
    ```
- Deshacer el último commit:
    ```bash
    git reset --soft HEAD~1
    ```

## Eliminar Archivos
```bash
git rm <archivo>
```

## Ignorar Archivos
Crear un archivo `.gitignore` y añadir los patrones de archivos a ignorar.

## Ver Cambios en Archivos
```bash
git diff
```

Este manual cubre los comandos básicos para trabajar con Git. Para más información, consulta la [documentación oficial de Git](https://git-scm.com/doc).