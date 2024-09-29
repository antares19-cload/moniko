# Simulador De Maquina De Galton

# generar números enteros aleatorios
import random
# para trazar gráficos
import matplotlib.pyplot as plt
# biblioteca NumPy para trabajar con arreglos numéricos
import numpy as np

# Función para simular la máquina de Galton
def simular_canica(niveles):
    """ Simula el recorrido de una canica a través de la máquina de Galton.
    :param niveles: Número de niveles de obstáculos
    :return: Posición final de la canica
    """
    # Crea una lista para contar las canicas en cada contenedor
    posicion = 0
    # simular la caída en los niveles
    for _ in range(niveles):
        # Decidir si va a la izquierda (-1) o a la derecha (+1)
        posicion += random.choice([-1, 1])
    return posicion

def crear_histograma(resultados):
    """Crea y muestra un histograma de los resultados.:para resultados: Lista de posiciones finales de las canicas"""
    plt.figure(figsize=(10, 6))
    n, bins, patches = plt.hist(resultados, bins=range(min(resultados), max(resultados) + 2, 1), 
             align='left', rwidth=0.8)
    plt.title('Histogra Máquina de Galton')
    plt.xlabel('Distribución canicas')
    plt.ylabel('Cantidad canicas')
    plt.xticks(range(min(resultados), max(resultados) + 1))
    max_y = int(np.ceil(max(n) / 100) * 100)
    plt.yticks(range(0, max_y + 100, 100))
    plt.grid(True, alpha= 0.9)
    plt.show()

if __name__ == "__main__":
    num_canicas = 3000
    niveles = 12
    # Simular las canicas
    resultados = [simular_canica(niveles) for _ in range(num_canicas)]
    # Crear mostrar histograma
    crear_histograma(resultados)
