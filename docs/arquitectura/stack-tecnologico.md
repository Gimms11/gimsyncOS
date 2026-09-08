# Stack Tecnológico y Decisiones de Arquitectura

Documento técnico que detalla las tecnologías seleccionadas, sus roles y la justificación técnica para el desarrollo de la plataforma de gestión del gimnasio.

---

## 1. Visión General del Sistema

El sistema está diseñado para reemplazar integralmente las funciones operativas, comerciales y de facturación de ABC EVO y el software Click, soportando escalabilidad futura hacia control de acceso por hardware y aplicación móvil para alumnos.

```
                  ┌──────────────────────────────────────────────┐
                  │                 CLIENTES                     │
                  │  ┌───────────────┐        ┌───────────────┐  │
                  │  │ Navegador Web │        │   App Móvil   │  │
                  │  │   (Next.js)   │        │ (Expo/ReactN) │  │
                  │  └───────┬───────┘        └───────┬───────┘  │
                  └──────────┼────────────────────────┼──────────┘
                             │                        │
                             ▼                        ▼
                  ┌──────────────────────────────────────────────┐
                  │          REVERSE PROXY / GATEWAY             │
                  │                (Nginx / SSL)                 │
                  └──────────────────────┬───────────────────────┘
                                         │
                                         ▼
                  ┌──────────────────────────────────────────────┐
                  │             BACKEND PRINCIPAL                │
                  │         Spring Boot 3 (Java 21)             │
                  │       (Arquitectura Monolito Modular)        │
                  │                                              │
                  │  ┌───────────┐ ┌───────────┐ ┌────────────┐  │
                  │  │ Auth/RBAC │ │  Ventas   │ │ Membresías │  │
                  │  └───────────┘ └───────────┘ └────────────┘  │
                  │  ┌───────────┐ ┌───────────┐ ┌────────────┐  │
                  │  │ Catálogo  │ │ Clientes  │ │Facturación │  │
                  │  └───────────┘ └───────────┘ └────────────┘  │
                  └──────────────┬──────────────────┬────────────┘
                                 │                  │
                         Async   ▼                  ▼
                  ┌──────────────────┐    ┌──────────────────────┐
                  │  MICROSERVICIOS  │    │    BASE DE DATOS     │
                  │     FastAPI      │    │    PostgreSQL 16     │
                  │ (Analytics/Jobs) │    │  (Relacional ACID)   │
                  └──────────────────┘    └──────────────────────┘
```

---

## 2. Componentes del Stack

### 2.1 Backend Principal: Spring Boot 3 + Java 21
- **Rol:** Núcleo transaccional, lógica de negocio central, persistencia y seguridad.
- **Patrón:** **Monolito Modular** (Modular Monolith). Permite desarrollo rápido, despliegue unificado y mantenibilidad sin la sobrecarga operativa de microservicios distribuidos.
- **Justificación:**
  - Robustez tipada, transaccionalidad ACID estricta para inventario, caja y pagos.
  - Ecosistema Spring Security con JWT para control de accesos RBAC (Administrador, Recepción, Cliente).
  - Migraciones de base de datos controladas mediante Flyway.

### 2.2 Microservicios Auxiliares: FastAPI + Python 3.11+
- **Rol:** Tareas secundarias, reportería pesada, analítica de retención/churn y jobs asíncronos.
- **Justificación:**
  - Python sobresale en manipulación de datos (Pandas) y generación de reportes ejecutivos.
  - FastAPI ofrece velocidad asíncrona nativa (`asyncio`) y bajo consumo de recursos para workers auxiliares.

### 2.3 Frontend Web: Next.js 14+ (App Router) + TypeScript
- **Rol:** Portal web público, catálogo e-commerce para clientes, pantalla de venta POS para recepcionista (Gustavo) y panel de control del administrador (Iván).
- **Justificación:**
  - Server-Side Rendering (SSR) y Static Site Generation (SSG) para SEO en el portal público de captación y compra de membresías.
  - React moderno para interfaces de counter rápidas e interactivas con atajos de teclado y lectores de códigos de barras.

### 2.4 Aplicación Móvil (Fase 2): React Native + Expo
- **Rol:** Carnet digital del socio, check-in QR en counter, visualización de vigencia y notificaciones push.
- **Justificación:**
  - Código único para Android e iOS.
  - Expo simplifica el ciclo de compilación y despliegue OTA (Over-the-Air) sin fricción en tiendas de apps.

### 2.5 Base de Datos: PostgreSQL 16
- **Rol:** Motor relacional central.
- **Justificación:**
  - Consistencia relacional, integridad referencial y soporte nativo de JSONB para configuraciones flexibles.

### 2.6 Infraestructura y Despliegue: Docker + Nginx
- **Rol:** Contenedores estandarizados y proxy inverso con terminación SSL/TLS automática (Let's Encrypt).
