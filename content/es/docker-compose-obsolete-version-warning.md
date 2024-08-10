---
tags: ["docker", "docker compose", "yaml", "versión", "terminal"]
description: "ADVERTENCIA: docker-compose.yml: `version` es obsoleto"
title: "Cómo Solucionar la ADVERTENCIA: docker-compose.yml: `version` es Obsoleto"
date: 2024-06-04
---

# Cómo Solucionar la ADVERTENCIA: docker-compose.yml: `version` es Obsoleto

Al trabajar con Docker Compose, puede encontrar el mensaje de advertencia: `ADVERTENCIA: docker-compose.yml: 'version' es obsoleto`. Esta advertencia indica que el campo `version` en su archivo `docker-compose.yml` ya no es necesario con las últimas versiones de Docker Compose. En esta guía, explicaremos por qué aparece esta advertencia y cómo actualizar su archivo `docker-compose.yml` para resolverla.

## Por Qué Aparece la Advertencia

En versiones anteriores de Docker Compose, se requería el campo `version` para especificar la versión del formato de archivo Compose que se estaba utilizando. Esto ayudaba a Docker Compose a entender cómo analizar e interpretar el archivo. Sin embargo, con el lanzamiento de Docker Compose v1.27.0, la herramienta ya no requiere el campo `version`. En su lugar, determina automáticamente la versión apropiada según la sintaxis y las características utilizadas en el archivo.

## Pasos para Resolver la Advertencia

Aquí hay una guía paso a paso para actualizar su archivo `docker-compose.yml` y eliminar el campo `version` obsoleto:

### 1. Abra su Archivo `docker-compose.yml`

Abra su archivo `docker-compose.yml` en su editor de texto preferido. Puede parecer algo así:

```yaml
version: '3.8'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: example
```

### 2. Elimine el Campo `version`

Simplemente elimine la línea de `version` de su archivo. Su archivo `docker-compose.yml` actualizado debería verse así:

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: example
```

### 3. Guarde el Archivo

Guarde los cambios en su archivo `docker-compose.yml`.

### 4. Verifique los Cambios

Para asegurarse de que todo funcione correctamente, ejecute el siguiente comando en su terminal:

```sh
docker-compose up
```

Docker Compose debería iniciar sus servicios sin mostrar la advertencia de `version`.

## Consejos Adicionales

- **Verifique la Compatibilidad**: Antes de eliminar el campo `version`, asegúrese de que su versión de Docker Compose sea compatible con este cambio. Esta función está disponible desde Docker Compose v1.27.0 en adelante.
- **Actualice Docker**: Si encuentra problemas, considere actualizar Docker y Docker Compose a las versiones más recientes para aprovechar nuevas funciones y mejoras.

## Conclusión

Siguiendo estos pasos, puede resolver la advertencia `ADVERTENCIA: docker-compose.yml: 'version' es obsoleto` y optimizar su configuración de Docker Compose. Eliminar el campo `version` hace que su archivo `docker-compose.yml` sea más limpio y garantiza la compatibilidad con las últimas versiones de Docker Compose.

Para más información y actualizaciones, consulte la [documentación oficial de Docker Compose](https://docs.docker.com/compose/compose-file/).

---

Ahora que ha actualizado su archivo `docker-compose.yml`, puede continuar desarrollando sus aplicaciones con menos advertencias y una configuración más optimizada.

---

Esta guía proporcionó una solución integral al problema de la advertencia. Si tiene más preguntas o necesita asistencia adicional, no dude en comunicarse.