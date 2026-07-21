# Plataforma Híbrida de Gestión de Laboratorios de Computación

**Proyecto Académico-Empresarial**  
**Carrera de Sistemas / Ingeniería de Software**  
**Universidad [Nombre]**  
**Versión:** 1.0  
**Fecha:** Julio 2026

## Tabla de Contenidos

- [Introducción](README.md#introducción)
- [Problemática Común](#problemática-común)
- [Objetivos](#objetivos)
- [Justificación y Beneficios](#justificación-y-beneficios)
- [Modelo Organizacional](#modelo-organizacional-ágil-spotify-adaptado)
- [Arquitectura](#arquitectura-técnica-propuesta)
- [Fases del Proyecto](#fases-de-implementación)

---

## Introducción

Este proyecto busca desarrollar una **plataforma híbrida** (local + nube) para la gestión integral de laboratorios de computación, aplicable en universidades y empresas de software.

---

## Problemática Común

- Pérdida de tiempo en instalaciones manuales por parte de estudiantes y administradores.
- Entornos no estandarizados entre computadoras.
- Falta de trazabilidad del software utilizado.
- Dificultad para replicar el entorno del laboratorio en las computadoras personales de los alumnos.
- Gestión ineficiente de hardware y recursos.

> 🔴 **Comentario (Santiago):** En esta versión simplificada es aún más notoria la falta de separación entre la problemática del entorno educativo y el de la empresa. Además, se añade la "Gestión ineficiente de hardware y recursos", lo cual es un problema sumamente físico (inventarios, componentes rotos, asignación de laboratorios físicos), y la plataforma que estamos diseñando no aborda en absoluto esta complejidad en sus especificaciones técnicas reales.

---

## Objetivos

**General:** Desarrollar una plataforma que estandarice, automatice y trace los entornos de desarrollo en laboratorios.

**Específicos:**
- Gestión centralizada de hardware y usuarios.
- Catálogo de imágenes de contenedores (Docker) con procesos automáticos.
- Trazabilidad completa del software.
- Posibilidad de que los alumnos descarguen y usen las mismas imágenes en sus PCs.
- Dos versiones: Académica y Empresarial (con estándares más altos).

> 🔴 **Comentario (Santiago):** La "Gestión centralizada de hardware" sigue figurando como objetivo específico prioritario. Dado que la arquitectura técnica del proyecto se limita exclusivamente al plano del software (Kubernetes, GitLab, Harbor, Keycloak, etc.), incluir la gestión de hardware físico como objetivo es inconsistente con el diseño del sistema. Por otro lado, "Dos versiones: Académica y Empresarial" sigue presentándose de forma superficial sin establecer qué diferencia real existe entre ambos niveles de servicio o seguridad.

---

## Justificación y Beneficios

- **Universidad:** Ahorro de tiempo para estudiantes y administradores. Entornos reproducibles.
- **Industria:** Formación con estándares profesionales reales.
- **Trazabilidad:** Registro auditable de todas las imágenes y herramientas utilizadas.

> 🔴 **Comentario (Santiago):** Presentar los beneficios de forma tan esquemática e imprecisa debilita la justificación del proyecto. Por ejemplo, indicar simplemente "Ahorro de tiempo" o "Estándares profesionales reales" sin métricas o un caso de estudio inicial no permite defender la inversión de tiempo y recursos ante las autoridades académicas o la gerencia empresarial.

---

## Modelo Organizacional Ágil (Spotify Adaptado)

Ver detalle completo en: [`docs/organizacion-agil.md`](docs/organizacion-agil.md)

## Arquitectura Técnica Propuesta

Ver detalle completo en: [`docs/arquitectura.md`](docs/arquitectura.md)

## Gestión de Imágenes y Trazabilidad

Ver detalle completo en: [`docs/gestion-imagenes.md`](docs/gestion-imagenes.md)

## Fases de Implementación

Ver detalle completo en: [`docs/fases-implementacion.md`](docs/fases-implementacion.md)

## Anexos

- [Requisitos de Roles y Habilidades](docs/roles-habilidades.md)
- [Cuadro Comparativo de Conocimientos](docs/roles-habilidades.md#cuadro-comparativo)
- [Plan de Dedicación](docs/plan-dedicacion.md)

---

**Estado:** Propuesta Inicial  
**Licencia:** MIT

---
> 🔴 **Comentario general (Santiago):** Es de vital importancia cuestionar la existencia simultánea de dos archivos README en la raíz (`README.md` y `README2.MD`). Esto rompe directamente el principio fundamental DRY (Don't Repeat Yourself). Mantener dos copias que intentan describir lo mismo en dos niveles de detalle diferentes en la raíz del proyecto es ineficiente y conducirá inevitablemente a desincronizaciones de alcance y a malentendidos en el equipo. Se propone eliminar `README2.MD` por completo y consolidar una versión única y robusta en `README.md`, enlazando a la carpeta `/docs/` para detalles complementarios.