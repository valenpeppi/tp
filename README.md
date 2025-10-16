# Venta de Entradas – TP DSW 2025

---

## Tecnologías Principales

| Capa | Tecnología | Descripción |
|------|-------------|--------------|
| **Frontend** | HTML + CSS + React + TypeScript (Vite) | SPA moderna, con rutas protegidas, contextos globales y componentes dinámicos. |
| **Backend** | Node.js + Express | API REST modular, con controladores, validaciones y manejo de errores. |
| **ORM / DB** | Prisma ORM + MySQL | Mapeo de modelos relacionales y migraciones automáticas. |
| **Autenticación** | JWT + Bcrypt | Registro e inicio de sesión seguros. |
| **Pagos** | Stripe / MercadoPago | Integración para pagos en línea simulados y reales. |
| **Tests** | Vitest / Jest / Playwright | Pruebas unitarias, de integración y end-to-end. |

---

## Instalación y Ejecución del Proyecto

### Requisitos previos
Tener instalado:
- [Node.js](https://nodejs.org/) (v18 o superior)  
- [MySQL](https://dev.mysql.com/downloads/) (v8 o superior)  
- [Git](https://git-scm.com/)  
- Un editor como [VSCode](https://code.visualstudio.com/)

---

## Clonar los repositorios

```bash
# Clonar el frontend
git clone https://github.com/tu-usuario/FrontEnd-Venta-de-Entradas.git
cd FrontEnd-Venta-de-Entradas

# Clonar el backend
git clone https://github.com/tu-usuario/BackEnd-Venta-de-Entradas.git
cd BackEnd-Venta-de-Entradas

```

## Configurar base de datos

```bash
# Crear el archivo .env en el backend
OPENROUTER_API_KEY=

DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=password
DB_NAME=ticketapp
DATABASE_URL="mysql://root:password@localhost:3306/ticketapp"
FRONTEND_URL=http://localhost:5173
BACKEND_URL=http://localhost:3000

# Clave secreta de reCAPTCHA
RECAPTCHA_SECRET_KEY=
#Clave MP
MP_ACCESS_TOKEN=
#Clave Stripe
STRIPE_SECRET_KEY=
STRIPE_WEBHOOK_SECRET=

# Ejecutar migraciones y seeds iniciales
npx prisma migrate reset

```
## Ejecutar el backend

```bash
cd BackEnd-Venta-de-Entradas
npm install
npm run dev

```
## Ejecutar el frontend

```bash
cd FrontEnd-Venta-de-Entradas
npm install
npm run dev

```

---

## Credenciales de prueba

| ROL | EMAIL | CONTRASEÑA |
|------|-------------|--------------|
| **Usuario** | gian@hotmail.com | gian |
| **Administrador** | peppi@gmail.com | peppi |
| **Organizador** | sbrolla@gmail.com | peppi |

---

## Ejecucion de test

### Backend - JEST

```bash
npm run test

```
### Frontend - VITEST

```bash
npm run test

```

### E2E - PLAYWRIGHT

```bash
npx playwright test --headed

```

---

## Video demostrativo
[Link](https://youtu.be/8xIs6wFfBYE?si=NOzRUeTZ0B0ZajA8)

---

## Documentación de la API
link al docs

---

## Contacto
Email: gianzabaleta6@hotmail.com
Teléfono: 2478509639

