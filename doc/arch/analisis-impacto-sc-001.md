# Análisis de impacto — SC-001: Fotografías antes y después de la reparación

## Estado y origen
**Solicitud recibida de la dupla.** Se propone que recepción o limpieza adjunten una fotografía al registrar la falla y que mantenimiento adjunte otra al finalizar la reparación. Ambas deben poder consultarse en el detalle de la falla y en el historial de la habitación.

**Estado:** cambio propuesto, no implementado.

## Requisitos y casos de uso afectados
- **RF-001 / CU-01 — Registrar falla:** permitir adjuntar una fotografía inicial y asociarla a la falla.
- **RF-006 / CU-05 — Finalizar reparación:** permitir adjuntar una fotografía final al cierre de la reparación.
- **RF-008 / CU-07 — Consultar historial:** mostrar las imágenes asociadas a la falla y su reparación.
- **RNF-CON-001 — Integridad:** asegurar que las fotografías se asocien al reporte correcto.
- **RNF-CON-002 — Trazabilidad:** conservar la relación entre la falla, su estado y las evidencias.

Las fotografías son una ampliación propuesta; no se consideran requisitos ya implementados.

## Impacto en la arquitectura y el diseño
| Artefacto o pieza | Cambio necesario |
| --- | --- |
| C4 — Contenedores | Explicar dónde se almacenarán las imágenes y cómo la aplicación y API las cargarán y consultarán. La tecnología de almacenamiento aún no está definida. |
| C4 — Componentes | **Gestión de reportes:** fotografía inicial; **Mantenimiento:** fotografía final; **Seguimiento:** acceso a evidencias e historial. |
| UML — Clases | Ampliar **Falla** y/o **Reparacion** con referencias a fotografías, o introducir una entidad **EvidenciaFotografica** si se decide admitir varias imágenes. La decisión exacta queda pendiente de diseño. |
| UML — Secuencia | Extender CU-01 para validar y asociar una fotografía inicial; representar la carga final en CU-05. |
| UML — Estados | Mantener el cierre condicionado a que la reparación esté realmente terminada; definir si la foto final será obligatoria antes de permitirlo. |
| Prototipo | Agregar controles para adjuntar y consultar fotografías, con mensajes de error claros. |
| Datos y permisos | Definir formatos, tamaño máximo, almacenamiento, acceso según perfil y manejo de fallas de carga. |

## Estimación de esfuerzo
**Total estimado: 18 horas**, bajo el supuesto de un desarrollador familiarizado con RoomFix y disponibilidad de un mecanismo de almacenamiento de archivos.

| Actividad | Horas | Justificación |
| --- | ---: | --- |
| Diseño y documentación | 4 | Actualizar requisitos, flujos, modelo de datos y diagramas afectados. |
| Desarrollo | 10 | Adaptar formularios, carga y almacenamiento, vinculación de imágenes con fallas y consulta en detalle/historial. |
| Pruebas | 4 | Probar carga, consulta, asociación correcta, errores de archivo y permisos por rol. |
| **Total** | **18** | Estimación inicial; puede variar según almacenamiento, límites de archivos y validaciones definitivas. |

## Decisión
**Aceptar el cambio como propuesta para una siguiente iteración.** Aporta evidencia visual y facilita la verificación de reparaciones. Es compatible con el monolito modular, aunque requiere modificar interfaz, lógica de negocio y persistencia. No se afirma que esté implementado.

## Pendientes de definición
- ¿La fotografía inicial y la final serán obligatorias u opcionales?
- ¿Qué formatos, tamaños y cantidades se permitirán?
- ¿Quién podrá ver, sustituir o eliminar evidencias?
- ¿Se usará almacenamiento de archivos, objetos u otra alternativa?
