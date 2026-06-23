# Manual de Buenas Prácticas de Git y Control de Versiones - EduCampus LMS

Este documento recopila las directrices, estándares de calidad y metodologías de Git recomendadas para optimizar el flujo de desarrollo, mitigar riesgos de pérdida de código y mantener una línea de tiempo limpia y auditable.

---

## 💬 1. Buenas Prácticas de Commits

El historial de commits es la bitácora de ingeniería del proyecto. Un buen historial permite diagnosticar errores rápidamente y automatizar lanzamientos.

* **Sigue la Especificación Semántica:** Es obligatorio el uso de *Conventional Commits* (`tipo(alcance): descripción`). Nunca agrupes cambios no relacionados en un solo commit.
* **Haz Commits Pequeños y Atómicos:** Un commit debe encargarse de resolver **una sola cosa**. Si estás desarrollando una vista y encuentras un error ortográfico en otra página, no mezcles ambos cambios; haz un commit para la característica y otro diferente para el ajuste de texto.
* **Evita Commits Genéricos:** Mensajes como `git commit -m "arreglos"`, `git commit -m "actualización"` o `git commit -m "f"` reducen radicalmente la trazabilidad del código y están estrictamente prohibidos.
* **Mantén el Código Funcional:** Nunca hagas un commit de código que rompa la compilación del proyecto local, a menos que estés respaldando de emergencia tu rama de trabajo en el servidor remoto al final de la jornada.

---

## 🌿 2. Buenas Prácticas de Ramas

Las ramas aíslan el trabajo de forma segura para prevenir regresiones en las funcionalidades que ya están estables.

* **Usa la Rama Base Correcta:** Todas las ramas de características (`feature/`), correcciones (`bugfix/`) o documentación (`docs/`) deben nacer obligatoriamente desde la versión más reciente de la rama `develop`.
* **Ramas de Vida Corta:** Una rama de trabajo debe tener un alcance delimitado para que pueda integrarse en un par de días. Mantener una rama abierta durante semanas incrementa exponencialmente la probabilidad de sufrir conflictos masivos de fusión.
* **Elimina las Ramas Integradas:** Una vez que un Pull Request ha sido aprobado y mezclado exitosamente en `develop`, la rama remota y local debe eliminarse para mantener el repositorio limpio.
```bash
  # Eliminar rama local de forma segura
  git branch -d feature/nombre-rama