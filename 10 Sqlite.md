# Configuración de sqlite en Windows



ini
Copiar
Editar
;extension=sqlite3
y quita el ; para que quede:

ini
Copiar
Editar
extension=sqlite3
Guarda y cierra.

Verifica que PHP cargue el archivo de configuración:

powershell
Copiar
Editar
php --ini
Deberías ver:

mathematica
Copiar
Editar
Loaded Configuration File: C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.4_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini
Verifica que la extensión esté habilitada:

powershell
Copiar
Editar
php -m | findstr sqlite3




Cuando está disponible una nueva versión de parche de una versión de PHP ya instalada, winget updatela muestra.

Ejecutar winget update PHP.PHP.%version%para actualizar a la última versión del parche para esa versión. Por ejemplo, para actualizar PHP 8.4 a la última versión, ejecutar:

```powershell
winget update PHP.PHP.8.4

```
