# Terminar_juego
import random

def jugar_juego():
    print("Bienvenido al juego de adivinanza de números.")
    nivel = int(input("Elige un nivel (1-4): "))
    
    if nivel == 1:
        rango = (1, 100)
        intentos_maximos = 10
    elif nivel == 2:
        rango = (1, 1000)
        intentos_maximos = 20
    elif nivel == 3:
        rango = (1, 1000000)
        intentos_maximos = 30
    elif nivel == 4:
        rango = (1, 1000000000000)
        intentos_maximos = 40
    else:
        print("Nivel no válido. Elige un nivel del 1 al 4.")
        return

    numero_secreto = random.randint(rango[0], rango[1])
    intentos_realizados = 0

    while intentos_realizados < intentos_maximos:
        intento_usuario = int(input(f"Intento {intentos_realizados + 1}. Adivina el número: "))

        if intento_usuario == numero_secreto:
            print(f"¡Felicidades! ¡Adivinaste el número {numero_secreto} en {intentos_realizados + 1} intentos!")
            nombre_jugador = input("Introduce tu nombre: ")
            mostrar_tabla_ganadores(nombre_jugador, intentos_realizados + 1)
            break
        elif intento_usuario < numero_secreto:
            print("El número es mayor. Intenta de nuevo.")
        else:
            print("El número es menor. Intenta de nuevo.")

        intentos_realizados += 1

    if intentos_realizados == intentos_maximos:
        print(f"Lo siento, has agotado tus {intentos_maximos} intentos. El número secreto era {numero_secreto}.")

def mostrar_tabla_ganadores(name, intentos):
    print("\nTabla de Ganadores:")
    print(f"{name}: {intentos} intentos")

if __name__ == "_main_":
    jugar_juego()
