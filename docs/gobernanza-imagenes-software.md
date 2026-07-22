# UNIVERSIDAD NACIONAL DE SAN AGUSTÍN DE AREQUIPA
## Escuela Profesional de Ingeniería de Sistemas

### GOBERNANZA DE IMÁGENES Y GESTIÓN DE SOFTWARE

**Proyecto:** Plataforma de Gestión de Laboratorios

**Curso:** Organización y Métodos

**Docente:** Ing. Juan Juárez Bueno

**Integrantes:**
- Baca Calsin Leonardo Juan José
- Chipana Jeronimo German Arturo
- Palma Apaza Santiago Enrique
- Mejia Rondan Giovanni Patrick
- Ponce Llerena Renato Xavier
- Auccacusi Conde Brayan Carlos
- Aragon Carpio Fredy Jose

**Fecha:** Julio 2026

---

## Índice

1. [Introducción](#1-introducción)
2. [Objetivos](#2-objetivos)
3. [Gobernanza de Imágenes Docker](#3-gobernanza-de-imágenes-docker)
4. [Gestión de Software](#4-gestión-de-software)
5. [Gestión de Licencias](#5-gestión-de-licencias)
6. [Trazabilidad](#6-trazabilidad)
7. [Auditoría](#7-auditoría)
8. [Seguridad y Control de Cambios](#8-seguridad-y-control-de-cambios)
9. [Riesgos Identificados](#9-riesgos-identificados)
10. [Recomendaciones](#10-recomendaciones)
11. [Conclusiones](#11-conclusiones)

---

## 1. Introducción

En un entorno académico de Ingeniería de Sistemas, la proliferación descontrolada de software, herramientas y dependencias representa un riesgo para la estabilidad de los laboratorios y el cumplimiento legal. Este documento establece las directrices fundamentales para la gobernanza del catálogo de software de la "Plataforma de Gestión de Laboratorios". El presente entregable se alinea con la consigna del curso de Organización y Métodos (Punto 2.2), enfocado en la gobernanza de licencias y trazabilidad operativa.

La gobernanza garantiza que cada imagen de contenedor, programa y librería empleada por estudiantes y docentes atraviese un proceso regulado de validación, garantizando un entorno educativo seguro, reproducible y libre de conflictos legales (licenciamiento).

## 2. Objetivos

### 2.1 Objetivo General
Definir las políticas de gobernanza técnica orientadas al ciclo de vida del software, la gestión de imágenes virtuales y la trazabilidad de operaciones dentro de la plataforma de laboratorios de la universidad.

### 2.2 Objetivos Específicos
- Establecer reglas claras para la creación, aprobación y retiro de imágenes de contenedores.
- Formular directrices para la revisión de licencias de software, distinguiendo el uso puramente académico.
- Definir lineamientos de auditoría y trazabilidad que permitan conocer el origen y estado de cualquier recurso de software desplegado.
- Proponer buenas prácticas y herramientas futuras orientadas a incrementar la seguridad de la plataforma.

## 3. Gobernanza de Imágenes Docker

La plataforma utilizará un catálogo privado para el almacenamiento y distribución de entornos basados en contenedores (imágenes Docker). Su administración obedecerá a las siguientes reglas:

### 3.1 Políticas de aprobación y publicación
- Ninguna imagen podrá ser considerada "oficial" ni será expuesta a los estudiantes sin una validación previa del docente o del *Chapter* correspondiente.
- Se establecerá una clara separación entre entornos "experimentales" (espacios de prueba limitados) e "imágenes aprobadas" para dictado de cursos.

### 3.2 Versionado semántico estricto
Todas las imágenes deberán estar obligatoriamente etiquetadas utilizando reglas de versionado semántico estándar (ej. `curso-bases-datos/v1.0.2`), descartando por completo el uso exclusivo de la etiqueta `latest`. Esto asegura que los estudiantes de un semestre específico mantengan entornos idénticos de principio a fin, sin sufrir cambios abruptos a mitad de ciclo.

### 3.3 Políticas de retención y obsolescencia (Garbage Collection)
El espacio de almacenamiento universitario es finito. Se instituirá una política de retención donde las imágenes no utilizadas en los últimos dos semestres académicos (1 año) serán marcadas como "deprecadas" y posteriormente purgadas del registro principal.

## 4. Gestión de Software

### 4.1 Criterios de inclusión de software base
Cualquier dependencia o utilidad adicional que se desee incorporar a una imagen oficial deberá justificar su necesidad académica. Se dará estricta prioridad a herramientas de código abierto (Open Source) y lenguajes estándar de la currícula universitaria.

### 4.2 Diferenciación entre Entorno Académico y Empresarial
Para fines de este proyecto universitario, se permite la inclusión de software con licencias exclusivas para educación (ej. versiones de comunidad o licencias de estudiante). Sin embargo, el diseño del catálogo advertirá explícitamente cuáles imágenes están restringidas, a fin de evitar que, en un escenario de transferencia tecnológica hacia la industria, se infrinjan términos de uso.

## 5. Gestión de Licencias

Uno de los mayores riesgos ocultos en la construcción de entornos digitales es la mezcla de licenciamientos incompatibles.

### 5.1 Auditoría de licencias en imágenes base
Es imperativo clasificar el software según su licencia dominante:
- **Licencias Permisivas (MIT, BSD, Apache):** Fomento máximo para su uso en la plataforma.
- **Licencias Virales (GPLv2, GPLv3):** Su uso es aceptado en la academia, pero se documentará su presencia debido a que obligan a compartir modificaciones.
- **Software Propietario / Comercial:** Prohibida su inclusión por defecto en imágenes base públicas del catálogo, a menos que exista un convenio expreso de la universidad que cubra su uso por parte de los estudiantes.

### 5.2 Control de dependencias (Recomendación futura)
Como buena práctica, se proyecta la generación futura de Listas de Materiales de Software (SBOM, por sus siglas en inglés) para cada imagen, lo cual permitiría a la universidad tener un inventario claro de todas las bibliotecas internas y prevenir el uso de componentes no autorizados.

## 6. Trazabilidad

### 6.1 Ciclo de vida auditable del software
Toda imagen en el catálogo deberá contar con metadata que responda a:
- **¿Quién** solicitó la imagen? (El docente/curso).
- **¿Quién** construyó y aprobó la imagen?
- **¿Qué** versión de sistema operativo base utiliza?
- **¿Cuándo** fue actualizada por última vez?

### 6.2 KPIs y métricas de desempeño
El rendimiento operativo de la gobernanza se evaluará semestralmente a través de:
- Porcentaje de imágenes que cumplen con el etiquetado semántico (Meta: 100%).
- Tiempo promedio desde la solicitud de una imagen hasta su disponibilidad en el catálogo.

## 7. Auditoría

### 7.1 Revisiones de cumplimiento
El *Chapter de Organización y Procesos* liderará una revisión semestral para certificar que las imágenes presentes en el catálogo no incluyen software obsoleto, inseguro o sin uso activo en la currícula académica.

### 7.2 Reportes de uso y descargas
Se deberá monitorear la tasa de descarga y uso de cada entorno. Esto permitirá a la administración concentrar recursos de mantenimiento únicamente en las plataformas tecnológicas de mayor demanda por parte del estudiantado.

## 8. Seguridad y Control de Cambios

Si bien la implementación de herramientas avanzadas se realizará de forma progresiva, la plataforma asume las siguientes directrices fundacionales:

### 8.1 Evaluaciones de seguridad y firmas
Se establece la meta a mediano plazo de incorporar sistemas de escaneo automatizado (por ejemplo, herramientas de análisis de vulnerabilidades como Trivy) antes de la publicación final de las imágenes, así como mecanismos de firma digital para garantizar a los estudiantes que el entorno que descargan no ha sido modificado maliciosamente.

### 8.2 Autenticación y acceso seguro
El acceso a descargas y recursos del laboratorio deberá transaccionar bajo estándares seguros. Se recomienda, para etapas posteriores del proyecto, la integración de protocolos de cifrado en tránsito (HTTPS/TLS) y sistemas de control de identidad robustos (tipo Keycloak) que validen el rol (docente/estudiante) del usuario.

## 9. Riesgos Identificados

| Nivel de Riesgo | Riesgo Identificado | Impacto Potencial | Medida de Mitigación (Política) |
| :---: | :--- | :--- | :--- |
| **Alto** | Inclusión involuntaria de software con licencias restrictivas. | Problemas legales o bloqueos en caso de transferencia empresarial. | Revisión manual de licencias base; priorizar uso exclusivo de Open Source. |
| **Medio** | Acumulación de imágenes "huérfanas" no mantenidas. | Saturación del espacio de almacenamiento del servidor. | Aplicación rigurosa de la política de retención (eliminación anual). |
| **Medio** | Desincronización de versiones en un mismo curso. | Estudiantes evaluados bajo diferentes condiciones técnicas. | Uso obligatorio de versionado semántico; prohibición de `latest` en aulas. |

## 10. Recomendaciones

1. **Adopción de Buenas Prácticas de Industria:** Promover entre los estudiantes que desarrollen imágenes el conocimiento básico sobre licencias de software, elevando el valor formativo del proyecto.
2. **Implementación de Herramientas de Seguridad:** Reservar tiempo técnico durante la *Fase Empresa* del proyecto para investigar e incorporar paulatinamente análisis automatizados (SBOM, Trivy) sin sobrecargar al equipo durante la fase universitaria inicial.
3. **Mantenimiento Preventivo:** Programar "ventanas de limpieza" del catálogo al finalizar cada ciclo lectivo, lideradas por el *Tribe Lead* y los *Process Owners*.

## 11. Conclusiones

- La gobernanza de software es indispensable no solo como requerimiento técnico, sino como salvaguarda institucional. Normar cómo se construyen y versionan las imágenes previene el desorden y estandariza la calidad educativa.
- Las normativas de licencias y trazabilidad planteadas se ajustan de manera realista al contexto académico actual, reconociendo restricciones de tiempo y recursos, pero sentando las bases (mediante recomendaciones) para escalar la plataforma a los más altos estándares empresariales en el futuro.
- El éxito de esta plataforma depende de que tanto docentes como alumnos respeten los ciclos de auditoría y aprobación establecidos, convirtiendo a la plataforma en una herramienta predecible, auditable y segura.
