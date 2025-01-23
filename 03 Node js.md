# Configuración de Node.js en Windows

Este documento describe los pasos necesarios para instalar y verificar Node.js en un sistema Windows utilizando la terminal. Sigue estas instrucciones para configurar tu entorno de desarrollo.

---

## **Descargar e instalar Node.js**

Node.js puede instalarse fácilmente utilizando el gestor de paquetes `winget` incluido en Windows.

### **Pasos:**

1. Abre la terminal de Windows.
2. Ejecuta el siguiente comando para instalar Node.js:

   ```powershell
   winget install OpenJS.NodeJS
   ```

   > **Nota:** Este comando instalará la última versión estable de Node.js. Si `winget` solicita aceptar términos de uso, confirma la instalación.

---

## Reiniciar la consola
Reiniciar Windows Terminal para aplicar todos los cambios.

## **Verificar la instalación**

Tras completar la instalación, verifica que tanto Node.js como npm se hayan instalado correctamente.

### **Comprobación de Node.js:**

Ejecuta el siguiente comando para comprobar la versión instalada de Node.js:

```powershell
node -v
```

Esto debería mostrar la versión actual de Node.js instalada en tu sistema.

### **Comprobación de npm:**

Verifica la versión instalada de npm (el gestor de paquetes de Node.js) ejecutando:

```powershell
npm -v
```

Si ambos comandos muestran versiones, significa que la instalación fue exitosa.

---

## **Próximos pasos**

Ahora que tienes Node.js configurado, puedes:

- Desarrollar aplicaciones utilizando JavaScript en el servidor.
- Instalar paquetes y dependencias con npm.
- Configurar entornos de desarrollo para frameworks como React, Angular, o Express.

Con estos pasos, tu entorno Windows estará listo para proyectos basados en Node.js.

