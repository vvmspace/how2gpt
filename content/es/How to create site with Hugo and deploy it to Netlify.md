---
title: Cómo crear un sitio con Hugo y desplegarlo en Netlify (Primera edición)
tags: ["hugo", "netlify", "sitio web", "despliegue"]
description: Una guía concisa sobre cómo crear un sitio web con Hugo y desplegarlo en Netlify.
---

Crear un sitio web con Hugo y desplegarlo en Netlify implica una serie de pasos. Aquí tienes una guía concisa sobre cómo configurarlo, asumiendo que ya tienes una comprensión básica de cómo usar tu terminal y Git.

Consulta también:
- [Cómo alojar notas de Obsidian en Netlify usando Hugo con una plantilla SEO](/How_to_Host_Obsidian_Markdown_Website_Netlify_Hugo) - **Segunda Edición**
- [Cómo especificar una versión de Hugo para el Despliegue en Netlify](/Hugo_Version_Netlify_Revised)

## 1: Instalar Hugo

Primero, necesitas instalar Hugo en tu sistema. Como estás usando macOS, puedes instalar Hugo a través de Homebrew:

### Mac: 
```bash
brew install hugo
hugo version
```

### Windows: 
```bash
choco install hugo -confirm
hugo version
```

### Linux: 
```bash
snap install hugo --channel=extended
hugo version
```

## 2: Crear un Nuevo Sitio Hugo

Crea un nuevo sitio usando Hugo:

```bash
hugo new site how2gpt.xyz
cd how2gpt.xyz
```

### 3: Agregar un Tema

Agrega un tema desde el directorio de temas de Hugo. Por ejemplo, para agregar el tema "Hugo SEO Theme":
```bash
git init
git submodule add https://github.com/vvmspace/hugo-seo-theme.git vvmspace/hugo-seo-theme
echo 'theme = "hugo-seo-theme"' >> config.toml
```

### 4: Agregar Contenido

```bash
hugo new posts/mi-primer-post.md
```

Edita `content/posts/mi-primer-post.md` en tu editor de texto y añade contenido.

[Cómo empezar a escribir en Markdown](/how_to_start_writing_in_markdown)

### 5: Ejecutar Hugo Localmente

Inicia el servidor de Hugo con:

```bash
hugo server
```

Visita `http://localhost:1313` para ver tu nuevo sitio web.

### 6: Preparar para el Despliegue

Asegúrate de que el contenido de tu sitio web esté listo para el despliegue. Detén el servidor (Ctrl + C) y ejecuta:

```bash
hugo
```
Este comando construye tu sitio estático en el directorio `public/`.

### 7: Desplegar en Netlify

1. Configura `baseURL` en tu archivo `config.toml`:

```toml
baseURL = "https://how2gpt.netlify.app/"
```

2. **Sube tu código a GitHub:**
    
    - Crea un nuevo repositorio en GitHub y nómbralo `how2gpt.xyz`.
    - Inicializa el repositorio local y sube el código:
    
```bash
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin https://github.com/tuusuario/how2gpt.xyz.git
git push -u origin main
```
    
3. **Configura Netlify:**
    
    - Ve a [Netlify](https://netlify.com/) y accede a tu cuenta.
    - Haz clic en "Nuevo sitio desde Git" y selecciona GitHub.
    - Elige el repositorio que acabas de subir.
    - Establece el comando de construcción como `hugo` y el directorio de publicación como `public/`.
    - Haz clic en "Desplegar sitio".

Netlify desplegará automáticamente tu sitio y te proporcionará una URL para acceder a él. También puedes configurar un dominio personalizado en la configuración de gestión de dominios de Netlify para usar `how2gpt.xyz`.