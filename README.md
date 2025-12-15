<h1>🏠 TicketApp – Repositorio Central</h1>

<p align="center">
  <a href="https://github.com/valenpeppi/FrontEnd-Venta-de-Entradas" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/💻%20Ir%20al%20Frontend-React%20%7C%20Vite-0b7285?style=for-the-badge&logo=react&logoColor=white" alt="Repo Frontend"/>
  </a>
  <a href="https://github.com/valenpeppi/BackEnd-Venta-de-Entradas" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/⚙️%20Ir%20al%20Backend-Node.js%20%7C%20Express-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Repo Backend"/>
  </a>
  <a href="https://drive.google.com/file/d/1JQ4jZBuJwJ3PSq4Bxjy0-jp5qHoPxyZK/view" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/🗺️%20Ver%20Modelo%20ER-DER-ff9800?style=for-the-badge&logo=googledrive&logoColor=white" alt="DER TicketApp"/>
  </a>
  <a href="https://github.com/valenpeppi/tp/blob/main/docs.md" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/📄%20Documentación%20API-Docs-4C51BF?style=for-the-badge&logo=readme&logoColor=white" alt="Docs API"/>
  </a>
</p>

<p align="center">
  <a href="https://github.com/agussantinelli" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/👤%20Agustín%20Santinelli-agussantinelli-000000?style=for-the-badge&logo=github&logoColor=white" alt="Agus"/>
  </a>
  <a href="https://github.com/martin-ratti" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/👤%20Martín%20Ratti-martin--ratti-000000?style=for-the-badge&logo=github&logoColor=white" alt="Martín"/>
  </a>
  <a href="https://github.com/gianzaba" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/👤%20Gianlucas%20Zabaleta-gianzaba-000000?style=for-the-badge&logo=github&logoColor=white" alt="Gianlucas"/>
  </a>
  <a href="https://github.com/valenpeppi" target="_blank" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/👤%20Valentín%20Peppino-valenpeppi-000000?style=for-the-badge&logo=github&logoColor=white" alt="Valentín"/>
  </a>
</p>

<hr/>

<h2>🎯 Visión General</h2>

<p>
  <strong>TicketApp</strong> es una solución integral para la <strong>venta y gestión de entradas</strong> desarrollada como trabajo práctico final para la cátedra <strong>Desarrollo de Software (DSW) – UTN FRRO 2025</strong>.
</p>
<p>
  El sistema está compuesto por dos grandes módulos desacoplados (Frontend y Backend) que interactúan mediante una API RESTful, permitiendo a usuarios comprar entradas, a empresas organizar eventos y a administradores gestionar la plataforma.
</p>

<hr/>

<h2>🏗️ Arquitectura y Tecnologías</h2>

<table>
  <thead>
    <tr>
      <th align="left">Capa</th>
      <th align="left">Stack Tecnológico</th>
      <th align="left">Detalles de Implementación</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>🎨 Frontend</strong></td>
      <td>
        <code>React 19</code>
        <code>TypeScript</code>
        <code>Vite</code>
        <code>React Router</code>
        <code>Axios</code>
      </td>
      <td>SPA con arquitectura modular. Uso de <strong>Context API</strong> para estado global y hooks personalizados. Diseño responsivo sin frameworks CSS pesados.</td>
    </tr>
    <tr>
      <td><strong>⚙️ Backend</strong></td>
      <td>
        <code>Node.js</code>
        <code>Express</code>
        <code>TypeScript</code>
        <code>Prisma ORM</code>
        <code>Zod</code>
      </td>
      <td>API RESTful escalable. Validaciones estrictas de entrada, manejo centralizado de errores y arquitectura MVC.</td>
    </tr>
    <tr>
      <td><strong>🗄️ Base de Datos</strong></td>
      <td>
        <code>MySQL 8</code>
      </td>
      <td>Modelo relacional para gestión compleja de eventos, sectores enumerados, reservas y ventas.</td>
    </tr>
    <tr>
      <td><strong>🔒 Seguridad</strong></td>
      <td>
        <code>JWT</code>
        <code>Bcrypt</code>
        <code>Google reCAPTCHA</code>
      </td>
      <td>Autenticación basada en tokens, protección de rutas y prevención de bots en formularios públicos.</td>
    </tr>
    <tr>
      <td><strong>💳 Pagos</strong></td>
      <td>
        <code>Stripe Checkout</code>
      </td>
      <td>Integración de pasarela de pagos con gestión de webhooks para confirmación asíncrona de transacciones.</td>
    </tr>
    <tr>
      <td><strong>🧪 Testing</strong></td>
      <td>
        <code>Vitest</code>
        <code>Playwright</code>
        <code>Jest</code>
        <code>Supertest</code>
      </td>
      <td>Estrategia completa de pruebas: Unitarias, de Integración y End-to-End (E2E).</td>
    </tr>
  </tbody>
</table>

<hr/>

<h2>⚡ Instalación y Despliegue Local</h2>

<h3>1️⃣ Requisitos Previos</h3>
<ul>
  <li><strong>Node.js</strong> (v18 o superior).</li>
  <li><strong>MySQL</strong> (v8 o superior).</li>
  <li><strong>Git</strong>.</li>
</ul>

<h3>2️⃣ Clonar Repositorios</h3>
<p>Debes clonar ambos repositorios en carpetas adyacentes:</p>

<pre><code># Clonar Frontend
git clone https://github.com/valenpeppi/FrontEnd-Venta-de-Entradas.git

# Clonar Backend
git clone https://github.com/valenpeppi/BackEnd-Venta-de-Entradas.git
</code></pre>

<h3>3️⃣ Configuración del Backend</h3>
<p>Crea un archivo <code>.env</code> en la raíz de la carpeta <strong>BackEnd-Venta-de-Entradas</strong>:</p>

<pre><code># Servidor y Base de Datos
PORT=3000
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=password
DB_NAME=ticketapp
DATABASE_URL="mysql://root:password@localhost:3306/ticketapp"

# URLs del Ecosistema
FRONTEND_URL=http://localhost:5173
BACKEND_URL=http://localhost:3000

# Integraciones Externas
OPENROUTER_API_KEY=tu_api_key_ai
RECAPTCHA_SECRET_KEY=tu_recaptcha_secret
STRIPE_SECRET_KEY=tu_stripe_secret
STRIPE_WEBHOOK_SECRET=tu_stripe_webhook_secret
VITE_GOOGLE_CLIENT_ID=tu_google_client_id

# Servicio de Email
EMAIL_USER=ticketapp15@gmail.com
EMAIL_PASS="bbkawrefeqezufei"
</code></pre>

<p><strong>Ejecutar migraciones y seeds (datos iniciales):</strong></p>
<pre><code>cd BackEnd-Venta-de-Entradas
npm install
npx prisma migrate reset
</code></pre>

<h3>4️⃣ Ejecución</h3>

<strong>Terminal 1 - Backend:</strong>
<pre><code>cd BackEnd-Venta-de-Entradas
npm run dev
</code></pre>

<strong>Terminal 2 - Frontend:</strong>
<pre><code>cd FrontEnd-Venta-de-Entradas
npm install
npm run dev
</code></pre>

<hr/>

<h2>🔑 Credenciales de Acceso (Demo)</h2>

<table>
  <thead>
    <tr>
      <th>Rol</th>
      <th>Email</th>
      <th>Contraseña</th>
      <th>Permisos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Usuario</strong></td>
      <td><code>gian@hotmail.com</code></td>
      <td><code>gian</code></td>
      <td>Comprar entradas, ver historial, chat IA.</td>
    </tr>
    <tr>
      <td><strong>Organizador</strong></td>
      <td><code>sbrolla@gmail.com</code></td>
      <td><code>peppi</code></td>
      <td>Crear eventos, gestionar ventas.</td>
    </tr>
    <tr>
      <td><strong>Administrador</strong></td>
      <td><code>peppi@gmail.com</code></td>
      <td><code>peppi</code></td>
      <td>Aprobar eventos, destacar eventos, gestión global.</td>
    </tr>
  </tbody>
</table>

<hr/>

<h2>🧪 Ejecución de Pruebas</h2>

<p>Comandos para verificar la integridad del sistema:</p>

<h3>Backend (Jest + Supertest)</h3>
<pre><code># Unitarios
npm run test:unit

# Integración
npm run test:integration
</code></pre>

<h3>Frontend (Vitest + Playwright)</h3>
<pre><code># Unitarios (Componentes/Hooks)
npm run test:unit

# End-to-End (Flujos completos)
npm run test:e2e
</code></pre>

<hr/>

<h2>📺 Demo y Documentación</h2>

<p align="center">
  <a href="https://youtu.be/8xIs6wFfBYE?si=NOzRUeTZ0B0ZajA8" target="_blank">
    <img src="https://img.shields.io/badge/🎥%20Ver%20Video%20Demo-YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Video Demo"/>
  </a>
  <a href="https://github.com/valenpeppi/tp/blob/main/docs.md" target="_blank">
    <img src="https://img.shields.io/badge/📄%20Documentación%20Técnica-Leer-blue?style=for-the-badge&logo=markdown&logoColor=white" alt="Docs"/>
  </a>
</p>

<hr/>

<h2>📞 Contacto</h2>

<p align="center">
  <strong>Gianlucas Zabaleta</strong><br>
  📧 gianzabaleta6@hotmail.com<br>
  📱 2478509639
</p>
