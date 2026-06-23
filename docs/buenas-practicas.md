# Manual de Buenas Prácticas de Git y Control de Versiones - EduCampus LMS

Este documento recopila las directrices, estándares de calidad y metodologías de Git recomendadas para optimizar el flujo de desarrollo, mitigar riesgos de pérdida de código y mantener una línea de tiempo limpia y auditable dentro del proyecto.

---

## 💬 1. Buenas Prácticas de Commits

El historial de commits es la bitácora de ingeniería del proyecto. Un buen historial permite diagnosticar errores rápidamente y automatizar lanzamientos.

* **Sigue la Especificación Semántica:** Es obligatorio el uso de *Conventional Commits* (tipo(alcance): descripción). Nunca agrupes cambios no relacionados en un solo commit.
* **Haz Commits Pequeños y Atómicos:** Un commit debe encargarse de resolver **una sola cosa**. Si estás desarrollando una vista y encuentras un error ortográfico en otra página, no mezcles ambos cambios; haz un commit para la característica y otro diferente para el ajuste de texto.
* **Evita Commits Genéricos:** Mensajes como "arreglos", "actualización" o "f" reducen radicalmente la trazabilidad del código y están estrictamente prohibidos.
* **Mantén el Código Funcional:** Nunca hagas un commit de código que rompa la compilación del proyecto local, a menos que estés respaldando de emergencia tu rama de trabajo en el servidor remoto al final de la jornada.

---

## 🌿 2. Buenas Prácticas de Ramas

Las ramas aíslan el trabajo de forma segura para prevenir regresiones en las funcionalidades que ya están estables.

* **Usa la Rama Base Correcta:** Todas las ramas de características (feature/), correcciones (bugfix/) o documentación (docs/) deben nacer obligatoriamente desde la versión más reciente de la rama develop.
* **Ramas de Vida Corta:** Una rama de trabajo debe tener un alcance delimitado para que pueda integrarse en un par de días. Mantener una rama abierta durante semanas incrementa exponencialmente la probabilidad de sufrir conflictos masivos de fusión.
* **Elimina las Ramas Integradas:** Una vez que un Pull Request ha sido aprobado y mezclado exitosamente en develop, la rama remota y local debe eliminarse para mantener el repositorio limpio.
  Ejemplo en consola: git branch -d feature/nombre-rama

---

## 🔍 3. Buenas Prácticas de Revisión de Código (Code Review)

La revisión es una herramienta pedagógica y de control de calidad para asegurar que el código se adhiera a las reglas del diseño de software.

* **Revisa tu Propio Código Primero:** Antes de solicitar que un compañero o líder técnico revise tu Pull Request, inspecciona tu pestaña de Files Changed en GitHub. Asegúrate de eliminar comentarios temporales (// TODO), declaraciones console.log o código muerto.
* **Proporciona Contexto en el PR:** No asumas que el revisor sabe exactamente qué hiciste. Documenta el "por qué" se tomó esa decisión técnica, adjunta capturas de pantalla si modificaste elementos de la interfaz de usuario y detalla los pasos para probarlo.
* **Mentalidad Colaborativa y Empática:** Al comentar el código de un compañero, enfócate en la solución técnica y no en la persona. Sé constructivo. Al recibir feedback, tómalo como una oportunidad de mejora para el producto.

---

## 🔄 4. Buenas Prácticas de Sincronización

Sincronizar el entorno local evita el aislamiento del código y reduce las sorpresas al momento de la integración.

* **Sincronización Diaria Obligatoria:** Lo primero que debe hacer un desarrollador al iniciar su jornada es actualizar sus referencias locales con respecto al servidor remoto.
  Ejemplo en consola: git checkout develop && git pull origin develop
* **Integra los Avances de la Rama Principal en tu Rama:** Si estás trabajando en una funcionalidad compleja que requiere varios días, integra periódicamente (merge o rebase) los cambios que otros desarrolladores hayan subido a develop hacia tu rama de trabajo. Esto distribuirá la resolución de conflictos en micro-pasos en lugar de acumularlos todos para el final.

---

## 🚀 5. Buenas Prácticas Antes de Integrar Cambios

Antes de presionar el botón de fusión o solicitar el cierre de una tarea, se debe certificar la estabilidad técnica de los cambios.

* **Ejecuta Pruebas y Linters Locales:** Asegúrate de que el formateador de código y el analizador estático no reporten advertencias ni errores en tu terminal.
  Ejemplo en consola: npm run lint
* **Prueba el Flujo de Instalación Limpio:** Simula el comportamiento que experimentaría otro desarrollador al descargar tus cambios. Levanta el servidor desde cero, limpia la base de datos local y ejecuta las migraciones para validar que tus modificaciones no alteren los entornos de tus compañeros.
* **Cero Conflictos Activos:** Nunca solicites la aprobación de un Pull Request que contenga alertas de conflictos con la rama destino en la interfaz de GitHub. Es responsabilidad del autor de la rama resolverlos localmente antes de delegar la revisión.