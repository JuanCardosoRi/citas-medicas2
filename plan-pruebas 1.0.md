# Plan de pruebas

Este documento describe las pruebas que se realizarán para comprobar que el sistema cumple con los requisitos funcionales (RF). Cada caso indica qué se prueba, qué datos se usan y qué debería ocurrir si el sistema funciona correctamente.

| ID | Requisito | Caso de prueba | Datos de entrada | Resultado esperado |
|---|---|---|---|---|
| CP-01 | RF-01 | Registrar a un paciente nuevo | Nombre, correo electrónico válido y contraseña | Se crea la cuenta y el paciente puede ingresar al sistema |
| CP-02 | RF-01 | Iniciar sesión con una contraseña incorrecta | Correo electrónico válido y contraseña equivocada | El sistema niega el acceso y muestra un mensaje de error |
| CP-03 | RF-02 | Buscar un médico por especialidad | Especialidad "Pediatría" | Se muestra la lista de pediatras con su disponibilidad |
| CP-04 | RF-03 | Agendar una cita en un horario disponible | Médico, fecha y hora que estén libres | La cita queda confirmada y aparece en la sección "Mis citas" |
| CP-05 | RF-04 | Cancelar una cita con menos de 24 horas de anticipación | Cita programada dentro de 5 horas | El sistema no permite la cancelación y explica la regla de las 24 horas |

## Estado de ejecución

**Pendiente.** Las pruebas se realizarán cuando el sistema esté implementado.
