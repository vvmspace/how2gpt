---
title: Cómo Especificar una Versión de Hugo para el Despliegue en Netlify
description: Aprende a especificar una versión de Hugo para tu despliegue en Netlify para asegurar la consistencia entre tu entorno local y el entorno de producción.
tags: [Hugo, Netlify, Despliegue, Control de Versiones]
---

# Cómo Especificar una Versión de Hugo para el Despliegue en Netlify

Al desplegar un sitio de Hugo en Netlify, es crucial asegurarte de que la versión de Hugo que usas localmente coincida con la que se utiliza en Netlify. Esta consistencia previene discrepancias entre tu entorno de desarrollo y el entorno de producción, lo que podría llevar a un comportamiento inesperado o fallos en la construcción. Aquí tienes una guía paso a paso sobre cómo especificar una versión de Hugo para tu despliegue en Netlify.

## Paso 1: Determina Tu Versión Local de Hugo

Antes de configurar Netlify, necesitas saber qué versión de Hugo estás utilizando localmente. Esto asegura que la misma versión se use durante el proceso de construcción de Netlify. Puedes averiguar tu versión de Hugo ejecutando el siguiente comando en tu terminal:

```bash
hugo version
```

Este comando mostrará la versión de Hugo que tienes instalada, como por ejemplo `Hugo Static Site Generator v0.80.0/extended darwin/amd64 BuildDate: unknown`.

## Paso 2: Configura Tu Archivo `netlify.toml`

El archivo `netlify.toml` se utiliza para configurar la configuración de construcción de Netlify. Si aún no tienes un archivo `netlify.toml` en el directorio raíz de tu proyecto, debes crear uno. Aquí te mostramos cómo puedes especificar la versión de Hugo:

1. **Abre tu editor de texto** y crea un nuevo archivo llamado `netlify.toml` en la raíz de tu proyecto.

2. **Agrega las siguientes líneas** al archivo `netlify.toml`, reemplazando `0.80.0` con el número de versión que obtuviste de tu entorno local:

    ```toml
    [build]
      publish = "public"
      command = "hugo"

    [context.production.environment]
      HUGO_VERSION = "0.80.0"
    ```

    Esta configuración hace lo siguiente:
    - Establece el directorio en el que se publicará tu sitio (`public`).
    - Especifica el comando de construcción (`hugo`).
    - Establece la versión de Hugo para el entorno de producción.

3. **Guarda** el archivo.

## Paso 3: Sube los Cambios a Tu Repositorio

Después de haber configurado el archivo `netlify.toml`, necesitas subir los cambios a tu repositorio de Git. Utiliza los siguientes comandos de Git:

```bash
git add netlify.toml
git commit -m "Especificar versión de Hugo para la construcción en Netlify"
git push
```

## Paso 4: Verifica la Configuración en Netlify

Una vez que hayas subido tus cambios, Netlify desencadenará una nueva construcción. Puedes revisar los registros de construcción en tu panel de control de Netlify para asegurarte de que la versión de Hugo especificada esté en uso. Si hay algún problema con la construcción, los registros te proporcionarán la información necesaria para solucionar problemas.

## Conclusión

Especificar la versión de Hugo en tu despliegue en Netlify asegura que tu sitio se construya correctamente y refleje tu entorno de desarrollo local, ayudando a evitar sorpresas durante la construcción. Al seguir los pasos descritos arriba, puedes gestionar tu versión de Hugo en Netlify con facilidad, lo que lleva a un proceso de despliegue más estable y predecible.