# Base de Datos — PostgreSQL

Scripts de esquema relacional, migraciones versionadas y datos de prueba (seeds).

## Estructura

```
db/
├── migrations/                # Scripts SQL incrementales (V1__..., V2__...)
├── seeds/                     # Datos iniciales (catálogo base, roles, usuarios demo)
└── backups/                   # Políticas y scripts de dumps
```

## Motor

- **Motor Principal:** PostgreSQL 15+
- **Extensiones recomendadas:** `uuid-ossp`, `pgcrypto`
