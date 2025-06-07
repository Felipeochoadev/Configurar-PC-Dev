# Configuración de sqlite en Windows

Este documento describe cómo habilitar la extensión SQLite3 

---


## 1. Ir a la carpeta de instalación de PHP

Verifica la ruta de configuración:

```powershell
php --ini

```

Deberías ver:

```powershell
Loaded Configuration File: C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.4_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini

```
> ⚠️ **Nota**: si la ruta de configuracion esta vacia o dice none realice los pasos del instructivo de `PHP`.

Navegamos a la carpeta de instalacion

```powershell
cd C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.4_Microsoft.Winget.Source_8wekyb3d8bbwe

```

Para editar el php.ini abrimos el archivo .ini

```powershell
code php.ini

```

Busca las siguientes líneas y quita el ; al inicio para habilitarlas:

```ini
;extension=sqlite3
;extension=pdo_sqlite

```

Quedan asi:

```ini
extension=sqlite3
extension=pdo_sqlite

```

Guarda y cierra.

Verifica que PHP cargue sqlite correctamente:

```powershell
php -m | findstr sqlite3

```

## **Abrir Base de datos desde la consola**

Navegamos a la ruta donde esta base de datos SQLite

```powershell
cd /var/www/php/PruebaTecnica

```

Abrimos el .db desde la consola para ver la base de datos

```powershell
sqlite3 events.db

```

Verás el prompt de SQLite:
```powershell
SQLite version 3.x.x ...
Enter ".help" for usage hints.
sqlite>

```

## **Ver tablas y datos**

Ver todas las tablas
```sql
.tables

```

Ver la estructura de la tabla events
```sql
.schema events

```

Ver todos los registros:
```sql
SELECT * FROM events;

```

Salir de SQLite:
```sql
.exit

```

Si estás en ...> (prompt de continuación), termina con ; y enter
