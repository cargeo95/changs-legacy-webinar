# Chang's Legacy — Landing Page Webinar

## Contexto del proyecto

**Cliente:** Barbara Chang — fundadora de Chang's Legacy Financial Services  
**Servicio:** Especialista certificada en reparación y construcción de crédito bajo FCRA y CROA  
**Producto:** Sistema "Crédito Nuevo en 90 Días" — curso de restauración de crédito para familias latinas en EE.UU.  
**Plataforma de despliegue:** GoHighLevel (GHL) — subir HTML directo como página de funnel

---

## Estructura de páginas

| Archivo | Propósito | Fecha del evento |
|---|---|---|
| `webinar.html` | Landing corta — clase gratuita de captación | 4 de junio de 2026 |
| *(pendiente)* `vsl.html` | Landing larga con VSL — venta principal | 21 de junio de 2026 |

---

## Identidad visual

| Token | Valor | Uso |
|---|---|---|
| `--navy-deep` | `#0B1C3D` | Fondo principal, nav |
| `--navy-mid` | `#112952` | Fondos secundarios |
| `--navy-light` | `#1A3A6B` | Acentos, cards |
| `--gold` | `#C9973A` | CTAs, acentos principales |
| `--gold-light` | `#E8B84B` | Hover, énfasis |
| `--white` | `#FFFFFF` | Texto sobre fondos oscuros |

**Tipografías:** Montserrat (headings, 700–900) · Open Sans (body, 400–600) — Google Fonts  
**Tono visual:** Tony Robbins — impacto, fuerza, transformación. NO corporativo frío.  
**Audiencia:** Familias latinas/hispanas en EE.UU. con crédito dañado (score < 620)

---

## Estructura de `webinar.html`

```
NAV            → sticky, blur on scroll, logo CL + botón CTA
HERO           → full-viewport, foto hero.JPG de fondo, mensaje aspiracional
COUNTDOWN      → cuenta regresiva al 4 de junio 7PM Atlanta (EDT)
PAIN           → frases de rechazo que se tachan con scroll
LEARN          → split sticky: foto Barbara izq + 3 errores revelándose der
TESTIMONIALS   → 4 video cards full-width, play on hover
ABOUT          → Barbara + stats + badge FCRA/CROA
REGISTRO       → form 2 columnas (copy izq + form der) ← embed GHL aquí
FOOTER         → logo, disclaimer legal, redes sociales
```

---

## Assets

| Archivo | Uso |
|---|---|
| `hero.JPG` | Fondo hero — foto grupal evento, familias celebrando |
| `IMG_5203 3.JPG` | Foto de Barbara — sección "learn" sticky izquierda |
| `logo.png` | Logo oficial Chang's Legacy — árbol CL navy+dorado |
| `favicon.svg` | Favicon generado del logo |
| `testimonio/Testimonio 1.mp4` | Video testimonio card 1 |
| `testimonio/Testimonio 2.mp4` | Video testimonio card 2 |
| `testimonio/Testimonio 3.mp4` | Video testimonio card 3 |
| `testimonio/WhatsApp Video...mp4` | Video testimonio card 4 |
| `Parte 1.mp4` | VSL principal Barbara (para `vsl.html`) |
| `Parte 2 .mp4` | VSL principal Barbara parte 2 |

> **Nota:** Los videos (.mp4) están en `.gitignore`. Para producción se suben a GoHighLevel o Vimeo y se embeden via `<iframe>` o GHL video element.

---

## Integraciones pendientes

- [ ] **Formulario de registro** — reemplazar `<form>` en sección `#registro` con embed de GoHighLevel
- [ ] **Videos de testimonios** — subir a GHL o Vimeo y actualizar `src` en las video cards
- [ ] **Redes sociales** — actualizar `href="#"` en el footer con URLs reales de Barbara
- [ ] **Countdown timezone** — verificar zona horaria exacta del evento (actualmente `2026-06-04T19:00:00-04:00`, EDT Atlanta)
- [ ] **VSL principal** — crear `vsl.html` para el evento del 21 de junio

---

## Comportamientos JavaScript

| Función | Descripción |
|---|---|
| Countdown | Cuenta regresiva en tiempo real hacia el evento |
| Sticky nav | Blur backdrop al hacer scroll > 60px |
| Floating CTA | Aparece cuando el hero sale del viewport |
| Reveal animations | `.reveal`, `.reveal-left`, `.reveal-right`, `.reveal-scale` — IntersectionObserver |
| Rejection strike | Frases se tachan con scroll, se destachan al subir |
| Error strips | Cards de errores entran desde la derecha |
| Video hover | `onmouseenter` / `onmouseleave` en cada `.video-card` |
| Hero bg zoom | Zoom-in suave al cargar la página |

---

## Decisiones de diseño tomadas

- **Sección pain (tachaduras):** Se eligió "Opción A — frases de rechazo" sobre texto corrido. Las frases se tachan al hacer scroll y se destachan al subir (bidireccional).
- **Sección learn:** Split layout con foto de Barbara sticky a la izquierda mientras el usuario scrollea los 3 errores a la derecha. Transmite "Barbara te acompaña mientras descubres cada error".
- **Testimonios:** Video cards full-width en grid 4 columnas (2 en mobile). Sin header de sección — los videos hablan solos.
- **CTA final:** Form con 2 columnas (copy + form) en lugar de solo botón. El form es placeholder — se reemplazará con embed de GHL.
- **No se usó top bar** — se eliminó por redundancia con las pills del hero.
- **Videos en producción:** Van en GoHighLevel/Vimeo, no en el repo. Los `src` locales son para desarrollo.

---

## Comandos útiles

```bash
# Servidor local de desarrollo (requiere Node.js)
npx http-server -p 3000 -o webinar.html

# Inicializar repositorio
git init
git add .
git commit -m "feat: initial landing page webinar Chang's Legacy"
```

---

## Notas para futuros desarrollos

- La landing `vsl.html` usará la misma paleta y componentes base
- El flujo de conversión es: webinar gratuito (4 jun) → email → clase de pago (21 jun)
- GoHighLevel maneja el email marketing — el form solo necesita enviar nombre, email y teléfono a GHL
- Barbara opera bajo FCRA y CROA — el disclaimer legal en el footer es obligatorio
