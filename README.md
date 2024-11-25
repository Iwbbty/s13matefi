# s13matefi
import numpy as np

# Función para calcular el valor presente de una anualidad con gradiente uniforme
def valor_presente_gradiente_uniforme(cuota_base, gradiente, tasa, n):
    gradiente_vp = gradiente * ((1 - (1 + tasa) ** -n) / tasa**2 - n / (tasa * (1 + tasa)**n))
    return gradiente_vp

# Caso 1
def caso_1():
    C = 100
    Cuota_final = 240
    n = 8
    i = 0.05
    gradiente = (Cuota_final - C) / (n - 1)
    VP = valor_presente_gradiente_uniforme(0, gradiente, i, n)
    return round(VP, 2)

# Caso 2
def caso_2():
    C = 500
    G = 100
    n = 12
    i = 0.03
    MC = C * ((1 + i)**n - 1) / i
    MG = G * (((1 + i)**n - 1) / i**2 - n / (i * (1 + i)**n))
    return round(MC + MG, 2)

# Caso 3
def caso_3():
    C = 100
    G = 20
    n = 12
    i = 0.04
    VPC = C * (1 - (1 + i)**-n) / i
    VPG = valor_presente_gradiente_uniforme(0, G, i, n)
    return round(4000 + VPC + VPG, 2)

# Caso 4
def caso_4():
    S = 10000
    R = 500
    n = 10
    i = 0.03
    valor_final_renta = R * ((1 + i)**n - 1) / i
    G = (S - valor_final_renta) / (((1 + i)**n - 1) / i - n)
    return round(G, 2)

# Caso 5
def caso_5():
    P = 10000
    G = 100
    n = 12
    i = 0.05
    Pg = valor_presente_gradiente_uniforme(0, G, i, n)
    Pr = P - Pg
    R = Pr * (i * (1 + i)**n) / ((1 + i)**n - 1)
    R_final = R + (G * n)
    return round(R_final, 2)

# Caso 6
def caso_6():
    P = 2000
    R = 50
    G = 20
    n = 10
    i = 0.05
    VPC = R * ((1 + i)**n - 1) / (i * (1 + i)**n)
    VPG = valor_presente_gradiente_uniforme(0, G, i, n)
    costo_mensual = (P + VPC + VPG) * (i * (1 + i)**n) / ((1 + i)**n - 1)
    return round(costo_mensual, 2)

# Caso 7
def caso_7():
    VP = 5000
    cuota_base = 500
    n = 10
    TET = 0.092727
    VP_base = cuota_base * ((1 - (1 + TET)**-n) / TET)
    VP_gradiente = VP - VP_base
    G = VP_gradiente / (((1 - (1 + TET)**-n) / TET**2 - n / (TET * (1 + TET)**n)))
    return round(G, 2)

# Caso 8
def caso_8():
    flujos = [60, 60, 80, 100, 120, 140, 160, 180, 200]
    i = 0.05
    VP = sum(flujo / (1 + i)**(t + 1) for t, flujo in enumerate(flujos))
    n = len(flujos)
    R = VP * (i * (1 + i)**n) / ((1 + i)**n - 1)
    return round(R, 2)

# Caso 9
def caso_9():
    cuota_base = 1000
    gradiente = -50
    n = 20
    TET = 0.1576
    VP_base = cuota_base * ((1 - (1 + TET)**-n) / TET)
    VP_gradiente = valor_presente_gradiente_uniforme(0, gradiente, TET, n)
    return round(VP_base + VP_gradiente, 2)

# Caso 10
def caso_10():
    cuota_base = 500
    incremento = 0.05
    n = 24
    TET = 0.0927
    VP = cuota_base / TET * ((1 + incremento)**n - (1 + TET)**n / incremento - TET)
    return round(VP, 2)

# Ejecución de todos los casos
print("Caso 1:", caso_1())
print("Caso 2:", caso_2())
print("Caso 3:", caso_3())
print("Caso 4:", caso_4())
print("Caso 5:", caso_5())
print("Caso 6:", caso_6())
print("Caso 7:", caso_7())
print("Caso 8:", caso_8())
print("Caso 9:", caso_9())
print("Caso 10:", caso_10())
