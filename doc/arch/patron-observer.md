# Patrón de diseño propuesto — Observer en RoomFix

## Estado
**Propuesta de diseño, no implementación existente.** Este documento describe dónde podría utilizarse Observer en el monolito modular de RoomFix.

## Problema
Cuando mantenimiento cambia el estado de una falla, la información debe quedar disponible para las consultas de recepción, limpieza y gerencia. Además, **RNF-CON-002** exige conservar el 100 % de los cambios de estado asociados a la falla.

## Propuesta
Aplicar **Observer** a los eventos de cambio de estado de una falla:

1. **Sujeto observado:** una falla, o el servicio del módulo **Seguimiento** que administra sus cambios de estado.
2. **Evento:** cambio de estado de una falla (por ejemplo, de *Pendiente* a *En atención*).
3. **Observadores propuestos:** un registrador de historial que crea **CambioEstado** y un actualizador de vistas o consultas de seguimiento.
4. **Mantenimiento** solicita el cambio; **Seguimiento** lo valida, registra y comunica a los observadores.
5. **Recepción, limpieza y gerencia** consultan el estado actualizado desde la aplicación web.

**Aclaración:** Observer no significa por sí solo actualizaciones en tiempo real del navegador. Para notificaciones instantáneas haría falta definir además un mecanismo de comunicación con la interfaz. La arquitectura actual no especifica ese mecanismo.

## Relación con el diseño existente
- **C4 — Componentes:** Mantenimiento -> Seguimiento; Seguimiento -> Gestión de reportes.
- **UML — Clases:** Falla.cambiarEstado(...) y CambioEstado.registrarCambio(...).
- **UML — Estados:** Pendiente -> En atención -> Terminada, con cierre condicionado a reparación completada.
- **RNF-CON-002:** todo cambio debe quedar asociado a su reporte y disponible para consulta.

## Por qué este patrón
Separa la operación que cambia el estado de las acciones que reaccionan a ese cambio, como guardar la trazabilidad o actualizar una vista. Facilita agregar nuevos observadores sin concentrar toda la lógica en una sola operación.

## Costo y límite
Introduce interfaces y coordinación entre observadores, por lo que puede ser innecesario en una versión inicial muy pequeña. Debe evitarse que un error de un observador haga perder el registro obligatorio de trazabilidad.

## Próximo paso
Si se decide implementar el patrón, actualizar los diagramas C4/UML con las interfaces y operaciones concretas y agregar pruebas de propagación y registro de cambios. Hasta entonces, se presenta únicamente como una **propuesta arquitectónica**.
