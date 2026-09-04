# Visión del producto

> **Plantilla del curso · Ingeniería de Software I · SIS3407**
> Este documento es el primer entregable del semestre y la base de todo lo que viene después.
> Se entrega completo en la **semana 4** y se presenta ante el grupo.

---

**Autor:** Sebastián Mayorga Galicia
**Fecha de la última versión:** 1 de septiembre de 2026
**Repositorio:**

---

## 1. Descripción del sistema

**Nombre del sistema:** RoomFix

**Descripción:**
RoomFix es un sistema para reportar y dar seguimiento a fallas de mantenimiento en las habitaciones de un hotel. Ayuda a identificar qué problemas necesitan atención primero para evitar afectar a los huéspedes o dejar habitaciones fuera de servicio.

---

## 2. Problema y usuarios

**El problema:**
En un hotel pueden surgir fallas constantemente: aire acondicionado, agua caliente, cerraduras, iluminación, televisión, fugas, entre otras. Cuando no existe un buen control, una falla puede tardar en atenderse, afectar a un huésped o impedir que una habitación pueda utilizarse.

**Cómo se resuelve hoy sin el sistema:**
Las fallas pueden comunicarse directamente a mantenimiento, por llamada, mensaje o de forma verbal. Esto dificulta saber qué problemas siguen pendientes, quién los está atendiendo y cuáles deberían resolverse primero.

**Usuarios del sistema:**

| Tipo de usuario           | Qué necesita del sistema                                         | Qué le preocupa                                                  |
| ------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| Recepción / Limpieza      | Reportar una falla y consultar si ya fue atendida                | Que una habitación siga con problemas cuando llegue un huésped   |
| Personal de mantenimiento | Ver las fallas pendientes, su prioridad y actualizar su avance   | Atender primero una falla menor mientras existe otra más urgente |
| Gerente                   | Consultar el estado de las habitaciones y el historial de fallas | Tener habitaciones fuera de servicio por demasiado tiempo        |

**Un conflicto entre usuarios:**
Recepción puede necesitar que una habitación sea reparada rápidamente porque está próxima a ocuparse, mientras que mantenimiento puede tener otras fallas más graves pendientes. El sistema debe ayudar a establecer qué problema requiere atención primero.

---

## 3. Alcance

### Dentro del alcance

* Registrar fallas indicando habitación, tipo de problema y descripción.
* Clasificar las fallas por nivel de prioridad.
* Asignar fallas al personal de mantenimiento y registrar su estado.
* Consultar el historial de fallas y reparaciones de cada habitación.
* Mostrar las fallas pendientes y las habitaciones afectadas.

### Explícitamente fuera del alcance

* Gestionar reservaciones, pagos o check-in de huéspedes.
* Comprar automáticamente piezas o materiales de mantenimiento.
* Detectar fallas automáticamente mediante sensores.

**Por qué queda fuera:**
La detección automática mediante sensores requeriría integrar dispositivos físicos y tecnología adicional. El proyecto se enfoca en mejorar el reporte, seguimiento y priorización de las fallas que detecta el personal del hotel.

---

## 4. Tipo de sistema y restricciones

**Tipo de sistema:**
De información.

**Por qué es de ese tipo:**
El sistema registra, consulta y organiza información sobre habitaciones, fallas y reparaciones para ayudar al personal del hotel a coordinar el mantenimiento y tomar decisiones.

**Atributos de calidad que impone:**

| Atributo                | Por qué importa en mi caso                                           | Qué pasa si no se cumple                                                         |
| ----------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Usabilidad              | El personal debe poder reportar una falla rápidamente                | Los empleados podrían evitar usar el sistema o registrar información incompleta  |
| Integridad de los datos | El estado, prioridad y habitación de cada falla deben ser correctos  | Mantenimiento podría atender una habitación o problema equivocado                |
| Trazabilidad            | Es necesario conocer qué ocurrió con cada falla desde que se reportó | No se podría saber quién la atendió, cuánto tardó o si el problema es recurrente |

**Reglas de negocio que ya identifiqué:**

1. Una falla que impida utilizar una habitación debe tener mayor prioridad que una falla que no afecte su funcionamiento.
2. La prioridad de una falla puede aumentar si la habitación está ocupada o será utilizada próximamente.
3. Una falla no puede marcarse como resuelta hasta que mantenimiento registre que el trabajo fue terminado.

---

## 5. Ciclo de vida elegido

**Modelo elegido:**
Prototipado rápido.

**Por qué le conviene a este proyecto:**
Aunque el problema principal de RoomFix está definido, algunos requisitos pueden cambiar al conocer mejor cómo trabaja el personal del hotel. Un prototipo permitiría mostrar rápidamente cómo se registrarían, priorizarían y atenderían las fallas para recibir retroalimentación de recepción, mantenimiento y gerencia antes de desarrollar el sistema completo.

### Alternativas descartadas

**Alternativa 1:**
Cascada.

*Por qué la descarté:*
Obligaría a definir prácticamente todos los requisitos desde el inicio. En este proyecto algunas reglas, como la prioridad de las fallas, pueden necesitar cambios después de recibir retroalimentación del personal del hotel.

**Alternativa 2:**
Modelo en V.

*Por qué la descarté:*
Su nivel de planificación y validación es mayor al que necesita este proyecto. RoomFix no es un sistema crítico ni requiere certificaciones, por lo que un modelo incremental permite avanzar de forma más sencilla y recibir retroalimentación durante el desarrollo.

---

## Antes de entregar

Reviso que el documento cumpla lo siguiente:

* [x] La descripción del apartado 1 se entiende sin ser del área
* [x] Hay al menos dos tipos de usuario con necesidades distintas
* [x] Identifiqué un conflicto real entre usuarios
* [x] El alcance dice qué queda fuera, no solo qué queda dentro
* [x] Las exclusiones son específicas, no genéricas
* [x] Identifiqué el tipo de sistema y al menos dos atributos de calidad
* [x] Anoté al menos tres reglas de negocio no obvias
* [x] Justifiqué el ciclo de vida contra dos alternativas descartadas
* [ ] El documento está en mi repositorio y se puede leer desde el navegador
* [x] Borré todas las instrucciones en cursiva de la plantilla
