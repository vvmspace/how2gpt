---
title: "Cómo agregar una insignia de estado de despliegue de Netlify a la plantilla de Hugo"
description: "Aprende cómo agregar una insignia de estado de despliegue de Netlify a la plantilla de tu sitio web Hugo. Esta guía cubre cómo obtener la URL de la imagen, configurar parámetros y agregar la insignia al pie de página."
tags: ["Hugo", "Netlify", "Despliegue", "Insignia de Estado"]
---

Agregar una insignia de estado de despliegue de Netlify a tu plantilla de Hugo es una excelente manera de mostrar el estado de tu sitio. En esta guía, te guiaremos a través de los pasos para obtener la URL de la imagen, configurar los parámetros necesarios y agregar la insignia al pie de página de tu sitio.

## Paso 1: Obtener la URL de la Insignia de Estado de Despliegue de Netlify

Netlify proporciona una URL para la insignia de estado de despliegue que puedes usar directamente en tu plantilla de Hugo. Para encontrar la URL de tu insignia:

1. Ve a tu panel de control de Netlify.
2. Selecciona el sitio para el cual deseas agregar la insignia.
3. Navega a **Configuración del sitio** > **Insignias de estado**.
4. Copia la URL de la imagen en Markdown proporcionada. Debería verse algo así:
   ```
   ![Estado de Netlify](https://api.netlify.com/api/v1/badges/YOUR-BADGE-ID/deploy-status)
   ```

## Paso 2: Configurar Parámetros en `config.toml`

Para hacer que la URL de la insignia sea configurable, vamos a agregar un nuevo parámetro en el archivo de configuración de tu sitio Hugo. Abre tu archivo `config.toml` y añade las siguientes líneas:

```toml
[params]
  netlifyBadgeURL = "https://api.netlify.com/api/v1/badges/YOUR-BADGE-ID/deploy-status"
```

Reemplaza `YOUR-BADGE-ID` con el ID de insignia real que copiaste desde el panel de control de Netlify.

## Paso 3: Agregar la Insignia al Pie de Página

Ahora que tenemos configurada la URL de la insignia, podemos agregarla al pie de página de nuestra plantilla de Hugo. Abre el archivo de plantilla del pie de página, que generalmente se encuentra en `layouts/partials/footer.html`. Añade el siguiente código para mostrar la insignia de estado de Netlify:

```html
<footer>
  <div class="footer-content">
    <!-- Otro contenido del pie de página -->
    <div class="netlify-badge">
      <img src="{{ .Site.Params.netlifyBadgeURL }}" alt="Estado de Netlify">
    </div>
  </div>
</footer>
```

Este fragmento de código añadirá la imagen de la insignia de Netlify al pie de página de tu sitio, utilizando la URL definida en tu archivo de configuración.

## Conclusión

Siguiendo estos pasos, has agregado con éxito una insignia de estado de despliegue de Netlify al pie de página de la plantilla de tu Hugo. Esta insignia proporciona un indicador visual del estado del despliegue de tu sitio, lo cual puede ser útil tanto para ti como para tus visitantes.

Siéntete libre de ajustar el estilo de la insignia añadiendo CSS personalizado para que coincida con el diseño de tu sitio. ¡Feliz codificación!