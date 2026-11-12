from datetime import datetime, timedelta

def validar_modificacion_cita(fecha_cita: datetime, fecha_actual: datetime = None) -> dict:
    """
    Valida si una cita médica puede ser cancelada o reprogramada 
    cumpliendo con el requisito de al menos 24 horas de anticipación (RF-04).
    """
    if fecha_actual is None:
        fecha_actual = datetime.now()
    
    # Calcular la diferencia de tiempo restante hasta la cita
    tiempo_restante = fecha_cita - fecha_actual
    horas_restantes = tiempo_restante.total_seconds() / 3600
    
    # Validar si cumple con el mínimo de 24 horas
    if horas_restantes >= 24:
        return {
            "permitido": True,
            "mensaje": "La cita puede ser modificada o cancelada exitosamente."
        }
    elif horas_restantes > 0:
        return {
            "permitido": False,
            "mensaje": "No es posible modificar o cancelar la cita. Se requiere un mínimo de 24 horas de anticipación (RF-04)."
        }
    else:
        return {
            "permitido": False,
            "mensaje": "La fecha de la cita ya ha transcurrido."
        }

# --- Ejemplo de uso ---
if __name__ == "__main__":
    # Simulamos que hoy es 11 de noviembre de 2026 a las 8:00 AM
    ahora = datetime(2026, 11, 11, 8, 0, 0)
    
    # Cita programada para el 12 de noviembre de 2026 a las 10:00 AM (más de 24h)
    cita_futura = datetime(2026, 11, 12, 10, 0, 0)
    print(validar_modificacion_cita(cita_futura, ahora))
    
    # Cita programada para el mismo 11 de noviembre a las 2:00 PM (menos de 24h)
    cita_cercana = datetime(2026, 11, 11, 14, 0, 0)
    print(validar_modificacion_cita(cita_cercana, ahora))
