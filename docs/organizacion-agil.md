# Modelo Organizacional Ágil - Spotify Adaptado

## Tribe Principal
**Nombre:** Platform Lab

> 🔴 **Comentario (Fredy):** No se define quién lidera el Tribe ni cómo se elige (¿un profesor coordinador, un estudiante Tech Lead, rotativo?). En el modelo Spotify real el Tribe Lead resuelve conflictos de prioridad *entre* squads — sin ese rol explícito, no queda claro quién decide si, por ejemplo, Squad Core Platform y Squad Image & Container Management compiten por el mismo recurso o bloquean una dependencia mutua.

## Squads - Proyecto Universitario (Fase 1)

- **Squad Core Platform**
- **Squad Image & Container Management**
- **Squad Hardware & Lab Operations**
- **Squad Frontend & User Experience**

> 🔴 **Comentario (Fredy):** Se listan 4 squads pero no su tamaño (el material teórico de `material-organizaciones-agiles` exige 5-9 personas por squad para ser "multidisciplinario"). Si el grupo de práctica tiene 7-8 integrantes en total, es matemáticamente imposible cubrir 4 squads con la composición mínima teórica — o el modelo se aplica a escala real de curso completo (varios grupos de práctica combinados) o hay que aclarar que aquí "squad" significa algo más pequeño de lo que dice la teoría.

> 🔴 **Comentario (Fredy):** No hay mapeo entre estos squads y las épicas del backlog (`backlog/inicial.md`). ¿Squad Hardware & Lab Operations es dueño de qué épica exactamente — "Hardware e Inventario"? Sin esa trazabilidad squad→épica, la estructura organizacional queda desconectada del trabajo real que hay que entregar.

## Squads - Proyecto Empresa (Fase 2)

- Squad Core Enterprise Platform
- Squad Advanced Image & Security
- Squad Hardware Fleet & Hybrid Operations
- Squad Enterprise Experience & Analytics
- Squad Integration & Ecosystem

> 🔴 **Comentario (Fredy):** El salto de 4 a 5 squads no explica el criterio de transición: ¿se dividen squads existentes (ej. ¿Core Platform se separa en Core Enterprise Platform + Integration & Ecosystem?), se disuelven y arman de cero, o se suma gente nueva? Sin esa regla de transformación, "evolución" es solo una palabra — no hay un mecanismo real de cómo pasa una persona de un squad de Fase 1 a uno de Fase 2.

> 🔴 **Comentario (Fredy):** Si en esta fase se habla de "estándares profesionales" y estructura tipo empresa, este documento debería aclarar aquí mismo — no en otro archivo — si los squads de Fase 2 siguen siendo estudiantes del curso o ya involucran roles externos (egresados, personal contratado). Ahora mismo el documento organizacional no distingue nada entre la naturaleza de las personas de Fase 1 y Fase 2, solo cambia nombres de squads.

## Roles de Profesores
Los **Chapters** serán liderados por profesores con experiencia en industria (mínimo 5 años).

> 🔴 **Comentario (Fredy):** No se define cómo se verifica ese requisito de "mínimo 5 años de experiencia en industria" (¿autodeclarado, CV, currícula del docente?), ni qué pasa si un Chapter no tiene ningún profesor disponible que cumpla el requisito — ¿queda ese Chapter sin líder, se baja el requisito, o se busca fuera de la plantilla docente? Tampoco se indica si esta labor de Chapter Lead se reconoce dentro de la carga académica del profesor o es trabajo adicional no remunerado, lo cual afecta directamente si el rol es sostenible en el tiempo.

**Chapters:**
- Chapter Backend & Arquitectura
- Chapter DevOps & Platform Engineering
- Chapter Security & Compliance
- Chapter Frontend & UX

> 🔴 **Comentario (Fredy):** Este es el hallazgo más importante del documento: **falta por completo el "Chapter de Organización y Procesos"** que el propio material base del curso (`material-organizaciones-agiles/Organizaciones_Agiles_Caso_Laboratorios.md`, sección 6.5) propone explícitamente como solución al dilema de dónde ubicar la gestión de procesos administrativos (reserva de equipos, aprobación de imágenes, matriz RACI). Ese material también define un rol de "Process Owner" dentro de cada squad, y ninguno de los dos aparece aquí. Si este documento es la fuente de verdad del modelo organizacional del proyecto, necesita incluir ambos — de lo contrario, precisamente el punto 2.1 que pide la consigna del curso (definición de organización y roles, con procesos como pedido de imágenes y separación de horarios) queda sin dueño formal en la estructura real.

> 🔴 **Comentario (Fredy):** El documento tampoco menciona los **Guilds**, a pesar de que son una de las cuatro unidades del Modelo Spotify descritas en el material teórico del propio curso (guild de seguridad, guild de accesibilidad, etc.). Si se omiten a propósito por ser "opcionales", debería decirlo explícitamente; si es una omisión, es una inconsistencia entre la teoría que el equipo usa como marco (Cynefin + Spotify completo) y el diseño organizacional que realmente se está proponiendo.

---
> 🔴 **Comentario general (Fredy):** El documento presenta Squads y Chapters con buen nivel de detalle nominal, pero le falta la capa de gobernanza que conecta todo: quién lidera el Tribe, cómo se transita de Fase 1 a Fase 2, y sobre todo, dónde queda la gestión de procesos y el Process Owner que el propio caso de estudio del curso ya resolvió en teoría (sección 6.5 del material base) pero que no se trasladó a este archivo. Recomiendo agregar tres bloques: (1) Tribe Lead y su rol, (2) Chapter de Organización y Procesos + Process Owner por squad, (3) Guilds (aunque sea como sección "opcional/futura"), para que este documento quede alineado con el marco teórico que el grupo está usando y con lo que pide explícitamente la consigna del trabajo (punto 2.1).