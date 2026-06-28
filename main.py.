# ==============================================================================
# PROYECTO: OPTIMIZER v1.0
# AUTOR: Bryan Jacome
# ASIGNATURA: Lógica de Programación
# ==============================================================================

def simular_optimizacion():
    print("=================================================================")
    print("     BIENVENIDO A OPTIMIZER v1.0 - LÓGICA DE PROGRAMACIÓN        ")
    print("=================================================================\n")
    
    try:
        presupuesto_total = float(input("Ingrese el presupuesto total disponible ($): "))
        costo_objetivo = float(input("Ingrese el costo máximo objetivo ($): "))
        num_canales = int(input("Ingrese el número de canales a evaluar: "))
    except ValueError:
        print("\n[ERROR] Los datos ingresados no son válidos.")
        return

    if presupuesto_total <= 0 or costo_objetivo <= 0 or num_canales <= 0:
        print("\n[ERROR] Los valores deben ser mayores a cero.")
        return

    canales = []
    presupuesto_asignado_total = 0

    # BUCLE REPETITIVO (FOR) PARA PROCESAR CADA CANAL
    for i in range(1, num_canales + 1):
        print(f"\n---> Configuración del Canal #{i}:")
        nombre = input(f"  Nombre del canal: ")
        costo_actual = float(input(f"  Ingrese el costo actual ($): "))
        eficiencia = float(input(f"  Ingrese la eficiencia actual (%): "))
        
        # ESTRUCTURAS LÓGICAS CONDICIONALES (IF-ELIF-ELSE)
        if costo_actual <= (costo_objetivo * 0.8) and eficiencia >= 2.0:
            estado = "EXCELENTE (Rendimiento Óptimo - Priorizar Capital)"
            factor_ajuste = 1.25
        elif costo_actual <= costo_objetivo:
            estado = "ACEPTABLE (Dentro del rango esperado)"
            factor_ajuste = 1.00
        elif costo_actual > costo_objetivo and costo_actual <= (costo_objetivo * 1.3):
            estado = "EN OBSERVACIÓN (Costo Elevado)"
            factor_ajuste = 0.85
        else:
            estado = "CRÍTICO (Inversión Deficiente)"
            factor_ajuste = 0.50

        presupuesto_base = presupuesto_total / num_canales
        presupuesto_sugerido = presupuesto_base * factor_ajuste
        presupuesto_asignado_total += presupuesto_sugerido

        canales.append({
            "id": i, "nombre": nombre, "costo": costo_actual, "eficiencia": eficiencia,
            "estado": estado, "presupuesto": presupuesto_sugerido
        })

    # BUCLE ITERATIVO DE COMPENSACIÓN (WHILE)
    while presupuesto_asignado_total > presupuesto_total:
        excedente = presupuesto_asignado_total - presupuesto_total
        for canal in canales:
            if "EXCELENTE" not in canal["estado"]:
                canal["presupuesto"] -= (excedente / num_canales)
        presupuesto_asignado_total = sum(c["presupuesto"] for c in canales)

    # IMPRESIÓN DEL INFORME FINAL
    print("\n=================================================================")
    print("              INFORME FINAL DE OPTIMIZACIÓN LÓGICA               ")
    print("=================================================================")
    for c in canales:
        print(f"\nCanal #{c['id']}: {c['nombre']} -> {c['estado']}")
        print(f"  Presupuesto Optimizado Asignado: ${max(0.0, c['presupuesto']):,.2f}")

if __name__ == "__main__":
    simular_optimizacion()
