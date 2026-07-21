# Gestión de Imágenes y Trazabilidad

## Flujo Principal

1. Solicitud de imagen (Proyecto o Curso)

> 🔴 **Comentario (Brayan):** No se define quién puede solicitar una imagen ni por qué canal (¿formulario, ticket, comando?). Sin esto no queda claro quién es responsable si una solicitud está mal hecha o incompleta.

2. Búsqueda automática en Harbor

> 🔴 **Comentario (Brayan):** ¿"Automática" es un match exacto por nombre/tag, o hay algún criterio de similitud? Si dos imágenes tienen nombres parecidos pero configuraciones distintas, se podría aprobar por error una imagen que no es la que realmente se necesita.

3. Si no existe → Responsable revisa y aprueba creación

> 🔴 **Comentario (Brayan):** No se dice quién es "el Responsable" ni cuánto debería tardar esta aprobación. Si un alumno necesita la imagen para un laboratorio de esa semana y la aprobación se demora días, todo el flujo se cae en la práctica aunque en el papel se vea bien.

4. Escaneo de vulnerabilidades (Trivy)

> 🔴 **Comentario (Brayan):** No especifica qué pasa si el escaneo encuentra vulnerabilidades. ¿Se rechaza automático, se notifica, hay un umbral tolerado (crítico/alto/medio)? Sin esa regla, "escanear" es un paso decorativo que no lleva a ninguna acción concreta.

5. Firma de imagen

> 🔴 **Comentario (Brayan):** No dice quién firma ni cómo se protege esa llave/credencial. Si es una sola persona la que firma todas las imágenes de todos los cursos, se vuelve un cuello de botella que ni siquiera está contemplado como carga de trabajo de nadie.

6. Publicación con metadatos de trazabilidad

> 🔴 **Comentario (Brayan):** No detalla qué metadatos se guardan exactamente (¿autor, fecha, curso, resultado del escaneo?). Se habla de "trazabilidad" pero no se especifica el esquema de datos ni dónde queda almacenado ese registro.

7. Estudiantes pueden descargar la imagen oficial

> 🔴 **Comentario (Brayan):** No se dice cómo se controla quién puede descargar (¿todos los estudiantes, solo los matriculados en el curso?) ni qué pasa si muchos alumnos descargan la misma imagen pesada al mismo tiempo, por ejemplo la semana antes de un examen.

---

> 🔴 **Comentario general (Brayan):** El flujo no contempla manejo de errores ni rechazos: ¿qué pasa si el escaneo falla o si el Responsable no aprueba la solicitud? Tampoco hay paso de actualización de versiones de una imagen ya publicada, ni qué pasa si dos cursos piden imágenes parecidas pero con configuraciones distintas (¿se versiona, se clona, se pide justificación?).

> 🔴 **Comentario general (Brayan):** Sobre el "Beneficio clave" (mismo entorno dentro y fuera del laboratorio): esto asume que todo estudiante tiene el hardware necesario en su propia PC para correr la imagen (memoria, CPU, Docker instalado). No se menciona ningún requisito mínimo ni qué alternativa hay para quien no cuenta con una laptop capaz de sostener ese entorno.