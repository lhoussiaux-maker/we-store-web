# We Store — Landing page

Página de aterrizaje para **We Store**, servicio de almacenamiento de larga duración
para material deportivo y equipaje en Verbier, Suiza.

Sitio estático: HTML, CSS y JavaScript puros. Sin build, sin dependencias, sin `npm install`.
Se abre haciendo doble clic en `index.html`.

---

## Estructura

```
.
├── index.html              ← estructura de la página
├── assets/
│   ├── css/styles.css      ← todos los estilos
│   ├── js/main.js          ← textos en 3 idiomas + lógica
│   └── img/
│       ├── hero.png        ← ilustración del hero (fondo transparente)
│       ├── og-image.png    ← miniatura al compartir el link
│       └── favicon.png     ← icono de la pestaña
└── README.md
```

---

## Cómo editar

### Cambiar un precio

Los precios están en `index.html`, en la sección `<!-- PRICES -->`. Busca `CHF` y edita
el número. Son iguales en los tres idiomas, por eso no están en el archivo de traducciones.

También aparece un precio en la meta descripción (línea 7 de `index.html`), que es el
texto que se ve en Google y en la vista previa de WhatsApp.

### Cambiar un texto

Todos los textos están en `assets/js/main.js`, en el objeto `I18N`, agrupados por idioma:

```js
const I18N = {
  en: { h1:"Fly home light. Your gear stays in Verbier.", ... },
  de: { h1:"Leicht heimreisen. Deine Ausrüstung bleibt in Verbier.", ... },
  fr: { h1:"Rentrez léger. Votre matériel reste à Verbier.", ... }
};
```

Cada clave (`h1`, `s1_h`, `q1`…) corresponde a un `data-i18n="..."` en `index.html`.
**Si cambias un texto, cámbialo en los tres idiomas** o ese bloque quedará en inglés.

### Cambiar el número de WhatsApp

Una sola línea, arriba de `assets/js/main.js`:

```js
const PHONE = "41772696644";
```

Formato internacional, sin `+` ni espacios. También hay que actualizarlo en los enlaces
`tel:` de `index.html` (busca `tel:`).

### Añadir un idioma

1. Añade un bloque nuevo en `I18N` con todas las claves.
2. Añade el botón en `index.html`: `<button type="button" data-lang="it" aria-pressed="false">IT</button>`

---

## Ilustración del hero

Los rótulos *"1. Drop it off / 2. Travel light / 3. Pick it up when you're back"* están
**dibujados dentro de la imagen**, así que no se traducen al cambiar de idioma.

Si exportas versiones en alemán y francés, ponlas en `assets/img/` y declara las rutas en
`assets/js/main.js`:

```js
const SCENE_IMG = { en:null, de:"assets/img/hero-de.png", fr:"assets/img/hero-fr.png" };
```

`null` significa "usa la imagen por defecto".

---

## Publicar

### GitHub Pages
1. Sube el repositorio a GitHub.
2. *Settings → Pages → Source: Deploy from a branch → `main` / `root`.*
3. En un par de minutos queda en `https://<usuario>.github.io/<repo>/`.

### Netlify o Cloudflare Pages
Conecta el repositorio y deja los ajustes de build vacíos (no hay build). Ambos dan
HTTPS y dominio propio gratis, y despliegan solos con cada `git push`.

---

## Pendiente

- [ ] Revisar las respuestas del FAQ: están redactadas a partir del flyer, hay que
      contrastarlas con la operación real (pagos, seguro, horarios).
- [ ] Fotos reales del depósito y testimonios de clientes (falta prueba social).
- [ ] Versiones DE y FR de la ilustración del hero.
- [ ] Dirección física y datos legales en el pie de página.
- [ ] El cambio de idioma no modifica la URL, así que Google solo indexa la versión en
      inglés. Si el SEO en francés importa, hay que separar en `/fr/` con páginas propias.

---

## Créditos

Ilustración y sistema visual: material original de We Store.
Tipografías: Archivo Black, Instrument Sans y Architects Daughter (Google Fonts, licencia OFL).
