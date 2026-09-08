# Infraestructura y Despliegue

Configuraciones de contenedores, proxies inversos y scripts de orquestación local y producción.

## Estructura

```
infra/
├── docker/
│   ├── Dockerfile.backend      # Build multi-stage para Spring Boot (JDK 21)
│   ├── Dockerfile.frontend     # Build multi-stage para Next.js (Node 20)
│   └── Dockerfile.services     # Build para FastAPI (Python 3.11)
├── nginx/
│   └── default.conf            # Proxy inverso y enrutamiento SSL/TLS
└── scripts/                    # Scripts de backup y mantenimiento
```

## Ejecución Local

Desde la raíz del proyecto:

```bash
docker compose -f docker-compose.yml up -d
```
