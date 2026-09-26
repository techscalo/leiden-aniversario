# Grupo Leiden · aniversario 18 años + sitio nuevo

Regalo de Scalo a Grupo Leiden por su aniversario (26-09-2026). Celebramos sus **18 años**, según la corrección del aniversario.

| Página | URL | Archivo |
|---|---|---|
| Saludo de aniversario (con el regalo al final) | https://leiden-21.vercel.app | `index.html` |
| Sitio nuevo (el regalo) | https://leiden-21.vercel.app/sitio/ | `sitio/index.html` |
| Sitio actual de ellos (referencia) | https://www.grupoleiden.com | captura en `referencia/sitio-viejo-captura.png` |

**Nunca decir que el sitio actual es feo.** El regalo se presenta como "una versión
nueva para los próximos 18".

## Cómo se publica

Todo push a `main` se publica solo en https://leiden-21.vercel.app (GitHub Actions,
`.github/workflows/deploy.yml`). Tarda ~1 minuto. Para ver si salió:
pestaña **Actions** del repo.

No hace falta build: es HTML estático, sin frameworks. Para verlo en local:

    python3 -m http.server 8000     # y abrir http://localhost:8000

## Estructura

- `index.html` — saludo. Todo el CSS y JS está adentro del archivo.
  Secciones: hero (isotipo + 18 que cuenta), línea de tiempo, números, marcas
  (cintas de logos), carta del equipo de Scalo, regalo (caja que se abre con
  fuegos artificiales y lleva a `/sitio/`).
- `sitio/index.html` — sitio nuevo. Secciones: hero, clientes, servicios (se
  arman desde el array `S` en el JS), método, Sales Team + Leiden Academy,
  nosotros, manifiesto, contacto, footer.
- `img/` — logos de Leiden sacados de su web (`logo-blanco.png`, `isotipo-grande.png`,
  `wordmark.png`, `leidenacademy.png`, `logosalesteam.png`), logos de clientes
  pasados a blanco (`clientes/c1..c14.png`) y las imágenes de preview para
  WhatsApp (`og-18.png`, `og-sitio-18.png`).

## Marca

- Tipografía: **Sora** (la que usa su web).
- Colores en `:root` de cada archivo: fondo `#040A1C`, cyan `#97F5FF`,
  turquesa `#2DD4B4` (sale del fondo verde de su logo), azul `#2B7BFF`, naranja
  `#FF5A1F` sólo para Sales Team.
- Los logos son los PNG reales de su web. No redibujarlos.

## Contacto de Leiden (usado en el sitio)

- WhatsApp: 351 686 9096 → `https://wa.me/5493516869096` (en su web el link está
  mal armado, sin el 549). Tel. 351 686 8682.
- Mail: info@grupoleiden.com · IG @grupoleiden · FB GrupoLeidenComunicacion
- El formulario de contacto no manda mails: abre WhatsApp con el mensaje armado.

## Texto propio (no sale de su web)

La sección "Cómo trabajamos" (escuchamos, planificamos, creamos, medimos), las
bajadas de Paid media y Producción audiovisual, la línea de tiempo y la carta del
aniversario. Todo lo demás es copy de ellos.

## Cosas a cuidar

- Probar siempre en celular (390 px): lo abren desde WhatsApp.
- Las imágenes `og*.png` tienen URL absoluta en el `<head>`; si cambia el
  dominio, actualizarlas.
- Si Actions falla con `The token provided via --token argument is not valid`,
  venció el secret `VERCEL_TOKEN`: avisarle a Tomás para reponerlo.
