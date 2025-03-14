# README - Plataforma Escolar Laredu

## Descripción General
Laredu es una plataforma escolar desarrollada con **Laravel 11** para el backend y **React 19 con TypeScript** para el frontend. Su objetivo es gestionar usuarios, cursos, asignaturas, tareas, asistencia, eventos, mensajería interna y roles/permisos dentro del sistema educativo.

## Tecnologías Utilizadas
- **Backend**: Laravel 11 (PHP 8.2+), MySQL 8
- **Frontend**: React 19, Vite, TypeScript, Tailwind CSS 4
- **Autenticación**: Laravel Sanctum
- **Calendario**: FullCalendar.js
- **ORM**: Eloquent (Laravel)

---

## Instalación
### Requisitos Previos
- **Node.js** (versión recomendada: 18 o 20)
- **npm** (versión recomendada: 8+)
- **PHP 8.2+**, **Composer**, **MySQL 8**

### Instalación Backend (Laravel 11)
```bash
composer create-project laravel/laravel backend
cd backend
php artisan serve
```
Configura la base de datos en el archivo `.env`:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laredu
DB_USERNAME=root
DB_PASSWORD=
```
Ejecuta las migraciones y seeders:
```bash
php artisan migrate --seed
```

### Instalación Frontend (React 19 + Vite)
```bash
cd frontend
npm create vite@latest .
npm install
npm run dev
```

---

## Estructura del Proyecto
```
laredu/
├── backend/   # Código Laravel 11
└── frontend/  # Código React 19
```
**Backend:**
```
backend/
├── app/
├── database/
│   ├── migrations/
│   ├── seeders/
├── routes/
│   ├── api.php
└── .env
```
**Frontend:**
```
frontend/
├── src/
│   ├── components/
│   ├── pages/
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── package.json
└── vite.config.ts
```

---

## Funcionalidades Implementadas
### Backend (Laravel 11)
- **Autenticación con Laravel Sanctum**
- **Gestión de Usuarios, Roles y Permisos**
- **Manejo de Cursos, Asignaturas y Evaluaciones**
- **Registro de asistencia y eventos en calendario**
- **Mensajería interna entre usuarios**
- **API RESTful con protección de rutas**

### Frontend (React 19 + TypeScript)
- **Registro e inicio de sesión con tokens**
- **Lista de cursos y asignaturas**
- **Gestión de tareas y entrega de asignaciones**
- **Interfaz responsive con Tailwind CSS 4**
- **Consumo de API con Fetch/Axios**

---

## Configuración de CORS
En `backend/config/cors.php`:
```php
return [
    'paths' => ['api/*'],
    'allowed_methods' => ['*'],
    'allowed_origins' => ['http://127.0.0.1:5173'],
    'allowed_headers' => ['*'],
];
```

---

## Uso de la API (Ejemplos con Fetch)
### Login
```js
fetch("http://127.0.0.1:8000/api/login", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ email, password })
})
.then(res => res.json())
.then(data => localStorage.setItem("token", data.token));
```

### Obtener Cursos
```js
fetch("http://127.0.0.1:8000/api/courses", {
  headers: { Authorization: "Bearer " + localStorage.getItem("token") }
})
.then(res => res.json())
.then(data => console.log(data));
```

---

## Desarrollo y Contribuciones
1. Clona el repositorio:
```bash
git clone https://github.com/usuario/laredu.git
```
2. Crea una nueva rama:
```bash
git checkout -b feature/nueva-funcionalidad
```
3. Realiza cambios y súbelos:
```bash
git commit -m "Añadida nueva funcionalidad"
git push origin feature/nueva-funcionalidad
```
4. Crea un Pull Request en GitHub.

---

## Contacto y Soporte
Para consultas o reportes de errores, abre un issue en el repositorio o contacta al equipo de desarrollo en `soporte@laredu.com`.

