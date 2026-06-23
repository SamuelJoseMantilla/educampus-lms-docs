# Guía de Instalación y Configuración Local - EduCampus LMS

Este documento proporciona las instrucciones técnicas necesarias para configurar, desplegar y verificar el entorno de desarrollo local de la plataforma EduCampus LMS de manera correcta y estandarizada.

---
## 💻 1. Requisitos del Entorno

Antes de iniciar con la instalación, asegúrate de tener instaladas y configuradas las siguientes dependencias de software globales en tu sistema operativo:

* **Node.js:** Versión v20.x (LTS) o superior.
* **Gestor de Paquetes:** `npm` v10.x o superior (incluido de forma nativa con Node.js) o `pnpm` v9.x.
* **Control de Versiones:** `git` v2.40 o superior.
* **Editor de Código Recomendado:** Visual Studio Code con las extensiones oficiales de ESLint, Prettier y Tailwind CSS IntelliSense instaladas.

---

## 🗄️ 2. Base de Datos

La plataforma utiliza un motor de base de datos relacional para garantizar la integridad de los registros académicos, usuarios e inscripciones.

* **Motor:** PostgreSQL v15 o superior.
* **Configuración Inicial:**
  1. Asegúrate de que el servicio de PostgreSQL se encuentre activo en tu máquina local.
  2. Crea una base de datos vacía dedicada para el proyecto ejecutando la siguiente sentencia en tu terminal de base de datos o cliente de preferencia (pgAdmin, DBeaver, etc.):
```sql
     CREATE DATABASE educampus_db;
     ```
* **Migraciones y Semillas:** No es necesario importar un volcado SQL manual. Los esquemas de tablas, índices y datos iniciales de prueba (seeds) se ejecutan de forma automatizada mediante scripts del ORM desde la consola.

---

## 🔑 3. Variables de Entorno

El sistema requiere de configuraciones clave para interactuar de forma segura con la base de datos, servicios de autenticación y claves criptográficas.

1. En la raíz del proyecto, localiza el archivo de plantilla `.env.example`.
2. Duplica el archivo y renómbralo exactamente como `.env`:
```bash
   cp .env.example .env