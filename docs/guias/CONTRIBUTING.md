# Guía de Contribución

Reglas y buenas prácticas para colaborar en el repositorio.

## 1. Estrategia de Ramas (GitFlow Simplificado)

- `main`: Código en producción, estable y desplegable. Protegida contra pushes directos.
- `develop`: Rama de integración para el siguiente release.
- `feature/<nombre>`: Nuevas funcionalidades (ej. `feature/modulo-auth-spring`).
- `fix/<nombre>`: Corrección de bugs (ej. `fix/calculo-igv-boleta`).

## 2. Flujo de Trabajo

1. Clona el repositorio y crea tu rama desde `develop`:
   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/nombre-funcionalidad
   ```
2. Realiza cambios atómicos y estructurados.
3. Asegura que los tests locales compilen y pasen.
4. Abre un Pull Request (PR) apuntando hacia `develop`.
5. Requiere al menos una aprobación (code review) antes de hacer merge.
