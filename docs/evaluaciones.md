# Sistema de Evaluaciones Académicas - EduCampus LMS

Este documento técnico y operativo describe en detalle los mecanismos de evaluación, las metodologías de calificación y la estructura de consolidación de rendimiento estudiantil dentro de la plataforma EduCampus LMS.

---

## 📋 1. Metodologías y Tipos de Evaluación

La plataforma soporta un enfoque de evaluación integral, permitiendo a los instructores combinar métricas cuantitativas y cualitativas.

### Tipos de Evaluación
* **Evaluación Formativa:** Cuestionarios ágiles, foros de debate y actividades prácticas semanales diseñadas para monitorear el progreso continuo del estudiante y ofrecer retroalimentación en tiempo real.
* **Evaluación Sumativa:** Exámenes parciales, entregas de proyectos de fin de módulo y defensas prácticas orientadas a validar la adquisición global de competencias al cierre de un ciclo.
* **Evaluación Diagnóstica:** Pruebas iniciales automatizadas aplicadas al inicio de cada periodo para medir los conocimientos previos del estudiante sin afectar su promedio ponderado.

### Evaluación Numérica
* **Esquema Cuantitativo:** Implementación de un sistema métrico estandarizado (escala por defecto de `0.0` a `5.0`, con soporte configurable para escalas de `0` a `100`).
* **Cálculo de Ponderaciones:** El sistema permite asignar pesos porcentuales específicos a cada actividad dentro del libro de calificaciones virtual, automatizando el cálculo de promedios ponderados y previniendo errores manuales de digitación.

### Evaluación por Logros
* **Enfoque Basado en Competencias:** Vinculación de actividades evaluativas con objetivos de aprendizaje u objetivos de cumplimiento previamente configurados en el programa curricular.
* **Criterios de Aceptación:** Para aprobar una evaluación bajo esta modalidad, el estudiante debe demostrar el dominio de indicadores específicos (Saber, Hacer y Ser), facilitando un seguimiento detallado que va más allá de una simple nota numérica.

---

## ⚙️ 2. Escalas de Desempeño y Control de Calificaciones

Para unificar la interpretación del rendimiento académico, el sistema traduce los datos métricos en niveles estandarizados de competencia.

### Escalas de Desempeño
El sistema homologa los resultados numéricos y los logros alcanzados bajo una matriz de cuatro niveles institucionales:
* **Superior (4.6 - 5.0):** El estudiante excede los objetivos propuestos y demuestra un dominio autónomo y crítico de los temas.
* **Alto (4.0 - 4.5):** Cumple satisfactoriamente con la totalidad de las competencias y entregas en los tiempos estipulados.
* **Básico (3.0 - 3.9):** Alcanza los mínimos requeridos para aprobar, mostrando oportunidades de mejora en la profundización del contenido.
* **Bajo (0.0 - 2.9):** No logra demostrar la adquisición de los conocimientos base. Requiere planes de nivelación pedagógica obligatorios.

### Registro de Notas
* **Libro de Calificaciones Centralizado:** Una base de datos integrada y protegida donde se registran de forma automática los resultados de los cuestionarios interactivos, y de forma manual las rúbricas de proyectos evaluadas por los docentes.
* **Trazabilidad y Auditoría:** Cada inserción o modificación en el registro de notas genera un log de auditoría inmutable que detalla fecha, hora e identidad del usuario (docente o administrador) que realizó el cambio, garantizando la transparencia del proceso.

### Resultados por Periodo Académico
* **Cortes y Consolidados:** Al finalizar cada trimestre o ciclo escolar establecido, la plataforma ejecuta una rutina de consolidación de datos para cerrar el periodo actual.
* **Boletines Automatizados:** Generación de reportes analíticos descargables en formato PDF para estudiantes y acudientes, los cuales muestran el promedio acumulado del periodo, la posición del estudiante respecto al grupo, y alertas tempranas en caso de registrar materias en riesgo de reprobación.