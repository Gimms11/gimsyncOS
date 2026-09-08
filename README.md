# plataforma-gym
## Plataforma de Gestión Comercial para Gimnasio — Reemplazo de ABC EVO

> Monorepo del proyecto. Incluye backend (Spring Boot), microservicios auxiliares (FastAPI), frontend web (Next.js) y aplicación móvil (React Native + Expo).

---

### Estructura del Repositorio

```
plataforma-gym/
│
├── docs/                          # Documentación completa del proyecto
│   ├── README.md                  # Índice de toda la documentación
│   ├── reuniones/                 # Actas, transcripciones y audios
│   ├── requerimientos/            # SRS versionados
│   ├── negocio/                   # Propuestas comerciales, pricing y modelos de venta
│   ├── analisis-previo/           # Documentación pre-reunión (análisis EVO)
│   ├── arquitectura/              # Diagramas, decisiones técnicas, ADRs
│   ├── api/                       # Contratos de API (OpenAPI/Swagger)
│   ├── base-de-datos/             # Modelo ER, migraciones, diccionario de datos
│   ├── guias/                     # Guías de contribución, estilo, onboarding
│   └── assets/                    # Imágenes, diagramas, recursos de los docs
│
├── backend/                       # Monolito modular — Spring Boot (Java/Kotlin)
│   └── .gitkeep
│
├── services/                      # Microservicios auxiliares — FastAPI (Python)
│   └── .gitkeep
│
├── frontend/                      # Aplicación web — Next.js
│   └── .gitkeep
│
├── mobile/                        # Aplicación móvil — React Native + Expo
│   └── .gitkeep
│
├── infra/                         # Docker, nginx, scripts de despliegue
│   └── .gitkeep
│
├── db/                            # Scripts SQL, seeds, migraciones standalone
│   └── .gitkeep
│
├── .gitignore
├── docker-compose.yml
├── LICENSE
└── README.md                      # Este archivo
```

### Stack Tecnológico

| Capa | Tecnología | Directorio |
| :--- | :--- | :--- |
| Backend principal | Spring Boot (monolito modular) | `backend/` |
| Microservicios auxiliares | FastAPI (Python) | `services/` |
| Frontend web | Next.js (React) | `frontend/` |
| App móvil | React Native + Expo | `mobile/` |
| Base de datos | PostgreSQL | `db/` |
| Infraestructura | Docker, Nginx | `infra/` |

### Documentación

Toda la documentación del proyecto se encuentra en [`docs/`](./docs/README.md).

### Licencia

Por definir.
