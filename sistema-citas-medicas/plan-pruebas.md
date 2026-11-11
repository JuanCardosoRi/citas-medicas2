# Plan de pruebas

| ID | Requisito | Caso de prueba | Datos de entrada | Resultado esperado |
|---|---|---|---|---|
| CP-01 | RF-01 | Registro de paciente nuevo | Nombre, correo válido, contraseña | Cuenta creada y acceso permitido |
| CP-02 | RF-01 | Inicio de sesión con contraseña incorrecta | Correo válido, contraseña errónea | Se rechaza el acceso y se muestra mensaje de error |
| CP-03 | RF-02 | Búsqueda de médico por especialidad | Especialidad "Pediatría" | Lista de pediatras con su disponibilidad |
| CP-04 | RF-03 | Agendar cita en horario disponible | Médico, fecha y hora libres | Cita confirmada y visible en "Mis citas" |
| CP-05 | RF-04 | Cancelar cita con menos de 24 h | Cita en 5 horas | El sistema rechaza la cancelación e informa la regla |

## Estado de ejecución
Pendiente: las pruebas se ejecutarán cuando exista una implementación.
