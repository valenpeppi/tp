# Venta de entradas para eventos


## Instalación y ejecución del proyecto

### Requisitos previos
*Node js
*mySQL
*

# 🎟️ Venta de Entradas – TP Final DSW 2025

## 📘 Descripción del Proyecto
**Venta de Entradas** es un sistema web completo que permite a los usuarios visualizar eventos, seleccionar sectores o asientos específicos, comprar entradas mediante diferentes medios de pago (Stripe y MercadoPago), y gestionar las compras realizadas.  
Cuenta con un **frontend en React + TypeScript (Vite)** y un **backend en Node.js + Express + Prisma + MySQL**, desarrollados siguiendo las convenciones y buenas prácticas del framework.

El proyecto se desarrolló como **Trabajo Práctico Final 2025** de la asignatura **Desarrollo de Software (UTN – FRRO)**.

---

## 🧩 Tecnologías Principales

| Capa | Tecnología | Descripción |
|------|-------------|--------------|
| **Frontend** | React + TypeScript (Vite) | SPA moderna, con rutas protegidas, contextos globales y componentes dinámicos. |
| **Backend** | Node.js + Express | API REST modular, con controladores, validaciones y manejo de errores. |
| **ORM / DB** | Prisma ORM + MySQL | Mapeo de modelos relacionales y migraciones automáticas. |
| **Autenticación** | JWT + Bcrypt | Registro e inicio de sesión seguros. |
| **Pagos** | Stripe + MercadoPago | Integración para pagos en línea simulados y reales. |
| **Tests** | Vitest / Jest / Playwright | Pruebas unitarias, de integración y end-to-end. |

---

## ⚙️ Instalación y Ejecución del Proyecto

### 🔧 1. Requisitos previos
Asegurate de tener instalado:
- [Node.js](https://nodejs.org/) (v18 o superior)  
- [MySQL](https://dev.mysql.com/downloads/) (v8 o superior)  
- [Git](https://git-scm.com/)  
- Un editor como [VSCode](https://code.visualstudio.com/)

---

### 💾 2. Clonar los repositorios

```bash
# Clonar el frontend
git clone https://github.com/tu-usuario/FrontEnd-Venta-de-Entradas.git
cd FrontEnd-Venta-de-Entradas

# Clonar el backend
git clone https://github.com/tu-usuario/BackEnd-Venta-de-Entradas.git
cd BackEnd-Venta-de-Entradas
