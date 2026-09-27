# DEPLOY-HANDOFF — Invitación Yahil

## Proyecto

- **Ruta absoluta:** `/Users/randydominguez/Developer/invitacion-yahil`
- **Stack:** HTML estático (un solo `index.html` con CSS/JS inline). Sin Next.js, sin Vite, sin `package.json`.
- **Motivo:** el artefacto ya es publicable tal cual; no hace falta bundler ni framework. Prioridad: salir hoy.

## Build

- **Comando:** ninguno
- **Directorio a servir:** `/Users/randydominguez/Developer/invitacion-yahil` (raíz del proyecto)

## Nginx

Servir como sitio estático (root = directorio anterior). Puerto: lo elige Jinbe.

### Archivos a servir

| Archivo | Rol |
|---------|-----|
| `index.html` | Página completa (HTML + CSS + JS). Único documento requerido. |

No hay carpeta `assets/`, imágenes locales ni JS/CSS externos en el repo. Las tipografías se cargan desde Google Fonts (CDN).

### Notas operativas

- `try_files $uri $uri/ /index.html;` no es obligatorio (no hay SPA routing); con un solo `index.html` basta `index index.html;`.
- No hay secretos en el repo.
- RSVP abre WhatsApp con texto prefabricado (`api.whatsapp.com/send?text=...`) **sin número destino** en el HTML. Si el anfitrión quiere un `wa.me/<número>` fijo, hay que añadirlo después (no estaba en el proyecto).
- No hay `og:image` / favicon local: no existían assets de imagen en el proyecto.

## Checklist rápido

- [ ] Copiar `index.html` (o todo el directorio) al host
- [ ] Nginx root apuntando a ese directorio
- [ ] HTTPS / hostname (Cloudflare) a cargo de Jinbe
