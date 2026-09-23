# IDRD Laboratorio - Entorno Docker Unificado

Este repositorio contiene la configuración de infraestructura para desplegar y ejecutar el ecosistema completo del Laboratorio mediante **Docker Compose**.

---

## Arquitectura del Entorno

```text
  Frontend Angular
         │
         ▼
       Nginx (Proxy inverso / Servidor Web)
         │
         ▼
   Backend NestJS
         │
         ▼
     PostgreSQL
```

---

## Requisitos previos

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (o Docker Engine + Docker Compose) instalado y ejecutándose.
- Git.

---

## Estructura del Proyecto

Antes de desplegar, asegúrate de clonar los repositorios del **Frontend** y **Backend** dentro de este mismo nivel de directorio o mantener la estructura referenciada en el archivo `docker-compose.yml`:

```text
idrd-workspace/
├── idrd-materiales-backend/
├── idrd-materiales-frontend/
└── idrd-docker/
```

---

## Instrucciones de Despliegue

### 1. Iniciar los servicios

Desde el directorio `idrd-docker`, ejecuta:

```bash
docker compose up -d --build
```

> **Nota:** La opción `-d` ejecuta los contenedores en segundo plano y `--build` fuerza la reconstrucción de las imágenes si hubo cambios en el código.

### 2. Verificar que los contenedores estén corriendo

```bash
docker compose ps
```

---

## Accesos a la Aplicación

Una vez levantados los contenedores, los servicios estarán disponibles en:

| Servicio | Dirección URL |
| :--- | :--- |
| **Aplicación Frontend** | `http://localhost` |
| **API Backend** | `http://localhost:3000` |
| **Documentación Swagger** | `http://localhost:3000/api` |

---

## Comandos de Gestión Útiles

### Ver logs en tiempo real
```bash
docker compose logs -f
```

### Detener los servicios
```bash
docker compose stop
```

### Detener y eliminar contenedores y redes
```bash
docker compose down
```

### Reiniciar un servicio específico
```bash
docker compose restart backend
```