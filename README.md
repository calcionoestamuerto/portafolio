# portfolio-calcio

portafolio web de calcio — sistema de burbujas orgánicas interactivas.

## correr localmente

```bash
npm install
npm run dev
```

abre `http://localhost:5173` en el navegador.

## reemplazar imágenes

en cada proyecto, los placeholders están marcados con comentarios `// TODO: reemplazar con imagen real` en `pages/ProjectPage.jsx`.

para agregar imágenes reales, editar el array `media` del proyecto correspondiente en `data/projects.js`:

```js
{
  id: "cruda",
  media: [
    "/images/cruda-01.jpg",
    "/images/cruda-02.jpg",
  ],
}
```

colocar los archivos en la carpeta `public/images/`. para video usar extensiones `.mp4`, `.webm` o `.mov` — se renderizarán como `<video>` automáticamente.

## agregar / editar proyectos

`data/projects.js` es el único archivo que necesita editarse para gestionar contenido. cada proyecto acepta:

| campo | tipo | descripción |
|---|---|---|
| `id` | string | slug único, usado en la URL `/project/:id` |
| `title` | string | título del proyecto (se muestra tal cual) |
| `disciplines` | string[] | valores: `"video"`, `"sonido"`, `"estilismo"`, `"ropa"` |
| `role` | string | rol de calcio en el proyecto |
| `description` | string | descripción breve |
| `year` | number \| null | año del proyecto |
| `collaborators` | string | créditos opcionales |
| `link` | string \| null | URL externa (abre en nueva pestaña) |
| `media` | string[] | rutas a imágenes o videos |

## importar a framer

1. copiar el contenido de cada componente en `components/` y `pages/`
2. en framer: `+` → **Code Component** → pegar el JSX
3. los estilos CSS están en `styles/` — copiarlos como **Override** o convertirlos a estilos inline según el componente
4. framer no usa react-router — reemplazar `useNavigate` y `<Link>` con la navegación nativa de framer (`import { useRouter } from "framer"`)
5. el `BubbleMap` usa canvas nativo + `requestAnimationFrame` — funciona sin cambios en framer como code component

## estructura de archivos

```
portfolio-calcio/
├── src/
│   ├── main.jsx          — punto de entrada
│   └── App.jsx           — rutas
├── components/
│   ├── BubbleMap.jsx     — canvas interactivo principal
│   ├── Nav.jsx           — barra de navegación fija
│   └── ProjectCard.jsx   — tarjeta de proyecto (uso opcional)
├── pages/
│   ├── Home.jsx          — página de inicio con BubbleMap
│   ├── ProjectPage.jsx   — página individual de proyecto
│   └── SoundPage.jsx     — página de sonido → SoundCloud
├── data/
│   └── projects.js       — única fuente de datos
├── styles/
│   ├── global.css
│   ├── home.css
│   ├── project.css
│   └── nav.css
├── index.html
├── vite.config.js
└── package.json
```
