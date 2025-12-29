
![NodeJS](https://img.shields.io/badge/Node.js-v18-green)
![Express](https://img.shields.io/badge/Express-4.x-lightgrey)
![Socket.IO](https://img.shields.io/badge/Socket.IO-RealTime-black)

##  Descripción Técnica

Este repositorio contiene la lógica del lado del servidor  para el ecosistema **Manglar Manager**. Actúa como una API centralizada que gestiona la autenticación, la lógica de negocio empresarial y la persistencia de datos.

Adicionalmente, implementa un servidor de **WebSockets** dedicado para manejar la comunicación bidireccional en tiempo real (Chat) entre los clientes conectados.

---

##  Arquitectura y Tecnologías

El backend fue construido siguiendo el patrón MVC  adaptado a API REST:

* **Runtime:** Node.js
* **Framework Web:** Express.js
* **Base de Datos:** MongoDB con Mongoose 
* **Comunicación Real-Time:** Socket.IO
* **Autenticación:** JWT (JSON Web Tokens) & Bcrypt para hashing de contraseñas.
* **Seguridad:** Validación de roles (Middlewares para Admin/Empleado).

---

##  API Endpoints (Ejemplos)

La API expone los siguientes recursos principales:

###  Autenticación (Auth)
| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `POST` | `/api/auth/login` | Inicia sesión y devuelve Token JWT |
| `POST` | `/api/auth/register` | Registra un nuevo empleado (Solo Admin) |

###  Tareas (Tasks)
| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/tasks` | Lista todas las tareas del usuario |
| `POST` | `/api/tasks` | Crea una nueva asignación |
| `PUT` | `/api/tasks/:id` | Actualiza estado o detalles |

###  Departamentos
| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/departments` | Obtiene la estructura organizacional |

---

##  Eventos de Socket.IO (Real-Time)

El servidor escucha y emite los siguientes eventos para el módulo de chat:

* `connection`: Nuevo usuario conectado.
* `join_room`: Usuario entra a un canal de departamento.
* `send_message`: Envío de payload de mensaje.
* `receive_message`: Broadcast del mensaje a los suscriptores.

---

##  Instalación y Configuración

Sigue estos pasos para levantar el servidor en local:

1.  **Clonar repositorio e instalar dependencias:**
    ```bash
    git clone https://github.com/C-HARLY/Manglar-Manager-backend-.git
    cd ManglarManager-Backend
    npm install
    ```


2.  **Ejecutar en modo desarrollo:**
    ```bash
    npm run dev
    ```
    *El servidor iniciará en http://localhost:5173*

---

##  Estructura del Proyecto

El proyecto sigue una organización por **features**, facilitando el mantenimiento:

```text
/ManglarManagerBack-End-main
  ├── /config           # Configuraciones globales (DB, etc.)
  ├── /src
  │   ├── /Complaint    # Módulo de Quejas (Controller, Model, Routes)
  │   ├── /comunication # Lógica de Sockets/Chat
  │   ├── /departments  # Módulo de Departamentos
  │   ├── /services     # Servicios reutilizables
  │   ├── /task         # Gestión de Tareas
  │   ├── /user         # Gestión de Usuarios y Auth
  │   └── /utils        # Helpers y utilidades
  ├── index.js          # Punto de entrada (Entry Point)
  └── .env              # Variables de entorno 

