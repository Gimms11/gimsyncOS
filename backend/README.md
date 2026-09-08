# Backend — Monolito Modular (Spring Boot)

Servicio backend principal construido como un monolito modular con **Java 21 / Spring Boot 3**. Centraliza las reglas de negocio, persistencia relacional, seguridad y APIs REST.

## Arquitectura Modular

Estructurado en módulos de dominio desacoplados internamente:

```
backend/
├── src/main/java/com/gym/
│   ├── auth/              # Autenticación, JWT, usuarios y roles (RBAC)
│   ├── memberships/       # Planes, membresías activas, historial, congelamientos
│   ├── catalog/           # Productos, categorías, stock e inventario
│   ├── orders/            # Carrito, pedidos web y ventas POS counter
│   ├── billing/           # Integración con PSE (Nubefact/SUNAT), boletas y facturas
│   ├── customers/         # Clientes, prospectos (leads) e importador desde EVO
│   └── shared/            # Modelos comunes, excepciones, utilitarios
└── src/main/resources/
    ├── db/migration/      # Migraciones Flyway
    └── application.yml    # Configuración de entorno
```

## Requisitos Previos

- JDK 21+
- Maven 3.9+ (o wrapper `./mvnw`)
- PostgreSQL 15+
