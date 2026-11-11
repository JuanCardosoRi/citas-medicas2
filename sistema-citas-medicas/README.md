# Sistema de Citas Médicas

Proyecto académico de planificación y documentación (sin programación) para la actividad práctica de la Sesión 6 – Calidad del Software (SQA), Instituto i3.

## Objetivo
Planificar un sistema web que permita a los pacientes solicitar, consultar, reprogramar y cancelar citas médicas de forma ágil, reduciendo filas, llamadas y errores de agendamiento en una clínica.

## Descripción
El sistema centraliza la agenda de médicos y la gestión de citas de una clínica. El paciente agenda en línea, el personal administrativo administra la agenda y los médicos consultan sus citas del día.

## Usuarios
| Usuario | Descripción |
|---|---|
| Paciente | Solicita, consulta, reprograma y cancela sus citas. |
| Médico | Consulta su agenda y el listado de pacientes citados. |
| Recepcionista | Registra y gestiona citas en nombre de los pacientes. |
| Administrador | Gestiona médicos, especialidades, horarios y usuarios. |

## Funcionalidades principales
1. Registro e inicio de sesión de usuarios.
2. Búsqueda de médicos por especialidad y disponibilidad.
3. Agendamiento, reprogramación y cancelación de citas.
4. Agenda diaria del médico.
5. Administración de médicos, especialidades y horarios.

Los detalles están en [`requisitos.md`](requisitos.md); los casos de prueba en [`plan-pruebas.md`](plan-pruebas.md); y el control de cambios en [`auditoria.md`](auditoria.md).

## Equipo y roles
| Integrante | Usuario GitHub | Rol |
|---|---|---|
| Juan Felipe Cardoso Rivera | [@usuario_juan_felipe] | Líder del proyecto |
| Mauricio Alberto Parra Baez | [@usuario_mauricio] | Documentador (colaborador) |
| Jhoan Sebastian Zuluaga | [@usuario_jhoan] | Gestor de cambios (colaborador) |
| Juan Diego Herrera Correa | [@usuario_juan_diego] | Revisor de calidad – SQA (colaborador) |

## Flujo de trabajo
- La rama `main` contiene la versión aprobada de la documentación.
- Las mejoras se proponen en ramas separadas (ej. `mejora-documentacion`).
- Todo cambio a `main` entra mediante Pull Request revisado por otro integrante.
- Los commits usan mensajes claros (ej. "Agregar requisito RF-01").
