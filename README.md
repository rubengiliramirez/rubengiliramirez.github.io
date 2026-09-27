# Portfolio — Rubén Gili Ramírez

Portfolio personal publicado en **[rubengiliramirez.github.io](https://rubengiliramirez.github.io/)**. Bilingüe (ES/EN), sin frameworks, sin dependencias y sin paso de build.

## Estructura

```
index.html        Página única: HTML, CSS y JS
img/              Logo (WebP), favicon, icono de Apple e imagen para redes (Open Graph)
fonts/            Rajdhani 700 y Space Grotesk (variable), alojadas en el propio sitio
```

## Decisiones técnicas

**HTML, CSS y JavaScript sin framework.** Son cinco secciones de contenido estático: no hay estado de aplicación, ni rutas, ni datos que cambien. Un framework añadiría un runtime y un paso de build para pintar contenido que ya viene terminado. Además, el contenido se indexa al momento y se puede leer sin JavaScript.

**CSS con Custom Properties en lugar de Sass o Tailwind.** Los colores y medidas son tokens definidos en `:root`, y ningún componente usa valores hexadecimales sueltos. Al ser variables en tiempo de ejecución, se pueden leer desde JS y cambiar en media queries.

**Contraste comprobado (WCAG 2.1 AA).** El texto principal (`#e8ecf5`) tiene 16,7:1 sobre el fondo, el secundario (`#c3c8d6`) más de 10:1 y el terciario (`#8b8fa3`) entre 5,7:1 y 6,2:1 según la superficie. Todos los elementos interactivos miden al menos 44 px de alto en móvil. Auditado con axe-core sin incidencias.

**Bilingüe con un diccionario propio.** Son dos idiomas y unas 55 cadenas: no justifican una librería de i18n ni duplicar el sitio en `/es` y `/en`. El marcado se anota con `data-i18n` (texto), `data-i18n-html` (cadenas con `<strong>` o `<code>`, siempre estáticas y del autor) y `data-i18n-aria` (etiquetas accesibles). El idioma se elige por la preferencia guardada o, si no la hay, por el idioma del navegador. Contrapartida asumida: como no hay una URL distinta por idioma, los buscadores indexan solo la versión en español.

**Fuentes alojadas en el propio sitio.** Dos archivos `woff2` (unos 38 KB en total), precargados y con `font-display: swap`. No hay peticiones a terceros.

**Imágenes optimizadas.** El logo original (PNG de 872 KB) se recortó y se convirtió a WebP: 18 KB en el hero y 1,4 KB en la barra de navegación. El favicon es un PNG de 32 px.

**Partículas del hero con Canvas 2D nativo.** Sustituye a Three.js, del que solo se usaban escena, cámara y puntos. La densidad es proporcional al área del hero, el `devicePixelRatio` se limita a 2 y la animación se pausa cuando el hero sale de pantalla o la pestaña está oculta.

**IntersectionObserver en lugar de eventos de scroll.** Se usa para el revelado de secciones, el enlace activo del menú y el cambio de la barra de navegación. El navegador solo avisa cuando se cruza el umbral, sin recalcular el layout en cada fotograma de scroll.

**Movimiento reducido.** `prefers-reduced-motion` se respeta en CSS (se anulan animaciones y transiciones) y en JS (el canvas pinta un único fotograma y el cambio de idioma no hace fundido).

**Funciona sin JavaScript.** Un bloque `<noscript>` muestra todo el contenido revelado, oculta los controles que no pueden funcionar (idioma y menú) y deja el menú visible en móvil.

## Ejecutar en local

Basta con cualquier servidor estático:

```bash
python -m http.server 8000
# y abre http://localhost:8000
```
