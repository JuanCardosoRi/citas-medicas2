# Informe de Auditoría de Cambios

## Información General

- **Proyecto:** Sistema de Citas Médicas
- **Versión auditada:** v1.0
- **Auditor (SQA):** [Nombre del auditor]
- **Fecha de auditoría:** [dd/mm/aaaa]
- **Repositorio:** [URL GitHub]
- **Periodo evaluado:** [Fecha inicio - Fecha fin]

---

## 1. Objetivo de la Auditoría

Verificar que los cambios realizados en el proyecto cumplan con los procedimientos de gestión de configuración, control de versiones y aseguramiento de la calidad del software, garantizando la trazabilidad entre requisitos, commits y solicitudes de integración.

---

## 2. Registro de Cambios Auditados

| # | Cambio realizado | Archivo(s) afectados | Responsable | Fecha | Commit / PR | Requisito asociado | Evidencia de prueba | Revisado |
|---|------------------|---------------------|------------|--------|-------------|-------------------|--------------------|-----------|
| 1 | Mejora del formulario de citas | index.html | Juan Pérez | 10/11/2026 | Commit abc123 | RF-01 | Captura funcional | Sí |
| 2 | Validación de correo electrónico | app.js | María Gómez | 10/11/2026 | PR #5 | RF-02 | Prueba unitaria | Sí |
| 3 | | | | | | | | |
| 4 | | | | | | | | |
| 5 | | | | | | | | |

---

## 3. Verificación de Pull Request

- **PR #:**
- **Rama origen:**
- **Rama destino:**
- **Autor:**
- **Revisor:**
- **Fecha de revisión:**
- **Comentarios de revisión:**
- **Estado:** Aprobado / Rechazado / Integrado

### Lista de Verificación

| Criterio | Cumple |
|-----------|---------|
| El código compila correctamente | ☐ |
| No genera errores funcionales | ☐ |
| Cumple los requisitos asociados | ☐ |
| Tiene evidencia de pruebas | ☐ |
| Fue revisado por otro integrante | ☐ |
| Se integró correctamente a main | ☐ |

---

## 4. Trazabilidad

| Requisito | Commit | Pull Request | Responsable |
|------------|---------|--------------|-------------|
| RF-01 | abc123 | PR #5 | Juan Pérez |
| RF-02 | def456 | PR #6 | María Gómez |

---

## 5. Hallazgos

### Hallazgos Positivos

- Uso adecuado de control de versiones.
- Mensajes de commit descriptivos.
- Revisión de código realizada antes de la integración.

### No Conformidades

| ID | Descripción | Severidad | Responsable | Estado |
|----|-------------|------------|-------------|---------|
| NC-01 | Ejemplo de no conformidad | Media | Equipo | Abierta |

---

## 6. Recomendaciones de Mejora

1. Utilizar una convención estándar para nombres de commits.
2. Realizar revisiones cruzadas obligatorias.
3. Mantener actualizada la documentación técnica.
4. Asociar cada cambio a un requisito funcional o no funcional.
5. Registrar evidencias de pruebas en cada Pull Request.

---

## 7. Conclusiones

- ¿Todos los integrantes realizaron al menos un commit?: ________
- ¿Los mensajes de commit fueron claros y descriptivos?: ________
- ¿Todos los cambios fueron revisados antes de llegar a main?: ________
- ¿Existe trazabilidad entre requisitos, commits y PR?: ________

### Concepto Final de Auditoría

☐ Aprobado

☐ Aprobado con observaciones

☐ Requiere acciones correctivas

**Observaciones finales:**

____________________________________________________

____________________________________________________

**Firma del auditor:** ______________________
