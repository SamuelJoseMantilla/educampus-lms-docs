## ¿Qué problema resuelve publicar cambios en un repositorio remoto?
Respuesta: Resuelve el riesgo de pérdida de información al mantener el código únicamente en el entorno local (tu computadora). Además, centraliza el proyecto para permitir el respaldo en la nube, la integración con herramientas de despliegue automatizado y la colaboración, asegurando que el equipo tenga acceso a la última versión oficial.

## ¿Por qué es necesario traer cambios remotos antes de continuar trabajando?
Respuesta: Es fundamental para evitar trabajar sobre código obsoleto. Sincronizar la rama local con el repositorio remoto mediante un git pull garantiza que tus nuevos desarrollos se construyan sobre la base más reciente del proyecto, previniendo la acumulación de conflictos complejos y desalineaciones severas en el historial.

## ¿Qué ventaja tiene reorganizar una rama antes de integrarla?
Respuesta: La ventaja principal de usar git rebase es que reescribe la base de tu rama secundaria colocándola encima del último commit de la rama principal. Esto elimina los commits de fusión (merge commits) innecesarios y genera un historial completamente lineal y limpio, lo que facilita enormemente la lectura de la línea de tiempo y la auditoría del código.

## ¿Por qué se producen los conflictos?
Respuesta: Se producen cuando Git no puede determinar automáticamente cuál versión del código es la correcta. Esto ocurre típicamente cuando dos ramas modifican de forma distinta la misma línea o bloque de un mismo archivo, o cuando una rama borra un archivo que la otra rama está intentando modificar.

## Cuál es el proceso lógico para resolver un conflicto correctamente?
Respuesta:

Identificación: Detener la operación y abrir el archivo afectado para localizar los marcadores de conflicto de Git (<<<<<<<, =======, >>>>>>>).

Conciliación: Analizar ambas propuestas (la local y la entrante) y editar manualmente el documento, combinando las ideas o seleccionando la correcta bajo una redacción limpia y académica.

Limpieza: Eliminar por completo todas las marcas e indicadores que introdujo Git.

Consolidación: Guardar el archivo, añadirlo al área de preparación con git add y concluir el flujo de fusión mediante git commit o el comando de continuación respectivo (--continue).

## ¿Por qué conviene limpiar commits antes de hacer un Pull Request?
Respuesta: Conviene realizar un Squash para consolidar múltiples micro-commits desordenados (como correcciones ortográficas, pruebas de código o ajustes mínimos) en un único bloque de cambio atómico y semántico. Esto evita saturar la rama principal (develop), mantiene el historial limpio y facilita tareas críticas como los cambios de versión o reversiones (rollbacks).

## ¿Qué ventaja tiene aplicar solo un cambio específico desde otra rama?
Respuesta: El uso de git cherry-pick permite extraer un commit específico de manera quirúrgica (como un ajuste puntual de documentación o un hotfix urgente) sin tener que arrastrar características inestables, incompletas o experimentales que residen en la misma rama secundaria, preservando la estabilidad de la rama destino.

## ¿Qué riesgos existen al sobrescribir una rama remota?
Respuesta: El uso de comandos como git push --force altera y reescribe el historial del repositorio en el servidor. El riesgo principal es la pérdida irreversible de código, ya que se pueden eliminar o sobreescribir commits válidos que otros miembros del equipo hayan subido previamente, desincronizando por completo sus entornos de trabajo.

## ¿Qué buenas prácticas aplicaría en un proyecto real?
Respuesta:

Implementar de manera estricta el estándar de Conventional Commits para que cada mensaje del historial sea descriptivo y semántico (ej. feat:, fix:, docs:).

Trabajar con una estructura organizada de ramas independientes por cada funcionalidad o corrección, manteniendo develop o main protegidas.

Realizar limpiezas de historial (Squash) y reajustes lineales (Rebase) antes de abrir cualquier solicitud de integración.

Resolver los conflictos de forma consciente, asegurando una redacción técnica uniforme y libre de duplicidades.

## ¿Qué errores cometió durante el taller y cómo los solucionó?
Respuesta:

Falta de conflictos iniciales (Fast-Forward): Al intentar fusionar ramas en orden lineal directo, Git realizó una unión limpia automática. Se solucionó regresando el historial con git reset --hard para desviar las ramas de manera simultánea en el tiempo, obligando a Git a detenerse y generar el conflicto controlado.

Rechazo en el repositorio remoto (Non-fast-forward): Al reescribir el historial local para forzar el conflicto del taller, GitHub rechazó el push normal porque la punta de la rama estaba atrasada. Se solucionó de forma segura ejecutando un push forzado (git push origin develop --force), dado que el proyecto se estaba manejando individualmente.

Bloqueo en el Pull Request experimental: Al intentar integrar directamente la rama experimental hacia develop, GitHub retuvo la operación por conflictos de duplicidad. Se solucionó directamente en el editor web de GitHub, eliminando manualmente los marcadores de conflicto y removiendo el código experimental rechazado para dejar únicamente la sección de commits aprobada.