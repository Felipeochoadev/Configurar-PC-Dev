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

