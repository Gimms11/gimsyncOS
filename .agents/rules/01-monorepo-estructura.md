# Regla 01: Límites y Estructura del Monorepo

## Directorios y Responsabilidades
- `docs/`: Documentación centralizada. NUNCA crear archivos `.md`, `.doc` o `.txt` sueltos en la raíz del proyecto.
- `backend/`: Monolito modular Spring Boot 3 (Java 21). Contiene la lógica transaccional, persistencia, seguridad RBAC y APIs REST.
- `services/`: Microservicios FastAPI (Python 3.11+). Tareas asíncronas, analítica y procesamiento por lotes.
- `frontend/`: Web Next.js 14+ (App Router). Landing, catálogo e-commerce, POS counter de recepción y panel admin.
- `mobile/`: App de socios React Native + Expo (Fase 2).
- `infra/`: Docker compose, Dockerfiles y configuraciones Nginx.
- `db/`: Scripts SQL, migraciones versionadas y seeds.

## Archivos Permitidos en Raíz
Solo se permiten archivos globales estándar: `.gitignore`, `docker-compose.yml`, `README.md`, `AGENTS.md`, `CLAUDE.md`. Prohibido crear archivos temporales o de código en la raíz.
