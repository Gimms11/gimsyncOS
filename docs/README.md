# 📚 Documentación del Proyecto — Plataforma de Gestión de Gimnasio

> Índice central de toda la documentación del proyecto. Cada subcarpeta agrupa un área temática específica.

---

## Estructura

```
docs/
├── README.md                        ← Estás aquí
│
├── reuniones/                       # Actas, transcripciones y archivos de reuniones
│   ├── README.md                    # Índice de reuniones con fechas y resumen
│   ├── 2026-09-08_reu1/             # Reunión 1: Levantamiento de requerimientos
│   │   ├── transcripcion.md         # Transcripción formateada con timestamps
│   │   └── acta.md                  # Acta resumen (decisiones + acuerdos)
│   └── plantilla_acta.md            # Plantilla para futuras reuniones
│
├── requerimientos/                  # Especificaciones de requisitos (SRS)
│   ├── README.md                    # Índice de versiones
│   ├── v1/                          # Versión 1.0 — Pre-reunión
│   │   └── SRS_Fase_1_v1.0.md
│   └── v2/                          # Versión 2.1 — Post-reunión (vigente)
│       └── SRS_Fase_1_v2.1.md
│
├── negocio/                         # Propuesta comercial, pricing y monetización
│   ├── README.md
│   └── modelo-de-venta-y-monetizacion.md # Venta directa, SaaS, modelos híbridos
│
├── analisis-previo/                 # Documentos de análisis pre-reunión
│   ├── README.md                    # Índice de documentos de análisis
│   ├── 01_Analisis_Ecosistema_ABC_EVO.docx
│   ├── 02_Arquitectura_y_Propuesta_Tecnologica.docx
│   ├── 03_Requerimientos_Funcionales_No_Funcionales.docx
│   ├── 04_Alcance_MVP_Roadmap.docx
│   ├── 05_Matriz_EVO_vs_Nuestro_Sistema.xlsx
│   └── 06_Casos_de_Uso_y_Flujos.docx
│
├── arquitectura/                    # Decisiones técnicas y diagramas
│   ├── README.md                    # Índice de ADRs y diagramas
│   ├── adr/                         # Architecture Decision Records
│   │   └── 000_plantilla.md
│   ├── diagramas/                   # C4, ER, flujos, componentes
│   └── stack-tecnologico.md         # Detalle del stack y justificación
│
├── api/                             # Contratos y documentación de APIs
│   └── README.md                    # Estándares REST y códigos HTTP
│
├── base-de-datos/                   # Modelo de datos y migraciones
│   ├── README.md
│   ├── modelo-conceptual.md         # Modelo ER conceptual
│   └── diccionario-datos.md         # Diccionario de entidades y campos
│
├── guias/                           # Guías para el equipo
│   ├── README.md
│   ├── CONTRIBUTING.md              # Guía de contribución y ramas Git
│   ├── CONVENCIONES.md              # Convenciones de código y commits
│   └── ONBOARDING.md               # Guía de inicio para nuevos miembros
│
└── assets/                          # Imágenes, logos, recursos de docs
    └── .gitkeep
```

---

## Convenciones de Documentación

1. **Formato principal:** Markdown (`.md`). Los archivos binarios (`.docx`, `.xlsx`) se mantienen solo cuando no existe equivalente markdown.
2. **Nombrado de archivos:** `snake_case` o `kebab-case` con minúsculas. Sin espacios ni caracteres especiales.
3. **Reuniones:** Cada reunión se almacena en `reuniones/YYYY-MM-DD_nombre/`.
4. **Versionado de SRS:** Cada versión mayor en su propia carpeta `v1/`, `v2/`, etc. Solo la última versión es la vigente.
5. **ADRs:** Numerados secuencialmente `001_titulo.md`, `002_titulo.md`.
6. **Audios y videos:** NO se versionan en Git (están en `.gitignore`). Almacenar en Google Drive / OneDrive y enlazar.

---

## Estado Actual

| Documento | Versión | Estado |
| :--- | :---: | :--- |
| SRS Fase 1 | v2.1 | ✅ Vigente — Post-reunión, revisión integral (10 decisiones pendientes) |
| Transcripción Reunión 1 | 1.0 | ✅ Completa — Formateada con 10 secciones temáticas |
| Modelos de Venta y Monetización | 1.0 | 📄 Completo — Venta S/. 8K vs SaaS S/. 600 vs 5 modelos híbridos |
| Análisis previo EVO | 1.0 | 📦 Archivado — 6 documentos pre-reunión |
| Stack Tecnológico | 1.0 | ✅ Completado — Spring Boot + FastAPI + Next.js + Expo |
| Modelo Conceptual y Diccionario BD | 1.0 | 🔲 Pendiente de definición final |
| Guías (Contribución, Commits, Onboarding) | 1.0 | ✅ Completado |
| Reglas para Agentes (AGENTS.md, CLAUDE.md) | 1.0 | ✅ Activo — Protocolos para Antigravity, Codex y Claude |
