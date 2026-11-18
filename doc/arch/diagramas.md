# Diagramas de arquitectura de RoomFix

## 1. Diagrama de contexto (C4 - Nivel 1)

```mermaid
flowchart TB
    sis["RoomFix - Sistema de gestion de mantenimiento"]

    rec([Recepcionista])
    limp([Personal de limpieza])
    mant([Personal de mantenimiento])
    ger([Gerente del hotel])

    sis ---|Reporta fallas y consulta estados| rec
    sis ---|Reporta problemas en habitaciones| limp
    sis ---|Atiende fallas y actualiza estados| mant
    sis ---|Supervisa reportes y reparaciones| ger

    style sis fill:#ff5d00,color:#fff
```

## 2. Diagrama de contenedores (C4 - Nivel 2)

```mermaid
flowchart TB
    usuarios([Usuarios del hotel])

    subgraph sistema["RoomFix - Sistema de mantenimiento"]
        web["Aplicacion web<br/>Interfaz de usuario"]
        api["API de RoomFix<br/>Logica de negocio"]
        db[("Base de datos<br/>Reportes, habitaciones y usuarios")]
    end

    usuarios -->|Accede desde el navegador| web
    web -->|Solicitudes HTTPS/JSON| api
    api -->|Consulta y guarda informacion| db

    style api fill:#ff5d00,color:#fff
```

## 3. Diagrama de componentes (C4 - Nivel 3)

```mermaid
flowchart TB
    web["Aplicacion web de RoomFix"]

    subgraph api["API de RoomFix - Logica de negocio"]
        hab["Habitaciones<br/>Informacion y disponibilidad"]
        rep["Gestion de reportes<br/>Registro y seguimiento de fallas"]
        mant["Mantenimiento<br/>Asignacion y reparaciones"]
        seg["Seguimiento<br/>Estados y verificacion"]
    end

    db[("Base de datos de RoomFix")]

    web -->|Envia solicitudes| rep
    web -->|Consulta habitaciones| hab
    web -->|Gestiona reparaciones| mant
    web -->|Consulta estados| seg

    rep -->|Identifica habitacion| hab
    rep -->|Solicita atencion| mant
    mant -->|Actualiza progreso| seg
    seg -->|Verifica solucion| rep

    hab -->|Consulta y guarda datos| db
    rep -->|Consulta y guarda datos| db
    mant -->|Consulta y guarda datos| db
    seg -->|Consulta y guarda datos| db

    style rep fill:#ff5d00,color:#fff
```

## 4. Tecnologías y límites de la propuesta

Los diagramas C4 describen una **aplicación web**, una **API de lógica de negocio** y una **base de datos**. La comunicación entre la aplicación web y la API se representa como **HTTPS/JSON**. **No se han seleccionado ni documentado todavía** el framework web, el lenguaje de la API ni el motor de base de datos; no deben presentarse como decisiones ya tomadas.

La arquitectura elegida es un **monolito modular**. Véase [ADR-001](./adr-001-monolito-modular.md).

## 5. Diseño propuesto y cambio solicitado

- [Patrón Observer propuesto](./patron-observer.md): posible reacción a cambios de estado, aún no implementada.
- [Análisis de impacto SC-001](./analisis-impacto-sc-001.md): fotografías antes y después de la reparación, estimación y decisión.

## 6. Concordancia entre diagramas UML

En el diagrama de secuencia de **CU-01 Registrar falla**, la aplicación invoca `Usuario.registrarFalla(numeroHabitacion, tipo, descripcion)` y este solicita `Falla.crearRegistro(numeroHabitacion, tipo, descripcion)`. Ambas operaciones figuran en el diagrama de clases. La segunda se hizo explícita para que el mensaje de creación del diagrama de secuencia tenga una operación correspondiente. Estos diagramas describen el **diseño**, no código implementado.
