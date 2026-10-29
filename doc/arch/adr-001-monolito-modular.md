# ADR-001: Monolito modular en lugar de microservicios

## Estado
Aceptada, 29 de octubre de 2026.

## Contexto
RoomFix es un sistema para gestionar reportes y reparaciones de mantenimiento en un hotel boutique de 12 habitaciones. Lo utilizan recepción, limpieza, mantenimiento y gerencia.

El proyecto es desarrollado por dos estudiantes y sus requisitos pueden cambiar durante el desarrollo. Se necesita una arquitectura sencilla de implementar, mantener y organizar.

Se consideraron tres alternativas: monolito tradicional, monolito modular y microservicios.

## Decisión
Elegimos un monolito modular, con una sola aplicación desplegable y funciones organizadas en cuatro módulos: Habitaciones, Gestión de reportes, Mantenimiento y Seguimiento.

Cada módulo tendrá responsabilidades definidas y se comunicará con los demás mediante interfaces claras.

## Consecuencias
Esta arquitectura facilita el desarrollo, las pruebas y el mantenimiento, sin necesidad de administrar varios servicios independientes.

Como desventaja, los módulos no podrán desplegarse ni escalarse por separado. También existe el riesgo de mezclar responsabilidades si no se respetan sus límites.

Si RoomFix crece o comienza a utilizarse en varios hoteles, tendremos que revisar si esta arquitectura sigue siendo adecuada.
