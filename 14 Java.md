# Configuración de java devdevelopment en Windows
Este documento detalla como instalar paso a paso el java por terminal.

---

## buscar el build del OpenJDK usando el siguiente comando
```bash
winget search Microsoft.OpenJDK

```
Esto mostrala la lista disponbile ejemplo:, Microsoft.OpenJDK.25

## Install the paquete usando el IDS, para la ultima version
```bash
winget install Microsoft.OpenJDK.25

```
La instalacion se ejecutara de manera silenciosa y se configurar automaticamente.

## Verificar la instalacions
```bash
java -version

```
Si todo es correto mostrara la version del java.