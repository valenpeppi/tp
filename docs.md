# Documentación

## Link al [README.md](https://github.com/valenpeppi/tp/blob/main/README.md) del proyecto.

---

## Minuta mensual de avance en el proyecto

### Abril 2025 — Idea

- Definición de idea. Entrega de la proposal. Creación del Modelo entidad-relación
- Definición de los requerimientos tecnicos y funcionales.

---

### Mayo 2025 — Aprendizaje

-Primeros conocimientos de los lenguajes a utilizar en la aplicación.
-Definición grupal de tecnologías a implementar

---

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


### 1) [BE] PrismaClientValidationError en `getSectorsByPlace`
Síntoma: error al invocar `prisma.sector.findMany()` por tipado/parsing del `idPlace` recibido como `string`.  
Impacto: endpoint `/api/places/:idPlace/sectors` caía con 500.  
Acción: conversión explícita `Number(idPlace)` y manejo de error con `details: error.message`.   
Refs: `src/places/places.controller.ts`

---

### 2) [TEST][FE] Timeout E2E al esperar `/cart` (flujo compra mixta)
Síntoma: `buy.e2e.spec.ts` fallaba por selector de cantidad inexistente cuando el evento ofrecía entradas enumeradas o no enumeradas de forma condicional.  
Impacto: test se quedaba en “Waiting for navigation to /cart”.   
Refs: `react-app/tests/buy.e2e.spec.ts`

---

### 3) [FE] Agrupación de ítems (enumeradas vs generales) en carrito
Síntoma: Asientos enumerados y cantidades generales se mezclaban en el mismo grupo, rompiendo el POST a backend.  
Impacto: totales erróneos y confirmaciones inconsistentes.  
Acción: lógica `buildTicketGroups()` separa por `idEvent-idPlace-idSector` y sólo agrega `ids` cuando son enumeradas; para generales usa `quantity` donde see limpian IDs.
Refs: `CartContext`.

---

### 4) [BE][PAY] Webhook Stripe
Síntoma: confirmaciones duplicadas cuando llegaban reintentos.  
Impacto: ventas confirmadas dos veces o ignoradas sin trazabilidad.  
Acción: chequeo previo de `seatEvent.state='sold'`, y rutas de “release” para devolver `reserved → available` en fallos/expiraciones.   
Refs: `src/payments/stripe.webhook.ts`

---

### 5) [TEST][FE] Configuración Vitest + TS + JSDOM
Síntoma: errores de tipos y ambiente de pruebas (matchers de jest-dom, tipos globales).  
Impacto: tests de UI fallaban al montar componentes.  
Acción: `vitest.config.ts` + `tsconfig.vitest.json` con `"types": ["vitest/globals", "@testing-library/jest-dom"]`, `environment: 'jsdom'`, `setupFiles`.  
Refs: `react-app/vitest.config.ts`, `react-app/tsconfig.vitest.json`, `react-app/src/setupTests.ts`

---

### 6) [BE] Carga de `.env`
Síntoma: log mostraba ` Cargando variables desde ${envFile}` y path de `.env.test`.  
Impacto: confusión al cargar variables de entorno, especialmente en testeos.  
Acción: TEMPLATE STRING real en `console.log`, y `dotenv.config({ path: path.resolve(envFile) })`.  
Refs: `src/config/env.ts`

---

### 7) [DB][BE] Estados de `seatEvent`
Síntoma: asientos quedaban “enganchados” en `reserved` bajo fallas/expiraciones o múltiples tabs.  
Impacto: inventario “fantasma” no liberado y mal diseño UX.  
Acción: `updateMany` en release; chequeos previos a confirmar; limpieza de `idSale/lineNumber` al liberar.  
Refs: `src/payments/stripe.webhook.ts`

---

### 8) [FE] Fallback de imágenes y assets 404 en `EventDetail`
Síntoma: imágenes remotas ausentes generaban 404/“broken image”.  
Impacto: estética deteriorada.  
Acción: assets locales (`estadio-arroyito`, `bioceres-arena`, `el-circulo`) como fallback.  
Refs: `src/pages/eventDetail/EventDetailPage.*`

---

### 9) [TEST][BE] Mocks de Prisma en unit tests
Síntoma: unit tests dependían del DB real o se rompían por retorno de tipos.  
Acción: mock estático de `prisma` (findMany/… con `jest.fn()`), limpieza de mocks en `beforeEach`.  
Refs: `src/places/places.controller.test.ts`

---

### 10) [SEC][BE] Endpoints sensibles
Síntoma: riesgo de replay/brute-force sobre `/payments/*`.  
Impacto: Riesgos de doble proceso.  
Acción: `webhookRateLimit` y límites razonables aplicados a rutas de pago.  
Refs: `src/middlewares/rateLimit.ts`, `src/payments/*.routes.ts`

---

### 11) [FE] Validaciones de login y manejo de errores HTTP
Síntoma: confusión entre mensajes 401/422 y estados locales; ausencia de limpieza de mensajes previos.  
Impacto: UX inconsistente al reintentar login.  
Acción: tests que cubren vacíos, formato de email, 401; mocks de Axios tipados; `clearMessages()` al iniciar. 
Refs: `src/pages/login/LoginUser.test.tsx`

---

### 12) [FE] Puntos de quiebre y layout.
Síntoma: solapamientos en modales/overlays en móviles y “tablet” al rotar.  
Impacto: imposibilidad de seleccionar asiento/cantidad.  
Acción: CSS Modules con breakpoints y grid/areas más conservadoras en modal. 
Refs: `seatSelector/styles/*.module.css`

---

### 13) [BE] ConfirmSale vía webhook
Síntoma: `SalesController.confirmSale` esperaba shape específico (`body: { dniClient, tickets }` y `auth.dni`).  
Impacto: confirmación no hacía flujo correcto de usuario/venta.  
Acción: armado explícito de `mockReq`/`mockRes` y logs controlados en webhook.  
Refs: `src/payments/stripe.webhook.ts`

---

## EVIDENCIA DE RESULTADOS DE TESTING

### Test unitario - Backend

#### Places
<img width="1190" height="305" alt="image" src="https://github.com/user-attachments/assets/6fc30515-1189-4292-aff7-982c23152935" />


#### Seats
<img width="1174" height="253" alt="image" src="https://github.com/user-attachments/assets/0249d56e-ad2c-4f0d-b2b1-a7586113594b" />


#### Sales
<img width="1194" height="251" alt="image" src="https://github.com/user-attachments/assets/055fe55f-add5-40d7-951d-937ae116e945" />


#### Events
<img width="1188" height="262" alt="image" src="https://github.com/user-attachments/assets/213745d7-6cb0-4331-b404-4bedc05d6539" />

---

### Test de integración - Backend

#### Places
<img width="863" height="356" alt="image" src="https://github.com/user-attachments/assets/d843137a-6c0b-4921-87ef-ce4d22612a15" />


### Test unitario - FrontEnd

#### Login
<img width="895" height="457" alt="image" src="https://github.com/user-attachments/assets/7a92b5b0-2652-437a-98c4-77105236fa7c" />


### Test E2E - FrontEnd

<img width="806" height="198" alt="image" src="https://github.com/user-attachments/assets/5a481fea-ca05-4ced-ab21-6e0134804522" />


---

## DOCUMENTACION DE LA API

### Base URL y conceptos globales

- **Servidor HTTP**: `http://localhost:3000` (puerto configurable via `PORT`).
- **Prefijo común de la API**: `/api`.
- **Archivos estáticos** (imágenes de eventos): `GET /uploads/<nombre_archivo>`.

#### Autenticación

- Se utiliza **JWT** con esquema `Authorization: Bearer <token>`.
- Los tokens de usuarios finales se obtienen en `POST /api/auth/login`.
- Los tokens de empresas organizadoras se obtienen en `POST /api/auth/login-company`.
- Endpoints protegidos agregan `verifyToken`; algunos requieren además `isCompany` o `isAdmin`.
- Los tokens incluyen un `bootId`. Si el servidor se reinicia y cambia el `bootId`, los tokens previos quedan invalidados (respuesta `401` con código `RESTART_INVALIDATED_TOKEN`).

#### Formato de respuestas y errores

- Controladores públicos suelen devolver `200` con datos crudos o `{ ok: true, data: ... }`.
- Errores controlados incluyen un mensaje en castellano y, en algunos casos, `details`.
- Errores de validación usan `400`, falta de autenticación `401`, falta de permisos `403`, no encontrado `404`, conflictos `409`, error interno `500`.

---

### Endpoints del Sistema

#### `GET /api/system/boot`
- **Descripción:** Expone el identificador de arranque actual del backend para validar la vigencia de tokens.
- **Auth:** No requiere.
- **Respuesta 200:**
  ```json
  { "bootId": "uuid-..." }
  ```

---

### Autenticación y Usuarios

#### `POST /api/auth/register`
- **Descripción:** Alta de usuario final con verificación reCAPTCHA.
- **Body:**
  ```json
  {
    "dni": 12345678,
    "name": "Juan",
    "surname": "Perez",
    "mail": "juan@example.com",
    "password": "Secreta123",
    "birthDate": "2000-01-31",
    "captchaToken": "<token_recaptcha>"
  }
  ```
- **Respuesta 201:** `{"message": "Usuario registrado correctamente."}`
- **Errores:**
    - `400`: Campos faltantes, contraseña débil, CAPTCHA inválido.
    - `409`: DNI o Email ya registrados.

#### `POST /api/auth/register-company`
- **Descripción:** Alta de empresa organizadora con verificación reCAPTCHA.
- **Body:**
  ```json
  {
    "companyName": "Eventos SRL",
    "cuil": "30-12345678-9",
    "contactEmail": "contacto@eventos.com",
    "password": "Clave123",
    "phone": "341...",
    "address": "Calle Falsa 123",
    "captchaToken": "<token_recaptcha>"
  }
  ```
- **Respuesta 201:** `{"message": "Empresa registrada exitosamente"}`
- **Errores:**
    - `400`: Campos faltantes o contraseña débil.
    - `409`: CUIL o Email ya registrados (incluso si el mail pertenece a un usuario).

#### `POST /api/auth/login`
- **Descripción:** Login de usuario final.
- **Body:** `{"mail": "...", "password": "..."}`
- **Respuesta 200:**
  ```json
  {
    "token": "eyJhbG...",
    "user": { "dni": 123.., "role": "user", ... }
  }
  ```
- **Errores:** `401` Credenciales inválidas.

#### `POST /api/auth/login-company`
- **Descripción:** Login de empresas organizadoras.
- **Body:** `{"contactEmail": "...", "password": "..."}`
- **Respuesta 200:**
  ```json
  {
    "token": "eyJhbG...",
    "user": { "idOrganiser": "...", "role": "company", ... }
  }
  ```

#### `GET /api/auth/validate`
- **Descripción:** Valida si el token actual sigue activo y devuelve el payload.
- **Auth:** Requiere Token.
- **Respuesta 200:** `{"valid": true, "user": { ... }}`
- **Errores:** `401` No autorizado, `403` Token inválido.

#### `POST /api/auth/google`
- **Descripción:** Login o Registro mediante Google OAuth.
- **Body:** `{"credential": "<google_token_id>"}`
- **Respuesta 200:** `{"token": "...", "user": { ... }}`
- **Errores:** `401` Token Google inválido.

#### `POST /api/auth/check-password-strength`
- **Descripción:** Evalúa la seguridad de una contraseña.
- **Body:** `{"password": "..."}`
- **Respuesta 200:** `{"strength": "medium", "score": 50, "feedback": [...]}`

#### `POST /api/auth/forgot-password`
- **Descripción:** Envía email para recuperación de contraseña.
- **Body:** `{"mail": "..."}`
- **Respuesta 200:** `{"message": "Si el correo existe..."}`

#### `POST /api/auth/reset-password`
- **Descripción:** Establece nueva contraseña con token de recuperación.
- **Body:** `{"token": "...", "newPassword": "..."}`
- **Respuesta 200:** `{"message": "Contraseña actualizada correctamente."}`

#### `POST /api/auth/change-password`
- **Descripción:** Cambia la contraseña del usuario logueado.
- **Auth:** Requiere Token.
- **Body:** `{"currentPassword": "...", "newPassword": "..."}`
- **Respuesta 200:** `{"message": "Contraseña actualizada correctamente."}`

#### `PUT /api/auth/profile`
- **Descripción:** Actualiza datos del perfil (nombre, teléfono).
- **Auth:** Requiere Token.
- **Body:** `{"name": "...", "surname": "...", "phone": "..."}`
- **Respuesta 200:** `{"ok": true, "message": "Perfil actualizado", "user": ...}`

---

### Lugares y Sectores

#### `GET /api/places/getPlaces`
- **Descripción:** Lista todos los lugares ordenados alfabéticamente.
- **Respuesta 200:** `[{ "idPlace": "...", "name": "...", ... }]`

#### `GET /api/places/:idPlace/sectors`
- **Descripción:** Obtiene los sectores de un lugar.
- **Respuesta 200:** `[{ "idSector": 1, "name": "Platea", "sectorType": "enumerated" }]`

---

### Eventos (Público)

#### `GET /api/events/approved`
- **Descripción:** Listado principal de eventos aprobados y con stock.
- **Respuesta 200:** `{"ok": true, "data": [{ "idEvent": "...", "availableSeats": 50, ... }]}`

#### `GET /api/events/featured`
- **Descripción:** Listado de eventos destacados.
- **Respuesta 200:** `{"ok": true, "data": [...]}`

#### `GET /api/events/search`
- **Descripción:** Busca eventos por nombre o tipo.
- **Query:** `?query=recital`
- **Respuesta 200:** `{"ok": true, "data": [...]}`
- **Errores:** `400` Consulta vacía o muy corta.

#### `GET /api/events/available-dates/:idPlace`
- **Descripción:** Devuelve fechas ocupadas en un lugar para validación de calendario.
- **Respuesta 200:** `{"ok": true, "data": ["2025-10-20", ...]}`

#### `GET /api/events/events/:id`
- **Descripción:** Detalle resumido del evento.
- **Respuesta 200:**
  ```json
  {
    "ok": true,
    "data": {
      "id": "...", "eventName": "Show", "minPrice": 5000, "agotado": false, ...
    }
  }
  ```

#### `GET /api/events/events/:id/sectors`
- **Descripción:** Sectores del evento con precios y disponibilidad.
- **Respuesta 200:**
  ```json
  { "ok": true, "data": [{ "idSector": 1, "price": 5000, "availableTickets": 20 }] }
  ```

#### `GET /api/events/events/:id/tickets/map`
- **Descripción:** Mapa optimizado de asientos disponibles.
- **Respuesta 200:** `{"ok": true, "data": { "place-sector-seat": seatId, ... }}`

---

### Eventos (Gestión Empresa)

#### `POST /api/events/createEvent`
- **Descripción:** Crea un evento (Estado: Pending). Valida contenido con IA.
- **Auth:** Requiere Token (Rol Company).
- **Body (FormData):** `name`, `description`, `date`, `idPlace`, `sectors` (JSON), `image` (File).
- **Respuesta 201:** `{"ok": true, "message": "Evento creado...", "data": ...}`
- **Errores:** `400` Contenido inapropiado (IA) o datos inválidos.

#### `GET /api/events/company`
- **Descripción:** Lista los eventos creados por la empresa logueada.
- **Auth:** Requiere Token (Rol Company).
- **Respuesta 200:** `{"ok": true, "data": [{ "idEvent": "...", "soldPercentage": 45.5, ... }]}`

#### `PUT /api/events/:id`
- **Descripción:** Edita un evento existente.
- **Auth:** Requiere Token (Rol Company).
- **Respuesta 200:** `{"ok": true, "message": "Evento actualizado"}`

#### `DELETE /api/events/:id`
- **Descripción:** Elimina un evento si no tiene ventas asociadas.
- **Auth:** Requiere Token (Rol Company).
- **Respuesta 200:** `{"ok": true, "message": "Evento eliminado"}`

---

### Eventos (Gestión Admin)

#### `GET /api/events/pending`
- **Descripción:** Eventos pendientes de aprobación.
- **Auth:** Requiere Token (Rol Admin).

#### `PATCH /api/events/:id/approve`
- **Descripción:** Aprueba un evento (Pasa a estado Approved).
- **Auth:** Requiere Token (Rol Admin).

#### `PATCH /api/events/:id/reject`
- **Descripción:** Rechaza un evento (Pasa a estado Rejected).
- **Auth:** Requiere Token (Rol Admin).

#### `PATCH /api/events/:id/feature`
- **Descripción:** Marca/Desmarca un evento como destacado.
- **Auth:** Requiere Token (Rol Admin).

---

### Ventas

#### `POST /api/sales/confirm`
- **Descripción:** Confirma venta, asigna tickets y envía email. Uso interno.
- **Body:** `{"dniClient": ..., "tickets": [...]}`
- **Respuesta 201:** `{"message": "Venta confirmada", "idSale": "..."}`

#### `GET /api/sales/my-tickets`
- **Descripción:** Historial de compras del usuario.
- **Auth:** Requiere Token (User).
- **Respuesta 200:** `{"data": [{ "eventName": "...", "qrUrl": "..." }]}`

#### `GET /api/sales/stats`
- **Descripción:** Estadísticas globales del sistema (Ventas hoy, recaudación, etc.).
- **Auth:** Requiere Token (Admin).
- **Respuesta 200:** `{"salesToday": 10, "revenueToday": 50000, ...}`

#### `GET /api/sales/company-stats`
- **Descripción:** Estadísticas propias de la empresa.
- **Auth:** Requiere Token (Company).
- **Respuesta 200:** `{"activeEvents": 2, "ticketsSold": 150, "totalRevenue": 450000}`

---

### Pagos (Stripe)

#### `POST /api/stripe/checkout`
- **Descripción:** Inicia sesión de pago y reserva.
- **Body:** `{"items": [...], "dniClient": ...}`
- **Respuesta 200:** `{"url": "https://checkout.stripe.com/..."}`

#### `POST /api/stripe/webhook`
- **Descripción:** Webhook para confirmar/liberar tickets según estado del pago.
- **Auth:** Valida firma `Stripe-Signature`.

---

### Mensajes y Soporte

#### `POST /api/messages`
- **Descripción:** Crea un nuevo mensaje de contacto.
- **Body:** `{"title": "...", "description": "...", "senderEmail": "..."}`
- **Respuesta 201:** `{"idMessage": "...", "state": "unread"}`

#### `GET /api/messages`
- **Descripción:** Lista mensajes no descartados.
- **Auth:** Requiere Token (Admin).
- **Respuesta 200:** `[{ "state": "unread", "title": "...", ... }]`

#### `PUT /api/messages/:id/reply`
- **Descripción:** Responde un mensaje y notifica por email.
- **Auth:** Requiere Token (Admin).
- **Body:** `{"responseText": "..."}`
- **Respuesta 200:** `{"message": "Mensaje respondido."}`

#### `PUT /api/messages/:id/reject`
- **Descripción:** Rechaza un mensaje.
- **Auth:** Requiere Token (Admin).

#### `PUT /api/messages/:id/discard`
- **Descripción:** Mueve un mensaje a descartados (borrado lógico).
- **Auth:** Requiere Token (Admin).

---

### Inteligencia Artificial

#### `POST /api/ai/`
- **Descripción:** Chatbot asistente.
- **Body:** `{"message": "Hola..."}`
- **Respuesta 200:** `{"reply": "Soy el asistente de TicketApp..."}`

