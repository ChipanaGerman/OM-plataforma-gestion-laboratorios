# Procesos y Organización del Laboratorio

**Documento Integral de Organización y Métodos**  
**Proyecto:** Plataforma Híbrida de Gestión de Laboratorios  
**Asignatura:** Organización y Métodos  
**Versión:** 1.0  
**Fecha:** Julio 2026

---

## 1. Introducción

Este documento presenta la **organización completa** y los **procesos clave** del laboratorio de computación. Su propósito es estandarizar el funcionamiento, reducir tiempos improductivos, garantizar trazabilidad y servir como referencia para la asignatura de **Organización y Métodos**.

Se incluyen descripciones detalladas, diagramas BPMN textuales, matriz RACI, indicadores y propuestas de mejora.

---

## 2. Estructura Organizacional Mínima

### Roles Principales

- **Administrador de Laboratorio**: Responsable general de la operación física y digital.
- **Responsable de Imágenes**: Gestor del catálogo de contenedores (Docker).
- **Chapter de Organización y Procesos**: Profesor líder (encargado de definir, documentar y mejorar procesos).
- **Docente / Product Owner**: Solicita y valida recursos por curso/proyecto.
- **Estudiante / Desarrollador**: Usuario final.
- **Chapter Leads Técnicos**: Profesores por especialidad (DevOps, Seguridad, etc.).

### Propuesta de Organización

Se recomienda un **Chapter de Organización y Procesos** (transversal) en lugar de un squad completo. Este Chapter trabajará junto con un **Rol de "Process Owner"** dentro de cada Squad técnico.

**Justificación**: Permite mantener los squads enfocados en desarrollo mientras se garantiza que los procesos sean prácticos y bien documentados.

> `feat(org): definir estructura de roles y Chapter de Procesos`
> * **Implementación:** <span style="color:red">Implementado mediante un modelo híbrido (Chapter transversal y Squads técnicos) para asegurar que los desarrolladores mantengan el foco técnico sin descuidar la gobernanza y documentación de procesos.</span>
> * **Mejora posible:** Evaluar la rotación semestral del rol "Process Owner" dentro de los squads para democratizar el conocimiento.

---

## 3. Procesos Principales (con Descripción Detallada)

### 3.1 Proceso: Solicitud y Asignación de Recursos de Hardware

**Objetivo:** Gestionar de forma eficiente las computadoras, servidores e impresoras.

**Flujo BPMN (Textual):**

Start → Solicitud por Portal → Verificación Automática de Disponibilidad 
→ ¿Disponible? 
   → Sí → Aprobación Automática / Manual → Asignación + Notificación → Check-in (QR) → Uso → Check-out → Liberación → End
   → No → Notificación de Espera → Cola de Prioridad → Revisión Manual



**Descripción Detallada:**
1. El usuario inicia sesión y selecciona el recurso.
2. El sistema verifica disponibilidad en tiempo real.
3. Se registra el préstamo con fecha/hora de devolución.
4. Al llegar al laboratorio se realiza Check-in.

> `feat(hardware): integrar flujo de solicitud y check-in QR`
> * **Implementación:** <span style="color:red">Automatizado mediante validación de disponibilidad en tiempo real y validación por código QR para reducir la fricción del usuario, evitar reservas fantasma y controlar el inventario físico.</span>
> * **Mejora posible:** Implementar penalizaciones automáticas o liberación temprana por *no-show* (ausencia tras 15 minutos).

---

### 3.2 Proceso: Gestión del Catálogo de Imágenes de Contenedores (Core)

**Objetivo:** Proporcionar entornos estandarizados y trazables.

**Flujo BPMN (Textual):**

Start → Solicitud de Imagen (Estudiante/Docente)
→ Búsqueda Automática en Harbor
→ ¿Imagen Disponible y Actualizada?
   → Sí → Entrega de Enlace de Descarga → Uso Local / Laboratorio → End
   → No → Notificación al Responsable de Imágenes
      → Análisis (Oficial vs Crear)
      → Descarga / Creación de Imagen
      → Escaneo de Vulnerabilidades
      → Firma Digital
      → Aprobación
      → Publicación en Harbor
      → Notificación a Solicitante



**Descripción Detallada:**
- Toda imagen debe estar **escaneada y firmada**.
- Los estudiantes pueden descargar la imagen oficial y ejecutarla en su computadora personal con Docker o Podman.
- Se mantiene un historial completo de versiones.

> `feat(images): implementar catálogo seguro en Harbor`
> * **Implementación:** <span style="color:red">Centralizado utilizando Harbor como registro, integrando escaneo de vulnerabilidades y firmas digitales de manera obligatoria para garantizar un entorno de desarrollo seguro, estandarizado y libre de malware.</span>
> * **Mejora posible:** Añadir un sistema de *Garbage Collection* automático para purgar imágenes no utilizadas en los últimos 6 meses.

---

### 3.3 Proceso: Actualización y Mantenimiento de Imágenes

**Flujo BPMN:**

Start → Detección Automática de Nueva Versión
→ Pipeline de Rebuild
→ Escaneo de Seguridad
→ ¿Requiere Aprobación Manual?
   → Sí → Revisión por Responsable → Aprobación/Rechazo
   → No → Actualización Automática
→ Publicación → Notificación a Usuarios Activos → End

---

> `feat(ci-cd): automatizar pipeline de rebuild de imágenes`
> * **Implementación:** <span style="color:red">Configurado a través de un flujo CI/CD que detecta nuevas versiones y lanza un rebuild automático, minimizando la intervención manual y priorizando la entrega continua de entornos actualizados.</span>
> * **Mejora posible:** Incorporar un mecanismo de *rollback* automático si la nueva imagen presenta fallas críticas en los tests de salud.

### 3.4 Proceso: Reserva y Uso de Laboratorio

**Flujo BPMN:**

Start → Login → Seleccionar Horario y Equipo
→ Validación de Disponibilidad
→ Reserva Confirmada → Recordatorio 15 min antes
→ Check-in en Laboratorio → Uso → Check-out → Liberación Automática

> `feat(booking): añadir módulo de reservas y liberación de equipos`
> * **Implementación:** <span style="color:red">Desarrollado como un sistema de auto-reserva con liberación automática tras el check-out, diseñado para maximizar la tasa de ocupación y evitar tiempos muertos de las computadoras.</span>
> * **Mejora posible:** Integrar notificaciones push multiplataforma (ej. Telegram o WhatsApp) para los recordatorios de reserva.

---

## 4. Matriz RACI General

| Actividad / Proceso                    | Administrador Lab | Responsable Imágenes | Docente | Estudiante | Chapter Organización |
|---------------------------------------|-------------------|----------------------|---------|----------|----------------------|
| Solicitud de Recursos Hardware        | A                 | I                    | C       | R        | C                    |
| Solicitud y Aprobación de Imágenes    | A                 | R                    | C       | R        | C                    |
| Creación de Nueva Imagen              | C                 | R/A                  | C       | I        | C                    |
| Reserva de Equipos                    | A                 | I                    | C       | R        | I                    |
| Actualización de Imágenes             | I                 | R                    | C       | I        | C                    |
| Definición y Mejora de Procesos       | C                 | C                    | C       | I        | R/A                  |

---

## 5. Indicadores de Desempeño (KPIs)

- Tiempo promedio de aprobación de nueva imagen: **≤ 48 horas**
- Porcentaje de solicitudes resueltas automáticamente: **≥ 70%**
- Tiempo promedio de configuración de entorno por estudiante: **≤ 15 minutos**
- Tasa de utilización de imágenes oficiales: **≥ 75%**
- Nivel de satisfacción de usuarios (Encuesta): **≥ 85%**
- Tiempo promedio de reserva de equipo: **≤ 5 minutos**

> Gobernanza y KPIs:** `docs(gobernanza): establecer Matriz RACI y métricas de desempeño`
> * **Implementación:** <span style="color:red">Definidos e integrados estáticamente en la documentación para delimitar responsabilidades exactas por actor y establecer una línea base que permita auditar los SLAs del laboratorio.</span>
> * **Mejora posible:** Migrar la recolección de KPIs a un *dashboard* interactivo (ej. Grafana) conectado directamente a los logs del sistema.

---

## 6. Mejora Continua y Recomendaciones

- Realizar **revisiones mensuales** de procesos con el Chapter de Organización.
- Utilizar herramientas como **Draw.io, Bizagi o Camunda** para mantener diagramas BPMN actualizados.
- Implementar **automatización progresiva** de decisiones mediante reglas de negocio.
- Crear un **manual de usuario** y **guías rápidas** para estudiantes.
- Establecer un **comité de procesos** (Administrador + Chapter Leads + Estudiantes representantes).

**Próximos Pasos:**
1. Modelar todos los diagramas BPMN en herramienta gráfica.
2. Validación del documento con docentes y administradores.
3. Integración de flujos automatizados en la plataforma.

---

**Este documento integra toda la parte de Organización y Procesos del Laboratorio.**  
Está diseñado para ser entregado como **trabajo de curso de Organización y Métodos**.

---

¿Deseas que agregue más procesos (ej. Gestión de Incidentes, Onboarding de Nuevos Usuarios, Cierre de Semestre, etc.) o que prepare una versión con PlantUML para generar diagramas reales?

---
### Resumen General de Trazabilidad y Mejoras

La arquitectura de procesos documentada establece una base sólida y escalable para la gestión del laboratorio. **Las implementaciones** destacan por su enfoque en la seguridad (escaneo de imágenes) y la automatización (validaciones en tiempo real). **La cuestión principal** a vigilar es el balance entre las aprobaciones manuales (cuellos de botella potenciales) y los procesos automatizados, especialmente en la creación de nuevas imágenes. **Las mejoras propuestas** apuntan hacia una mayor autonomía del sistema: integrando telemetría en tiempo real (dashboards), políticas de limpieza de recursos (*garbage collection*) y alertas proactivas (ausencias y notificaciones móviles), cerrando así el ciclo para un laboratorio 100% eficiente y autogestionado.
