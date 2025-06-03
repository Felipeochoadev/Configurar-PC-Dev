# Configuración de Angular con Angular CLI en Windows

Este documento describe cómo configurar un entorno de desarrollo moderno para Angular usando **Angular CLI** junto con **TypeScript**.

---

## **Requisitos previos**

Antes de comenzar, asegúrate de tener instalados:

* **Node.js** (versión recomendada: 18.x o superior)
* **npm**

Verifica su instalación con:

```powershell
node -v
npm -v
```

---

## **Paso 1: Instalar Angular CLI**

```powershell
npm install -g @angular/cli
```

---

## **Paso 2: Crear el proyecto**

```powershell
ng new MiProyecto
```

Durante la creación se te harán preguntas como:

### ¿Deseas añadir routing?

```powershell
? Would you like to add Angular routing? (y/N): y
```

### ¿Qué estilo de hoja de estilos deseas usar?

Selecciona con las flechas y confirma con Enter. Ejemplo:

```powershell
? Which stylesheet format would you like to use?
> CSS
  SCSS
  Sass
  Less
  Stylus
```

---

## **Paso 3: Entrar al proyecto**

```powershell
cd MiProyecto
```

---

## **Paso 4: Levantar el servidor de desarrollo**

```powershell
ng serve
```

Esto iniciará la aplicación en:
[http://localhost:4200](http://localhost:4200)

---

## **Estructura del proyecto**

```plaintext
MiProyecto/
├─ angular.json
├─ package.json
├─ tsconfig.json
├─ src/
│  ├─ main.ts
│  ├─ index.html
│  ├─ app/
│  │  ├─ app.module.ts
│  │  ├─ app.component.ts
│  │  ├─ app.component.html
│  │  └─ app.component.css
```

---

# Pruebas Unitarias con Angular (Karma + Jasmine)

Angular ya viene con soporte para pruebas unitarias usando **Karma** y **Jasmine**.

---

## Ejecutar las pruebas

```powershell
ng test
```

Esto abrirá una ventana del navegador y mostrará los resultados en tiempo real.

---

## Crear un archivo de prueba adicional

Por defecto, Angular genera archivos `.spec.ts` junto con tus componentes. Por ejemplo:

```plaintext
src/app/
├─ ejemplo/
│  ├─ ejemplo.component.ts
│  ├─ ejemplo.component.html
│  ├─ ejemplo.component.css
│  └─ ejemplo.component.spec.ts
```

Puedes crear componentes con pruebas automáticamente usando:

```powershell
ng generate component ejemplo
```

---

## **Para compilar la aplicación (modo producción)**

```powershell
ng build --configuration production
```

---

## **Para servir la app compilada**

Puedes usar un servidor como `http-server` para servir los archivos de `dist/`:

```powershell
npm install -g http-server
http-server dist/mi-proyecto
```
