# CLAUDE.md — Directrices para Claude Code

Monorepo de plataforma de gestión comercial para gimnasio (reemplazo de ABC EVO). Reglas universales detalladas en [`AGENTS.md`](./AGENTS.md).

---

## 1. Estructura del Monorepo

- `docs/`: Documentación central. Prohibido crear archivos sueltos en raíz.
- `backend/`: Monolito modular Spring Boot 3 (Java 21). Módulos: auth, memberships, catalog, orders, billing, customers.
- `services/`: Microservicios auxiliares FastAPI (Python 3.11+). Analytics y workers asíncronos.
- `frontend/`: Web pública, e-commerce, POS counter y panel admin en Next.js 14+ (TypeScript).
- `mobile/`: App socios en React Native + Expo (Fase 2).
- `infra/`: Docker compose y Nginx reverse proxy.
- `db/`: Migraciones y seeds SQL (PostgreSQL).

---

## 2. Casos Específicos para Agregar Documentación (`docs/`)

Cualquier adición documental debe seguir el caso que corresponda:

1. **Caso 1: Fin de Reunión:** Formatear `docs/reuniones/YYYY-MM-DD_<nombre>/transcripcion.md` (timestamps `[MM:SS]`) + `acta.md` (plantilla obligatoria). Audios solo en Google Drive (nunca en Git). Actualizar `docs/reuniones/README.md` y evaluar impacto en SRS y Decisiones Pendientes.
2. **Caso 2: Requerimientos (SRS):** `docs/requerimientos/v<N>/`. Cambios menores = editar SRS vigente, bump decimal (v2.1 -> v2.2) y registrar en control de versiones. Cambios mayores = crear `v(N+1)/`. Actualizar `docs/requerimientos/README.md`.
3. **Caso 3: Decisiones de Arquitectura (ADR):** `docs/arquitectura/adr/NNN_<titulo_kebab_case>.md` usando `000_plantilla.md`. Actualizar `docs/arquitectura/README.md`.
4. **Caso 4: Base de Datos:** `docs/base-de-datos/` (`modelo-conceptual.md` con Mermaid ER, `diccionario-datos.md`). Sincronizar con scripts Flyway. Actualizar `docs/base-de-datos/README.md`.
5. **Caso 5: Contratos de API:** `docs/api/` (OpenAPI specs o endpoints markdown con método, ruta, auth, request/response y códigos HTTP). Actualizar `docs/api/README.md`.
6. **Caso 6: Negocio y Pricing:** `docs/negocio/` (propuestas comerciales, análisis de monetización). **Prohibido inventar precios o comisiones.** Actualizar `docs/negocio/README.md`.
7. **Caso 7: Guías del Equipo:** `docs/guias/` (`CONTRIBUTING.md`, `CONVENCIONES.md`, `ONBOARDING.md`). Actualizar `docs/guias/README.md`.
8. **Caso 8: Diagramas y Activos:** `docs/arquitectura/diagramas/` y `docs/assets/`. Priorizar Mermaid. Solo imágenes SVG, PNG, WebP optimizadas.
9. **Caso 9: Post-Mortems de Incidencias:** `docs/arquitectura/post-mortems/` con causa raíz, cronología y prevención.

### Regla Mandatoria: Doble Índice
Todo nuevo documento debe enlazarse en el `README.md` del subdirectorio correspondiente Y en [`docs/README.md`](./docs/README.md).

---

## 3. Comandos Útiles

```bash
# Docker local
docker compose up postgres -d
docker compose up -d

# Commits: Conventional Commits
git commit -m "docs(reuniones): agregar acta de reu 2"
git commit -m "feat(backend): modulo de membresias"
```
