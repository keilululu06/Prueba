# Prueba

1- obtener el nombre de todos los usuario mayores a 20 años de los siguientes países: España, Francia y Turquía. Cuántos son masculinos y cuántos femeninos, hacer un gráfico con matplotlib 

2- obtener todos los usuarios entre las edades de 45 y 60. Cuántos son masculinos y cuántos femeninos,hacer el gráfico con matplotlib

import pandas as pd
import matplotlib.pyplot as plt

# Cargar el archivo CSV
df = pd.read_csv("users.csv")  # Asegurate de tener el archivo en el mismo directorio o cambiar la ruta

# 1. Usuarios mayores a 20 años de España, Francia y Turquía
paises_objetivo = ['Spain', 'France', 'Turkey']
usuarios_filtrados_1 = df[(df['edad'] > 20) & (df['pais'].isin(paises_objetivo))]

# Obtener nombres
nombres_mayores_20 = usuarios_filtrados_1['nombre'].tolist()

# Contar por género
conteo_genero_1 = usuarios_filtrados_1['genero'].value_counts()

# 2. Usuarios entre 45 y 60 años
usuarios_filtrados_2 = df[(df['edad'] >= 45) & (df['edad'] <= 60)]

# Contar por género
conteo_genero_2 = usuarios_filtrados_2['genero'].value_counts()

# Graficar
fig, axs = plt.subplots(1, 2, figsize=(12, 5))

# Gráfico para mayores de 20 años en España, Francia y Turquía
axs[0].bar(conteo_genero_1.index, conteo_genero_1.values, color=['skyblue', 'lightcoral'])
axs[0].set_title('Mayores de 20 en España, Francia y Turquía')
axs[0].set_xlabel('Género')
axs[0].set_ylabel('Cantidad')

# Gráfico para usuarios entre 45 y 60 años
axs[1].bar(conteo_genero_2.index, conteo_genero_2.values, color=['skyblue', 'lightcoral'])
axs[1].set_title('Usuarios entre 45 y 60 años')
axs[1].set_xlabel('Género')
axs[1].set_ylabel('Cantidad')

plt.tight_layout()
plt.show()
