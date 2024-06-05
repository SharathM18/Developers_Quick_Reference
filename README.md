# Setup Guide

### React

#### Install React with vite
```bash
npm create vite@latest
```

### Tailwind CSS

#### Install Tailwind CSS with Vite
```bash
npm install -D tailwindcss postcss autoprefixer
```
```bash
npx tailwindcss init -p
```

#### Configure your template paths to `tailwind.config.js` file.
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
