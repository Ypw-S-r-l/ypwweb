# YPW Web – Despliegue estático con Traefik y Docker

Este proyecto levanta una **web estática (un único `index.html`)** usando una imagen ligera de **nginx (`nginx:alpine`)**, expuesta detrás de **Traefik** con HTTPS automático usando Let’s Encrypt.

El sitio corresponde a:

> **YPW - Yolfry Paginas Web S.R.L.**  
> Empresa de desarrollo de apps móviles, web, APIs e Inteligencia Artificial en Santo Domingo, República Dominicana.

---

## 1. Requisitos previos

Antes de levantar la web, asegúrate de tener:

1. **Docker** y **Docker Compose** instalados.
2. Un **Traefik** ya configurado y corriendo, por ejemplo:
   - Con un _entrypoint_ llamado `websecure` (para HTTPS).
   - Con un _certresolver_ llamado `le` (Let’s Encrypt).
   - Unido a una red externa llamada `traefik-net`.
3. Los dominios apuntando al servidor:
   - `ypw.com.do`
   - `www.ypw.com.do`  
     Ambos deben apuntar a la IP pública del servidor donde corre Traefik.

Si aún no existe la red `traefik-net`:

```bash
docker network create traefik-net
Ojo: La red la debe usar también tu contenedor de Traefik.

2. Estructura del proyecto
Dentro de la carpeta del proyecto, la estructura recomendada es:

text
Copiar código
.
├─ docker-compose.yml
└─ html
   └─ index.html
docker-compose.yml: define el servicio ypwweb con nginx y las labels para Traefik.

html/index.html: tu web estática (con Vue, Tailwind y Font Awesome por CDN).
```
