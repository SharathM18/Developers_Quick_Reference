# Setup Guide

### React

```bash
npm create vite@latest
```

```bash
npm install react-router-dom
```

```bash
npm install react-redux @reduxjs/toolkit
```

```bash
npm install react-hook-form @hookform/resolvers zod
```

```bash
npm install axios
```

### Node.js + Express + TypeScript + MongoDB

```bash
npm init
```

#### Runtime dependencies

```bash
npm install express mongoose dotenv
```

#### Development dependencies

```bash
npm install -D typescript ts-node-dev @types/node @types/express @types/mongoose

```

#### Create tsconfig.json

```bash
npx tsc --init
```

#### Then modify `tsconfig.json`

```ts
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "CommonJS",
    "rootDir": "./src",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  }
}
```

#### modify `package.json`

```ts
"scripts": {
  "dev": "ts-node-dev --respawn --transpile-only src/server.ts",   // Fast TS hot reload
  "build": "tsc",                                                  // Compile TS → JS
  "start": "node dist/server.js",                                  // Start production build
}
```

### Tailwind CSS

```bash
npm install -D tailwindcss postcss autoprefixer
```

```bash
npx tailwindcss init -p
```

#### Configure your template paths to the `tailwind.config.js` file.

```
content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
```

#### Add the Tailwind directives to your `./src/index.css` file.

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

#### Installation of `prettier-plugin-tailwindcss` for automatic class sorting with Prettier

```bash
npm install -D prettier prettier-plugin-tailwindcss
```

#### Create a file named `.prettierrc` in the root directory

```
{
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

### Bootstrap

```bash
npm install bootstrap
```

#### Import Bootstrap CSS `src/main.jsx`

```
import 'bootstrap/dist/css/bootstrap.min.css';
```

#### Install Bootstrap [Icons](https://icons.getbootstrap.com/)

```bash
npm install bootstrap-icons
```

#### Import Bootstrap Icons CSS `src/main.jsx`

```
import 'bootstrap-icons/font/bootstrap-icons.css';
```

#### Pre-defined icon size

- `.fs-1`: Makes the icon very large (around 3.5rem)
- `.fs-2`: Makes the icon large (around 3rem)
- `.fs-3`: Makes the icon medium-large (around 2.5rem)
- `.fs-4`: Makes the icon medium (around 2rem)
- `.fs-5`: Makes the icon medium-small (around 1.5rem)
- `.fs-6`: Makes the icon small (around 1rem)

or you can use `fontSize`

- <i className="bi bi-check" `style={{ fontSize: '2em' }}`></i> {/_ Check icon, 2x larger _/}

### Uninstall Packages

```bash
npm uninstall <package-name>
```
