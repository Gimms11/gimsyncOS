**DOCUMENTO DE REQUERIMIENTOS**  
**FASE 1 — WEB + E-COMMERCE**  
Plataforma web para gimnasio

<table><tbody><tr><td><strong>Documento</strong></td><td>Requerimientos Funcionales y No Funcionales — Fase 1</td></tr><tr><td><strong>Versión</strong></td><td>1.0 — Borrador para validación</td></tr><tr><td><strong>Alcance</strong></td><td>Web pública + E-commerce + gestión interna básica</td></tr><tr><td><strong>Estado</strong></td><td>Propuesta basada en el levantamiento inicial</td></tr></tbody></table>

1\. Introducción
================

El gimnasio actualmente realiza parte de sus procesos comerciales y operativos de forma manual. Las ventas de productos y el control de inventario se apoyan en archivos de Excel, mientras que las membresías, clases y asistencia también presentan procesos manuales. Asimismo, el negocio utiliza ABC EVO para determinadas funciones, pero considera que la cantidad de funcionalidades disponibles puede resultar excesiva frente a sus necesidades reales.  
Como primera etapa se propone desarrollar una plataforma web propia que combine la presencia digital del gimnasio con un comercio electrónico. La plataforma permitirá promocionar el negocio, vender productos y membresías, gestionar pedidos y pagos, y proporcionar herramientas internas básicas para trabajadores y administradores.

2\. Propósito
=============

Establecer de manera clara el alcance y los requisitos de la primera fase del proyecto, evitando implementar funcionalidades que no sean necesarias para la entrega inicial. La plataforma se diseñará con una visión de crecimiento para que posteriormente pueda incorporar un sistema administrativo más completo y aplicaciones móviles.

3\. Objetivos
=============

3.1 Objetivo general
--------------------

Desarrollar una plataforma web de e-commerce para el gimnasio que permita promocionar y comercializar productos y membresías, facilitar las ventas online y presenciales, reducir la dependencia de procesos manuales y proporcionar información básica para la administración del negocio.

3.2 Objetivos específicos
-------------------------

*   Crear una presencia web moderna y orientada a la conversión.
*   Permitir la consulta y compra de productos y membresías.
*   Implementar carrito y proceso de compra.
*   Integrar los medios de pago que el negocio utilice, según la viabilidad técnica de cada método.
*   Gestionar pedidos online con modalidad de recojo en el gimnasio.
*   Registrar ventas presenciales desde la plataforma.
*   Reducir la dependencia del control de stock realizado actualmente mediante Excel.
*   Permitir la administración de productos, membresías y promociones.
*   Proporcionar un dashboard con indicadores comerciales y operativos relevantes.

4\. Alcance de la Fase 1
========================

4.1 Incluido
------------

*   Sitio web público y e-commerce como una sola plataforma.
*   Catálogo de productos.
*   Catálogo de membresías.
*   Sección de promociones.
*   Registro e inicio de sesión de clientes.
*   Carrito de compras.
*   Checkout y registro de pedidos.
*   Integración de pagos según los medios definidos por el negocio.
*   Historial de compras del cliente.
*   Recojo de pedidos en el gimnasio.
*   Ventas presenciales para trabajadores autorizados.
*   Consulta y gestión básica de inventario.
*   Gestión de pedidos online por trabajadores.
*   Administración de productos, membresías y promociones.
*   Gestión básica de clientes.
*   Dashboard administrativo.
*   Reportes básicos de ventas y productos.

4.2 Fuera de alcance de la Fase 1
---------------------------------

*   Aplicación móvil para clientes.
*   Aplicación móvil para profesores.
*   Aplicación de escritorio administrativa completa.
*   Gestión avanzada de profesores.
*   Sistema completo de clases y reservas.
*   Control avanzado de asistencia.
*   CRM avanzado.
*   Analítica predictiva avanzada.
*   Reproducción completa de todas las funcionalidades de ABC EVO.
*   Sistema contable o módulo completo de gastos.
*   Delivery o gestión de envíos a domicilio.

5\. Visión y roadmap
====================

La primera fase constituye el punto de entrada de una plataforma propia que podrá crecer progresivamente. El objetivo no es replicar todas las funcionalidades de ABC EVO desde el inicio, sino resolver primero los procesos de mayor valor para el negocio.

<table><tbody><tr><td><strong>Fase</strong></td><td><strong>Producto</strong></td><td><strong>Prioridad</strong></td></tr><tr><td>Fase 1</td><td>Web + E-commerce</td><td>Actual</td></tr><tr><td>Fase 2</td><td>Sistema administrativo completo</td><td>Posterior</td></tr><tr><td>Fase 3</td><td>Aplicaciones móviles</td><td>Posterior</td></tr><tr><td>Fase 4</td><td>Analítica avanzada y nuevas funcionalidades</td><td>Futuro</td></tr></tbody></table>

6\. Usuarios y roles
====================

<table><tbody><tr><td><strong>Rol</strong></td><td><strong>Descripción</strong></td><td><strong>Principales acciones</strong></td></tr><tr><td>Visitante</td><td>Persona que navega sin iniciar sesión.</td><td>Consultar información, productos, membresías y promociones.</td></tr><tr><td>Cliente</td><td>Usuario registrado que compra en la plataforma.</td><td>Gestionar perfil, carrito, compras, pagos y pedidos.</td></tr><tr><td>Trabajador</td><td>Personal autorizado para operaciones del gimnasio.</td><td>Registrar ventas, consultar productos, gestionar pedidos y stock según permisos.</td></tr><tr><td>Administrador</td><td>Responsable de la gestión del negocio.</td><td>Gestionar catálogo, promociones, membresías, clientes, inventario, ventas y dashboard.</td></tr></tbody></table>

7\. Módulos funcionales
=======================

*   Sitio público y catálogo.
*   Autenticación y cuentas de clientes.
*   Productos.
*   Membresías.
*   Promociones.
*   Carrito y checkout.
*   Pagos.
*   Pedidos y recojo.
*   Ventas presenciales.
*   Inventario.
*   Clientes.
*   Administración y dashboard.

8\. Requerimientos funcionales
==============================

<table><tbody><tr><td><strong>ID</strong></td><td><strong>Módulo</strong></td><td><strong>Requisito</strong></td></tr><tr><td>RF-001</td><td>Sitio público</td><td>El sistema deberá mostrar información general del gimnasio, sus productos, membresías y promociones.</td></tr><tr><td>RF-002</td><td>Productos</td><td>El sistema deberá permitir consultar productos con nombre, imagen, descripción, precio y disponibilidad.</td></tr><tr><td>RF-003</td><td>Productos</td><td>El sistema deberá organizar los productos en categorías.</td></tr><tr><td>RF-004</td><td>Productos</td><td>El sistema deberá mostrar el detalle de un producto antes de añadirlo al carrito.</td></tr><tr><td>RF-005</td><td>Membresías</td><td>El sistema deberá mostrar las membresías disponibles con precio, vigencia y condiciones definidas por el negocio.</td></tr><tr><td>RF-006</td><td>Promociones</td><td>El sistema deberá mostrar promociones vigentes y sus condiciones.</td></tr><tr><td>RF-007</td><td>Clientes</td><td>El sistema deberá permitir registrar una cuenta de cliente.</td></tr><tr><td>RF-008</td><td>Autenticación</td><td>El sistema deberá permitir iniciar sesión y acceder a las funciones correspondientes al rol.</td></tr><tr><td>RF-009</td><td>Clientes</td><td>El cliente deberá poder consultar y actualizar los datos personales permitidos.</td></tr><tr><td>RF-010</td><td>Carrito</td><td>El cliente deberá poder agregar, eliminar y modificar cantidades de productos.</td></tr><tr><td>RF-011</td><td>Carrito</td><td>El sistema deberá validar la disponibilidad de productos antes de confirmar una compra.</td></tr><tr><td>RF-012</td><td>Checkout</td><td>El sistema deberá permitir revisar el resumen y registrar los datos necesarios para generar el pedido.</td></tr><tr><td>RF-013</td><td>Pagos</td><td>El sistema deberá admitir los medios de pago definidos por el negocio, incluyendo tarjeta y transferencia, y contemplando Yape, Plin u otros cuando sea técnicamente viable.</td></tr><tr><td>RF-014</td><td>Pagos</td><td>El sistema deberá registrar el resultado del pago y asociarlo al pedido.</td></tr><tr><td>RF-015</td><td>Pedidos</td><td>El sistema deberá generar un pedido asociado al cliente y a los artículos adquiridos.</td></tr><tr><td>RF-016</td><td>Pedidos</td><td>El sistema deberá gestionar estados como pendiente de pago, pagado, preparando, listo para recoger, entregado y cancelado, según corresponda.</td></tr><tr><td>RF-017</td><td>Pedidos</td><td>El sistema deberá utilizar inicialmente el recojo en el gimnasio como modalidad de entrega.</td></tr><tr><td>RF-018</td><td>Clientes</td><td>El cliente deberá poder consultar su historial de compras y pedidos.</td></tr><tr><td>RF-019</td><td>Ventas</td><td>El trabajador autorizado deberá poder registrar ventas realizadas en el gimnasio.</td></tr><tr><td>RF-020</td><td>Ventas</td><td>El trabajador deberá seleccionar el medio de pago utilizado en cada venta.</td></tr><tr><td>RF-021</td><td>Inventario</td><td>Una venta confirmada deberá actualizar la disponibilidad del producto.</td></tr><tr><td>RF-022</td><td>Inventario</td><td>Los trabajadores autorizados deberán poder consultar el stock.</td></tr><tr><td>RF-023</td><td>Inventario</td><td>El sistema deberá registrar movimientos de inventario, como entradas, ventas, ajustes y otros definidos por el negocio.</td></tr><tr><td>RF-024</td><td>Inventario</td><td>Los movimientos deberán conservar información suficiente para identificar qué ocurrió, cuándo y qué usuario realizó la operación.</td></tr><tr><td>RF-025</td><td>Inventario</td><td>El sistema deberá permitir identificar productos con stock bajo mediante un umbral configurable.</td></tr><tr><td>RF-026</td><td>Administración</td><td>El administrador deberá poder crear, consultar, actualizar y desactivar productos.</td></tr><tr><td>RF-027</td><td>Administración</td><td>El administrador deberá poder gestionar las membresías disponibles y sus condiciones.</td></tr><tr><td>RF-028</td><td>Administración</td><td>El administrador deberá poder crear, modificar, activar, pausar y finalizar promociones.</td></tr><tr><td>RF-029</td><td>Clientes</td><td>El personal autorizado deberá poder consultar información básica de clientes.</td></tr><tr><td>RF-030</td><td>Pedidos</td><td>El trabajador autorizado deberá poder consultar y actualizar el estado de pedidos online.</td></tr><tr><td>RF-031</td><td>Pedidos</td><td>El trabajador autorizado deberá poder marcar un pedido como entregado cuando el cliente lo recoja.</td></tr><tr><td>RF-032</td><td>Dashboard</td><td>El administrador deberá disponer de un dashboard con indicadores de ventas, ingresos, productos, membresías, clientes y pedidos.</td></tr><tr><td>RF-033</td><td>Dashboard</td><td>El dashboard deberá permitir consultar información por periodos como día, semana y mes.</td></tr><tr><td>RF-034</td><td>Reportes</td><td>El sistema deberá permitir consultar la evolución histórica de las ventas y principales indicadores registrados.</td></tr><tr><td>RF-035</td><td>Dashboard</td><td>El dashboard deberá mostrar los productos con mayor volumen de ventas.</td></tr><tr><td>RF-036</td><td>Dashboard</td><td>El dashboard deberá mostrar información sobre las membresías comercializadas y su evolución.</td></tr><tr><td>RF-037</td><td>Dashboard</td><td>El dashboard deberá mostrar indicadores básicos de clientes, como total y nuevos registros.</td></tr><tr><td>RF-038</td><td>Dashboard</td><td>El sistema deberá permitir identificar pedidos pendientes de atención.</td></tr><tr><td>RF-039</td><td>Seguridad</td><td>El sistema deberá restringir las funciones según el rol y permisos asignados.</td></tr><tr><td>RF-040</td><td>Auditoría</td><td>El sistema deberá conservar información de operaciones administrativas relevantes para facilitar la trazabilidad.</td></tr></tbody></table>

9\. Requerimientos no funcionales
=================================

<table><tbody><tr><td><strong>ID</strong></td><td><strong>Categoría</strong></td><td><strong>Requisito</strong></td></tr><tr><td>RNF-001</td><td>Seguridad</td><td>Las funciones administrativas deberán requerir autenticación y autorización según el rol.</td></tr><tr><td>RNF-002</td><td>Protección de datos</td><td>Los datos deberán transmitirse y almacenarse aplicando medidas de seguridad adecuadas.</td></tr><tr><td>RNF-003</td><td>HTTPS</td><td>La plataforma deberá utilizar HTTPS en producción.</td></tr><tr><td>RNF-004</td><td>Responsive</td><td>La web deberá adaptarse a computadoras, tablets y teléfonos.</td></tr><tr><td>RNF-005</td><td>Usabilidad</td><td>El proceso de compra deberá ser claro y requerir la menor cantidad razonable de pasos.</td></tr><tr><td>RNF-006</td><td>Rendimiento</td><td>Las páginas y operaciones frecuentes deberán responder en tiempos adecuados para la carga esperada.</td></tr><tr><td>RNF-007</td><td>Disponibilidad</td><td>La plataforma deberá contar con mecanismos adecuados de recuperación ante fallos.</td></tr><tr><td>RNF-008</td><td>Mantenibilidad</td><td>La solución deberá organizarse modularmente para facilitar futuras ampliaciones.</td></tr><tr><td>RNF-009</td><td>Escalabilidad</td><td>La solución deberá permitir incorporar nuevas funcionalidades sin rediseñarla por completo.</td></tr><tr><td>RNF-010</td><td>Auditoría</td><td>Las operaciones administrativas relevantes deberán contar con trazabilidad.</td></tr><tr><td>RNF-011</td><td>Compatibilidad</td><td>La web deberá funcionar correctamente en navegadores modernos.</td></tr><tr><td>RNF-012</td><td>Accesibilidad</td><td>La interfaz deberá aplicar buenas prácticas básicas de accesibilidad.</td></tr></tbody></table>

10\. Reglas de negocio iniciales
================================

*   Un producto no deberá venderse por encima de la disponibilidad registrada, salvo una excepción autorizada por el administrador.
*   Una venta confirmada deberá generar el movimiento de inventario correspondiente.
*   Los pedidos online utilizarán inicialmente el recojo en el gimnasio.
*   Las operaciones administrativas dependerán de los permisos del usuario.
*   Las promociones deberán respetar sus fechas, condiciones y productos o membresías aplicables.
*   Los estados de pedido y pago deberán mantenerse consistentes.
*   Los productos desactivados no deberán aparecer como disponibles para nuevas compras.

11\. Flujos principales
=======================

11.1 Compra online
------------------

1.  Cliente consulta un producto o membresía.
2.  Añade el artículo al carrito.
3.  Revisa el carrito.
4.  Inicia sesión o crea una cuenta.
5.  Selecciona el medio de pago.
6.  Realiza o confirma el pago según el método.
7.  El sistema registra el pedido y su estado.
8.  El gimnasio prepara el pedido.
9.  El pedido pasa a 'Listo para recoger'.
10.  El cliente recoge el pedido.
11.  El trabajador confirma la entrega.

11.2 Venta presencial
---------------------

1.  Trabajador inicia una venta.
2.  Selecciona productos y cantidades.
3.  El sistema verifica disponibilidad.
4.  Selecciona el medio de pago.
5.  Confirma la venta.
6.  El sistema registra la operación.
7.  El stock se actualiza.
8.  La venta queda disponible para reportes.

11.3 Inventario
---------------

1.  Se registra una entrada, venta, ajuste u otro movimiento.
2.  El sistema actualiza el stock.
3.  Se guarda usuario y fecha de la operación.
4.  El personal autorizado consulta el historial.

12\. Pagos e integraciones
==========================

El negocio utiliza actualmente tarjeta y transferencia, y en determinadas operaciones Yape y Plin de forma manual. El sistema deberá admitir diferentes medios de pago sin acoplar toda la lógica comercial a un único proveedor.

*   La selección del proveedor de pagos deberá realizarse después de validar costos, métodos soportados, comisiones, seguridad y facilidad de integración.
*   Cuando un método permita confirmación automática, el sistema deberá registrar el resultado mediante la integración correspondiente.
*   Para métodos que requieran confirmación manual, el sistema deberá permitir registrar o confirmar el pago de forma controlada.
*   La integración deberá contemplar estados como pendiente, aprobado, rechazado, cancelado y reembolsado cuando corresponda.
*   La facturación electrónica es una necesidad del negocio y deberá definirse con el proveedor y flujo que se utilizarán antes de cerrar la implementación.

13\. Dashboard administrativo — propuesta inicial
=================================================

El dashboard se plantea como una vista ejecutiva, no como un sistema contable. Debe priorizar información que pueda obtenerse de las operaciones registradas.

*   Ventas e ingresos del día, semana y mes.
*   Cantidad de ventas y pedidos.
*   Productos más vendidos.
*   Membresías vendidas y evolución.
*   Clientes totales y nuevos registros.
*   Pedidos pendientes de preparación o recojo.
*   Productos con stock bajo.
*   Comparaciones con periodos anteriores.

La analítica predictiva avanzada no forma parte del MVP. Puede incorporarse posteriormente cuando exista suficiente historial de datos para generar predicciones útiles.

14\. Criterios de aceptación generales
======================================

*   Un visitante puede consultar productos, membresías y promociones.
*   Un cliente puede registrarse, iniciar sesión y realizar una compra.
*   El sistema valida la disponibilidad antes de confirmar una venta.
*   Una venta confirmada actualiza el inventario.
*   Un trabajador autorizado puede registrar una venta presencial.
*   Un trabajador autorizado puede gestionar el estado de un pedido.
*   Un pedido puede pasar a 'Listo para recoger' y posteriormente a 'Entregado'.
*   Un administrador puede gestionar productos, membresías y promociones.
*   El administrador puede consultar indicadores básicos en el dashboard.
*   Los usuarios no pueden acceder a funciones que no correspondan a su rol.

15\. Decisiones pendientes antes del desarrollo
===============================================

<table><tbody><tr><td><strong>Tema</strong></td><td><strong>Decisión pendiente</strong></td></tr><tr><td>Proveedor de pagos</td><td>Definir proveedor(es) para tarjeta y otros pagos online.</td></tr><tr><td>Transferencias</td><td>Definir cómo se validarán y conciliarán.</td></tr><tr><td>Yape / Plin</td><td>Definir si se usarán mediante integración, QR con confirmación manual u otro mecanismo.</td></tr><tr><td>Facturación electrónica</td><td>Definir proveedor y flujo de emisión.</td></tr><tr><td>Membresías</td><td>Confirmar tipos, precios, vigencia y condiciones.</td></tr><tr><td>Productos</td><td>Confirmar catálogo inicial, categorías, precios e imágenes.</td></tr><tr><td>Promociones</td><td>Definir reglas y condiciones.</td></tr><tr><td>Roles</td><td>Confirmar permisos exactos de trabajador y administrador.</td></tr><tr><td>Datos iniciales</td><td>Definir si se migrarán productos/clientes desde Excel u otras fuentes.</td></tr></tbody></table>

16\. Fases posteriores
======================

Fase 2 — Sistema administrativo
-------------------------------

Se podrá ampliar la plataforma para cubrir procesos internos más completos: gestión de profesores, clases, asistencia, operaciones de recepción, CRM y reportes avanzados, según las necesidades validadas con el negocio.

Fase 3 — Aplicaciones móviles
-----------------------------

Se podrán desarrollar aplicaciones para clientes y profesores consumiendo los servicios del backend existente.

Fase 4 — Analítica avanzada
---------------------------

Podrán incorporarse indicadores avanzados, automatizaciones y modelos predictivos cuando exista suficiente información histórica.

17\. Nota de validación
=======================

Este documento es una propuesta inicial basada en el levantamiento realizado. Antes de iniciar el desarrollo, los requisitos que afecten directamente reglas comerciales, pagos, facturación, membresías y promociones deberán ser validados con el propietario del gimnasio.