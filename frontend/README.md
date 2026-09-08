# Frontend — Aplicación Web (Next.js)

Frontend unificado construido con **Next.js 14+ (App Router) / TypeScript**. Agrupa el portal público, la tienda virtual (e-commerce), la consola de punto de venta (POS) y el panel administrativo.

## Módulos de la Aplicación

```
frontend/
├── src/app/
│   ├── (public)/          # Landing page institucional, horarios, promociones, pase diario
│   ├── (shop)/            # Catálogo e-commerce de membresías y suplementos, checkout
│   ├── (counter)/         # POS para recepcionista (Gustavo): ventas rápidas, pases, cobros Yape
│   └── (admin)/           # Panel del administrador (Iván): reportes, caja, auditoría, config
├── src/components/        # Componentes UI reutilizables
├── src/lib/               # Clientes API, utilitarios de formateo y helpers
└── src/types/             # Definiciones TypeScript de entidades y DTOs
```

## Requisitos Previos

- Node.js 20+
- pnpm o npm
