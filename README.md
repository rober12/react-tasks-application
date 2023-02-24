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