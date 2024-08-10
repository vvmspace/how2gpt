---
title: "Cómo proxy de Hosts Virtuales de Node.js en Nginx con HTTPS usando Let's Encrypt y Certbot"
description: "Aprende a configurar Nginx para proxy de aplicaciones Node.js con HTTPS usando Let's Encrypt y Certbot. Sigue esta guía paso a paso para una configuración segura y eficiente."
tags: ["Node.js", "Nginx", "HTTPS", "Let's Encrypt", "Certbot"]
---

# Cómo proxy de Hosts Virtuales de Node.js en Nginx con HTTPS usando Let's Encrypt y Certbot

Configurar un servidor web seguro que haga proxy de aplicaciones Node.js con Nginx es un requerimiento común para el desarrollo web moderno. Al usar Let's Encrypt y Certbot, puedes obtener y gestionar fácilmente certificados SSL/TLS para tus hosts virtuales. En este artículo, te guiaremos a través del proceso paso a paso.

## Requisitos Previos

Antes de comenzar, asegúrate de tener lo siguiente:

1. Un servidor con una dirección IP pública.
2. Acceso root o sudo al servidor.
3. Nginx y Node.js instalados.
4. Nombres de dominio apuntando a la dirección IP de tu servidor.

## Paso 1: Instalar Certbot

Certbot es una herramienta gratuita y de código abierto para obtener y renovar certificados SSL de Let's Encrypt. Para instalar Certbot en tu servidor, ejecuta los siguientes comandos:

```bash
sudo apt update
sudo apt install certbot python3-certbot-nginx
```

## Paso 2: Configurar Nginx para tus Aplicaciones Node.js

A continuación, deberás configurar Nginx para hacer proxy de las solicitudes a tus aplicaciones Node.js. Crea un nuevo archivo de configuración para cada host virtual en el directorio `/etc/nginx/sites-available/`. Por ejemplo, si tienes dos aplicaciones, `app1` y `app2`, crea los siguientes archivos:

### Ejemplo de Configuración para `app1`

```bash
sudo nano /etc/nginx/sites-available/app1.ejemplo.com
```

Agrega el siguiente contenido al archivo:

```nginx
server {
    listen 80;
    server_name app1.ejemplo.com;

    location / {
        proxy_pass http://localhost:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

### Ejemplo de Configuración para `app2`

```bash
sudo nano /etc/nginx/sites-available/app2.ejemplo.com
```

Agrega el siguiente contenido al archivo:

```nginx
server {
    listen 80;
    server_name app2.ejemplo.com;

    location / {
        proxy_pass http://localhost:3002;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

Habilita estas configuraciones creando enlaces simbólicos en el directorio `/etc/nginx/sites-enabled/`:

```bash
sudo ln -s /etc/nginx/sites-available/app1.ejemplo.com /etc/nginx/sites-enabled/
sudo ln -s /etc/nginx/sites-available/app2.ejemplo.com /etc/nginx/sites-enabled/
```

Prueba la configuración de Nginx para errores de sintaxis:

```bash
sudo nginx -t
```

Si no hay errores, recarga Nginx para aplicar los cambios:

```bash
sudo systemctl reload nginx
```

## Paso 3: Obtener Certificados SSL con Certbot

Ejecuta el siguiente comando para obtener certificados SSL para tus dominios:

```bash
sudo certbot --nginx -d app1.ejemplo.com -d app2.ejemplo.com
```

Sigue las instrucciones en pantalla para completar el proceso de emisión de certificados. Certbot configurará automáticamente Nginx para usar los certificados obtenidos.

## Paso 4: Verificar la Configuración de HTTPS

Después de que Certbot haya obtenido y configurado con éxito los certificados SSL, verifica que tus hosts virtuales sean accesibles a través de HTTPS. Abre un navegador web y navega a:

- `https://app1.ejemplo.com`
- `https://app2.ejemplo.com`

Deberías ver tus aplicaciones Node.js funcionando de forma segura sobre HTTPS.

## Paso 5: Configurar la Renovación Automática de Certificados

Los certificados de Let's Encrypt son válidos por 90 días, pero Certbot puede renovarlos automáticamente por ti. Para configurar la renovación automática, agrega un trabajo cron que ejecute el comando de renovación regularmente. Abre la configuración del crontab:

```bash
sudo crontab -e
```

Agrega la siguiente línea al archivo crontab:

```bash
0 3 * * * /usr/bin/certbot renew --quiet
```

Este trabajo cron ejecutará el comando de renovación de Certbot todos los días a las 3 AM. Certbot verificará si los certificados están próximos a vencer y los renovará si es necesario.

## Conclusión

Siguiendo esta guía, has configurado con éxito Nginx para hacer proxy de tus hosts virtuales de Node.js con HTTPS usando Let's Encrypt y Certbot. Tus aplicaciones ahora son seguras y accesibles a través de HTTPS, con la renovación automática de certificados asegurando la continuidad de la seguridad. Si encuentras algún problema, consulta la documentación de Nginx, Certbot y Let's Encrypt para obtener ayuda adicional.