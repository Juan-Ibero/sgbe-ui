# 🧠 SGBE-UI — Sistema de Gestión del Bienestar Estudiantil

> **Universidad Iberoamericana** | Facultad de Ingeniería | Gestión de Proyectos de Software  
> Autor: Juan Manuel Peña | Línea: Mente Activa — Bienestar Mental y Hábitos Digitales

---

## 📌 Descripción del Proyecto

El **SGBE-UI** es una plataforma web y móvil diseñada para apoyar el bienestar mental y emocional de los estudiantes de la Universidad Iberoamericana. Permite a los estudiantes hacer seguimiento de su estado emocional, gestionar hábitos saludables y acceder a recursos de mindfulness de forma autónoma y privada.

### Problema que resuelve
- El 40-50% de estudiantes universitarios experimentan síntomas de ansiedad o depresión
- Tiempos de espera de 2-4 semanas para acceder a consejería profesional
- Falta de herramientas digitales de autogestión del bienestar disponibles 24/7

---

## 🚀 Funcionalidades Principales

| Módulo | Descripción | Estado |
|--------|-------------|--------|
| 🔐 Autenticación | Registro e inicio de sesión con correo institucional | ✅ Completado |
| 📊 Dashboard | Panel de bienestar con tendencias emocionales | ✅ Completado |
| 😊 Registro Emocional | Check-in diario de estado emocional y estrés | 🔄 En progreso |
| 🎯 Gestión de Hábitos | Creación y seguimiento de hábitos con racha | 📅 Sprint 2 |
| 🧘 Recursos Mindfulness | Biblioteca de meditación y técnicas de relajación | 📅 Sprint 2 |
| 💬 Foro Estudiantil | Comunidad de apoyo entre pares | 📅 Sprint 3 |

---

## 🛠️ Stack Tecnológico

### Frontend
- **React 18** + Vite
- React Router v6
- Chart.js (visualizaciones)
- Axios (consumo de API)
- Tailwind CSS

### Backend
- **Node.js** + Express
- JWT (autenticación)
- bcrypt (hash de contraseñas)
- Swagger / OpenAPI 3.0 (documentación API)

### Base de Datos
- **MongoDB Atlas** (base de datos principal)
- Mongoose (ODM)
- Redis (caché de sesiones)

### Servicios Externos
- SendGrid (correos de verificación)
- Firebase Cloud Messaging (notificaciones push)
- AWS S3 (almacenamiento de media)

### Herramientas de Calidad
- ESLint + Prettier (linting y formateo)
- Husky (pre-commit hooks)
- GitHub Actions (CI/CD)

---

## 📁 Estructura del Proyecto

```
sgbe-ui/
├── frontend/                  # Aplicación React (SPA)
│   ├── src/
│   │   ├── components/        # Componentes reutilizables
│   │   ├── pages/             # Páginas principales
│   │   ├── hooks/             # Custom hooks
│   │   ├── services/          # Llamadas a la API
│   │   ├── context/           # Context API (Auth, Theme)
│   │   └── utils/             # Funciones utilitarias
│   ├── .eslintrc.js
│   ├── .prettierrc
│   └── package.json
├── backend/                   # API REST Node.js/Express
│   ├── src/
│   │   ├── controllers/       # Lógica de cada endpoint
│   │   ├── models/            # Modelos Mongoose
│   │   ├── routes/            # Rutas REST
│   │   ├── middleware/        # Auth JWT, validación
│   │   ├── config/            # Configuración DB y env
│   │   └── utils/             # Helpers
│   ├── swagger.yaml           # Documentación API
│   ├── .eslintrc.js
│   └── package.json
├── .husky/                    # Pre-commit hooks
├── .github/
│   └── workflows/             # GitHub Actions CI/CD
├── docker-compose.yml
└── README.md
```

---

## 🔌 Endpoints de la API

| Método | Endpoint | Auth | Descripción |
|--------|----------|------|-------------|
| POST | `/api/auth/register` | Pública | Registro de nuevo usuario |
| POST | `/api/auth/login` | Pública | Inicio de sesión + JWT |
| POST | `/api/auth/logout` | JWT | Cerrar sesión |
| GET | `/api/users/profile` | JWT | Perfil del usuario |
| POST | `/api/emotions` | JWT | Registrar estado emocional |
| GET | `/api/emotions` | JWT | Historial emocional |
| PUT | `/api/emotions/:id` | JWT | Actualizar registro del día |

> 📖 Documentación completa disponible en `/api-docs` (Swagger UI)

---

## 🌿 Estrategia de Ramas

```
main          ← Producción (protegida)
└── develop   ← Integración
    └── feature/HU-001-registro-usuario
    └── feature/HU-002-login
    └── feature/HU-003-dashboard
    └── fix/bug-cors-config
```

| Rama | Uso |
|------|-----|
| `main` | Solo merges desde `release`. Protegida. |
| `develop` | Integración de features terminadas |
| `feature/HU-XXX-*` | Una rama por historia de usuario |
| `fix/bug-*` | Corrección de errores |
| `release/v*` | Preparación de versión |

---

## ⚙️ Cómo ejecutar el proyecto localmente

### Prerrequisitos
- Node.js v18+
- MongoDB Atlas (cuenta gratuita en [mongodb.com](https://mongodb.com))
- Git

### 1. Clonar el repositorio
```bash
git clone https://github.com/TU-USUARIO/sgbe-ui.git
cd sgbe-ui
```

### 2. Configurar el backend
```bash
cd backend
cp .env.example .env
# Editar .env con tus credenciales de MongoDB y JWT_SECRET
npm install
npm run dev
```

### 3. Configurar el frontend
```bash
cd ../frontend
cp .env.example .env
# Editar .env con la URL de tu backend
npm install
npm run dev
```

### 4. Variables de entorno requeridas

**Backend `.env`:**
```env
PORT=3000
MONGODB_URI=mongodb+srv://usuario:password@cluster.mongodb.net/sgbe-ui
JWT_SECRET=tu_clave_secreta_muy_larga
JWT_EXPIRES_IN=24h
SENDGRID_API_KEY=tu_api_key
```

**Frontend `.env`:**
```env
VITE_API_URL=http://localhost:3000/api
```

---

## 📋 Tablero Scrum

El progreso del proyecto se gestiona en **GitHub Projects**:

👉 [Ver Tablero Sprint 1](https://github.com/users/Juan-Ibero/projects/1)

### Sprints

| Sprint | Período | Objetivo |
|--------|---------|----------|
| Sprint 1 | Abr 21 — May 4, 2025 | Autenticación, Dashboard, Registro Emocional |
| Sprint 2 | May 5 — May 18, 2025 | Hábitos, Recursos Mindfulness |
| Sprint 3 | May 19 — Jun 1, 2025 | Foro, Notificaciones, Reportes |

---

## 🎨 Prototipo Figma

👉 [Ver Prototipo de Alta Fidelidad en Figma](https://www.figma.com/make/AHxIiJGXXidtMQXmmJCaL0/Sistema-de-Gesti%C3%B3n-del-Bienestar-Estudiantil?t=zhdMxi4z5snOUi8H-1)

Incluye navegabilidad completa entre:
- Pantalla de Registro
- Inicio de Sesión
- Dashboard Principal
- Registro Emocional
- Perfil de Usuario

---

## 📊 Métricas de Usabilidad

| Métrica | Resultado |
|---------|-----------|
| Usuarios evaluados | 5 |
| Tasa de éxito promedio | 92% |
| Puntuación SUS | 82/100 (Bueno) |
| Errores críticos | 0 |

---

## 📄 Licencia

Este proyecto es de uso académico — Universidad Iberoamericana 2025.

---

<div align="center">
  Desarrollado por Juan Manuel Peña · Universidad Iberoamericana · 2025
</div>
