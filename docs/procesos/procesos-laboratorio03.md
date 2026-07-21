Start → [Detección de Nueva Versión (Renovate/Dependabot)]
   → [Pipeline Automático de Rebuild]
   → ¿Cambios críticos?
      → Sí → [Aprobación Manual del Responsable]
      → No → [Actualización Automática]
   → [Escaneo de Seguridad] → [Publicación] → [Notificación a Usuarios] → End

**Implementación:** <span style="color:red">Configurado apoyado en flujos CI/CD (Renovate/Dependabot) para delegar la carga operativa a pipelines automáticos, reservando la intervención humana exclusivamente para actualizaciones críticas o "breaking changes".</span>  
**Mejora posible:** Añadir tests automatizados de salud de la imagen (*smoke tests*) tras el rebuild para detectar fallos antes del escaneo de seguridad.
