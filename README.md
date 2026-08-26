# Python Kata

## 1. Python Kata

### Planteamiento

Tenemos una lista de recursos AWS obtenidos desde diferentes cuentas. Queremos detectar recursos que no cumplan nuestra política de tagging. Todo recurso debe tener los tags **owner** y **environment**. Implementa una función que devuelva los recursos no compliant indicando qué tags faltan.

> **Nota:** los datos de recursos AWS son ficticios y no provienen de una cuenta ni API real. El objetivo de esta kata no es AWS en sí, sino practicar el manejo de Python y la creación de funciones y tests unitarios.

```python
resources = [
    {"account": "prod", "type": "ec2", "id": "i-123",
     "tags": {"owner": "payments", "environment": "prod"}},
    {"account": "prod", "type": "s3", "id": "logs-prod",
     "tags": {"environment": "prod"}},
    {"account": "dev", "type": "ec2", "id": "i-456",
     "tags": {"owner": "platform", "environment": "dev"}},
    {"account": "dev", "type": "rds", "id": "db-001", "tags": {}},
]
```

## Requisitos

- [Docker](https://docs.docker.com/get-started/) (requerido): necesario para poder trabajar con el devcontainer del proyecto. Antes de empezar la práctica, comprueba que Docker está en ejecución lanzando:

  ```bash
  docker ps
  ```

  Si el comando falla (no responde o da error de conexión), arranca el demonio de Docker antes de continuar.

### Instalar la extensión Dev Containers en VS Code

Para abrir el proyecto directamente dentro del devcontainer desde VS Code, puedes instalar la extensión [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers):

1. Abre VS Code Quick Open con `Ctrl+P`.
2. Pega el siguiente comando y pulsa Enter:

   ```text
   ext install ms-vscode-remote.remote-containers
   ```

Una vez instalada la extensión, con el proyecto abierto en VS Code:

1. Abre la paleta de comandos con `Ctrl+Shift+P`.
2. Busca y selecciona **Dev Containers: Reopen in Container**.

VS Code reconstruirá (o reutilizará) el devcontainer definido en `.devcontainer/` y reabrirá la ventana ya conectada dentro del contenedor.

## Instalar dependencias

Este proyecto usa [uv](https://docs.astral.sh/uv/) para la gestión de dependencias.

```bash
uv sync
```

## Ejecutar los tests

```bash
uv run pytest
```

## Arrancar la aplicación

```bash
uv run python src/main.py
```

## Lint

```bash
uv run flake8 .
```
