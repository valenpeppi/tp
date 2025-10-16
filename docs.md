# Documentación

## Link al [README.md](https://github.com/valenpeppi/tp/blob/main/README.md) del proyecto.

---

## Minuta mensual de avance en el proyecto

### Abril 2025 — Idea

- Definición de idea. Entrega de la proposal. Creación del Modelo entidad-relación
- Definición de los requerimientos tecnicos y funcionales.
---

### mayo 2025 — Aprendizaje

-Primeros conocimientos de los lenguajes a utilizar en la aplicación.
-Definición grupal de tecnologías a implementar

### Junio 2025 — Kickoff 

**Frontend**
- Instalacion de Vite + React + TypeScript.
- Base de rutas (`App`/`Main`) y estructura de `pages/` y `shared/`.
- Contexts iniciales: Auth, Events, Message.
- Interfaz de usuario: Home, Login, Registro, layout y estilos base.

**Backend**
- Inicialización de **Express** con estructura modular en `src/`.
- Seguridad de la navegación de rutas y autenticación con JWT y Bcrypt.

---

### Julio 2025 — Modelo de Datos y CRUDs

**Prisma / DB**
- Configuración de ambiente y conexión de la ORM Prisma con MySQL.
- Modelado completo: `User`, `Event`, `EventType`, `Place`, `Sector`, `EventSector`, `Seat`, `Ticket`, `Sale`, `SaleItem`, etc.
- Relaciones, claves compuestas e índices.
- Migraciones y seeds (lugares, sectores, eventos de prueba).

**API REST**
- CRUDs para places, sectors, events, seats, users, sales.
- Middlewares base (CORS, parsing, manejo de errores).

**Frontend**
- Hardcodeo de eventos y usuarios para trabajar la lógica y funcionamiento.
- Listado/catálogo de eventos.

---

### Agosto 2025 — Linea de Venta y UI Interactiva

**Event Detail**
- `EventDetailPage` (header + body) con EventDetailContext.

**Carrito y Linea de venta**
- CartContext y páginas: `Cart`, `Pay`.
- Validaciones iniciales de stock y agrupación por evento/sector.

**Responsive**
- Ajustes de breakpoints, iconografía y componentes reutilizables.

---

### Septiembre 2025 — Pagos iniciales, gestion como Administrador
**Pagos**
- Comienzos de integración Stripe y MercadoPago (clients, endpoints y webhooks).
- Estados de compra.

**Admin**
- Implementación del AdminHome y FeatureEvents (marcar eventos como destacados).

**Organizador**
- Flujo de crear evento para organizadores.

---

### Octubre 2025 — Testing y adicionales

**Testing**
- Playwright E2E: flujo completo de compra; casos de login y navegación.
- Vitest (FE): validaciones y rutas en testeos unitarios del FrontEnd.
- Jest (BE): validaciones y rutas en testeos unitarios del BackEnd.
- Supertest: Test de integración en el BackEnd.

**Seguridad + Correcion de errores** 
- Correcciones de grouping en carrito: enumeradas vs generales.
- Mejoras de UX (loading states, mensajes, errores).

**Extras**
- Asistente virtual de ayuda: ChatBot.

---

## Tracking de features, bugs e issues





## DOCUMENTACION DE LA API


