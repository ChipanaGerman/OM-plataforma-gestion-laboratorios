Start → [Solicitud de Imagen] → [Búsqueda Automática en Harbor]
   → ¿Existe y está actualizada?
      → Sí → [Entrega de Imagen] → [Descarga Local] → End
      → No → [Notificación al Responsable de Imágenes]
         → [Búsqueda Imagen Oficial] → ¿Existe oficial?
            → Sí → [Importar + Escanear] → [Aprobación] → [Publicar]
            → No → [Crear Imagen Personalizada] → [Escaneo Seguridad] → [Aprobación] → [Publicar]

---
* **Implementación:** <span style="color:red">Centralizado utilizando Harbor como único registro confiable, imponiendo un paso estricto de escaneo de seguridad antes de cualquier publicación para garantizar un entorno libre de vulnerabilidades.</span>  
* **Mejora posible:** Integrar alertas directas (ej. Slack/Teams) para notificar instantáneamente al responsable cuando se requiere la creación manual de una imagen.
