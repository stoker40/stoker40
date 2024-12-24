import os
import time
import random

def limpiar_pantalla():
    os.system('cls' if os.name == 'nt' else 'clear')

def generar_nieve(ancho, alto):
    return [[' ' if random.random() > 0.1 else '*' for _ in range(ancho)] for _ in range(alto)]

def dibujar_arbol(alto):
    arbol = []
    # Estrella
    arbol.append("    ★    ")
    # Niveles del árbol
    for i in range(alto):
        espacios = " " * (alto - i - 1)
        ramas = "*" * (2 * i + 1)
        arbol.append(espacios + ramas)
    # Tronco
    arbol.append("    |||    ")
    return arbol

def mostrar_mensaje():
    mensaje = """
    🎄 ¡Feliz Navidad! 🎄
    🎅 Ho Ho Ho 🎅
    """
    return mensaje

def animar_navidad():
    alto_arbol = 5
    ancho_pantalla = 40
    alto_pantalla = 20
    
    while True:
        try:
            limpiar_pantalla()
            nieve = generar_nieve(ancho_pantalla, 3)  # Nieve en la parte superior
            arbol = dibujar_arbol(alto_arbol)
            
            # Mostrar nieve superior
            for fila in nieve:
                print(''.join(fila))
            
            # Mostrar árbol
            for linea in arbol:
                print(linea.center(ancho_pantalla))
                
            # Mostrar mensaje
            print(mostrar_mensaje().center(ancho_pantalla))
            
            time.sleep(0.5)
        except KeyboardInterrupt:
            break

if __name__ == "__main__":
    print("¡Presiona Ctrl+C para detener la animación!")
    animar_navidad()
