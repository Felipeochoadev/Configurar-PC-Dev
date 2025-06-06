# Configuración de php en Windows

Este documento explica cómo instalar PHP en Windows . Ideal para entornos de desarrollo ligeros o personalizados.

---

## **Buscar paquetes PHP en Winget**

Todas las compilaciones de PHP de Windows se encuentran bajo el PHP.PHPespacio de nombres, y el ID completo del paquete se construye agregando el número de versión principal y secundaria de las versiones de PHP al espacio de nombres.

Por ejemplo, PHP 8.4 se llama PHP.PHP.8.4.

Para buscar todos los paquetes PHP, ejecute:

## **Instalar PHP**
```powershell
winget search PHP.PHP

```

`winget search PHP.PHP` muestra todos los paquetes PHP disponibles y sus últimas versiones.


## **Instalar una versión de PHP**
Si bien el comando winget downloadwinget install solo descarga una versión determinada de PHP, el comando descarga una compilación de PHP de Windows, la verifica, la extrae y actualiza la variable PATH del sistema para que esté phpdisponible para ejecutarse desde la línea de comandos.

```powershell
winget install PHP.PHP.8.4

```

`winget install PHP.PHP.8.4` instala PHP en el sistema como una aplicación portátil y actualiza la variable `PATH` en el sistema

Reiniciar la consola y verifica su instalación con:

```powershell
php -v

```

## Actualizar paquetes PHP**
Cuando está disponible una nueva versión de parche de una versión de PHP ya instalada, winget updatela muestra.

Ejecutar winget update PHP.PHP.%version%para actualizar a la última versión del parche para esa versión. Por ejemplo, para actualizar PHP 8.4 a la última versión, ejecutar:

```powershell
winget update PHP.PHP.8.4

```

## Configurar archivo php.ini**

Buscar la ruta de instalacion del PHP en PowerShell (esto buscará en todo el disco C, puede tardar un poco):

```powershell
Get-ChildItem -Path C:\ -Filter php.exe -Recurse -ErrorAction SilentlyContinue -Force

```

Nos mostrara algo parecido a lo siguiente como resultado


```powershell

        Directory: C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.4_Microsoft.Winget.Source_8wekyb3d8bbwe


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---       3/06/2025  5:39 p. m.         182784 ﬓ  php.exe

```

Navegamos a la carpeta de instalacion

```powershell
cd C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.4_Microsoft.Winget.Source_8wekyb3d8bbwe

```

Buscamos los archivos ini por defecto

```powershell
dir php.ini-*

```

Creamos el archivo ini del php.ini-development

```powershell
copy php.ini-development php.ini

```

Configuramos el .ini para habilitar las extensiones

Para editar el php.ini abrimos el archivo .ini

```powershell
code php.ini

```

Busca las siguientes líneas y quita el ; al inicio para habilitarlas:

```powershell
; On windows:
;extension_dir = "ext"

```

Quedan asi:

```powershell
; On windows:
extension_dir = "ext"

```

Guarda y cierra.


Verifica que PHP cargue el archivo de configuración:

```powershell
php --ini

```

Deberías ver:

```powershell
Loaded Configuration File: C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.4_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini

```

## Iniciar un servidor local con PHP (modo desarrollo)**
Por defecto, php buscará un archivo index.php en el directorio actual. asegúrate de estar en el directorio correcto:

```powershell
cd /var/www/php/Proyecto

```

utilizamos el siguiente comando
```powershell
php -S localhost:8000

```

si queremos inicializar un .php diferente al index.php usamos el siguiente comando

```powershell
php -S localhost:8000 nombre.php

```