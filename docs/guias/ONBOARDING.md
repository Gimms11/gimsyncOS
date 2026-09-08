# Guía de Onboarding para Desarrolladores

Bienvenido al equipo de desarrollo de la plataforma de gestión de gimnasio. Sigue estos pasos para configurar tu entorno local.

## 1. Herramientas Obligatorias

- **Git** 2.40+
- **Docker Desktop** (o Docker Engine + Docker Compose)
- **JDK 21** (Eclipse Temurin / Amazon Corretto recomendado)
- **Node.js** 20 LTS o superior
- **Python** 3.11 o superior
- **IDE Recomendado:** IntelliJ IDEA (para Spring Boot), VS Code / Cursor / WebStorm (para Next.js/Expo)

## 2. Puesta en Marcha Rápida (Entorno Local)

1. **Clonar el proyecto:**
   ```bash
   git clone <URL_DEL_REPOSITORIO>
   cd plataforma-gym
   ```

2. **Levantar base de datos con Docker:**
   ```bash
   docker compose up postgres -d
   ```
   *PostgreSQL quedará escuchando en `localhost:5432` con usuario `gym_user` y base de datos `gym_db`.*

3. **Verificar documentación:**
   - Lee el SRS vigente en [`docs/requerimientos/v2/SRS_Fase_1_v2.1.md`](../requerimientos/v2/SRS_Fase_1_v2.1.md).
   - Revisa el modelo conceptual en [`docs/base-de-datos/modelo-conceptual.md`](../base-de-datos/modelo-conceptual.md).
   - Consulta el modelo comercial en [`docs/negocio/modelo-de-venta-y-monetizacion.md`](../negocio/modelo-de-venta-y-monetizacion.md).
