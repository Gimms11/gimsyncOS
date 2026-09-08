# Regla 03: Casos de Incorporación de Documentación

Cualquier nuevo documento debe catalogarse y gestionarse bajo uno de estos 9 casos específicos:

---

### Caso 1: Minuta / Fin de Reunión
- **Ruta:** `docs/reuniones/YYYY-MM-DD_<nombre>/`
- **Archivos:** `transcripcion.md`, `acta.md`.
- **Obligatorio:** Indexar en `docs/reuniones/README.md` y evaluar impacto en SRS.

### Caso 2: Especificación y Evolución de Requerimientos (SRS)
- **Ruta:** `docs/requerimientos/v<N>/SRS_Fase_<F>_v<N.M>.md`
- **Regla:** Mantener numeración de identificadores (`RF-xxx`, `RNF-xxx`, `DP-xxx`). Todo cambio menor incrementa el decimal (v2.1 -> v2.2) con registro en la tabla de control de versiones. Nuevas fases o cambios radicales de arquitectura crean `v(N+1)`.
- **Obligatorio:** Indexar en `docs/requerimientos/README.md`.

### Caso 3: Registro de Decisión Arquitectónica (ADR)
- **Ruta:** `docs/arquitectura/adr/NNN_<titulo_kebab_case>.md` (ej. `001_monolito_modular_spring_boot.md`).
- **Plantilla:** Usar obligatoriamente `docs/arquitectura/adr/000_plantilla.md`.
- **Contenido:** Estado, Contexto, Decisión, Alternativas evaluadas y Consecuencias.
- **Obligatorio:** Indexar en `docs/arquitectura/README.md`.

### Caso 4: Diseño de Base de Datos y Diccionario
- **Ruta:** `docs/base-de-datos/`
- **Archivos:** `modelo-conceptual.md` (Mermaid ER), `diccionario-datos.md` (tablas, campos, restricciones, llaves foráneas).
- **Consistencia:** Debe coincidir exactamente con las entidades del código Spring Boot y los scripts de Flyway.
- **Obligatorio:** Indexar en `docs/base-de-datos/README.md`.

### Caso 5: Contratos y Especificación de APIs REST
- **Ruta:** `docs/api/`
- **Archivos:** Especificaciones OpenAPI 3.0 (`.yaml` / `.json`) o documentos markdown por módulo.
- **Contenido:** Método HTTP, ruta, cabeceras de autorización, request body, códigos HTTP (200, 400, 401, 403, 404, 500) con JSONs de ejemplo.
- **Obligatorio:** Indexar en `docs/api/README.md`.

### Caso 6: Propuestas Comerciales, Modelos de Venta y Pricing
- **Ruta:** `docs/negocio/`
- **Archivos:** `<nombre_propuesta_kebab_case>.md`.
- **Restricción estricta:** NO inventar precios ni comisiones. Toda cifra debe provenir de acuerdos con el cliente o cotizaciones reales de pasarelas/PSE.
- **Obligatorio:** Indexar en `docs/negocio/README.md`.

### Caso 7: Guías Normativas, Convenciones y Procesos de Equipo
- **Ruta:** `docs/guias/`
- **Archivos:** `CONTRIBUTING.md`, `CONVENCIONES.md`, `ONBOARDING.md` o guías temáticas en `kebab-case.md`.
- **Obligatorio:** Indexar en `docs/guias/README.md`.

### Caso 8: Diagramas y Activos Visuales
- **Ruta:** `docs/arquitectura/diagramas/` (diagramas de flujo, secuencia, C4) y `docs/assets/` (imágenes, logos).
- **Formatos:** Priorizar Mermaid embebido en markdown. Si se requieren imágenes, usar exclusivamente SVG, PNG o WebP optimizados. Prohibido subir archivos de diseño pesado (.psd, .ai).

### Caso 9: Reportes de Incidencias Técnicas (Post-Mortem)
- **Ruta:** `docs/arquitectura/post-mortems/` o `docs/guias/`
- **Formato:** `YYYY-MM-DD_<descripcion>.md`.
- **Contenido:** Causa raíz, impacto, acciones correctivas y prevención de recurrencia.

---

## Regla del Doble Índice (Mandatoria)
Todo documento agregado debe ser enlazado en:
1. El `README.md` de su subdirectorio local.
2. El índice central `docs/README.md`.
