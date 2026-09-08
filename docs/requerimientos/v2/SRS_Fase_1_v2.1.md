# DOCUMENTO DE REQUERIMIENTOS DE SOFTWARE (SRS)
## FASE 1 — WEB PÚBLICA, E-COMMERCE, POS COUNTER Y FACTURACIÓN ELECTRÓNICA
### Plataforma de Gestión Comercial para Gimnasio (Reemplazo de ABC EVO)

---

### Control de Versiones del Documento

| Versión | Fecha | Autor / Equipo | Cambios Principales |
| :--- | :--- | :--- | :--- |
| **1.0** | 08/09/2026 | Equipo de Análisis | Borrador inicial pre-reunión basado en relevamiento preliminar. |
| **2.0** | 08/09/2026 | Equipo de Análisis y Desarrollo | Consolidación post-reunión con titular identificado, integración de facturación electrónica, priorización de Yape, POS de counter, captura de leads y exclusión formal de asistencia QR. |
| **2.1** | 08/09/2026 | Equipo de Análisis y Desarrollo | **Revisión integral para compartir al equipo:**<br>• Añadido módulo de **Autenticación y Cuentas** (RF-005 a RF-008).<br>• Añadido módulo de **Gestión de Promociones** con CRUD y reglas de aplicación (RF-021 a RF-024).<br>• Añadida **Máquina de Estados de Pedidos** con transiciones explícitas (RF-033 a RF-036).<br>• Añadidas **Notificaciones por Correo y WhatsApp básico** (RF-043 a RF-045).<br>• Nuevo **Glosario de Términos** (Sección 13).<br>• Nueva sección de **Decisiones Pendientes** (Sección 14).<br>• Nuevo diagrama de **Modelo de Entidades** conceptual (Sección 12).<br>• Ampliados RNF con respaldo de datos y compatibilidad de navegadores.<br>• Regla de negocio añadida sobre pases diarios gratuitos para prospectos.<br>• Criterios de aceptación ampliados a 15 escenarios verificables. |

---

### 1. Introducción

El gimnasio opera actualmente mediante una combinación de herramientas fragmentadas:

1. **ABC EVO:** Plataforma SaaS internacional de gestión fitness que, según el dueño **Iván Francisco Chaparro Purizaga**, resulta excesivamente rígida: menús redundantes (ej. *Ventas* aparece dos veces en distintos submenús con la misma funcionalidad), configuraciones complejas que el personal no utiliza y una interfaz que no diferencia permisos por rol de manera limpia.
2. **Software Externo "Click":** Herramienta complementaria de facturación electrónica donde el personal debe ingresar manualmente cada venta realizada en EVO para poder emitir la boleta o factura correspondiente ante SUNAT. Esto genera una **doble digitación** constante, pérdida de tiempo y propensión a errores u omisiones.
3. **Control en Hojas de Cálculo (Excel):** Utilizado en paralelo para:
   - Control de inventario de bebidas, suplementos y accesorios en almacén.
   - Reclasificación manual de compras y gastos mensuales (operativos, administrativos, publicidad) que EVO no permite categorizar.

Para iniciar la transición hacia una plataforma propia y modular, se define la **Fase 1**, orientada a resolver el frente comercial, la presencia web, la venta ágil en mostrador y la automatización tributaria en tiempo real.

> **Referencia de origen:** La información de esta sección fue validada directamente con el Sr. Chaparro durante la reunión de levantamiento del 08/09/2026 (`reu1/convesacion_grupal.ogg`, minutos 00:01 – 02:20).

---

### 2. Propósito del Documento

Establecer la especificación formal de requisitos funcionales y no funcionales para el desarrollo de la **Fase 1**, garantizando que:
- El sistema entregue valor inmediato en ventas y facturación.
- No se sobrecargue al equipo con módulos que corresponden a fases posteriores.
- Cada requerimiento sea verificable mediante un criterio de aceptación concreto.
- Los desarrolladores, diseñadores y testers compartan una visión unificada del alcance.

---

### 3. Objetivos

#### 3.1 Objetivo General
Desarrollar una plataforma web integral que unifique la presencia digital, la comercialización online y presencial de membresías y productos, la gestión ágil de caja en mostrador y la emisión automatizada de comprobantes electrónicos (SUNAT), eliminando la dependencia de software externo para facturación y de plantillas SaaS sobrecargadas.

#### 3.2 Objetivos Específicos

| # | Objetivo | Métrica de Éxito |
| :---: | :--- | :--- |
| OE-1 | Canal digital moderno y responsive para captación de prospectos y venta de membresías y suplementos 24/7. | Web accesible desde móvil con Lighthouse Performance ≥ 80. |
| OE-2 | Pasarelas de pago con soporte prioritario para **Yape y Plin**, checkout en máximo 2 pasos. | Proceso de pago completado en ≤ 2 pantallas. |
| OE-3 | **Punto de Venta (POS) de Mostrador** ágil para recepción, con atajos rápidos por buscador o código de barras/QR. | Venta presencial registrada en ≤ 30 segundos. |
| OE-4 | **API de Facturación Electrónica (Nubefact / PSE)** para emitir Boletas y Facturas automáticamente al registrarse cada pago. | 100% de ventas con comprobante SUNAT emitido automáticamente. |
| OE-5 | Catálogo e inventario físico de productos con actualización de stock en tiempo real. | Stock sincronizado entre web y counter sin diferencias al cierre del día. |
| OE-6 | Registro y seguimiento de **Pases Diarios (S/. 10)** como captura de clientes potenciales (leads). | Base de prospectos exportable con ≥ nombre, celular y correo. |
| OE-7 | Importación masiva de clientes actuales desde reportes Excel/CSV de ABC EVO. | Migración exitosa de la base completa sin pérdida de registros. |
| OE-8 | Panel de administración con métricas clave, comparativas históricas y alertas de membresías por vencer. | Dashboard operativo con datos del día, semana y mes. |

---

### 4. Alcance del Proyecto

#### 4.1 Incluido en Fase 1

| Módulo | Descripción |
| :--- | :--- |
| Web pública institucional | Página de inicio, información del gimnasio, ubicación, horarios, galería. SEO básico. |
| Catálogo de membresías y planes | Visualización y compra online de planes con precios y condiciones. |
| Catálogo de productos | Visualización por categorías y compra online. |
| Gestión de promociones | CRUD de promociones con fechas, descuentos y productos/membresías aplicables. |
| Autenticación y cuentas | Registro, login, perfil de cliente y recuperación de contraseña. |
| Carrito y checkout | Carrito persistente, resumen de orden, selección de pago. |
| Pasarela de pagos | Yape, Plin, tarjetas (Niubiz / Culqi), transferencia con confirmación manual. |
| POS de mostrador | Interfaz rápida para recepción: búsqueda, venta, cobro, cálculo de vuelto. |
| Facturación electrónica | API Nubefact / PSE para boletas, facturas, notas de crédito y reportes fiscales. |
| Gestión de pedidos online | Flujo de estados: Pendiente → Pagado → Preparando → Listo → Entregado / Cancelado. |
| Captura de leads | Pases diarios, formulario web, base de prospectos exportable. |
| Inventario básico | Stock por producto, movimientos, alertas de stock bajo, ajustes manuales. |
| Gestión de clientes | CRUD, búsqueda rápida, historial de compras, importador masivo desde EVO. |
| Dashboard administrativo | Indicadores de ventas, productos, membresías, clientes, pedidos pendientes. |
| Roles y permisos | RBAC con perfiles de Visitante, Cliente, Recepción y Administrador. |
| Auditoría | Bitácora de operaciones sensibles con usuario, fecha y detalle. |
| Notificaciones básicas | Confirmación de compra, comprobante por email, alerta de membresía por vencer. |

#### 4.2 Fuera de Alcance (Fase 2 y posteriores)

| Elemento | Fase Estimada | Motivo de Exclusión |
| :--- | :---: | :--- |
| Control de acceso por QR / asistencia de clientes | Fase 2 | Requiere hardware en recepción y definición de disciplinas. Confirmado con el cliente. |
| Membresías divididas por disciplina (solo baile, solo gym) | Fase 2 | Depende del control de acceso para ser útil operativamente. |
| Categorización de compras y gastos (operativos, admin, publicidad) | Fase 2 | Módulo financiero completo. Requiere validación con el contador. |
| Calendario de clases grupales y reservas | Fase 2 | Iván mencionó que manejan esto manualmente y con la app de EVO. |
| Gestión de horarios y asistencia de entrenadores/empleados | Fase 2 | Función interna que no bloquea las ventas. |
| Dashboard predictivo (churn, proyección de ingresos) | Fase 2/3 | Requiere historial de datos acumulado. |
| App móvil nativa (iOS / Android) | Fase 3 | Se priorizará PWA o portal responsive primero. |
| Reconocimiento facial / biometría | Fase 3+ | Alto costo de hardware y complejidad. |
| Delivery de productos a domicilio | Descartado | No aplica al modelo del gimnasio por ahora. |
| Automatizaciones avanzadas de CRM y WhatsApp masivo | Fase 3 | Complejidad alta; integrar API de WhatsApp requiere verificación de Meta Business. |

---

### 5. Roadmap de Implementación

| Fase | Denominación | Foco Estratégico | Estado |
| :---: | :--- | :--- | :---: |
| **Fase 1** | **Web, E-commerce, POS Counter y Facturación** | Presencia digital, ventas omnicanal, automatización de boletas y control de stock. | **En Desarrollo** |
| **Fase 2** | **Operaciones, Asistencias y Gestión Integral** | Control de accesos QR, membresías por disciplina, horarios de clases, categorización de gastos y reportes financieros. | Posterior |
| **Fase 3** | **Ecosistema Móvil y Fidelización** | Apps para clientes y entrenadores, planes de entrenamiento, rutinas, CRM avanzado y analítica predictiva. | Futuro |

> **Nota:** El modelo de datos de Fase 1 debe diseñarse contemplando la extensión hacia Fase 2 (ej. tablas de disciplinas, horarios y asistencia como stubs/migraciones vacías), para evitar reestructuraciones costosas.

---

### 6. Actores y Perfiles de Usuario

| Rol | Usuario Tipo | Descripción y Permisos Asignados |
| :--- | :--- | :--- |
| **Visitante** | Prospecto / Público | Navega la web sin autenticarse. Consulta membresías, productos, promociones y horarios. Puede comprar un pase diario o membresía registrándose en el proceso. |
| **Cliente** | Miembro registrado | Accede a su cuenta, visualiza el estado de su membresía y fecha de vencimiento, compra en línea, revisa historial de compras, descarga comprobantes electrónicos (PDF) y retira pedidos en counter. |
| **Recepción (Trabajador)** | Gustavo y personal de turno | **Interfaz limpia y restringida:** ventas de mostrador en pocos clics, consulta de stock, despacho de pedidos web por recoger, registro de pases diarios y búsqueda de clientes por DNI/nombre. **No** tiene acceso a dashboard, métricas globales, configuraciones ni gestión de precios. |
| **Administrador** | Iván F. Chaparro Purizaga | **Acceso total:** gestión de catálogo (productos, planes, promociones), gestión de precios, control de usuarios y roles, importación de datos, visualización del dashboard ejecutivo, reportes fiscales, bitácora de auditoría y configuración general del sistema. |

---

### 7. Requerimientos Funcionales (RF)

#### 7.1 Módulo: Sitio Web Público y Presencia Digital

| ID | Requisito |
| :--- | :--- |
| **RF-001** | El sistema presentará una página de inicio moderna, adaptable (responsive) y optimizada para buscadores (SEO básico: meta tags, títulos, descripción, URLs amigables), destacando información del gimnasio, ubicación con mapa y horarios de atención. |
| **RF-002** | El sistema exhibirá el catálogo de membresías vigentes con precios, duración, condiciones de congelamiento y beneficios. |
| **RF-003** | El sistema presentará el catálogo de productos disponibles para la venta, organizados por categoría, con imagen, nombre, descripción, precio y disponibilidad. |
| **RF-004** | El sistema incluirá un botón de contacto directo hacia el WhatsApp oficial del gimnasio para atención rápida de consultas. |

#### 7.2 Módulo: Autenticación y Cuentas de Usuario

| ID | Requisito |
| :--- | :--- |
| **RF-005** | El sistema permitirá el registro de clientes solicitando: nombres, apellidos, DNI, teléfono/WhatsApp, correo electrónico y contraseña. |
| **RF-006** | El sistema permitirá iniciar sesión con correo y contraseña, y proveerá funcionalidad de recuperación de contraseña vía correo electrónico. |
| **RF-007** | El sistema permitirá al cliente actualizar sus datos personales permitidos (teléfono, correo, contraseña). El DNI y nombres no serán editables por el cliente. |
| **RF-008** | El sistema redirigirá automáticamente a cada usuario a la vista correspondiente a su rol tras el inicio de sesión (dashboard para administrador, POS para recepción, perfil para cliente). |

#### 7.3 Módulo: Catálogo de Membresías y Planes

| ID | Requisito |
| :--- | :--- |
| **RF-009** | El Administrador podrá crear, editar, activar y desactivar membresías indicando: nombre, descripción, precio regular, precio promocional (opcional), duración en días, y si permite congelamiento (sí/no, días máximos). |
| **RF-010** | El sistema diferenciará planes regulares (con opción de congelamiento de hasta 15 días) de planes en promoción (sin congelamiento), según política comercial confirmada por Iván Chaparro. |
| **RF-011** | La compra online de una membresía activará el plan inmediatamente tras la confirmación del pago, registrando la fecha de inicio y la fecha de vencimiento calculada. |

> **Referencia:** Reunión min. 10:27 – 11:13. Iván explica la dinámica de precios regulares vs promocionales y las reglas de congelamiento.

#### 7.4 Módulo: Tienda Online (E-commerce)

| ID | Requisito |
| :--- | :--- |
| **RF-012** | El sistema organizará los productos en categorías configurables por el Administrador (ej. Suplementación, Bebidas, Ropa/Accesorios). |
| **RF-013** | El cliente podrá agregar productos al carrito de compras, modificar cantidades y consultar el subtotal en tiempo real. |
| **RF-014** | El sistema validará la disponibilidad de stock antes de confirmar la orden. Si el stock se agota entre el agregado al carrito y el pago, se notificará al cliente. |
| **RF-015** | El carrito será persistente para clientes autenticados (se conserva entre sesiones). |
| **RF-016** | Todos los pedidos online de productos físicos se entregarán bajo la modalidad exclusiva de **Recojo en Gimnasio** (*Pick-up in store*). |

#### 7.5 Módulo: Inventario y Control de Stock

| ID | Requisito |
| :--- | :--- |
| **RF-017** | Toda venta confirmada (online o presencial) actualizará automáticamente el inventario, descontando las unidades vendidas. |
| **RF-018** | El Administrador podrá registrar entradas de mercadería (compras al proveedor), ajustes manuales y otros movimientos de inventario con motivo obligatorio. |
| **RF-019** | Cada movimiento de inventario registrará: tipo de movimiento, cantidad, usuario responsable, fecha/hora y motivo. |
| **RF-020** | El Administrador podrá definir un umbral de stock mínimo por producto. El dashboard y el POS mostrarán alertas visuales cuando un producto esté por debajo de su umbral. |

#### 7.6 Módulo: Gestión de Promociones

| ID | Requisito |
| :--- | :--- |
| **RF-021** | El Administrador podrá crear, editar, activar, pausar y finalizar promociones. |
| **RF-022** | Cada promoción definirá: nombre, descripción, tipo de descuento (porcentaje o monto fijo), productos y/o membresías aplicables, fecha de inicio, fecha de fin y estado (activa/pausada/finalizada). |
| **RF-023** | El sistema aplicará automáticamente la promoción vigente al precio del producto o membresía en el catálogo web y en el POS de counter. |
| **RF-024** | Las promociones vencidas dejarán de aplicarse automáticamente sin intervención manual. Los productos o membresías volverán a mostrarse a su precio regular. |

> **Referencia:** Reunión min. 09:40 – 10:13. Iván menciona que usan promociones agresivas a mitad de precio para convertir prospectos de pase diario en miembros.

#### 7.7 Módulo: Pasarela de Pagos Digitales

| ID | Requisito |
| :--- | :--- |
| **RF-025** | El sistema integrará una pasarela de pagos nacional (Niubiz o Culqi, según evaluación técnica) con soporte para:<br>• **Billeteras Digitales (Yape y Plin):** Proceso optimizado en 1 a 2 pasos.<br>• **Tarjetas de Débito y Crédito (Visa, Mastercard, etc.).** |
| **RF-026** | Para pagos por **transferencia bancaria**, el sistema generará un código de pedido único y registrará la orden como "Pendiente de Verificación". Un trabajador autorizado podrá confirmar manualmente la recepción del depósito para liberar el pedido. |
| **RF-027** | El sistema registrará el estado de cada transacción (Pendiente, Aprobado, Rechazado, Cancelado, Reembolsado) y lo vinculará a la orden de compra correspondiente. |

> **Referencia:** Reunión min. 18:06 – 21:21. Iván confirma que el 60% de sus ventas son por Yape. Actualmente ya trabajan con Niubiz.

#### 7.8 Módulo: Punto de Venta (POS) para Mostrador

| ID | Requisito |
| :--- | :--- |
| **RF-028** | El sistema contará con una interfaz de cobro rápido para el personal de recepción, diseñada para operar ágilmente en pantalla táctil o teclado, con tipografía grande y botones amplios. |
| **RF-029** | El POS permitirá búsqueda inmediata de artículos (productos y membresías) por nombre, código rápido o lectura mediante escáner de código de barras/QR. |
| **RF-030** | El recepcionista seleccionará el medio de pago utilizado en cada venta: Efectivo, Yape/Plin (verificación visual de captura), Tarjeta (POS físico Niubiz) o Transferencia. |
| **RF-031** | En pagos en efectivo, el POS calculará automáticamente el vuelto/cambio a entregar tras ingresar el monto recibido. |
| **RF-032** | El recepcionista podrá asociar un cliente existente a la venta buscándolo por DNI, nombre o teléfono, o registrar un cliente nuevo en el momento. |

> **Referencia:** Reunión min. 40:44 – 41:47. Iván solicita que la venta en counter funcione con "atajos" tipo QR para que el personal no tenga que navegar múltiples pantallas.

#### 7.9 Módulo: Gestión de Pedidos Online

| ID | Requisito |
| :--- | :--- |
| **RF-033** | Los pedidos seguirán la siguiente máquina de estados: |

```
  ┌──────────┐    Pago       ┌─────────┐  Preparar  ┌────────────┐
  │ Pendiente │──confirmado──▶│ Pagado  │──────────▶│ Preparando │
  │ de pago   │               └─────────┘            └──────┬─────┘
  └─────┬─────┘                                             │
        │                                              Listo│
   Cancelado                                                ▼
   por timeout                                    ┌──────────────┐
   o usuario        Cancelado ◄───────────────────│Listo p/Recojo│
                    (admin)                       └──────┬───────┘
                                                         │
                                                    Entregado
                                                         ▼
                                                  ┌─────────────┐
                                                  │  Entregado  │
                                                  └─────────────┘
```

| ID | Requisito |
| :--- | :--- |
| **RF-034** | El trabajador autorizado podrá consultar la lista de pedidos pendientes de preparación y de recojo, ordenados por antigüedad. |
| **RF-035** | El trabajador marcará un pedido como "Listo para Recoger" cuando esté preparado, y como "Entregado" cuando el cliente lo retire presentando DNI o código de pedido. |
| **RF-036** | Los pedidos no recogidos dentro de un plazo configurable (ej. 72 horas) generarán una alerta al Administrador. |

#### 7.10 Módulo: Facturación Electrónica Integrada (API SUNAT / PSE)

| ID | Requisito |
| :--- | :--- |
| **RF-037** | El sistema se integrará vía API con un Proveedor de Servicios Electrónicos homologado (ej. Nubefact) para la emisión automática de comprobantes de pago electrónicos. |
| **RF-038** | Al confirmarse cualquier venta (online o presencial), el sistema generará automáticamente una **Boleta de Venta Electrónica** y enviará el comprobante (PDF y XML) al correo del cliente. |
| **RF-039** | A solicitud del cliente, el sistema permitirá emitir una **Factura Electrónica** previa validación del RUC y Razón Social contra el servicio de consulta de SUNAT. |
| **RF-040** | El Administrador podrá consultar el estado de envío ante SUNAT de cada comprobante emitido, descargar archivos PDF/XML y emitir **Notas de Crédito** para anulaciones autorizadas. |
| **RF-041** | El sistema generará un **reporte fiscal consolidado** (diario, semanal, mensual) exportable a Excel para el contador, incluyendo: serie, correlativo, tipo de comprobante, RUC/DNI del cliente, importe gravado, IGV, total e información del pago. |

> **Referencia:** Reunión min. 22:04 – 23:24. Iván describe cómo actualmente tiene que usar EVO para vender y luego Click para hacer la boleta. La integración elimina este flujo duplicado.

#### 7.11 Módulo: Captación de Leads y Pases Diarios

| ID | Requisito |
| :--- | :--- |
| **RF-042** | El sistema permitirá registrar pases diarios (acceso por 1 día a S/. 10) tanto desde la web como en el POS de counter. |
| **RF-043** | Para cada pase diario emitido, el sistema solicitará obligatoriamente: nombres completos, número de celular/WhatsApp y correo electrónico. |
| **RF-044** | Los datos de quienes compren pases diarios o soliciten información quedarán almacenados en la base de **Prospectos (Leads)**. |
| **RF-045** | El Administrador podrá consultar y exportar la lista de prospectos filtrada por fecha, para alimentar campañas de promociones de conversión. |

> **Referencia:** Reunión min. 09:02 – 10:13. Iván explica el flujo del prospecto: visita → pase diario o día gratis → recopilar datos → lanzar promoción a mitad de precio para convertir.

#### 7.12 Módulo: Gestión de Clientes y Migración desde EVO

| ID | Requisito |
| :--- | :--- |
| **RF-046** | El sistema contará con una función de **Importación Masiva de Clientes** mediante archivo Excel (.xlsx) o CSV con la estructura de campos exportable desde ABC EVO (Código, Nombres, Apellidos, DNI, Teléfono, Correo, Estado). |
| **RF-047** | El importador validará formato, datos obligatorios y duplicados (por DNI) antes de confirmar la carga. Mostrará un resumen de registros válidos, duplicados y erróneos. |
| **RF-048** | El cliente registrado podrá consultar su perfil, vigencia de su membresía (con indicador visual de estado: Activa / Por vencer / Vencida) e historial de compras con descarga de comprobantes electrónicos. |
| **RF-049** | El personal de recepción podrá buscar rápidamente a un cliente por DNI, nombre o teléfono para asociarlo a una venta en mostrador. |

#### 7.13 Módulo: Dashboard Administrativo y Métricas Comerciales

| ID | Requisito |
| :--- | :--- |
| **RF-050** | El sistema proveerá un panel de control con indicadores en tiempo real:<br>• Total de ingresos del día, semana y mes.<br>• Desglose de ingresos por canal (Web vs Mostrador).<br>• Desglose de ingresos por medio de pago (Yape, Tarjeta, Efectivo, Transferencia).<br>• Cantidad de membresías vendidas en el periodo.<br>• **Lista de membresías próximas a vencer** (7 y 15 días) para gestión de renovaciones.<br>• Lista de **cumpleaños del mes** entre los clientes activos.<br>• Ranking de productos más vendidos.<br>• Alertas de productos con stock bajo.<br>• Pedidos pendientes de preparación o recojo. |
| **RF-051** | El dashboard permitirá comparativas de ventas frente al mes anterior y frente al mismo mes del año anterior (cuando exista historial). |
| **RF-052** | El Administrador podrá exportar los datos de cualquier sección del dashboard a Excel o PDF. |

> **Referencia:** Reunión min. 25:41 – 27:08. Iván describe lo que ve (y lo que le falta) en el dashboard actual de EVO: ventas, comparativas históricas, cumpleaños y vencimientos de membresías.

#### 7.14 Módulo: Notificaciones

| ID | Requisito |
| :--- | :--- |
| **RF-053** | El sistema enviará correo electrónico automático al cliente al producirse: confirmación de compra con comprobante adjunto, cambio de estado de pedido (Listo para Recoger, Entregado) y recuperación de contraseña. |
| **RF-054** | El sistema enviará un correo de recordatorio al cliente cuando su membresía esté a 7 días de vencer, y otro cuando esté a 1 día de vencer. |
| **RF-055** | El sistema alertará al Administrador vía panel (notificación interna) cuando un producto alcance el umbral de stock bajo o cuando un pedido online lleve más de 24 horas sin prepararse. |

#### 7.15 Módulo: Seguridad, Roles y Auditoría

| ID | Requisito |
| :--- | :--- |
| **RF-056** | El sistema aplicará control de acceso estricto basado en roles (RBAC). Cada endpoint y vista validará el rol del usuario autenticado. El perfil de recepción **no** tendrá acceso a dashboard, métricas globales, configuración de precios ni gestión de promociones. |
| **RF-057** | El sistema registrará en una bitácora de auditoría inmutable toda operación sensible: modificación de precios, ajustes manuales de stock, creación/anulación de ventas y comprobantes, cambios de rol de usuario y eliminación de registros. Cada entrada incluirá: usuario, fecha/hora, acción, valor anterior y valor nuevo. |

---

### 8. Requerimientos No Funcionales (RNF)

| ID | Categoría | Requisito |
| :--- | :--- | :--- |
| **RNF-001** | Rendimiento | El tiempo de carga inicial de la web pública no superará los 2.0 segundos en conexiones móviles 4G. Las consultas del POS en mostrador responderán en menos de 500 ms. |
| **RNF-002** | Usabilidad | El checkout para compras con Yape/billetera digital no requerirá más de 2 pantallas. El POS de counter permitirá completar una venta en menos de 30 segundos. |
| **RNF-003** | Seguridad | Todo el tráfico cifrado mediante TLS/HTTPS. Contraseñas almacenadas con bcrypt o argon2. Tokens de sesión con expiración configurable. Protección CSRF y rate limiting en endpoints de autenticación. |
| **RNF-004** | Disponibilidad | La plataforma estará disponible el 99.5% del tiempo en horario operativo (06:00 – 23:00). |
| **RNF-005** | Concurrencia | El sistema soportará al menos 100 usuarios navegando concurrentemente y 10 transacciones de pago simultáneas sin degradación. |
| **RNF-006** | Integridad Transaccional | Toda operación de cobro + emisión de comprobante se ejecutará atómicamente: si la pasarela cobra pero la API fiscal falla, el sistema alertará y reintentará con política de reintentos (máx. 3) sin duplicar cargos. |
| **RNF-007** | Diseño Adaptable | Interfaz Mobile First adaptada a móviles (≥ 320px), tablets y escritorio. |
| **RNF-008** | Compatibilidad | La web funcionará en las últimas 2 versiones estables de Chrome, Firefox, Safari y Edge. |
| **RNF-009** | Respaldo y Recuperación | Se realizarán backups automáticos diarios de la base de datos con retención mínima de 30 días. El tiempo de recuperación ante desastre (RTO) no excederá las 4 horas. |
| **RNF-010** | Mantenibilidad | La solución se organizará modularmente (backend API + frontend desacoplado) para facilitar la incorporación de módulos de Fase 2 sin rediseño. |
| **RNF-011** | Accesibilidad | La interfaz aplicará buenas prácticas básicas de accesibilidad: contraste adecuado, etiquetas en formularios, navegación por teclado en flujos críticos. |

---

### 9. Reglas de Negocio Clave

| # | Regla | Fuente |
| :---: | :--- | :--- |
| RN-01 | No se permitirá la venta web de un producto cuyo stock sea igual a cero. En mostrador, solo el Administrador podrá autorizar una excepción de sobreventa. | Reunión min. 00:43 |
| RN-02 | Planes adquiridos bajo campaña promocional se emiten **sin derecho a congelamiento**. Planes a precio regular incluyen congelamiento de hasta 15 días previa solicitud. | Reunión min. 10:27 – 11:13 |
| RN-03 | Toda venta registrada (online o en counter) debe generar un comprobante electrónico válido con correlativo SUNAT. No existirán ventas sin comprobante en base de datos. | Reunión min. 22:04 – 23:33 |
| RN-04 | Ningún pase diario (S/. 10) podrá emitirse sin registrar nombre completo, celular/WhatsApp y correo del prospecto. | Reunión min. 09:02 – 09:46 |
| RN-05 | Todo pedido online de productos se entrega exclusivamente bajo recojo en counter presentando DNI o código de pedido. | Confirmado en doc. v1.0 |
| RN-06 | Iván mencionó que en ocasiones ofrece un **día gratuito** de prueba a prospectos para que se convenzan. El sistema deberá permitir registrar un "Pase Cortesía" (sin costo) que igualmente capture los datos del prospecto. | Reunión min. 09:09 – 09:40 |
| RN-07 | Los productos desactivados por el Administrador no aparecerán en el catálogo web ni en el POS. | Heredado de v1.0 |

---

### 10. Flujos Operativos Principales

#### 10.1 Flujo A — Compra Online de Membresía
```
Visitante consulta membresías ──▶ Selecciona plan ──▶ Agrega al carrito
                                                              │
                                                    ┌─────────▼──────────┐
                                                    │ ¿Tiene cuenta?     │
                                                    │  Sí → Login        │
                                                    │  No → Registro     │
                                                    └─────────┬──────────┘
                                                              │
                                                    Checkout: Elige pago
                                                    (Yape / Tarjeta)
                                                              │
                                              ┌───────────────▼────────────────┐
                                              │ Pasarela confirma pago         │
                                              │ → Membresía ACTIVA             │
                                              │ → Boleta emitida vía API SUNAT │
                                              │ → Comprobante PDF por email     │
                                              └───────────────────────────────┘
```

#### 10.2 Flujo B — Compra Online de Producto (Recojo)
```
Cliente agrega producto(s) al carrito ──▶ Checkout ──▶ Pago confirmado
                                                              │
                                                 Pedido: "Pagado"
                                                 Boleta emitida
                                                 Stock descontado
                                                              │
                                       Recepción: marca "Preparando" ──▶ "Listo para Recoger"
                                                                                    │
                                                              Cliente presenta DNI/código
                                                              Recepción marca "Entregado"
```

#### 10.3 Flujo C — Venta Rápida en Counter (Gustavo)
```
Cliente en mostrador ──▶ Gustavo busca producto/membresía (nombre, código o escáner)
                                          │
                              Agrega al ticket de venta
                              Selecciona medio de pago
                                          │
                         ┌────────────────┼────────────────────┐
                    Efectivo          Yape/Plin           Tarjeta POS
                  (calcula vuelto)  (verifica captura)   (Niubiz físico)
                         └────────────────┼────────────────────┘
                                          │
                              Boleta emitida al instante
                              Stock actualizado
```

#### 10.4 Flujo D — Importación Inicial de Datos desde EVO
```
Iván exporta clientes desde ABC EVO (Excel/CSV)
       │
Carga archivo en Panel de Administración ──▶ Sistema valida formato y duplicados
                                                              │
                                              Muestra resumen: X válidos, Y duplicados, Z errores
                                                              │
                                              Iván confirma ──▶ Clientes migrados y disponibles
```

---

### 11. Criterios de Aceptación para Cierre de Fase 1

| # | Escenario de Verificación | Resultado Esperado |
| :---: | :--- | :--- |
| CA-01 | Un visitante accede a la web desde su teléfono móvil. | Visualiza la página de inicio con membresías, productos y promociones correctamente. |
| CA-02 | Un visitante compra una membresía pagando con Yape. | El pago se confirma, la membresía se activa, la boleta electrónica se emite y llega al correo del cliente. Proceso completo en ≤ 3 minutos. |
| CA-03 | Un cliente compra 2 productos online con tarjeta. | El pedido queda en estado "Pagado". El stock se descuenta. La boleta se emite. |
| CA-04 | Un trabajador prepara y entrega un pedido. | El pedido transita por: Pagado → Preparando → Listo → Entregado. Cliente recibe notificación en cada cambio de estado. |
| CA-05 | Gustavo registra una venta presencial en counter. | La venta se completa en ≤ 30 segundos. La boleta se emite automáticamente. El inventario se actualiza. |
| CA-06 | Un cliente paga en efectivo en counter. | El POS calcula el vuelto correctamente. |
| CA-07 | Se registra un pase diario en counter. | El sistema exige nombre, celular y correo. El prospecto aparece en la base de leads. Se emite boleta por S/. 10. |
| CA-08 | Iván consulta el dashboard a las 6 PM. | Ve las ventas del día desglosadas por canal (web / counter) y por medio de pago. Ve la lista de membresías por vencer en 7 días. |
| CA-09 | Iván importa el Excel de clientes de EVO. | El sistema valida el archivo, muestra resumen de registros y los clientes quedan disponibles para búsqueda y ventas. |
| CA-10 | Una promoción vence a las 23:59 del día configurado. | Al día siguiente, los productos vuelven a su precio regular sin intervención manual. |
| CA-11 | Un producto llega a stock bajo (≤ umbral). | Aparece alerta visual en el dashboard y en el POS. |
| CA-12 | El Administrador emite una nota de crédito por una venta anulada. | La nota de crédito se envía a SUNAT vía API y queda registrada en el sistema. |
| CA-13 | El perfil de Recepción intenta acceder al dashboard. | El acceso es denegado y se muestra un mensaje apropiado. |
| CA-14 | El contador solicita el reporte fiscal del mes. | Iván lo exporta desde el panel: incluye serie, correlativo, tipo, DNI/RUC, gravado, IGV y total. |
| CA-15 | Se intenta comprar un producto con stock en cero desde la web. | El sistema muestra "Sin stock" y no permite agregar al carrito. |

---

### 12. Modelo de Entidades Conceptual

```
┌──────────┐       ┌───────────┐       ┌──────────────┐
│ Usuario  │───────│   Rol     │       │  Membresía   │
│          │  N:1  │(Visitante,│       │  (Plan)      │
│ nombre   │       │ Cliente,  │       │ nombre       │
│ email    │       │ Recepción,│       │ precio_reg   │
│ password │       │ Admin)    │       │ precio_promo │
│ dni      │       └───────────┘       │ duración     │
│ teléfono │                           │ congelable   │
└────┬─────┘                           └──────┬───────┘
     │                                        │
     │ 1:N                                    │ 1:N
     ▼                                        ▼
┌──────────────┐    N:1    ┌──────────┐  ┌────────────────┐
│    Orden     │◄──────────│  Pago    │  │ Membresía      │
│ (Pedido)     │           │ método   │  │ Activa         │
│ estado       │           │ monto    │  │ (por cliente)  │
│ canal        │           │ estado   │  │ fecha_inicio   │
│ fecha        │           │ ref_pago │  │ fecha_fin      │
│ total        │           └──────────┘  │ estado         │
└────┬─────────┘                         └────────────────┘
     │ 1:N
     ▼
┌──────────────┐    N:1    ┌──────────┐
│ Detalle      │◄──────────│ Producto │
│ Orden        │           │ nombre   │
│ cantidad     │           │ precio   │
│ precio_unit  │           │ stock    │
│ subtotal     │           │ umbral   │
└──────────────┘           │ categoría│
                           │ activo   │
┌──────────────┐           └──────────┘
│ Comprobante  │
│ tipo (B/F/NC)│    ┌──────────┐
│ serie        │    │Promoción │
│ correlativo  │    │ nombre   │
│ estado_sunat │    │ descuento│
│ pdf_url      │    │ tipo     │
│ xml_url      │    │ fecha_ini│
└──────────────┘    │ fecha_fin│
                    │ estado   │
┌──────────────┐    └──────────┘
│ Prospecto    │
│ (Lead)       │    ┌──────────────┐
│ nombre       │    │ Movimiento   │
│ celular      │    │ Inventario   │
│ email        │    │ tipo         │
│ fecha        │    │ cantidad     │
│ origen       │    │ motivo       │
└──────────────┘    │ usuario      │
                    │ fecha        │
┌──────────────┐    └──────────────┘
│ Auditoría    │
│ usuario      │
│ acción       │
│ entidad      │
│ valor_ant    │
│ valor_nuevo  │
│ fecha        │
└──────────────┘
```

> **Nota:** Este diagrama es conceptual. El modelo físico de base de datos incluirá claves foráneas, índices, timestamps y campos adicionales definidos durante el diseño técnico. Se recomienda incluir tablas stub para `Disciplina`, `Clase` y `Asistencia` (vacías) para facilitar la extensión en Fase 2.

---

### 13. Glosario de Términos

| Término | Definición |
| :--- | :--- |
| **ABC EVO** | Plataforma SaaS internacional de gestión para negocios fitness que el gimnasio utiliza actualmente y busca reemplazar. |
| **Click** | Software externo que el gimnasio usa para emitir comprobantes electrónicos (boletas/facturas) ante SUNAT, de forma independiente a EVO. |
| **PSE** | Proveedor de Servicios Electrónicos. Empresa autorizada por SUNAT para emitir comprobantes electrónicos (ej. Nubefact). |
| **SUNAT** | Superintendencia Nacional de Aduanas y de Administración Tributaria del Perú. |
| **POS** | Point of Sale / Punto de Venta. Interfaz para registrar ventas presenciales en el counter de recepción. |
| **Niubiz** | Plataforma de pagos electrónicos líder en Perú (acepta tarjetas, Yape, Plin). |
| **Culqi** | Alternativa de pasarela de pagos en Perú, con APIs bien documentadas. |
| **Lead / Prospecto** | Persona que ha mostrado interés en el gimnasio pero no tiene membresía activa. |
| **Pase Diario** | Acceso al gimnasio por un día mediante pago de S/. 10. Se usa como herramienta de captación. |
| **Congelamiento** | Suspensión temporal de la vigencia de una membresía, disponible solo en planes regulares (no promocionales). |
| **RBAC** | Role-Based Access Control. Modelo de control de acceso basado en roles asignados a usuarios. |
| **Pick-up in store** | Modalidad de entrega donde el cliente recoge su pedido presencialmente en el gimnasio. |

---

### 14. Decisiones Pendientes antes del Desarrollo

| # | Tema | Decisión Requerida | Responsable |
| :---: | :--- | :--- | :--- |
| DP-01 | **Proveedor de pasarela de pagos** | Evaluar Niubiz (ya en uso) vs Culqi: comisiones, soporte de Yape/Plin integrado, facilidad de API, costos de integración. | Equipo Técnico + Iván |
| DP-02 | **Proveedor de facturación electrónica** | Evaluar Nubefact vs alternativas (Facturador.pe, Efact): costos por comprobante, confiabilidad de API, soporte técnico. | Equipo Técnico + Contador |
| DP-03 | **Catálogo inicial de membresías** | Confirmar lista exacta de planes (nombres, precios regulares, precios promo, días de vigencia, reglas de congelamiento). | Iván Chaparro |
| DP-04 | **Catálogo inicial de productos** | Confirmar listado de productos con categorías, precios, imágenes y stock inicial. | Iván Chaparro |
| DP-05 | **Reglas de promociones** | Definir las primeras promociones a configurar: ¿descuento fijo o porcentual? ¿Aplican a membresías, productos o ambos? ¿Cuáles son las fechas típicas? | Iván Chaparro |
| DP-06 | **Verificación de transferencias** | ¿Quién confirma las transferencias bancarias: solo Iván, o también Gustavo (recepción)? ¿Se requiere adjuntar captura? | Iván Chaparro |
| DP-07 | **Datos del RUC del negocio** | RUC, Razón Social, dirección fiscal y datos de la serie de comprobantes para la configuración con el PSE. | Iván + Contador |
| DP-08 | **Hosting y dominio** | Definir si se usará dominio propio del gimnasio. Confirmar proveedor de hosting/cloud (AWS, GCP, DigitalOcean, etc.). | Equipo Técnico |
| DP-09 | **Estructura del Excel de EVO** | Obtener una muestra del archivo de exportación de clientes de EVO para definir el mapeo de campos del importador. | Iván Chaparro |
| DP-10 | **Modelo comercial y de venta** | Consolidar modelo: Venta directa (S/. 8,000), SaaS (S/. 600/mes) o Híbrido (Setup inicial + cuota mensual de soporte/hosting). Ver [análisis de comercialización](../../negocio/modelo-de-venta-y-monetizacion.md). | Equipo Comercial + Iván |

---

### 15. Nota de Validación

Este documento es la especificación de requerimientos consolidada tras el levantamiento inicial y la reunión presencial del 08/09/2026 con el Sr. Iván Francisco Chaparro Purizaga. Antes de iniciar el desarrollo, los requisitos marcados como **Decisiones Pendientes** (Sección 14) deberán resolverse para evitar bloqueos durante la implementación.

Todos los requerimientos que afecten directamente reglas comerciales (precios, congelamiento, promociones), pagos y facturación deberán contar con la aprobación escrita o digital del propietario del gimnasio antes de implementarse.
