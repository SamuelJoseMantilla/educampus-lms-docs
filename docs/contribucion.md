# Guía Exhaustiva de Contribución - EduCampus LMS

Este documento establece el flujo de trabajo oficial, los estándares de ingeniería de software, las políticas de ramificación y los procedimientos técnicos obligatorios para todo desarrollador que colabore en el ecosistema de EduCampus LMS. El cumplimiento estricto de esta guía garantiza la estabilidad del código, la legibilidad del historial y la eficiencia en la integración continua.

---

## 🌿 1. Modelo de Ramificación y Gestión de Código

Adoptamos una variante simplificada y robusta de *Git Flow*, donde la estabilidad de las ramas principales es una prioridad absoluta.

### Arquitectura de Ramas Core
* **`main` (Producción):** Contiene exclusivamente código completamente estable, testeado y desplegado en el entorno de producción. **Está estrictamente prohibido realizar commits directos o fusiones manuales a esta rama.** Solo recibe integraciones automatizadas tras un tag de versión estable.
* **`develop` (Línea Base de Desarrollo):** Es nuestra rama principal de integración diaria. Todos los equipos fusionan sus características aquí. Actúa como el origen y el destino final de todas las ramas de trabajo de los desarrolladores.

### Cómo crear una rama de trabajo de forma segura
Antes de iniciar cualquier tarea, debes asegurarte de que tu entorno local refleja fielmente el estado del servidor remoto para evitar desajustes en el historial de Git. Ejecuta la siguiente secuencia de comandos en tu terminal:

```bash
# 1. Asegúrate de estar posicionado en la rama de integración
git checkout develop

# 2. Descarga las últimas referencias y metadatos del servidor remoto
git fetch --all --prune

# 3. Sincroniza tu rama local aplicando un avance rápido (Fast-Forward)
git pull origin develop

# 4. Crea y muévete a tu nueva rama de características con un nombre descriptivo
git checkout -b feature/tu-tarea-especifica