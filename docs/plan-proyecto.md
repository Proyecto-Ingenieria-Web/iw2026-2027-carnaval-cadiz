# Plan de Proyecto (E3.1)

**Proyecto:** Plataforma de gestión del Concurso Oficial de Agrupaciones Carnavalescas (COAC) y archivo histórico del Carnaval de Cádiz  
**Asignatura:** Ingeniería Web — Grado en Ingeniería Informática (Universidad de Cádiz, curso 2026/2027)  
**Repositorio:** `https://github.com/Proyecto-Ingenieria-Web/iw2026-2027-carnaval-cadiz`

> Este documento constituye el **contrato de trabajo del equipo**: no fija un alcance cerrado, sino cómo trabajará y colaborará el equipo durante el cuatrimestre, revisándose y ajustándose tras cada retrospectiva.

---

## 1. Equipo y roles
Los integrantes del equipo comparten la responsabilidad técnica de análisis, diseño, implementación, pruebas y documentación, asumiendo además los siguientes roles de Scrum:

| Miembro | Usuario GitHub | Rol Scrum | Responsabilidades principales |
| :--- | :--- | :--- | :--- |
| **Juan Manuel Corchado Monje** | `@JuanCorchaMon` | **Product Owner** y Desarrollo | Interlocución con el cliente (profesor), validación de requisitos, gestión y priorización del *Product Backlog*, y desarrollo de historias de usuario. |
| **José María Fernández Salcedo** | `@[usuario-josema]` | **Scrum Master** y Desarrollo | Facilitación de eventos Scrum, supervisión del cumplimiento del proceso y de la *Definition of Done*, eliminación de impedimentos y desarrollo de historias de usuario. |

---

## 2. Roadmap e hitos de entrega
El proyecto se estructura en iteraciones (*sprints*) de **2 semanas**, culminando cada una con un incremento potencialmente entregable, su documentación actualizada y su correspondiente *Milestone* y *Release* en GitHub:

| Hito / Iteración | Fecha prevista | Objetivo principal | Entregables asociados |
| :--- | :--- | :--- | :--- |
| **Hito 0: Inicio** | `[28/11/2026]` | Configuración de la forja en GitHub, preparación de entornos locales (Java 21, Maven) y aprobación del plan de proyecto. | **E3.1** (`docs/plan-proyecto.md`), `AGENTS.md`, `README.md`. |
| **Hito 1: Sprint 1** | `[DD/MM/2026]` | Elicitación de requisitos con el cliente, modelado del dominio base, persistencia inicial y gestión básica de ediciones y agrupaciones (Back-office). | **E3.2** (`docs/requisitos.md`), **E3.3** (`docs/diseno.md` v1), Release `v0.1.0`. |
| **Hito 2: Sprint 2** | `[DD/MM/2026]` | Inscripciones, sorteo, programación de sesiones, evaluación del jurado y vistas públicas de la edición en curso (Front-office). | **E3.3** (`docs/diseno.md` v2), **E3.4** (`docs/pruebas.md` v1), Release `v0.2.0`. |
| **Hito 3: Sprint 3** | `[DD/MM/2026]` | Archivo histórico (búsqueda y catalogación), repertorios de letras, seguridad/roles, migración a MySQL con Flyway y despliegue en AWS. | **E3.4** (`docs/pruebas.md` v2), **E3.5** (`docs/despliegue.md`), Release `v0.3.0`. |
| **Hito final: Cierre** | `[Último día de clase]` | Estabilización, carga completa de datos de prueba en producción, revisión integral de documentación y defensa pública. | **E1** (JAR ejecutable en Release `v1.0.0`), **E2** (Código fuente), **E3** (Documentación completa). |

*(Nota: Los objetivos y fechas de los Sprints 1 a 3 se ajustarán tras la sesión de toma de requisitos con el cliente y al cierre de cada iteración).*

---

## 3. Eventos de Scrum
- **Sprint Planning:** Al inicio de cada sprint (máx. 1 hora). Se seleccionan los *issues* priorizados del *Product Backlog*, se acuerdan sus criterios de aceptación, se asigna un responsable único a cada tarea y se vinculan al *Milestone* del sprint.
- **Daily Scrum:** Reunión breve de seguimiento de **15 minutos** `[indicar días/canal, ej. lunes, miércoles y viernes por Discord/videollamada]` para sincronizar avances, detectar bloqueos y revisar el estado del tablero Kanban.
- **Sprint Review:** Al finalizar cada sprint, junto con el profesor (cliente), para demostrar el incremento funcional desplegado y recoger realimentación sobre requisitos.
- **Sprint Retrospective:** Tras cada *Sprint Review* (30 minutos). El equipo evalúa métricas de la forja (*Insights* de GitHub), revisa el reparto de trabajo y actualiza este documento (`docs/plan-proyecto.md`) si se acuerdan mejoras en el proceso.

---

## 4. Modelo de trabajo y estándares técnicos
El equipo sigue **GitHub Flow** combinado con prácticas de **Programación Extrema (XP)**:
1. **Gestión del trabajo en la forja:** Todo trabajo pendiente se registra como un *issue* en GitHub (usando las plantillas de `.github/ISSUE_TEMPLATE/`), con etiquetas descriptivas, criterios de aceptación verificables y una única persona asignada.
2. **Ramas por tarea:** Ningún integrante trabaja ni hace *push* directamente sobre `main`. Por cada *issue* se crea una rama desde `main` siguiendo el formato `<numero-issue>-<descripcion-corta>` (ejemplo: `12-gestion-ediciones`).
3. **Commits atómicos y convencionales:** Se realizan commits pequeños y coherentes siguiendo la especificación **Conventional Commits** (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `build:`, `ci:`, `chore:`), en imperativo, minúsculas y sin punto final (máximo 72 caracteres).
4. **Integración mediante Pull Request:** Todo cambio (código o documentación) se integra en `main` a través de un *Pull Request* vinculado al *issue* (`Closes #<numero>`), tras pasar las verificaciones automáticas (`./mvnw clean verify`) y recibir la revisión y aprobación de al menos otro miembro del equipo.
5. **Versionado y entregas:** Al cierre de cada *Milestone* se genera una etiqueta con versionado semántico (`vX.Y.Z`) y se publica una *Release* adjuntando el fichero `.jar` ejecutable.

---

## 5. Definición de Done (DoD)
Un *issue* o historia de usuario únicamente se considera terminado y puede cerrarse en la forja cuando cumple **todas** las siguientes condiciones:
- [ ] **Criterios de aceptación:** Satisface todos los criterios funcionales y reglas de negocio acordadas con el cliente para ese *issue*.
- [ ] **Calidad y pruebas:** El código compila sin avisos en el IDE, incluye pruebas automáticas de la funcionalidad y supera `./mvnw clean verify`.
- [ ] **Revisión por pares:** Se ha integrado en `main` mediante un *Pull Request* revisado y aprobado por al menos otro integrante del equipo.
- [ ] **Despliegue:** La funcionalidad opera correctamente en el entorno desplegado, no solo en local.
- [ ] **Documentación actualizada:** Los ficheros Markdown afectados en `docs/` se han actualizado dentro del mismo *Pull Request* que el código.

---

## 6. Acuerdos del equipo y uso responsable de la IA

### 6.1. Comunicación, reparto equitativo y resolución de conflictos
- **Canales:** El equipo utiliza `[WhatsApp / Discord]` para la comunicación diaria y el correo institucional `@alum.uca.es` junto con los comentarios de los *issues* en GitHub para decisiones formales.
- **Equilibrio de carga:** Todos los integrantes contribuyen de forma equilibrada al código de aplicación, a las pruebas automatizadas y a la redacción de la documentación en `docs/`. Cada miembro debe conocer y ser capaz de explicar y modificar cualquier parte del sistema en la defensa.
- **Resolución de conflictos:** Ante desacuerdos técnicos o de reparto de tareas, se debatirán las alternativas con criterios objetivos en la siguiente *Daily* o reunión de equipo buscando el consenso. Si no hubiera acuerdo, el **Scrum Master** (José María Fernández Salcedo) mediará en cuestiones de proceso/reparto y el **Product Owner** (Juan Manuel Corchado Monje) —o la consulta directa al cliente/profesor— decidirá en cuestiones de alcance y requisitos.

### 6.2. Uso responsable de asistentes de IA
De acuerdo con la política de la asignatura, el equipo utiliza herramientas de inteligencia artificial como apoyo al desarrollo bajo las siguientes normas:
- **Herramientas declaradas:**
  - **GitHub Copilot** (integrado en IntelliJ IDEA): autocompletado de código, generación de borradores de pruebas unitarias y sugerencias de refactorización.
  - **Gemini**: apoyo en la estructuración de documentación Markdown, revisión de consultas JPQL/SQL y contraste de alternativas de diseño.
- **Convenciones para agentes:** Se mantiene actualizado el fichero `AGENTS.md` en la raíz del repositorio con las reglas del stack (Java 21, Spring Boot 4, Vaadin 25) y restricciones de seguridad.
- **Supervisión y autoría:** Ningún requisito se extrae de una IA; todos proceden de las reuniones con el cliente. Todo código o texto sugerido por IA es revisado, probado y comprendido por el autor del *commit*, quien asume la plena responsabilidad sobre lo integrado.
