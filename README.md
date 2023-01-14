# astro-landing-page
Desarrollo de una landing pages usando Astro como tecnologia principal para la generación de contenido estático.

- [Repo](https://github.com/linkmao/astro-landing-page.git)
- [Video base](https://www.youtube.com/watch?v=sOXW0ZnJxbQ&t=11955s)
- [Despliegue](https//astro.maolink.co)

# Tecnologías usadadas
- Astro: Generador de sitios web estaticos
- Tailwind: Plantilla de estilos css
- Reat: Componentes html

### Otros recursos
- undraw.co: Portal web para descargar archivos graficos svg

# Como ejecutarlo en local
```
$ npm run dev
```


# Descripción del proyecto
Este proyecto consiste en el desarrollo de una página web del corte landing pages generada con astro. Se incia generando el proyecto con solo la linea de comando

```
 $ npm create astro 
```

Notese que no se instala astro sino que el comando crea la estructura del proyecto para Astro. Normalmente el proyecto corre en el puerto 3000 `localhost:3000`

Una de las caracteristicas de esta biblioteca es que se puede usar codigo de JavaScript en el mismo archivo.astro, lograndose así generar contenido html con base a la lógica que se escriba en la sección de JS.

Otra de las caracteristicas de esta biblioteca es que se usa (hasta el momento parcialmente) el lenguaje *typeScript* solo en este ejemplo se ve reflejado en la creacióin de interfaces sencillas para definir los tipos de datos que recibe la propiedad de una etiqueta.

Es una biblioteca basada en componentes creado por el mismo usuario o incorporando incluso componentes de React, para ello se debe simplemente agregar React al proyecto con el comando
```
$ npx astro add react
```
y se hace uso de los componentes de react


En ese proyecto en particular, el cual es solo esquemático, se usa un generador de estilos css llamado *tailwind*  el cual se instala con el comando
```
 $ npx astro add tailwind 
```

Luego de ello se despues se puede usar libremente los estilos de tailwind por medio de la propiedad `class` de las etiquetas html. (Se debe profundizar en el nombre de las clases tailwind). Esto es muy similar a boostrap pero desde mi concepto lo encuentro como mas sencillo.

# Build
Astro al ser un generador de paginas web estaticas debe generarse una carpeta *dist* la cual es la única que se sube al servidor, esa carpeta contiene todo el proyecto en una estructura simple de HTML facil de correrse en los servidores, la creación de la carpeta dist se realiza con el script.
```
$ npm run build
```
# Deploy
En el [video base](https://www.youtube.com/watch?v=sOXW0ZnJxbQ&t=11955s) se realiza el despliegue en Github-pages, para ello se realiza los siguientes pasos:

- En el archivo `astro.config.mjs` modificar el siguiente fragamneto de código
```
export default defineConfig({
  site: 'https://astronaut.github.io',
  base: '/my-repo',
})
```
  donde en **site** se cambia la palabra **astronaunt** por el nombre de usuario en GitHub, y en **base** Se escribe el nombre del repo donde se alojará el proyecto.
- Se crea la ruta y el archivo `.github/workflows/deploy.ym` y luego se copia allí todo el código tal cual
```
name: Deploy to GitHub Pages

on:
  # Trigger the workflow every time you push to the `main` branch
  # Using a different branch name? Replace `main` with your branch’s name
  push:
    branches: [ main ]
  # Allows you to run this workflow manually from the Actions tab on GitHub.
  workflow_dispatch:
  
# Allow this job to clone the repo and create a page deployment
permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout your repository using git
        uses: actions/checkout@v3
      - name: Install, build, and upload your site
        uses: withastro/action@v0
        # with:
            # path: . # The root location of your Astro project inside the repository. (optional)
            # node-version: 16 # The specific version of Node that should be used to build your site. Defaults to 16. (optional)
            # package-manager: yarn # The Node package manager that should be used to install dependencies and build your site. Automatically detected based on your lockfile. (optional)

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v1
```
- Se instala **hg-pages** en modo desarrollo
```
$ npm i gh-pages -D
```
- Se hace un *build* del proyecto para que se genere la carpeta *dist*
- Se hace un commit en git
- Se sube el commit a repo en GitHub
- Se despliega con el comando
```
$ gh-pages -d dist
```
En este caso **dist** es el nombre de la carpeta que se va a desplegar



# To do
- Escribir quizas contenido real.
- Agregar mas componentes de react
## Maolink Software
Enero 12 2023

V 1.0.0
***

# Doc Astro generated
# Astro Starter Kit: Minimal

```
npm create astro@latest -- --template minimal
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/minimal)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/s/github/withastro/astro/tree/latest/examples/minimal)

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```
/
├── public/
├── src/
│   └── pages/
│       └── index.astro
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                | Action                                           |
| :--------------------- | :----------------------------------------------- |
| `npm install`          | Installs dependencies                            |
| `npm run dev`          | Starts local dev server at `localhost:3000`      |
| `npm run build`        | Build your production site to `./dist/`          |
| `npm run preview`      | Preview your build locally, before deploying     |
| `npm run astro ...`    | Run CLI commands like `astro add`, `astro check` |
| `npm run astro --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).
