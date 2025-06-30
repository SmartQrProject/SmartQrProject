# ☁️ Infraestructura y Despliegue en Oracle Cloud

## 🧱 Arquitectura

- Servidor: Oracle Cloud Free Tier (Ampere ARM)
- Sistema: Ubuntu 22.04 LTS
- Reverse Proxy: NGINX
- Certificados SSL: Let's Encrypt (Certbot)
- Contenedor: Docker (docker-compose)
- Base de datos: Supabase (externa)

## 🛠️ Pasos realizados

1. Configuración de DNS (Cloudflare + dominio personalizado)
2. Instalación de Docker, Docker Compose, NGINX y Certbot
3. Configuración de proxy inverso con redirección HTTP → HTTPS
4. Obtención y renovación automática de certificados SSL (cronjob)
5. Exposición del puerto 80 y 443 (cierre de puertos extras como el 3000)
6. Pruebas de seguridad (SSL Labs A+ / Security Headers A)
