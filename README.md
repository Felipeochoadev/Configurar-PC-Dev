# Configuracion del computador para desarrollar

Bienvenido, este es un repositorio diseñado para documentar y compartir todo lo necesario para configurar un entorno de desarrollo profesional y funcional. Este repositorio tiene como objetivo centralizar conocimientos y guías que te permitirán preparar tu sistema para trabajar con herramientas de desarrollo, desplegar proyectos de manera eficiente.

## Propósito del repositorio

El propósito de este repositorio es ofrecer una guía clara y profesional para:

1. Configurar entornos de desarrollo en Windows.


---

## Contenido del repositorio

### Configuración de herramientas esenciales
- **Configurar PowerShell de Windows**: Pasos para optimizar tu terminal con personalización.
- **Configurar GitHub local**: Cómo gestionar repositorios localmente y sincronizarlos con GitHub.
- **Configuración de Node.js**: Instrucciones para preparar tu entorno.
- **Configuración de React**: Instrucciones para preparar tu entorno.
- **Configuración de Angular**: Instrucciones para preparar tu entorno.
- **Configuración de Php**: Instrucciones para preparar tu entorno.
- **Configuración de Laravel**: Instrucciones para preparar tu entorno.
- **Configuración de Mysql**: Instrucciones para preparar tu entorno.
- **Configuración de Postgresql**: Instrucciones para preparar tu entorno.
- **Configuración de Sqlite**: Instrucciones para preparar tu entorno.
- **Instalación y configuración de herramientas clave**:
  - Visual Studio Code
  - PuTTY
  - Filezilla


## Creación de estructura de directorios para proyectos

Una vez configuradas tus herramientas básicas, es recomendable organizar tus proyectos dentro de una estructura de carpetas que facilite el acceso, mantenimiento y escalabilidad. A continuación, se muestra cómo puedes crear una estructura común utilizando la terminal de Windows.

### Ruta base sugerida

Usaremos la ruta:

```
C:\var\www\

```

Dentro de esta ruta crearemos subdirectorios para los diferentes tipos de proyectos que vayas a desarrollar: `angular`, `laravel`, `php`, `react`.

### Comando para crear la estructura desde PowerShell

Abre PowerShell como administrador y ejecuta el siguiente comando:

```powershell
mkdir C:\var\www
mkdir C:\var\www\angular, C:\var\www\laravel, C:\var\www\php, C:\var\www\react, C:\var\www\docusaurus

```

> ⚠️ **Nota**: En PowerShell, puedes usar comas para crear múltiples carpetas dentro de un mismo comando `mkdir`.

Una vez creada esta estructura, puedes clonar o iniciar tus proyectos en cada subcarpeta, manteniendo así un entorno limpio y organizado.


### Organización interna de proyectos

Dentro de cada subcarpeta (`angular`, `laravel`, `php`, `react`), los proyectos estarán organizados como repositorios independientes de Git. Esto significa que cada carpeta de proyecto puede ser inicializada, versionada y gestionada de forma separada con Git.

Para facilitar la identificación y la asociación con la tecnología correspondiente, los nombres de las carpetas de los proyectos seguirán una convención clara, por ejemplo, para proyectos de React:


```
react-curso-02-triqui
react-landing-01
react-page-01
react-backoffice-01

```


```less
📁 Cada carpeta representa un proyecto independiente, y se recomienda que el nombre incluya:
> La tecnología (ej. `react`, `laravel`, etc.)
> Un tipo (ej. `curso`, `landing`, `page`, `backoffice`)
> Un número de secuencia (`01`, `02`, etc.)
> Un nombre descriptivo breve si es necesario (`triqui`, `admin`, `formulario`, etc.)

```

Esta convención mejora la claridad, facilita la navegación entre múltiples proyectos y permite trabajar con distintos repositorios Git sin conflictos.


esto hacer en el servidor en putty para formatear el log

```powershell
cat << 'EOF' > /usr/local/bin/verlogs
#!/usr/bin/env bash

LINES=${1:-50}

docker exec -i felipeochoa_backend tail -f -n "$LINES" /var/www/html/log/errores.log | python3 -c '
import sys, re, json

C_RESET = "\033[0m"
C_CYAN  = "\033[36m"
C_YEL   = "\033[33m"
C_GREEN = "\033[32m"

def format_json(match):
    raw = match.group(0)
    try:
        data = json.loads(raw)
        if isinstance(data, dict) and "respuesta" in data and isinstance(data["respuesta"], str):
            try:
                data["respuesta"] = json.loads(data["respuesta"])
            except Exception:
                pass
        pretty = json.dumps(data, indent=2, ensure_ascii=False)
        return f"\n{C_GREEN}{pretty}{C_RESET}\n"
    except Exception:
        return raw

first_entry = True
for line in sys.stdin:
    # Si la línea empieza con timestamp de log
    m = re.match(r"^(\[\d{2}-[A-Za-z]+-\d{4} [^\]]+\])\s*(\[[a-zA-Z0-9_.-]+:\d+\])?\s*(.*)", line, re.DOTALL)
    if m:
        timestamp, script_line, rest = m.group(1), m.group(2), m.group(3)
        
        # Salto de línea separador entre logs
        if not first_entry:
            sys.stdout.write("\n")
        first_entry = False

        # Línea 1: Timestamp
        sys.stdout.write(f"{C_CYAN}{timestamp}{C_RESET}\n")

        # Línea 2: [archivo:linea] (si existe)
        if script_line:
            sys.stdout.write(f"{C_YEL}{script_line}{C_RESET}\n")

        line = rest

    # Expandir saltos de línea y formatear JSON sin colores rojos
    line = line.replace("\\n", "\n  ")
    line = re.sub(r"\{[\s\S]*\}", format_json, line)
    print(line, end="", flush=True)
'
EOF
chmod +x /usr/local/bin/verlogs
```

Resultado al ejecutar verlogs:
