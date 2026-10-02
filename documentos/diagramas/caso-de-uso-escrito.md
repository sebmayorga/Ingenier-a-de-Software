[caso-de-uso-escrito.md](https://github.com/user-attachments/files/32941469/caso-de-uso-escrito.md)
# Caso de Uso Escrito — RoomFix

---

### CU-01 · Registrar una falla de mantenimiento

* **Actor principal:**
  `Recepción / Personal de limpieza`

* **Objetivo:**
  Registrar una falla detectada en una habitación para que mantenimiento pueda conocerla y darle seguimiento.

* **Precondición:**
  El usuario tiene acceso a la opción de registro de fallas de RoomFix.

* **Escenario principal:**
  1. El usuario selecciona la opción para registrar una nueva falla.
  2. El sistema muestra el formulario de registro.
  3. El usuario selecciona la habitación en la que se detectó el problema.
  4. El usuario indica el tipo de problema y escribe una descripción de la falla.
  5. El usuario confirma el registro.
  6. El sistema guarda el reporte y lo incorpora a la lista de fallas registradas para su seguimiento.

* **Flujos alternos:**
  * **3a. No se seleccionó una habitación:** Al intentar guardar el reporte sin indicar la habitación, el sistema señala el dato faltante y no completa el registro. El usuario selecciona una habitación y continúa.
  * **4a. Falta información del problema:** Si el usuario intenta registrar la falla sin indicar el tipo de problema o sin escribir una descripción, el sistema identifica el campo faltante y solicita completarlo antes de guardar.

* **Postcondición:**
  La falla queda registrada con su habitación, tipo de problema y descripción, y está disponible para su consulta y seguimiento.

* **Requisitos que realiza:**
  RF-001, RNF-USA-001, RNF-CON-001

---

**Nota:** Los flujos alternos representan condiciones propuestas en la especificación inicial y deben validarse con la entrevista real.
