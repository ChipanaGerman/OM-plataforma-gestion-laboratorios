# Plataforma Híbrida de Gestión de Laboratorios de Computación

**Proyecto Académico-Empresarial**  
**Carrera de Sistemas / Ingeniería de Software**  
**Universidad [Nombre de la Universidad]**  
**Versión:** 1.0 (Propuesta)  
**Fecha:** Julio 2026

---

## 📋 Tabla de Contenidos

- [Introducción](#introducción)
- [Problemática Común](#problemática-común)
- [Objetivos](#objetivos)
- [Justificación y Beneficios](#justificación-y-beneficios)
- [Enfoque Metodológico](#enfoque-metodológico)
- [Modelo Organizacional Ágil (Spotify Adaptado)](#modelo-organizacional-ágil-spotify-adaptado)
- [Requisitos de Conocimientos y Habilidades](#requisitos-de-conocimientos-y-habilidades)
- [Arquitectura Técnica Propuesta](#arquitectura-técnica-propuesta)
- [Gestión de Imágenes y Trazabilidad](#gestión-de-imágenes-y-trazabilidad)
- [Fases de Implementación](#fases-de-implementación)
- [Conclusiones y Recomendaciones](#conclusiones-y-recomendaciones)
- [Anexos](#anexos)

---

## Introducción

Este proyecto propone el desarrollo de una **Plataforma Híbrida** para la gestión integral de laboratorios de computación, aplicable tanto en entornos universitarios como en empresas de software.

La solución combina gestión de hardware (computadoras, servidores, impresoras), usuarios, proyectos/cursos, repositorios de código (GitLab) y un catálogo centralizado de imágenes de contenedores (Docker), garantizando **estandarización, trazabilidad y reproducibilidad** de entornos.

> 🔴 **Comentario (Santiago):** El concepto de "Plataforma Híbrida" (local + nube) se introduce de manera muy vaga. No se establece la línea de demarcación técnica: qué operaciones/servicios deben ejecutarse localmente por razones de latencia y acceso directo al hardware (como Proxmox o laboratorios físicos) y qué componentes se gestionarán en la nube. Además, el alcance de la "gestión integral" es confuso: ¿el sistema administrará inventario físico (hardware físico real, mantenimiento de máquinas) o solo aprovisionamiento lógico a través de virtualización y contenedores?

---

## Problemática Común

Los laboratorios universitarios y las empresas de software enfrentan problemas similares:

- Gestión fragmentada de recursos físicos y digitales.
- Pérdida significativa de tiempo en instalaciones y configuraciones manuales.
- Entornos no estandarizados que generan inconsistencias ("funciona en mi máquina").
- Falta de trazabilidad del software e imágenes utilizadas.
- Dificultad para replicar entornos entre laboratorio y computadoras personales de estudiantes/desarrolladores.
- Escalabilidad limitada al pasar de academia a industria.

> 🔴 **Comentario (Santiago):** Existe una generalización excesiva al agrupar bajo la misma problemática a la universidad y a la industria. Sus motivaciones y dolores reales son sustancialmente distintos. En la academia, el dolor principal es la pérdida de horas académicas en configuraciones iniciales por parte de alumnos inexpertos. En la industria, el dolor no es "instalar herramientas manualmente" (que ya está solucionado con automatización y scripts), sino la disparidad de entornos entre desarrollo/staging/producción, los costos elevados de infraestructura en la nube, y el estricto cumplimiento de políticas de seguridad y licencias corporativas. El texto debe separar claramente estas dos realidades.

**En el ámbito universitario** se busca especialmente que los alumnos **no pierdan tiempo** en instalaciones y que puedan llevarse las mismas imágenes oficiales a sus computadoras personales para practicar fuera del laboratorio.

> 🔴 **Comentario (Santiago):** Se menciona que la falta de trazabilidad de las imágenes es un problema común, pero en el contexto académico tradicional esto rara vez es un problema de primer orden (los profesores suelen evaluar la funcionalidad, no el origen legal o la compilación exacta de la imagen). En cambio, para una empresa, la trazabilidad, generación de SBOM y escaneo de vulnerabilidades son requisitos legales y de cumplimiento obligatorios. Nuevamente, se asumen necesidades industriales en un entorno educativo que no necesariamente las requiere, sobrecargando el alcance del proyecto académico sin justificación clara.

---

## Objetivos

### Objetivo General
Desarrollar una plataforma híbrida (local + nube) que permita la gestión estandarizada, segura y trazable de laboratorios de computación en contextos académicos y empresariales.

> 🔴 **Comentario (Santiago):** El objetivo general no cumple con los criterios SMART. Conceptos como "gestión estandarizada, segura y trazable" son altamente subjetivos y no definen una métrica de éxito clara. ¿Cómo mediremos la seguridad o la estandarización? Debería definirse un porcentaje de reducción de tiempo de aprovisionamiento, o número de entornos replicados sin fallos, para que sea cuantitativamente medible.

### Objetivos Específicos
- Implementar catálogo centralizado de imágenes de contenedores con procesos automatizados.

> 🔴 **Comentario (Santiago):** "Procesos automatizados" es ambiguo. ¿Se refiere al proceso de build (CI/CD), al escaneo de seguridad (Trivy), a la firma de imágenes, o a su despliegue? Es necesario explicitar el alcance de la automatización para guiar adecuadamente el desarrollo técnico.

- Gestionar usuarios, proyectos/cursos y recursos físicos de forma eficiente.

> 🔴 **Comentario (Santiago):** La mención de "recursos físicos" entra en contradicción con la arquitectura técnica propuesta y el backlog. En ninguna parte de la arquitectura (que usa Kubernetes, Harbor, Keycloak, etc.) o en el backlog se detalla un sistema de inventario de hardware o monitoreo físico. Si no se va a implementar un control real sobre el ciclo de vida del hardware físico, este objetivo representa un "scope creep" (corrupción del alcance) y debe eliminarse.

- Garantizar trazabilidad completa del software utilizado.
- Permitir a los estudiantes descargar y ejecutar localmente las imágenes del laboratorio.
- Crear dos versiones: Académica y Empresarial (con estándares superiores).

> 🔴 **Comentario (Santiago):** ¿Qué define técnicamente a los "estándares superiores" de la versión empresarial? ¿Alta disponibilidad (HA), soporte multi-tenant real, auditorías de seguridad, o cumplimiento de normativas como ISO/IEC 27001? El término es puramente comercial y carece de valor técnico si no se definen las características funcionales y no funcionales que diferencian ambas versiones.

- Formar estudiantes bajo metodologías ágiles reales (Modelo Spotify).

> 🔴 **Comentario (Santiago):** Este es un objetivo pedagógico del proceso de desarrollo/curso, no un objetivo de la plataforma de software en sí. El software no "forma estudiantes", lo hace la metodología de trabajo del equipo. Mezclar objetivos del producto de software con objetivos del proceso educativo de los desarrolladores es conceptualmente erróneo en un documento de requerimientos técnicos de la plataforma.

---

## Justificación y Beneficios

**Beneficios Universitarios:**
- Ahorro de tiempo para estudiantes y administradores.
- Entornos idénticos y reproducibles.
- Mayor calidad de proyectos y prácticas.
- Trazabilidad académica.

> 🔴 **Comentario (Santiago):** Falta una línea base o estimación de impacto. ¿Cuánto tiempo se ahorra realmente? Por ejemplo, estimar que el tiempo de configuración del entorno por alumno se reducirá de 2 horas a 10 minutos aportaría una justificación de negocio sólida y no solo una declaración cualitativa de intenciones.

**Beneficios Empresariales:**
- Plataforma lista para entornos productivos.
- Estudiantes formados con estándares profesionales.
- Reducción de riesgos operativos.

> 🔴 **Comentario (Santiago):** ¿Por qué una empresa de software querría adoptar una "plataforma de gestión de laboratorios"? En el entorno corporativo ya existen soluciones estándar muy robustas y maduras (como entornos de desarrollo en la nube administrados, plantillas Gitpod/Codespaces, o directamente infraestructuras internas de DevOps). La justificación falla en argumentar la propuesta de valor diferencial para la industria. Además, "plataforma lista para entornos productivos" es contradictorio con un proyecto que se define como "académico-empresarial" de propuesta inicial, sin garantías de nivel de servicio (SLA) ni planes de mantenimiento a largo plazo.

---

## Enfoque Metodológico

El proyecto se desarrollará utilizando el **Modelo Spotify** adaptado al contexto universitario:

- **Tribe:** Platform Lab
- **Squads** multidisciplinarios (5-9 miembros)
- **Chapters** liderados por profesores con experiencia en industria
- **Guilds** temáticos

Se ejecutarán dos proyectos secuenciales:
1. **Proyecto Universitario** (Fase 1)
2. **Proyecto Empresa** (Fase 2)

---

## Modelo Organizacional Ágil (Spotify Adaptado)

### Squads Principales

**Proyecto 1 - Universitario**
- Squad Core Platform
- Squad Image & Container Management
- Squad Hardware & Lab Operations
- Squad Frontend & User Experience

**Proyecto 2 - Empresa** (evolución)
- Squad Core Enterprise Platform
- Squad Advanced Image & Security
- Squad Hardware Fleet & Hybrid Operations
- Squad Enterprise Experience & Analytics
- Squad Integration & Ecosystem

Los **Chapters** serán liderados por profesores con mínimo 5 años de experiencia industrial.

---

## Requisitos de Conocimientos y Habilidades

### Cuadro Comparativo (Resumen)

| Rol                          | Proyecto 1 (Nivel)     | Tiempo Mín. Práctica | Proyecto 2 (Nivel)      | Tiempo Mín. Práctica |
|-----------------------------|------------------------|----------------------|-------------------------|----------------------|
| Tech Lead / Arquitecto      | Avanzado              | 2 semestres         | Senior                 | 4 semestres         |
| Backend Developer           | Intermedio-Avanzado   | 2 semestres         | Avanzado               | 3-4 semestres       |
| DevOps / Platform Engineer  | Intermedio            | 1-2 semestres       | Senior                 | 3-4 semestres       |
| Security Engineer           | Básico-Intermedio     | 1 semestre          | Avanzado               | 2-3 semestres       |
| UX/UI Designer              | Intermedio            | 1-2 semestres       | Avanzado               | 2-3 semestres       |

**Requisitos Generales:**
- Proyecto 1: 3er-4to semestre, promedio mínimo 14, portafolio GitHub.
- Proyecto 2: Haber participado en Proyecto 1 (preferible), conocimientos avanzados en Kubernetes, GitOps y Seguridad.

---

## Arquitectura Técnica Propuesta

- **Modelo Híbrido**: On-premise (Proxmox + Kubernetes) + Nube
- **Componentes principales**:
  - GitLab (código y CI/CD)
  - Harbor (Registry de imágenes)
  - Keycloak (Identity & Access)
  - PostgreSQL + MinIO
- **Infraestructura**: Proxmox VE, Kubernetes (K3s/Talos), Ansible + Terraform

---

## Gestión de Imágenes y Trazabilidad

**Flujo Principal:**
1. Solicitud de imagen
2. Búsqueda automática en Harbor
3. Creación/Importación + Escaneo (Trivy)
4. Firma digital y aprobación
5. Publicación con metadatos
6. Descarga segura por estudiantes
7. Actualizaciones controladas

Esto garantiza **estandarización y trazabilidad completa**.

---

## Fases de Implementación

1. Análisis y Diseño (1 mes)
2. Desarrollo Proyecto Universitario (4-6 meses)
3. Evolución a Proyecto Empresa (5-7 meses)
4. Piloto y Puesta en Producción
5. Mejora Continua

---

## Conclusiones y Recomendaciones

Esta plataforma representa una oportunidad estratégica para modernizar los laboratorios de la universidad, elevar la calidad formativa y generar un activo tecnológico de alto valor transferable a la industria.

**Recomendaciones:**
- Aprobar como proyecto inter-cátedra.
- Asignar presupuesto para infraestructura base.
- Formalizar participación de profesores como Chapter Leads.

---

## Anexos

### Anexo 1: Tabla Detallada de Roles y Habilidades

*(Ver documento complementario `roles-habilidades.md`)*

### Anexo 2: Diagrama de Arquitectura (C4)

*(Se incluirán diagramas en formato PlantUML o Draw.io dentro de la carpeta `/docs/architecture`)*

### Anexo 3: Backlog Inicial de Épicas

*(Ver carpeta `/backlog`)*

### Anexo 4: Plan de Dedicación Semanal por Squad

*(Ver documento `plan-dedicacion.md`)*

### Anexo 5: Estimación de Costos Iniciales

*(Ver documento `costos.md`)*

---

## Cómo Contribuir

1. Leer el [Code of Conduct](CODE_OF_CONDUCT.md)
2. Seguir las [guías de contribución](CONTRIBUTING.md)
3. Crear issues y pull requests

---

**Licencia:** MIT  
**Estado del Proyecto:** Propuesta Inicial (En fase de aprobación)

---

*Documento preparado para repositorio GitHub. Puedes copiar todo este contenido directamente en un archivo `README.md`.*

---
> 🔴 **Comentario general (Santiago):** El documento tiene un buen propósito conceptual para guiar el inicio del proyecto, pero sufre de una preocupante vaguedad en la definición de su alcance técnico y de negocio. Al intentar abarcar tanto el mundo académico como el empresarial de manera indiferenciada, plantea objetivos contradictorios (como la gestión de recursos físicos que no está respaldada por la arquitectura) y carece de métricas claras para validar si la plataforma realmente aporta valor. Es fundamental reestructurar la introducción, delimitar qué es la plataforma híbrida, definir objetivos cuantitativos medibles (SMART) y justificar técnicamente el valor de cara a una empresa de software real.