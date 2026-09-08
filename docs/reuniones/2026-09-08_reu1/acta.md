# Acta de Reunión — Levantamiento de Requerimientos (Reunión 1)

| Campo | Detalle |
| :--- | :--- |
| **Fecha** | 2026-09-08 |
| **Duración** | ~42 minutos (00:01 – 42:10) |
| **Lugar** | Presencial — Instalaciones del Gimnasio |
| **Cliente** | Sr. Iván Francisco Chaparro Purizaga (Dueño / Administrador) |
| **Equipo** | 7 integrantes del equipo de desarrollo y análisis (Oradores 2 al 8) |
| **Audio** | `convesacion_grupal.ogg` *(almacenado fuera del repo — ver Google Drive)* |

---

## Objetivo

Diagnosticar los problemas operativos con la plataforma ABC EVO actual y realizar el levantamiento formal de requerimientos para el desarrollo de un sistema personalizado a medida.

---

## Temas Tratados

1. **Diagnóstico de EVO:** Menús redundantes, funciones inutilizadas, falta de categorización de gastos.
2. **Flujo de trabajo diario:** Rutina del administrador al llegar, supervisión de áreas, apertura de turnos.
3. **Captación de clientes:** Pases diarios (S/. 10), días de prueba gratuitos, registro de prospectos.
4. **E-commerce:** Limitaciones de la vitrina actual de EVO; concepto de tienda online fue nuevo para Iván.
5. **Pagos:** 60% de ventas son por Yape. Se trabaja con Niubiz. PagoEfectivo genera fricción.
6. **Facturación:** Doble digitación obligatoria con software externo *Click* para emitir boletas SUNAT.
7. **Migración de datos:** Iván puede exportar backups de EVO en Excel/CSV.
8. **Control de acceso QR:** Propuesta de check-in por código QR → diferido a Fase 2.
9. **Membresías por disciplina:** Propuesta de segmentar por baile/gym → diferido a Fase 2.
10. **Roles y permisos:** Gustavo (recepción) ve demasiadas opciones en EVO que no le corresponden.
11. **Inventario físico:** Hoy se controla con Excel. Interés en lectores de código de barras/QR para counter.

---

## Decisiones Tomadas

| # | Decisión | Detalle |
| :---: | :--- | :--- |
| 1 | Fase 1 = Web + E-commerce + POS Counter + Facturación Electrónica | Se mantiene el plan comercial como prioridad. |
| 2 | Control de asistencia QR → Fase 2 | Requiere hardware y definición de disciplinas. |
| 3 | Membresías divididas por disciplina → Fase 2 | Depende del control de acceso para funcionar. |
| 4 | Facturación integrada por API desde Fase 1 | Eliminar la doble digitación con Click. |
| 5 | Pasarela de pagos: priorizar Yape/Plin | 60% del volumen actual. |

---

## Documentos Generados

- [`transcripcion.md`](./transcripcion.md) — Transcripción completa formateada (10 secciones, 201 turnos, ~42 min).
- [`../../requerimientos/v2/SRS_Fase_1_v2.1.md`](../../requerimientos/v2/SRS_Fase_1_v2.1.md) — SRS Fase 1 versión 2.1 consolidada.

---

## Próximos Pasos

- [ ] Resolver las 10 **Decisiones Pendientes** documentadas en el SRS v2.1 (Sección 14).
- [ ] Consolidar modelo de venta con el equipo e Iván: Venta directa (S/. 8,000), SaaS (S/. 600/mes) o Híbrido (ver [`../../negocio/modelo-de-venta-y-monetizacion.md`](../../negocio/modelo-de-venta-y-monetizacion.md)).
- [ ] Solicitar a Iván el catálogo de membresías y productos con precios.
- [ ] Obtener muestra del Excel exportado de EVO para diseñar el importador.
- [ ] Evaluar Niubiz vs Culqi y seleccionar PSE para facturación.
- [ ] Agendar Reunión 2 para validación del SRS con Iván.
