## Setup Guide

### React Vite

```bash
npm create vite@latest

npm install react-router-dom

npm install react-redux @reduxjs/toolkit

npm install react-hook-form @hookform/resolvers zod

npm install axios
```

### NestJS

```bash
npm install -g @nestjs/cli

nest new <project-name>

npm run start:dev

nest g module <module-name>
nest g controller <controller-name>
nest g service <service-name>
```

### Tailwind CSS for React Vite

```bash
npm install -D tailwindcss postcss autoprefixer

npx tailwindcss init -p

# Configure your template paths to the `tailwind.config.js` file.
content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],

# Add the Tailwind directives to your `./src/index.css` file.
@tailwind base;
@tailwind components;
@tailwind utilities;

# Installation of `prettier-plugin-tailwindcss` for automatic class sorting with Prettier
npm install -D prettier prettier-plugin-tailwindcss

# Create a file named `.prettierrc` in the root directory
{
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

### Bootstrap for React Vite

````bash
npm install bootstrap

# Import Bootstrap CSS `src/main.jsx`
import 'bootstrap/dist/css/bootstrap.min.css';

# Install Bootstrap [Icons](https://icons.getbootstrap.com/)
npm install bootstrap-icons

# Import Bootstrap Icons CSS `src/main.jsx`
import 'bootstrap-icons/font/bootstrap-icons.css';

# Pre-defined icon size
- `.fs-1`: Makes the icon very large (around 3.5rem)
- `.fs-2`: Makes the icon large (around 3rem)
- `.fs-3`: Makes the icon medium-large (around 2.5rem)
- `.fs-4`: Makes the icon medium (around 2rem)
- `.fs-5`: Makes the icon medium-small (around 1.5rem)
- `.fs-6`: Makes the icon small (around 1rem)

or you can use `fontSize`

- <i className="bi bi-check" `style={{ fontSize: '2em' }}`></i>

### PIP (Python Package Manager)

```bash
pip --version
python.exe -m pip install --upgrade pip

pip list

pip list --outdated

pip install <package-name>
pip install 'ruff==0.3.0'
pip install -r requirements.txt

pip install --upgrade <package-name>

pip uninstall <package-name>

pip freeze > requirements.txt
````

### UV Virtual Environment (Python)

```bash
pip install uv

uv venv
uv venv <my-venv>

source .venv/Scripts/activate
source <my-venv>/Scripts/activate

deactivate

uv pip list

uv pip install <package_name>
uv pip install 'ruff==0.3.0'
uv pip install -r requirements.txt

uv pip install --upgrade <package-uv>

uv pip uninstall <package_name>

uv pip freeze > requirements.txt
```

### NPM (Node Package Manager)

```bash
npm -v
npm install -g npm@latest

npm list
npm list -g

npm outdated

npm install <package-name>
npm install -g <package-name>

npm update <package-name>
npm update -g <package-name>

npm uninstall <package-name>
npm uninstall -g <package-name>

npm cache clean
npm cache clean --force
```

### NVM (Node Version Manager)

Manually download and install the latest version from: [nvm-windows](https://github.com/coreybutler/nvm-windows)

```bash
nvm version
nvm upgrade

nvm current

nvm list
nvm list available

nvm install <version-20,22,24....>
nvm reinstall <version>

nvm use <version>

nvm uninstall <version>
```
