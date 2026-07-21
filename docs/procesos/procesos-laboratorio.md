# Procesos del Laboratorio - Plataforma Híbrida de Gestión

**Documento Técnico y Operativo**  
**Asignatura:** Organización y Métodos  
**Proyecto:** Plataforma Híbrida de Gestión de Laboratorios  
**Versión:** 1.0  
**Fecha:** Julio 2026

---

## 1. Introducción

Este documento define los **procesos principales** del laboratorio de computación, modelados bajo una perspectiva de **Organización y Métodos**. Se utilizan diagramas BPMN (Business Process Model and Notation) para representar claramente los flujos, roles, actividades y decisiones.

El objetivo es estandarizar el funcionamiento del laboratorio, reducir tiempos improductivos y garantizar trazabilidad.

---

## 2. Roles Principales (RACI)

| Rol                            | Responsabilidad Principal                     |
|-------------------------------|-----------------------------------------------|
| **Administrador de Laboratorio** | Gestión general y aprobación final           |
| **Responsable de Imágenes**    | Gestión del catálogo de contenedores         |
| **Docente / Product Owner**    | Solicitud y validación académica             |
| **Estudiante / Desarrollador** | Uso de recursos e imágenes                   |
| **Chapter de Organización**    | Definición y mejora continua de procesos     |

<span style="color:red">**Implementación:** Definido mediante una matriz de responsabilidades directas para asegurar que la gestión técnica y la validación académica operen de manera coordinada sin superponer funciones.</span>  
**Mejora posible:** Establecer una rotación semestral en el "Chapter de Organización" para democratizar el conocimiento de los procesos.

---

## 3. Procesos Principales (BPMN)

### 3.1 Proceso 1: Solicitud y Asignación de Recursos (Hardware)

```bpmn
Start → [Solicitud de Recursos] → ¿Recursos disponibles? 
   → Sí → [Asignación Temporal] → [Registro en Sistema] → End
   → No → [Notificación de Espera] → [Cola de Espera] → Revisar disponibilidad
