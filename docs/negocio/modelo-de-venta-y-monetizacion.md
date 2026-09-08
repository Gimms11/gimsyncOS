# Análisis de Modelos de Venta y Comercialización
## Plataforma de Gestión de Gimnasio (Reemplazo de ABC EVO)

> **Documento Estratégico y Financiero para el Equipo de Desarrollo**  
> **Fecha de Elaboración:** 2026-09-08  
> **Estado:** Propuesta para debate y consolidación comercial  
> **Objetivo:** Definir el modelo de monetización óptimo considerando los parámetros base: venta directa a **S/. 8,000**, suscripción SaaS a **S/. 600/mes**, y modelos híbridos viables.

---

## 1. Contexto y Premisas Comerciales

El cliente (**Iván Francisco Chaparro Purizaga**, gimnasio con ~300-500 alumnos activos y counter físico) busca reemplazar la plataforma internacional **ABC EVO**.

### Situación actual del cliente:
- **Costo EVO actual:** Las suscripciones de EVO oscilan típicamente entre **$150 y $300 USD mensuales** (~S/. 560 a S/. 1,120/mes), más costos de soporte e implementación.
- **Dolor crítico:** EVO tiene funciones excesivas que no usa, falta de control de gastos, vitrina web deficiente y obliga a doble digitación manual en el software *Click* para facturación SUNAT.
- **Capacidad de pago:** Un gimnasio de este porte maneja flujos diarios constantes (60% Yape/Plin, pases diarios a S/. 10, membresías mensuales/anuales), pero cuida su flujo de caja mensual.

---

## 2. Comparativa de Modelos Base

### Modelo A: Venta Directa / Producto a Medida (Llave en Mano)
- **Precio propuesto:** **S/. 8,000 PEN** (pago único o en hitos de entrega: 40% inicio, 30% entrega Fase 1, 30% puesta en producción).
- **Esquema:** El cliente compra el derecho de uso o propiedad del software desarrollado para su negocio.

| Aspecto | Ventajas | Desventajas / Riesgos |
| :--- | :--- | :--- |
| **Flujo de caja para el equipo** | Ingreso fuerte e inmediato para financiar las horas de desarrollo de los 7 integrantes. | Ingreso no recurrente. Una vez cobrado, no hay ingresos futuros del mismo cliente. |
| **Para el cliente** | Sensación de "propiedad"; no siente la carga de una mensualidad fija para siempre. | Desembolso de capital inicial alto (CAPEX). |
| **Riesgos operativos** | Fin del compromiso tras garantía. | **Riesgo crítico:** El cliente asume que soporte, cambios de SUNAT, caídas de servidor y nuevas funciones son gratis de por vida si no se delimita estrictamente. |
| **Infraestructura** | Servidor a cuenta del cliente. | Si el cliente no paga el servidor o no hace backups, culpará al software ante pérdidas de datos. |

---

### Modelo B: Software as a Service (SaaS Puro)
- **Precio propuesto:** **S/. 600 PEN / mes** (cobro recurrente mensual o contrato anual).
- **Esquema:** El equipo de desarrollo es dueño del software y la infraestructura; el cliente paga por el servicio y acceso continuo.

| Aspecto | Ventajas | Desventajas / Riesgos |
| :--- | :--- | :--- |
| **Flujo de caja para el equipo** | **MRR (Ingreso Mensual Recurrente).** A los 14 meses ya supera los S/. 8,000. Al año 3 ha generado **S/. 21,600**. | En los primeros 3 a 6 meses el equipo ingresa poco dinero comparado con las horas invertidas. |
| **Para el cliente** | Cero costo inicial fuerte (OPEX). Incluye soporte, actualizaciones continuas y servidor. Es competitivo frente a lo que ya paga en EVO. | Costo acumulativo a largo plazo. |
| **Escalabilidad** | Permite empaquetar la plataforma y vendérsela a **otros gimnasios locales** a la misma tarifa, multiplicando ingresos con el mismo código. | El equipo debe asumir los costos fijos mensuales (servidor, PSE SUNAT, mantenimiento). |

---

## 3. Propuesta de Modelos Híbridos (Recomendados)

Ante la disyuntiva entre **dinero hoy** (cubrir horas de desarrollo) y **dinero recurrente** (sostenibilidad y soporte), se presentan 5 alternativas híbridas evaluadas:

```
                  ┌──────────────────────────────────────────────────┐
                  │          MATRIZ DE EQUILIBRIO COMERCIAL          │
                  └──────────────────────────────────────────────────┘
   Flujo Inmediato ▲
                   │  [Opción 1: Venta S/. 8K]
                   │
                   │        [Híbrido 1: Setup + SaaS S/. 3.5K + S/. 400]
                   │        [Híbrido 2: Licencia + SLA S/. 8K + S/. 200]
                   │        [Híbrido 4: Rent-to-Own S/. 800 x 12m]
                   │
                   │              [Híbrido 3: SaaS Escalonado Fases]
                   │              [Opción 2: SaaS Puro S/. 600/m]
                   └─────────────────────────────────────────────────────► Recurrencia / LTV
```

---

### Híbrido 1: "Setup Fee" Inicial + Cuota Mensual Reducida ⭐ *(Altamente Recomendado)*
- **Estructura:**
  - **Costo de Implementación (Setup):** **S/. 3,500 - S/. 4,000 PEN** (pago inicial dividido en 2 hitos).
  - **Suscripción de Mantenimiento & Plataforma:** **S/. 380 - S/. 450 PEN / mes**.
- **Justificación para el cliente:** El setup cubre la configuración inicial, personalización de marca, carga y migración del Excel de EVO, capacitación de Gustavo/recepción y puesta a punto con el PSE de facturación. La cuota mensual reducida cubre servidor, soporte continuo, copias de seguridad diarias y soporte ante incidentes SUNAT.
- **Rendimiento financiero:**
  - Mes 1: S/. 4,000
  - Año 1 (12 meses): S/. 4,000 + (S/. 400 × 12) = **S/. 8,800**
  - Año 2: + S/. 4,800 (Acumulado: **S/. 13,600**)
  - Año 3: + S/. 4,800 (Acumulado: **S/. 18,400**)

---

### Híbrido 2: Licencia Perpetua + Póliza de Soporte y Actualizaciones (SLA)
- **Estructura:**
  - **Venta de Licencia:** **S/. 8,000 PEN** (cubre desarrollo y entrega de la solución instalada).
  - **Póliza Anual/Mensual de Mantenimiento Obligatoria (SLA):** **S/. 180 - S/. 250 PEN / mes** (o S/. 2,200/año anticipado).
- **Justificación para el cliente:** El cliente es dueño de su sistema, pero un sistema con facturación electrónica SUNAT y pasarelas de pago **no puede quedar huérfano**: SUNAT cambia normativas, los certificados digitales vencen, y las APIs de Niubiz/Culqi se deprecian. La póliza garantiza que su sistema nunca se detenga.
- **Rendimiento financiero:**
  - Año 1: S/. 8,000 + S/. 2,400 = **S/. 10,400**
  - Año 2: + S/. 2,400 (Acumulado: **S/. 12,800**)
  - Año 3: + S/. 2,400 (Acumulado: **S/. 15,200**)

---

### Híbrido 3: SaaS Escalonado por Fases de Entrega
- **Estructura:**
  - **Durante Fase 1 (Web, E-commerce, POS counter, Facturación SUNAT):** **S/. 450 PEN / mes**.
  - **Al activar Fase 2 (App móvil Android/iOS, Control de acceso QR, Reservas):** Sube a **S/. 650 - S/. 700 PEN / mes**.
- **Justificación para el cliente:** El cliente no paga el precio de una plataforma completa hasta que tenga la App móvil y el control QR operativos. Reduce su fricción de entrada durante la marcha blanca.
- **Rendimiento financiero:**
  - Año 1 (Fase 1 6 meses + Fase 2 6 meses): (S/. 450 × 6) + (S/. 650 × 6) = **S/. 6,600**
  - Año 2: S/. 7,800 (Acumulado: **S/. 14,400**)
  - Año 3: S/. 7,800 (Acumulado: **S/. 22,200**)

---

### Híbrido 4: Modelo "Rent-to-Own" (Arrendamiento con Opción a Compra)
- **Estructura:**
  - Contrato a 12 o 18 meses a **S/. 750 - S/. 850 PEN / mes**.
  - Al completar el periodo de 12 o 18 meses, el cliente adquiere la licencia definitiva y el precio mensual baja automáticamente a una cuota mínima de soporte y servidor (**S/. 180 PEN / mes**).
- **Justificación para el cliente:** Da la seguridad psicológica de que "no pagará una cuota alta de por vida", pero al equipo le garantiza un flujo mensual constante equivalente a una venta financiada con intereses de mantenimiento.
- **Rendimiento financiero:**
  - Año 1 (12 meses × S/. 800): **S/. 9,600**
  - Año 2 (Soporte S/. 180 × 12): + S/. 2,160 (Acumulado: **S/. 11,760**)
  - Año 3: + S/. 2,160 (Acumulado: **S/. 13,920**)

---

### Híbrido 5: SaaS Base Reducido + Micro-comisión Transaccional
- **Estructura:**
  - **Base fija mensual:** **S/. 350 PEN / mes**.
  - **Fee variable:** **S/. 0.30 - S/. 0.50 PEN** por cada venta web o pase diario vendido por la tienda online.
- **Justificación para el cliente:** "Si el sistema vende más por internet y te ahorra tiempo en recepción, ganamos ambos". Si las ventas web crecen, el software genera ingresos crecientes.
- **Rendimiento financiero:** Con 300 transacciones mensuales online, suma S/. 90 - S/. 150 extra/mes (~S/. 450 - S/. 500/mes total).

---

## 4. Proyección Financiera Comparativa (Horizonte 3 Años)

| Modelo | Inversión Inicial Cliente | Mes 1 | Año 1 Total | Año 2 Total | Año 3 Acumulado | ¿Incluye Servidor/Soporte? |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **1. Venta Directa Pura** | S/. 8,000 | S/. 2,400 (adelanto) | S/. 8,000 | S/. 0 | **S/. 8,000** | ❌ Solo garantía 3 meses |
| **2. SaaS Puro (S/. 600/m)** | S/. 0 | S/. 600 | S/. 7,200 | S/. 7,200 | **S/. 21,600** | ✅ Sí, 100% cubierto |
| **3. Híbrido 1 (Setup S/. 3.8K + S/. 400/m)** | S/. 3,800 | S/. 4,200 | S/. 8,600 | S/. 4,800 | **S/. 18,200** | ✅ Sí, 100% cubierto |
| **4. Híbrido 2 (Licencia S/. 8K + SLA S/. 200/m)** | S/. 8,000 | S/. 2,400 | S/. 10,400 | S/. 2,400 | **S/. 15,200** | ✅ Sí, por SLA mensual |
| **5. Híbrido 4 (Rent-to-Own S/. 800/m × 12)** | S/. 0 | S/. 800 | S/. 9,600 | S/. 2,160 | **S/. 13,920** | ✅ Sí durante y post-compra |

---

## 5. Costos Operativos Fijos a Considerar (Deducciones)

Cualquier modelo que incluya servidor y facturación debe considerar estos costos reales:

1. **Servidor Cloud (VPS):**
   - Servidor DigitalOcean / Hetzner / AWS Lightsail (4GB RAM, 2 vCPU): ~$12 a $20 USD/mes (**~S/. 45 a S/. 75 PEN/mes**).
2. **Proveedor de Facturación Electrónica (PSE - Nubefact):**
   - Plan Pyme (~500 a 1,000 comprobantes mensuales): ~$15 a $25 USD/mes (**~S/. 60 a S/. 95 PEN/mes**).
3. **Dominio y Certificado SSL:**
   - Dominio `.pe` o `.com`: ~S/. 50 a S/. 110 anuales (**~S/. 8 PEN/mes**).
4. **Pasarela de Pagos (Niubiz/Culqi):**
   - No es costo del equipo: se descuenta directamente de cada venta realizada por el cliente (3.45% + IGV aprox.).

> **Total Costos Fijos de Infraestructura:** Entre **S/. 110 y S/. 180 PEN mensuales**.  
> En el SaaS puro de S/. 600/mes, el margen neto para el equipo es de **~S/. 420 a S/. 490 PEN mensuales limpios**.

---

## 6. Recomendación Estratégica del Equipo

### La Mejor Estrategia de Negociación: "Presentar 3 Opciones"

Para no perder la negociación y darle al cliente el control, se sugiere presentar una **oferta de 3 columnas**:

1. **Opción A — "Tu Propio Sistema" (Híbrido 2):**
   - **S/. 8,000 PEN** de compra (en 3 partes: 40% inicio, 30% entrega previa, 30% conformidad final).
   - Más póliza de soporte y servidores: **S/. 180 PEN/mes** (sin esto, el servidor y SUNAT corren por su cuenta).
   - *Ideal si Iván quiere sentir que el sistema es suyo.*

2. **Opción B — "Suscripción Todo Incluido" (Híbrido 1 - Opción Recomendada):**
   - **S/. 3,500 PEN** de implementación inicial (diseño personalizado, migración de datos de EVO, capacitaciones y puesta en marcha).
   - **S/. 450 PEN/mes** que incluye servidor, backups diarios, emisión de boletas/facturas ilimitadas por API y soporte prioritario.
   - *El cliente no gasta S/. 8,000 de golpe, y el equipo asegura S/. 8,900 en el primer año y recurrencia constante.*

3. **Opción C — "SaaS Flex Mensual" (Modelo B Puro):**
   - **S/. 600 PEN/mes**, sin costo de entrada, contrato mínimo de 6 meses.
   - *Ideal si el cliente no quiere desembolsar nada de capital hoy.*

---

## 7. Propiedad Intelectual y Cláusulas Clave

Independientemente del modelo elegido, el contrato comercial debe dejar blindados estos 3 puntos:
1. **Código Fuente vs Licencia:** A menos que el cliente pague un sobreprecio considerable (ej. > S/. 20,000), el cliente adquiere una **licencia de uso exclusivo para su sede o sedes**, mientras que la **propiedad intelectual de la plataforma y el código base pertenece al equipo de desarrollo**. Esto permite comercializar la plataforma a otros gimnasios en otras zonas/ciudades.
2. **Delimitación del Soporte:** El mantenimiento mensual cubre: corrección de bugs, caídas de servidor, cambios normativos de SUNAT y consultas de uso. No cubre nuevos módulos grandes no especificados en el SRS v2.1.
3. **Independencia de Pagos Externos:** Las comisiones de Niubiz/Culqi y el certificado digital tributario son cubiertos por la empresa del cliente.
