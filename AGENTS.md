# Instrucciones y Reglas Maestras para Agentes de IA (AGENTS.md)
> Aplica para: **Antigravity**, **Codex / Copilot / Cursor**, y **Claude Code**.

Este repositorio es un monorepo para la plataforma de gestión comercial de gimnasio (reemplazo de ABC EVO). Todos los agentes de IA deben seguir estrictamente estas reglas al interactuar con el proyecto.

---

## 1. Mapeo de Archivos de Configuración por Agente

Cada agente en el ecosistema cuenta con su punto de entrada nativo configurado para respetar estas directrices:

| Agente / Herramienta | Archivo(s) Nativo(s) | Ubicación en el Repo |
| :--- | :--- | :--- |
| **Antigravity** | `.agents/rules/*.md` + `AGENTS.md` | `.agents/rules/` y raíz |
| **Cursor** | `.cursor/rules/*.mdc` (con frontmatter) | `.cursor/rules/` |
| **Claude Code** | `CLAUDE.md` | Raíz |
| **GitHub Copilot / Codex** | `.github/copilot-instructions.md` + `AGENTS.md` | `.github/` y raíz |

---

## 2. Estructura y Límites del Monorepo

- `docs/`: Documentación centralizada. **NUNCA** crear documentos sueltos en la raíz (`.md`, `.docx`, `.txt`).
- `backend/`: Monolito modular Spring Boot 3 (Java 21). Módulos de dominio: `auth`, `memberships`, `catalog`, `orders`, `billing`, `customers`.
- `services/`: Microservicios FastAPI (Python 3.11+). Tareas asíncronas, analítica y reportería pesada.
- `frontend/`: Web Next.js 14+ (App Router). Portal público, e-commerce, POS counter recepcionista y panel admin.
- `mobile/`: App socios React Native + Expo (Fase 2).
- `infra/`: Dockerfiles, Nginx reverse proxy y scripts de despliegue.
- `db/`: Migraciones y seeds SQL (PostgreSQL).

**Prohibición de raíz:** Solo se permiten en raíz: `.gitignore`, `docker-compose.yml`, `README.md`, `AGENTS.md`, `CLAUDE.md`.

---

## 3. Protocolos por Caso Específico de Documentación

Cualquier adición o modificación documental DEBE clasificarse obligatoriamente en uno de estos 9 casos:

```
                  ┌──────────────────────────────────────────────┐
                  │       TAXONOMÍA DE CASOS DOCUMENTALES        │
                  └──────────────────────┬───────────────────────┘
                                         │
        ┌──────────────┬─────────────────┼────────────────┬──────────────┐
        ▼              ▼                 ▼                ▼              ▼
   [Caso 1: Reu]  [Caso 2: SRS]   [Caso 3: ADR]    [Caso 4: BD]    [Caso 5: API]
   reuniones/     requerimientos/ arquitectura/adr base-de-datos/  api/
        │              │                 │                │              │
        ▼              ▼                 ▼                ▼              ▼
   [Caso 6: Neg]  [Caso 7: Guías] [Caso 8: Diagram] [Caso 9: Inc]
   negocio/       guias/          diagramas/assets post-mortems/
```

### Caso 1: Fin de Reunión / Procesamiento de Minuta
- **Disparador:** Usuario pide registrar, formatear o resumir una reunión con clientes o equipo.
- **Ruta destino:** `docs/reuniones/YYYY-MM-DD_<nombre_descriptivo>/` (ej. `2026-09-08_reu1/`).
- **Archivos obligatorios:**
  1. `transcripcion.md`: Turnos de orador, marcas de tiempo `[MM:SS]`, muletillas limpias y resumen de secciones.
  2. `acta.md`: Estructura obligatoria de `docs/reuniones/plantilla_acta.md` (asistentes, acuerdos, decisiones, próximos pasos).
- **Regla de audio:** **NUNCA** subir archivos `.ogg`, `.mp3`, `.mp4`, `.wav` al repo (bloqueados en `.gitignore`). Subir a nube externa (Drive) y enlazar URL en el acta.
- **Doble índice y SRS:**
  - Agregar fila a `docs/reuniones/README.md`.
  - Evaluar impacto en requerimientos: actualizar SRS vigente o generar `v(N+1)` y actualizar tabla de *Decisiones Pendientes*.

### Caso 2: Evolución de Requerimientos (SRS)
- **Disparador:** Nuevas funciones solicitadas, cambios de alcance o aclaración de reglas de negocio.
- **Ruta destino:** `docs/requerimientos/v<N>/SRS_Fase_<F>_v<N.M>.md`.
- **Criterio de versionado:**
  - *Cambio mayor (nueva fase, reestructuración modular):* Crear carpeta `v(N+1)/`, archivar versión anterior.
  - *Cambio menor (nuevo RF puntual, ajuste de regla, aclaración):* Editar SRS vigente, incrementar versión menor (ej. v2.1 -> v2.2) y registrar la fila en la tabla *Control de Versiones del Documento*.
- **Identificadores:** Respetar la nomenclatura secuencial (`RF-xxx`, `RNF-xxx`, `DP-xxx`).
- **Doble índice:** Actualizar tabla en `docs/requerimientos/README.md`.

### Caso 3: Registro de Decisión Arquitectónica (ADR)
- **Disparador:** Elección o cambio de framework, base de datos, patrón de diseño, pasarela de pago o proveedor cloud.
- **Ruta destino:** `docs/arquitectura/adr/NNN_<titulo_kebab_case>.md` (ej. `001_monolito_modular_spring_boot.md`).
- **Plantilla:** Clonar obligatoriamente `docs/arquitectura/adr/000_plantilla.md`.
- **Campos obligatorios:** Estado (Propuesto/Aceptado/Rechazado), Contexto, Decisión, Alternativas Consideradas, Consecuencias.
- **Doble índice:** Agregar entrada en `docs/arquitectura/README.md`.

### Caso 4: Modelado y Esquema de Base de Datos
- **Disparador:** Nuevas entidades, cambios de campos, relaciones o claves foráneas.
- **Ruta destino:** `docs/base-de-datos/`.
- **Archivos:**
  - `modelo-conceptual.md`: Diagrama Mermaid ER actualizado.
  - `diccionario-datos.md`: Tabla markdown con Nombre de tabla, columna, tipo, PK/FK/NOT NULL y descripción.
- **Consistencia:** Todo cambio debe estar sincronizado con los scripts Flyway en `backend/src/main/resources/db/migration/` o `db/migrations/`.
- **Doble índice:** Actualizar `docs/base-de-datos/README.md`.

### Caso 5: Contratos y Especificación de APIs REST
- **Disparador:** Definición de nuevos endpoints, payloads o cambios en contratos cliente-servidor.
- **Ruta destino:** `docs/api/`.
- **Formato:** Archivos OpenAPI 3.0 (`.yaml` / `.json`) o documentos Markdown por módulo (`auth.md`, `billing.md`).
- **Campos mínimos:** Método HTTP, path, cabeceras (`Authorization: Bearer`), Request body (JSON esquema), Responses (200, 400, 401, 403, 404, 500 con JSON demo).
- **Doble índice:** Actualizar `docs/api/README.md`.

### Caso 6: Propuestas Comerciales, Modelos de Venta y Pricing
- **Disparador:** Análisis de monetización, propuestas para el cliente (ej. S/. 8,000 venta vs S/. 600 SaaS vs modelos híbridos), cotizaciones de terceros.
- **Ruta destino:** `docs/negocio/<nombre_propuesta_kebab_case>.md`.
- **Regla estricta:** **PROHIBIDO inventar precios, comisiones o penalizaciones.** Toda cifra debe basarse en actas con el cliente, costos reales demostrables de proveedores (servidor, PSE SUNAT, pasarelas) o escenarios explícitamente solicitados.
- **Doble índice:** Actualizar `docs/negocio/README.md`.

### Caso 7: Guías Normativas, Convenciones y Procesos de Equipo
- **Disparador:** Nuevas políticas de Git, configuración de entorno, guías de estilo o procesos de despliegue.
- **Ruta destino:** `docs/guias/`.
- **Nombres estándar:** `CONTRIBUTING.md`, `CONVENCIONES.md`, `ONBOARDING.md`, o temáticas en `kebab-case.md`.
- **Doble índice:** Actualizar `docs/guias/README.md`.

### Caso 8: Diagramas de Arquitectura y Activos Visuales
- **Disparador:** Creación de diagramas de arquitectura C4, flujos BPMN, mockups de interfaz o logos.
- **Ruta destino:**
  - Diagramas técnicos: `docs/arquitectura/diagramas/`.
  - Imágenes/assets generales: `docs/assets/`.
- **Reglas:** Priorizar código Mermaid embebido en Markdown. Para archivos binarios, admitir solo SVG, PNG o WebP optimizados. **Prohibido** subir archivos pesados de diseño editable (.psd, .ai, .fig).

### Caso 9: Reportes de Incidencias Técnicas (Post-Mortem)
- **Disparador:** Caída de servidor, rechazo masivo de comprobantes SUNAT, indisponibilidad de pasarela de pagos o pérdida de datos.
- **Ruta destino:** `docs/arquitectura/post-mortems/` o `docs/guias/`.
- **Nomenclatura:** `YYYY-MM-DD_<descripcion_kebab_case>.md`.
- **Contenido obligatorio:** Resumen del incidente, impacto en usuarios, causa raíz (RCA), cronología de eventos y plan de prevención.

---

## 4. Regla Mandatoria del Doble Índice

Ningún documento debe quedar "huérfano". Cada vez que un agente cree un documento nuevo, debe:
1. Enlazarlo en el `README.md` del subdirectorio correspondiente.
2. Enlazarlo en el índice general [`docs/README.md`](./docs/README.md).

---

## 5. Estilo y Buenas Prácticas del Agente

1. **Edición Quirúrgica:** Tocar únicamente las líneas pertinentes. No reescribir archivos enteros cuando un diff puntual resuelve la tarea.
2. **Commits Convencionales:** Usar siempre el formato `tipo(alcance): descripción` (ej. `docs(reuniones): agregar acta de reu 2`, `docs(negocio): agregar modelos hibridos`).
3. **Enlaces Clickeables:** En cada respuesta al usuario, enlazar los archivos creados o editados con la sintaxis markdown `[archivo](file:///ruta/completa)`.
4. **Validación Previa:** Antes de dar por terminada la tarea, verificar que los enlaces relativos funcionen y que las tablas de índice no tengan referencias rotas.
