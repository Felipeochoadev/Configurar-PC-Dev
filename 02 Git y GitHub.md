# Configuración de Git y GitHub

Este documento detalla los pasos necesarios para instalar, configurar y utilizar Git con GitHub, incluyendo la configuración de claves SSH y comandos básicos para manejar repositorios.

---

## Instalación de Git

Instalar Git en el equipo utilizando la terminal:

```shell
winget install --id Git.Git -e --source winget
```

Reiniciar la consola para aplicar los cambios.

---

## Configuración de Git

Configurar tu identidad en Git:

```shell
git config --global user.name "TuNombreEjemplo"
git config --global user.email "correo@ejemplo.com"
```

---

## Inicialización de un Repositorio Local

1. Iniciar Git en el directorio:
   ```shell
   git init
   ```

2. Cambiar a la rama principal:
   ```shell
   git branch -m main
   ```

3. Ver el estado de la rama:
   ```shell
   git status
   ```

---

## Comandos básicos de Git

- Agregar ficheros al área de preparación:
  ```shell
  git add .
  ```

- Sacar ficheros del área de preparación:
  ```shell
  git reset
  ```

- Crear un archivo `.gitignore` para ignorar ficheros:
  ```shell
  New-Item .gitignore -type file
  ```

- Hacer un commit:
  ```shell
  git commit -m "Descripción del cambio específico"
  ```

- Ver el log de cambios:
  ```shell
  git log
  ```

- Ver el log gráfico:
  ```shell
  git log --graph --pretty=oneline
  ```

- Restaurar un fichero a la última versión:
  ```shell
  git checkout HEAD nombre_fichero
  ```

- Ver los cambios:
  ```shell
  git diff
  ```

---

## Configuración de GitHub con Clave SSH

### Crear clave SSH

1. Crear la carpeta `.ssh` (si no existe):
   ```shell
   mkdir C:\Users\Ejemplo\.ssh
   ```

2. Moverse a la carpeta:
   ```shell
   cd C:\Users\Ejemplo\.ssh
   ```

3. Crear una clave SSH:
   ```shell
   ssh-keygen -t ed25519 -C "correo@ejemplo.com"
   ```

   - Presiona `Enter` para usar el nombre predeterminado (`id_ed25519`).
   - Asigna una contraseña para la clave.

4. Inicializar el agente SSH:
   ```shell
   Get-Service -Name ssh-agent | Set-Service -StartupType Manual
   Start-Service ssh-agent
   ```

5. Agregar la clave al agente:
   ```shell
   ssh-add C:/Users/Ejemplo/.ssh/id_ed25519
   ```

6. Copiar la clave pública:
   ```shell
   cat ~/.ssh/id_ed25519.pub | clip
   ```

### Agregar clave SSH a GitHub

1. En GitHub, ir a Configuración:
   - Foto de perfil > **Settings**.
   - En la sección "Acceso", seleccionar **Claves SSH y GPG**.

2. Hacer clic en **Nueva clave SSH**.

3. Agregar:
   - **Título**: Una descripción como "Laptop Personal".
   - **Clave**: Pegar la clave pública copiada.

4. Hacer clic en **Agregar clave SSH**.

### Probar conectividad

```shell
ssh -T git@github.com
```

Responder con `yes` si es necesario.

---

## Configuración del remoto y sincronización con GitHub

### Agregar remoto

1. Agregar el origen remoto (cambia `UsuarioEjemplo` y `RepositorioEjemplo`):
   ```shell
   git remote add origin git@github.com:UsuarioEjemplo/RepositorioEjemplo.git
   ```

2. Verificar el remoto:
   ```shell
   git remote -v
   ```

### Subir cambios al repositorio remoto

1. Fusionar historias al subir el primer repositorio:
   ```shell
   git pull origin main --allow-unrelated-histories
   git merge origin/main
   ```

2. Subir cambios:
   ```shell
   git push -u origin main
   ```

### Clonar repositorio existente

1. Clonar el repositorio:
   ```shell
   git clone git@github.com:UsuarioEjemplo/RepositorioEjemplo.git
   ```

2. Instalar dependencias y ejecutar (si aplica):
   ```shell
   npm install
   ng serve
   ```

### Actualizar repositorio local

1. Descargar cambios del remoto:
   ```shell
   git pull origin main
   ```

---

## Otros comandos útiles

- Eliminar un remoto:
  ```shell
  git remote remove origin
  ```

- Ver log de cambios remoto:
  ```shell
  git fetch origin
  git log origin/main --oneline --graph
  ```

