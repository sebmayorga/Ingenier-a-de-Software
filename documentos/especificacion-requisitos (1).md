# Especificación de requisitos

---

- **Sistema:** RoomFix
- **Autor:** Sebastián Mayorga Galicia
- **Versión:** 1.0
- **Fecha de la última actualización:** 01/10/2026

---

## 1. Propósito y alcance

- **Propósito del documento:** Definir los requisitos funcionales y no funcionales de RoomFix para establecer de manera clara qué debe hacer el sistema y bajo qué condiciones debe funcionar. Este documento servirá como referencia para el desarrollo de los casos de uso, el prototipo y la posterior validación de los requisitos.

- **Alcance del sistema:** RoomFix permitirá registrar fallas de mantenimiento en habitaciones de un hotel indicando la habitación, el tipo de problema y su descripción. Permitirá clasificar las fallas por prioridad considerando su gravedad y la situación de la habitación, asignarlas al personal de mantenimiento y consultar su estado. El personal de mantenimiento podrá registrar la finalización de una reparación y el sistema permitirá identificar cuándo una habitación afectada puede volver a utilizarse. También se podrá consultar el historial de fallas y reparaciones de cada habitación y visualizar los reportes que continúan pendientes.

- **Fuera del alcance:** RoomFix no administrará reservaciones, pagos ni procesos de check-in de huéspedes. Tampoco realizará compras automáticas de materiales o refacciones ni detectará fallas automáticamente mediante sensores.

---

## 2. Usuarios y su contexto

| Usuario | Qué hace hoy sin el sistema | Qué espera del sistema |
| :--- | :--- | :--- |
| **Recepción / Limpieza** | Reporta las fallas detectadas en las habitaciones mediante llamadas o mensajes al personal de mantenimiento y posteriormente debe comunicarse nuevamente para conocer el avance. | Registrar una falla de forma clara y consultar posteriormente si continúa pendiente, está siendo atendida o ya fue resuelta. |
| **Personal de mantenimiento** | Recibe reportes por llamadas o mensajes y decide qué problemas atender primero con la información disponible en ese momento. | Consultar los reportes pendientes, conocer su prioridad y registrar el avance de las fallas que está atendiendo. |
| **Gerencia** | Depende de la comunicación entre las distintas áreas para conocer qué habitaciones presentan problemas y cuáles continúan afectadas por mantenimiento. | Consultar el estado general de las fallas y dar seguimiento a las habitaciones afectadas. |

**Conflictos identificados entre usuarios:**

Recepción puede necesitar que una habitación sea reparada rápidamente porque está ocupada o será utilizada próximamente, mientras que mantenimiento puede considerar más urgente otra falla debido a su gravedad o al riesgo de causar mayores daños. RoomFix debe permitir que la prioridad considere tanto la gravedad de la falla como la situación de la habitación.

---

## 3. Requisitos funcionales

### 3.1 Resumen

| ID | Nombre | Prioridad | Origen |
| :--- | :--- | :--- | :--- |
| **RF-001** | Registro de fallas | Imprescindible | Visión del producto |
| **RF-002** | Clasificación de prioridad | Imprescindible | Visión del producto / Regla de negocio |
| **RF-003** | Actualización de prioridad | Importante | Visión del producto |
| **RF-004** | Asignación de fallas | Imprescindible | Visión del producto |
| **RF-005** | Consulta del estado de una falla | Imprescindible | Visión del producto |
| **RF-006** | Registro de finalización de reparación | Imprescindible | Regla de negocio / Visión del producto |
| **RF-007** | Identificación de habitación disponible | Imprescindible | Visión del producto |
| **RF-008** | Consulta del historial por habitación | Importante | Visión del producto |
| **RF-009** | Consulta de fallas pendientes | Imprescindible | Visión del producto |

### 3.2 Fichas

#### RF-001 · Registro de fallas

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema registra una falla de mantenimiento indicando la habitación, el tipo de problema y una descripción de la falla. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al registrar una falla con habitación, tipo de problema y descripción, el sistema guarda el reporte y lo muestra entre las fallas registradas. |
| **Relacionado con** | RF-002, RF-004, RF-005 |

#### RF-002 · Clasificación de prioridad

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema clasifica la prioridad de una falla considerando su gravedad y la situación de la habitación. |
| **Origen** | Visión del producto y reglas de negocio. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al registrar una falla, el sistema muestra una prioridad asociada al reporte tomando en cuenta la gravedad registrada y la situación de la habitación. |
| **Relacionado con** | RF-001, RF-003, RF-009 |

#### RF-003 · Actualización de prioridad

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema actualiza la prioridad de una falla cuando cambia la situación de la habitación. |
| **Origen** | Visión del producto y regla de negocio. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al modificarse la situación de una habitación con una falla activa, el sistema permite reflejar el cambio en la prioridad correspondiente. |
| **Relacionado con** | RF-002, RF-009 |

#### RF-004 · Asignación de fallas

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema asigna una falla pendiente a un integrante del personal de mantenimiento. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al asignar una falla a un integrante de mantenimiento, el reporte muestra al responsable asociado. |
| **Relacionado con** | RF-001, RF-005 |

#### RF-005 · Consulta del estado de una falla

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema muestra el estado actual de cada falla registrada. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al consultar una falla registrada, el sistema muestra su estado actual para identificar si continúa pendiente, está siendo atendida o fue resuelta. |
| **Relacionado con** | RF-004, RF-006, RF-009 |

#### RF-006 · Registro de finalización de reparación

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema registra la finalización de una reparación cuando mantenimiento indica que el trabajo terminó. |
| **Origen** | Regla de negocio y Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Cuando mantenimiento registra que terminó el trabajo de una falla, el sistema conserva la finalización de la reparación y la falla deja de aparecer como pendiente de atención. |
| **Relacionado con** | RF-005, RF-007, RF-008 |

#### RF-007 · Identificación de habitación disponible

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema muestra cuándo una habitación afectada por una falla puede volver a utilizarse después de finalizar la reparación. |
| **Origen** | Visión del producto corregida a partir de retroalimentación del profesor. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al finalizar la reparación de una falla que impedía utilizar una habitación, el sistema deja de mostrarla como afectada por esa falla de mantenimiento. |
| **Relacionado con** | RF-006, RF-009 |

#### RF-008 · Consulta del historial por habitación

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema muestra el historial de fallas y reparaciones registradas para una habitación. |
| **Origen** | Visión del producto. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al seleccionar una habitación, el sistema muestra las fallas y reparaciones previamente registradas para ella. |
| **Relacionado con** | RF-001, RF-006 |

#### RF-009 · Consulta de fallas pendientes

| Campo | Contenido |
| :--- | :--- |
| **Descripción** | El sistema muestra las fallas que permanecen pendientes y las habitaciones afectadas por ellas. |
| **Origen** | Visión del producto. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al consultar las fallas pendientes, el sistema muestra únicamente los reportes que todavía requieren atención junto con la habitación correspondiente. |
| **Relacionado con** | RF-002, RF-003, RF-005, RF-007 |

---

## 4. Requisitos no funcionales

### 4.1 Resumen

| ID | Atributo | Nombre | Prioridad | Origen |
| :--- | :--- | :--- | :--- | :--- |
| **RNF-USA-001** | Usabilidad | Registro sencillo de fallas | Importante | Atributo de calidad de la Visión del producto |
| **RNF-CON-001** | Confiabilidad | Integridad de los datos registrados | Imprescindible | Atributo de calidad de la Visión del producto |
| **RNF-CON-002** | Confiabilidad | Trazabilidad de cambios de estado | Importante | Atributo de calidad de la Visión del producto |

### 4.2 Fichas

#### RNF-USA-001 · Registro sencillo de fallas

| Campo | Contenido |
| :--- | :--- |
| **Atributo de calidad** | Usabilidad |
| **Descripción** | Un usuario puede completar el registro de una falla proporcionando la habitación, el tipo de problema y su descripción en una sola pantalla de captura. |
| **Métrica** | La tarea de registrar una falla se completa utilizando una sola pantalla de captura antes de la confirmación del registro. |
| **Origen** | Derivado del atributo de usabilidad establecido en la Visión del producto. La condición específica se mantiene como supuesto propio hasta su validación. |
| **Prioridad** | Importante |
| **Por qué importa** | El registro debe integrarse al trabajo cotidiano de recepción y limpieza sin agregar un proceso innecesariamente largo para reportar una falla. |
| **Afecta a** | RF-001 |

#### RNF-CON-001 · Integridad de los datos registrados

| Campo | Contenido |
| :--- | :--- |
| **Atributo de calidad** | Confiabilidad |
| **Descripción** | El sistema conserva los datos registrados de una falla sin alterar la habitación, el tipo de problema ni la descripción proporcionados al guardar el reporte. |
| **Métrica** | En el 100% de las pruebas de registro, los valores almacenados para habitación, tipo de problema y descripción deben coincidir con los valores confirmados por el usuario. |
| **Origen** | Derivado del atributo de integridad de los datos establecido en la Visión del producto. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Información incorrecta sobre una falla puede provocar que mantenimiento atienda una habitación o un problema distinto al reportado. |
| **Afecta a** | RF-001, RF-004, RF-008 |

#### RNF-CON-002 · Trazabilidad de cambios de estado

| Campo | Contenido |
| :--- | :--- |
| **Atributo de calidad** | Confiabilidad |
| **Descripción** | El sistema conserva un registro de los cambios de estado realizados sobre cada falla. |
| **Métrica** | El 100% de los cambios de estado de una falla deben quedar asociados al reporte correspondiente y permanecer disponibles para consulta posterior. |
| **Origen** | Derivado del atributo de trazabilidad establecido en la Visión del producto. |
| **Prioridad** | Importante |
| **Por qué importa** | Permite reconstruir el seguimiento de una falla y conocer cómo avanzó desde su registro hasta la finalización de la reparación. |
| **Afecta a** | RF-005, RF-006, RF-008 |

---

## 5. Casos de uso

### 5.1 Caso de Uso Escrito Completo

#### CU-01 · Registrar una falla de mantenimiento

* **Actor principal:** Recepción / Limpieza
* **Objetivo:** Registrar una falla detectada en una habitación para que pueda ser consultada y atendida por mantenimiento.
* **Precondición:** El usuario se encuentra en la opción de registro de fallas.
* **Escenario principal:**
  1. El usuario inicia el registro de una nueva falla.
  2. El usuario selecciona la habitación donde se detectó el problema.
  3. El usuario indica el tipo de problema.
  4. El usuario escribe una descripción de la falla.
  5. El sistema recibe la información del reporte.
  6. El sistema registra la falla y la incorpora a la lista de fallas que requieren seguimiento.
* **Flujos alternos:**
  * **2a. No se indica una habitación:** El sistema no completa el registro y solicita indicar la habitación correspondiente.
  * **3a. No se indica el tipo de problema:** El sistema no completa el registro y solicita indicar el tipo de problema.
  * **4a. No se proporciona una descripción:** El sistema no completa el registro y solicita escribir una descripción de la falla.
* **Postcondición:** La falla queda registrada y disponible para su consulta y seguimiento.
* **Requisitos que realiza:** RF-001, RNF-USA-001, RNF-CON-001

### 5.2 Resumen de Casos de Uso

| ID | Caso de Uso | Actor Principal | Requisitos que Realiza |
| :--- | :--- | :--- | :--- |
| **CU-01** | Registrar una falla de mantenimiento | Recepción / Limpieza | RF-001, RNF-USA-001, RNF-CON-001 |
| **CU-02** | Consultar y priorizar fallas | Mantenimiento | RF-002, RF-003, RF-009 |
| **CU-03** | Asignar una falla | Mantenimiento | RF-004 |
| **CU-04** | Consultar el estado de una falla | Recepción / Limpieza / Gerencia | RF-005, RNF-CON-002 |
| **CU-05** | Registrar finalización de reparación | Mantenimiento | RF-006, RNF-CON-002 |
| **CU-06** | Consultar habitaciones afectadas | Recepción / Gerencia | RF-007, RF-009 |
| **CU-07** | Consultar historial de una habitación | Mantenimiento / Gerencia | RF-008, RNF-CON-002 |

---

## 6. Trazabilidad

| Requisito | Origen | Caso de uso | Elemento del prototipo |
| :--- | :--- | :--- | :--- |
| **RF-001** | Visión del producto | CU-01 Registrar una falla | Pantalla de registro de falla |
| **RF-002** | Visión / Regla de negocio | CU-02 Consultar y priorizar fallas | Lista de fallas con prioridad |
| **RF-003** | Visión / Regla de negocio | CU-02 Consultar y priorizar fallas | Detalle de falla y prioridad |
| **RF-004** | Visión del producto | CU-03 Asignar una falla | Detalle de falla y responsable |
| **RF-005** | Visión del producto | CU-04 Consultar estado | Pantalla de seguimiento de falla |
| **RF-006** | Regla de negocio / Visión | CU-05 Registrar finalización | Pantalla de atención de falla |
| **RF-007** | Visión corregida | CU-06 Consultar habitaciones afectadas | Vista de habitaciones afectadas |
| **RF-008** | Visión del producto | CU-07 Consultar historial | Historial de habitación |
| **RF-009** | Visión del producto | CU-02 / CU-06 | Lista de fallas pendientes |
| **RNF-USA-001** | Visión / Supuesto propio | CU-01 | Pantalla de registro de falla |
| **RNF-CON-001** | Visión del producto | CU-01 | Registro de falla |
| **RNF-CON-002** | Visión del producto | CU-04, CU-05, CU-07 | Seguimiento e historial de falla |

---

## 7. Registro de cambios

| Fecha | Requisito | Qué cambió | Por qué |
| :--- | :--- | :--- | :--- |
| 01/10/2026 | Todos | Creación de la versión 1.0 de la especificación de requisitos. | Elaboración inicial a partir de la Visión del producto corregida y las reglas de negocio identificadas. |

---

## Antes de entregar

- [x] Todos los requisitos tienen identificador único y ninguno está repetido
- [x] Cada requisito expresa una sola idea
- [x] Cada requisito funcional tiene criterio de aceptación comprobable
- [x] Cada requisito no funcional tiene una métrica, no solo un adjetivo
- [x] El campo Origen distingue lo confirmado por el cliente de lo que sigo suponiendo
- [x] Hay al menos un requisito no funcional por cada atributo de calidad que impone mi tipo de sistema
- [x] Ningún requisito impone una solución técnica
- [x] Todos los requisitos caben dentro del alcance declarado
- [x] La tabla de trazabilidad está completa
- [ ] Mi dupla revisó el documento y su revisión está registrada
- [x] Borré los ejemplos y las instrucciones en cursiva
