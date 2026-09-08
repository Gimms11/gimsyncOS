# Convenciones de Código y Mensajes de Commit

Estándares acordados para mantener uniformidad técnica en el repositorio.

## 1. Convención de Commits (Conventional Commits)

Formato: `<tipo>(<alcance>): <descripción corta>`

### Tipos Permitidos:
- `feat`: Nueva funcionalidad para el usuario.
- `fix`: Corrección de un bug.
- `docs`: Modificaciones exclusivas en documentación.
- `refactor`: Cambio en el código que no corrige un bug ni añade una feature.
- `chore`: Tareas de build, dependencias o configuración sin impacto funcional.
- `test`: Añadir o corregir pruebas unitarias/integración.

### Ejemplos:
- `feat(auth): implementar generador de token JWT y refresh token`
- `fix(billing): corregir redondeo de dos decimales en IGV de factura`
- `docs(negocio): agregar modelos híbridos de venta y pricing`

## 2. Nomenclatura por Tecnología

- **Java / Spring Boot:**
  - Clases: `PascalCase` (ej. `MembershipService`, `ProductController`).
  - Métodos y variables: `camelCase` (ej. `findByDocumentNumber`).
  - Constantes: `UPPER_SNAKE_CASE` (ej. `DEFAULT_PAGE_SIZE`).
- **Python / FastAPI:**
  - Módulos y funciones: `snake_case` (ej. `generate_retention_report`).
  - Clases y esquemas Pydantic: `PascalCase` (ej. `SalesSummaryResponse`).
- **TypeScript / Next.js:**
  - Componentes: `PascalCase` (ej. `CounterCartDrawer.tsx`).
  - Hooks y utilidades: `camelCase` (ej. `useCart.ts`, `formatCurrency.ts`).
