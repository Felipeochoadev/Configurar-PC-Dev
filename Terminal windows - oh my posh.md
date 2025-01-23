# Actualizar Consola de Windows

## 1. Descargar e instalar herramientas necesarias

### Windows Terminal
Descargar e instalar desde la Microsoft Store:
[Windows Terminal](https://www.microsoft.com/es-es/p/windows-terminal/9n0dx20hk701)

### PowerShell
Descargar e instalar desde Microsoft Store:
[PowerShell](https://apps.microsoft.com/detail/9mz1snwt0n5d)

### Oh My Posh
Instalar Oh My Posh ejecutando el siguiente comando en PowerShell:
```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

---

## 2. Configurar PowerShell como predeterminado en Windows Terminal

1. Hacer clic derecho en la barra de la consola en un espacio vacío (al lado de los botones de minimizar y cerrar).
2. Seleccionar "Configuración".
3. En el menú de configuración, ir a la sección **Inicio**.
4. En la opcion **Perfil predeterminado** seleccionar de la lista la opción "PowerShell".

NOTA: hay dos opciones similares **Windows PowerShell** no es. Se debe selecionar la que solo dice **PowerShell**

---

## 3. Configuración de PowerShell

### Crear o editar archivo de configuración de PowerShell

Si ya tienes el archivo de configuración:
```powershell
notepad $PROFILE
```

Si no tienes el archivo, crearlo con:
```powershell
New-Item -Path $PROFILE -Type File -Force
```

En el Bloc de notas que se abre, pegar el siguiente contenido:
```powershell
import-module -name terminal-icons
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/cobalt2.omp.json" | Invoke-Expression
clear
```

Guardar y cerrar el archivo.

### Configurar permisos de ejecución
Los comandos listados a continuacion se ejecutan desde el PowerShell:


Para evitar problemas con la configuración de scripts se debe ejecutar como administrador:
```powershell
Set-ExecutionPolicy Unrestricted
```

### Instalar iconos
Instalar módulo de iconos:
```powershell
Install-Module -Name Terminal-Icons -RequiredVersion 0.9.0
```

---

## 4. Personalizar esquema de Windows Terminal

### Agregar fondo personalizado

1. Abrir configuración de Windows Terminal con **Ctrl + ,**.
2. Buscar el bloque de configuración "defaults" y agregar:
```json
"defaults": {
    "backgroundImage": "C:\\FondoTerminal.jpg",
    "backgroundImageOpacity": 0.1
},
```
3. Guardar los cambios y cerrar.


### Activar copiado automático con la selección
1. Hacer clic derecho en la barra de la consola en un espacio vacío (al lado de los botones de minimizar y cerrar).
2. Seleccionar "Configuración".
3. En el menú de configuración, ir a la sección **Interacción**.
4. Activar la opción "Copiar selección automáticamente en el portapapeles".

---

## 5. Reiniciar la consola
Reiniciar Windows Terminal para aplicar todos los cambios.