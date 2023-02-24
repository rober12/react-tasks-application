# 1. Creación del proyecto con vite
- `> npm create vite` --> Nos crea un proyecto en el que podemos seleccionar diferentes frameworks, react, vue...
    - Seleccionamos como framework `react`
    - Seleccionamos como variant `JavaScript`
- `> npm install` --> Instalar las dependencias
- `> npm run dev` --> Equivalente a npm start en create-react-app

- `> npm install -D tailwindcss postcss autoprefixer` --> Instalación de tailwindCSS
- `> npx tailwindcss init -p` --> Inicia tailwindCSS creando dos archivos de configuración: `tailwind.config.css` y `postcss.config.css`
    - Añadir lo siguiente al archivo tailwind.config.css sustituyendo content []
    ```
      content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
    ],
    ```
    - Añadir en index.css las siguientes líneas:
    ```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```

- Para publicar la web en github pages es necesario lo siguiente:
  - Instalar: https://www.npmjs.com/package/gh-pages con el comando `> npm install gh-pages --save-dev` desde la raiz del repositorio
  - Configurar en el archivo `vite.config.js`
  ```
  export default defineConfig({
  plugins: [react()],
  base: '/react-tasks-application/'
  })
  ```
  - Crear el archivo `deploy.sh` e introducir lo siguiente:
  ```
  #!/usr/bin/env sh

  # abort on errors
  set -e

  # build
  npm run build

  # navigate into the build output directory
  cd dist

  # if you are deploying to a cutom domain
  # echo "www.example.com" > CNAME

  git init
  git checkout -b main
  git add -A
  git commit -m "deploy"

  #if you are deploying to http://<USERNAME>.github.io
  # git push -f git@github.com:<USERNAME>/<USERNAME>.github.io.git main

  # if you are deploying to https://<USERNAME>.github.io/<REPO>
  git push -f git@github.com:rober12/react-tasks-application.git main:gh-pages

  cd -
  ```
  - Crear un script nuevo en el `package.json`
  ```
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "deploy": "gh-pages -d dist"
  ```
  - Posteriormente ejecutar
    - `npm run build`
    - `npm run deploy`

  - Por ultimo, visitar [github](https://github.com/rober12/react-tasks-application/settings/pages) la parte de _settings -> pages_ del repositorio donde aparecera el [enlace](https://rober12.github.io/react-tasks-application/) donde se ha publicado la web.