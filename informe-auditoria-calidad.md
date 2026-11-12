# Informe de Auditoría de Calidad

_Revisión de cambios y Pull Requests · Proyecto sistema-citas-medicas · 11 de noviembre de 2026_


## 1. Integrantes del equipo

| Integrante | Cuenta / rama en GitHub | Aporte al proyecto |
|---|---|---|
| Juan Felipe Cardoso Rivera | `JuanCardosoRi` | Abrió y fusionó el Pull Request hacia `main`. |
| Báez Parra Mauricio Alberto | `Mauricio-Báez` | Rama propia; por error la subió y la unió directamente a `main`. |
| Zuluaga Ramírez Jhoan Sebastián | `Jhoan_Zuluaga` | Plan de pruebas (`plan-pruebas 1.0.md`). |
| Herrera Correa Juan Diego | `correajuan606-ui` | Validación de citas, RF-04 (`requisitos (1).md`). |


## 2. Resumen ejecutivo

El equipo trabajó en ramas separadas sobre el sistema de citas médicas. Se revisaron tres contribuciones: el **plan de pruebas** de Jhoan Zuluaga (5 casos de prueba para RF-01 a RF-04), la **función de validación de citas** de Juan Diego Herrera (RF-04, regla de 24 horas) y la rama de Mauricio Báez, que fue integrada a `main` sin pasar por Pull Request. En ningún caso se registró una revisión por pares antes de integrar los cambios. El trabajo técnico es coherente entre sí (la prueba CP-05 verifica justamente la función entregada), pero el proceso de integración presenta desviaciones que se detallan en este informe.


## 3. Contribuciones por integrante

**3.1 Jhoan Sebastián Zuluaga Ramírez · rama `Jhoan_Zuluaga`**

- Archivo: `plan-pruebas 1.0.md` (15 líneas, 1,28 KB).
- Contenido: documento que describe las pruebas para comprobar que el sistema cumple los requisitos funcionales (RF). Cada caso indica qué se prueba, los datos de entrada y el resultado esperado.
- Estado del Pull Request: el PR #1, «Añadir archivos mediante subida», fue abierto por la cuenta `jszr1709-png` desde `Jhoan_Zuluaga` hacia `Mauricio-Báez` (1 commit, 1 archivo, +15 líneas). En la captura figuraba abierto, sin reseñadores, sin descripción y listo para fusionar.

| ID | Requisito | Caso de prueba | Datos de entrada | Resultado esperado |
|---|---|---|---|---|
| CP-01 | RF-01 | Registrar a un paciente nuevo | Nombre, correo electrónico válido y contraseña | Se crea la cuenta y el paciente puede ingresar al sistema |
| CP-02 | RF-01 | Iniciar sesión con una contraseña incorrecta | Correo electrónico válido y contraseña equivocada | El sistema niega el acceso y muestra un mensaje de error |
| CP-03 | RF-02 | Buscar un médico por especialidad | Especialidad «Pediatría» | Se muestra la lista de pediatras con su disponibilidad |
| CP-04 | RF-03 | Agendar una cita en un horario disponible | Médico, fecha y hora que estén libres | La cita queda confirmada y aparece en la sección «Mis citas» |
| CP-05 | RF-04 | Cancelar una cita con menos de 24 horas de anticipación | Cita programada dentro de 5 horas | El sistema no permite la cancelación y explica la regla de las 24 horas |

**3.2 Juan Diego Herrera Correa · rama `correajuan606-ui-patch-1`**

- Archivo: `requisitos (1).md` (43 líneas, 1,63 KB; archivo nuevo, +43 / -0).
- Contenido: función en Python `validar_modificacion_cita(fecha_cita, fecha_actual=None)` que implementa el requisito **RF-04**: una cita médica solo puede cancelarse o reprogramarse con al menos 24 horas de anticipación.
- Casos que cubre: 24 horas o más (permitido), entre 0 y 24 horas (no permitido, cita el RF-04) y cita ya transcurrida (no permitido). Incluye docstring y un ejemplo de uso con fechas simuladas.
- Integración: el PR fue abierto y fusionado a `main` por `JuanCardosoRi` en el mismo momento (commit de fusión `46a4eed`, 1 commit, 0 checks, sin reseñadores). La descripción del PR habla de mejoras a un informe de auditoría y no corresponde al contenido real del archivo.

```python
def validar_modificacion_cita(fecha_cita: datetime, fecha_actual: datetime = None) -> dict:
    if fecha_actual is None:
        fecha_actual = datetime.now()
    tiempo_restante = fecha_cita - fecha_actual
    horas_restantes = tiempo_restante.total_seconds() / 3600
    if horas_restantes >= 24:
        return {"permitido": True, "mensaje": "La cita puede ser modificada ..."}
    elif horas_restantes > 0:
        return {"permitido": False, "mensaje": "... mínimo de 24 horas (RF-04)."}
    else:
        return {"permitido": False, "mensaje": "La fecha de la cita ya ha transcurrido."}
```

**3.3 Mauricio Alberto Báez Parra · rama `Mauricio-Báez`**

- Incidente: Mauricio subió su rama a la rama principal y la unió (merge) directamente, sin Pull Request ni revisión. Por esa razón `main` y `Mauricio-Báez` ya no se ven como ramas diferentes: su contenido quedó dentro de `main`.
- Consecuencia: el cambio llegó a la rama principal sin aprobación de otro integrante, lo que incumple el paso 7 del proceso (revisar mediante Pull Request).
- Archivos y líneas modificadas: pendiente de completar por el equipo (no se aportó evidencia del contenido). Se puede consultar con `git log --stat --author="Mauricio"`.


## 4. Trazabilidad requisito, prueba y código

| Requisito | Caso(s) de prueba | Implementación entregada | Observación |
|---|---|---|---|
| RF-01 Registro e inicio de sesión | CP-01, CP-02 | No se vio código en las ramas revisadas | Prueba definida; falta evidencia de implementación |
| RF-02 Buscar médico por especialidad | CP-03 | No se vio código en las ramas revisadas | Prueba definida; falta evidencia de implementación |
| RF-03 Agendar cita | CP-04 | No se vio código en las ramas revisadas | Prueba definida; falta evidencia de implementación |
| RF-04 Cancelar con 24 h de anticipación | CP-05 | `validar_modificacion_cita` (rama `correajuan606-ui-patch-1`) | Coherente: con 5 h de anticipación la función devuelve `permitido = False`, igual que el resultado esperado de CP-05 |


## 5. Auditoría: quién, qué, cuándo y si fue revisado

| Integrante | Rama | Qué modificó | Fecha | ¿Revisado? |
|---|---|---|---|---|
| Juan Diego Herrera Correa | `correajuan606-ui-patch-1` | `requisitos (1).md`: función RF-04 (+43) | 11/11/2026 | No. Fusionado a `main` por Juan Felipe Cardoso, sin reseñadores |
| Jhoan S. Zuluaga Ramírez | `Jhoan_Zuluaga` | `plan-pruebas 1.0.md`: 5 casos de prueba (+15) | 11/11/2026 | Pendiente. PR #1 abierto, sin reseñadores al momento de la captura |
| Mauricio A. Báez Parra | `Mauricio-Báez` | Por completar | 11/11/2026 | No. Unida a `main` directamente, sin PR |
| Juan Felipe Cardoso Rivera | (PR hacia `main`) | Abrió y fusionó el PR de la rama de Juan Diego | 11/11/2026 | No. Abrió y fusionó sin segundo revisor |


## 6. Hallazgos

| N.º | Hallazgo | Tipo | Gravedad |
|---|---|---|---|
| 1 | Se integraron cambios a `main` sin revisión por pares: el PR de Juan Diego se abrió y fusionó al mismo tiempo, y la rama de Mauricio se unió directamente. | No conformidad | Alta |
| 2 | No hay checks automáticos ni pruebas ejecutadas (0 checks). El plan de pruebas existe pero no se ha ejecutado contra el código. | No conformidad | Media |
| 3 | La descripción del PR fusionado (mejoras a un informe de auditoría) no coincide con su contenido (función de validación RF-04). | No conformidad | Media |
| 4 | El PR #1 apunta a la rama `Mauricio-Báez` en lugar de `main`, y no tiene descripción ni reseñadores. | No conformidad | Media |
| 5 | Código Python guardado en un archivo `.md` llamado «requisitos (1).md». GitHub lo muestra mal (partes como texto y partes como bloque de código); por eso en la vista aparecen palabras como «Desde», «si» o «Ninguno» (traducción automática del navegador sobre texto mal interpretado). El archivo debería ser un `.py` con nombre claro. | Observación | Media |
| 6 | Los PR no referencian un issue ni el requisito correspondiente, lo que dificulta la trazabilidad. | Observación | Baja |
| 7 | El plan de pruebas es claro y completo en su formato (ID, requisito, caso, datos y resultado esperado) y la función RF-04 es correcta y coherente con CP-05. | Aspecto positivo | - |


## 7. Recomendaciones

- Activar la protección de la rama `main` (Settings, Branches) para exigir Pull Request y al menos una aprobación de otro integrante.
- Cada integrante debe trabajar en su rama y abrir un PR hacia `main`; quien abre el PR no debe ser quien lo fusiona.
- Cambiar la base del PR #1 a `main`, agregar descripción y asignar un reseñador.
- Completar en este informe el aporte de Mauricio Báez con el historial del repositorio (`git log --stat`).
- Renombrar `requisitos (1).md` a un archivo de código (por ejemplo `validar_cita.py`) y mantener los requisitos en un documento aparte.
- Ejecutar el plan de pruebas (CP-01 a CP-05) y registrar la evidencia; agregar pruebas unitarias y un check automático (GitHub Actions).
- Vincular cada PR con su requisito (RF) o issue.


## 8. Concepto final

**Conforme con observaciones.** El contenido técnico entregado es coherente y cumple lo que describe cada documento, pero el proceso de integración no cumplió la práctica de revisión por pares: hubo cambios que llegaron a la rama principal sin aprobación, sin pruebas ejecutadas y, en un caso, con una descripción que no corresponde al contenido. Se recomienda corregir los hallazgos 1 a 4 antes de dar el cambio por validado.
