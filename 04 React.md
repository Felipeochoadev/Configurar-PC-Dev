# Configuración de React con Vite + SWC en Windows

Este documento describe cómo configurar un entorno de desarrollo moderno para React usando **Vite** junto con **JavaScript + SWC**, un compilador rápido y eficiente que reemplaza a Babel.

---

## **Requisitos previos**

Antes de comenzar, asegúrate de tener instalados:

- **Node.js** (versión recomendada: 18.x o superior)
- **npm**

Verifica su instalación con:

```powershell
node -v
npm -v

```

## **Paso 1: Crear el proyecto**

```powershell
npm create vite@latest

```

## **Escribes el nombre del proyecto y presionas enter**

```powershell
│
◆  Project name:
│  MiProyecto
└

```

## **Escribes el nombre del paquete por lo general es el mismo nombre del proyecto y presionas enter**

```powershell
│
◇  Project name:
│  MiProyecto
│
◆  Package name:
│  miproyecto
└

```

## **Seleccionar el framework React desplazando con las flechas y selecionando con enter**

```powershell
│
◇  Project name:
│  MiProyecto
│
◇  Package name:
│  miproyecto
│
◆  Select a framework:
│  ○ Vanilla
│  ○ Vue
│  ● React
│  ○ Preact
│  ○ Lit
│  ○ Svelte
│  ○ Solid
│  ○ Qwik
│  ○ Angular
│  ○ Marko
│  ○ Others
└

```

## **Seleccionar el framework React desplazando con las flechas y selecionando con enter**

```powershell
│
◇  Project name:
│  MiProyecto
│
◇  Package name:
│  miproyecto
│
◆  Select a framework:
│  ○ Vanilla
│  ○ Vue
│  ● React
│  ○ Preact
│  ○ Lit
│  ○ Svelte
│  ○ Solid
│  ○ Qwik
│  ○ Angular
│  ○ Marko
│  ○ Others
└

```

## **Seleccionar la variante JavaScript + SWC desplazando con las flechas y selecionando con enter**

```powershell
│
◇  Project name:
│  MiProyecto
│
◇  Package name:
│  miproyecto
│
◇  Select a framework:
│  React
│
◆  Select a variant:
│  ○ TypeScript
│  ○ TypeScript + SWC
│  ○ JavaScript
│  ● JavaScript + SWC
│  ○ React Router v7 ↗
│  ○ TanStack Router ↗
│  ○ RedwoodSDK ↗
└

```


## **Paso 2: Entrar al proyecto**

```powershell
cd MiProyecto

```


## **Instalar las dependencias**

```powershell
npm install

```

## **Levantar el servidor de desarrollo**

```powershell
npm run dev

```


## **Estructura del proyecto**
La estructura básica se verá así:

```css
MiProyecto/
├─ index.html
├─ package.json
├─ vite.config.js
├─ src/
│  ├─ main.jsx
│  └─ App.jsx

```

# Pruebas Unitarias con Vitest y React

## Instalación y configuración

Instala Vitest como dependencia de desarrollo:

```bash
npm install -D vitest

```

Luego, agrega la configuración de entorno en tu archivo vite.config.js (debajo de plugins):

```javascript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  test: { // Configura el entorno para pruebas con DOM
    environment: 'jsdom', 
  },
});

```

Asegúrate también de tener instalado jsdom:

```bash
npm install -D jsdom

```

## Crear el archivo de prueba

Crea un archivo de prueba en src/App.test.jsx con el siguiente contenido el vitest busca todo los archivos que contengan el nombre test para hacer la prueba unitaria: 

```jsx
import { render, screen } from '@testing-library/react';
import { describe, it, expect } from 'vitest';
import App from './App';

describe('Componente App', () => {
  it('muestra el título principal', () => {
    render(<App />);
    const heading = screen.getByText(/Vite \+ React/i);
    expect(heading).to.exist;
  });
});

```

## Ejecutar las pruebas

```bash
npx vitest

```
Esto lanzará Vitest y ejecutará tus pruebas en entorno jsdom


## **Para compilar la aplicación (modo producción)**

```powershell
npm run build

```


## **Para servir la app compilada**

```powershell
npm run preview

```