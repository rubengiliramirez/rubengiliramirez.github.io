# Portfolio — Rubén Gili Ramírez

Portfolio personal publicado en **[rubengiliramirez.github.io](https://rubengiliramirez.github.io/)**, con estética de terminal retro: pantalla de entrada con el logo en ASCII, fondo de caracteres animado, títulos con efecto de máquina de escribir y navegación lateral. Bilingüe (ES/EN), sin frameworks, sin dependencias y sin paso de build.

## Estructura

```
index.html        Página única: HTML, CSS y JS
img/              Avatar pixel art, favicon, icono de Apple e imagen para redes (Open Graph)
fonts/            DotGothic16 (fuente pixel), alojada en el propio sitio
```

## Decisiones técnicas

**HTML, CSS y JavaScript sin framework.** Son cinco pantallas de contenido estático. Un framework añadiría un runtime y un paso de build para pintar contenido que ya viene terminado.

**Tipografía pixel a tamaños múltiplos de su rejilla.** DotGothic16 está dibujada sobre una rejilla de 16 px, así que el texto usa 16, 20, 24, 32, 48 y 64 px. A tamaños intermedios los píxeles se emborronan y letras como la `i` y la `l` se confunden.

**Logo en ASCII generado desde la imagen.** La pantalla de entrada muestra el logo convertido a caracteres según el brillo de cada zona. Las líneas aparecen una a una y la pantalla se cierra con Enter, Escape o con el botón. Solo se muestra una vez por pestaña (`sessionStorage`).

**Fondo de caracteres con Canvas 2D.** Caracteres aleatorios que caen despacio, cambian de glifo y parpadean con opacidad baja para no competir con el texto. La cantidad es proporcional al tamaño de la ventana, el `devicePixelRatio` se limita a 2 y la animación se pausa cuando la pestaña está oculta.

**Formulario de contacto sin servidor.** GitHub Pages solo sirve archivos estáticos, así que el formulario valida los campos y abre la aplicación de correo del visitante con el asunto y el mensaje ya escritos (`mailto:`).

**Bilingüe con un diccionario propio.** El marcado se anota con `data-i18n` (texto), `data-i18n-html` (cadenas con `<strong>` o `<code>`, siempre estáticas y del autor) y `data-i18n-aria` (etiquetas accesibles). El idioma se elige por la preferencia guardada o, si no la hay, por el idioma del navegador.

**Accesibilidad.** Enlace para saltar al contenido, pantalla de entrada como diálogo modal con el foco dentro, títulos de sección reales (`h2`) aunque se escriban con animación, adornos ASCII ocultos a lectores de pantalla y botones y enlaces de al menos 44 px de alto. `prefers-reduced-motion` desactiva las animaciones. Sin JavaScript, la pantalla de entrada no aparece y todo el contenido se ve.

## Ejecutar en local

```bash
python -m http.server 8000
# y abre http://localhost:8000
```
