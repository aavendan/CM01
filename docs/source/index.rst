..
   Copyright (c) 2025 Allan Avendaño Sudario
   Licensed under Creative Commons Attribution-ShareAlike 4.0 International License
   SPDX-License-Identifier: CC-BY-SA-4.0

=============
Memoria Caché
=============

.. topic:: Objetivo específico
    :class: objetivo

    Comprender el funcionamiento de la memoria caché en sistemas computacionales, incluyendo su estructura, tipos y estrategias de gestión, para la optimización del rendimiento en el acceso a datos.

Introducción
============

.. centered:: ¿Qué criterios usamos para elegir los objetos que llevamos en nuestra mochila, cartera o bolso?

.. image:: ./archivos/maleta.png
    :alt: La caché es la mochila del estudiante
    :width: 75%
    :align: center   


Contenido
=========

¿Qué es la memoria caché?
-------------------------

Es una porción de memoria de alta velocidad que almacena temporalmente datos e instrucciones a los que el procesador (CPU) accede con frecuencia. 

Niveles de caché de CPU
^^^^^^^^^^^^^^^^^^^^^^^

Hit y Miss
----------

¿Cómo acelera la ejecución? 
^^^^^^^^^^^^^^^^^^^^^^^^^^^

¿Qué pasa cuando falla?
^^^^^^^^^^^^^^^^^^^^^^^

Aplicaciones actuales
---------------------

.. raw:: html

    <div style="width: 100%;"> hello </div>

Demostración
============

En el siguiente ejemplo, mediremos el tiempo de acceso a cada uno de los elementos de un arreglo grande (N=10,000,000) de enteros.

.. code-block:: python3

    import time
    import numpy as np
    import matplotlib.pyplot as plt 

    N = 10_000_000
    a = np.zeros(N, dtype=np.int32)

Alta localidad y baja localidad
-------------------------------

Mediremos el tiempo que tarda en acceder a cada uno de los elementos del arreglo. En el primer caso, accederemos secuencialmente (alta localidad) con la función `sequential_access`, y en el segundo caso, accederemos de manera aleatoria (baja localidad) con la función `random_access`.

.. code-block:: python3

    # Acceso secuencial (alta localidad)
    def sequential_access():

        start = time.time()
        s = 0
        for i in range(N):
            s += a[i]
        end = time.time()
        
        return end - start

    # Acceso aleatorio (baja localidad)
    def random_access():

        indices = np.random.randint(0, N, N)
        start = time.time()
        s = 0
        for i in indices:
            s += a[i]
        end = time.time()
        
        return end - start

Pruebas y resultados
--------------------

Tomaremos 10 mediciones para cada tipo de acceso y graficaremos los resultados en un diagrama de cajas.

.. code-block:: python3

    # Número de muestras
    samples = 10
    
    # Medición de tiempos de acceso secuencial
    seq_times = [sequential_access() for _ in range(samples)]
    rand_times = [random_access() for _ in range(samples)]

    # Graficar resultados
    plt.boxplot([seq_times, rand_times], labels=['Secuencial', 'Aleatorio'])
    plt.ylabel('Tiempo de acceso (segundos)')
    plt.title('Comparación de tiempos de acceso a memoria')
    plt.show()

.. image:: ./archivos/comparacion.png
    :alt: Comparación de tiempos de acceso a memoria
    :width: 75%
    :align: center      

Conclusiones
------------

- La memoria caché mejora significativamente el rendimiento del acceso a datos cuando hay alta localidad.
- Los accesos aleatorios resultan en más fallos de caché, lo que ralentiza la ejecución.
- La optimización del acceso a datos es crucial para el rendimiento de las aplicaciones.

Bibliografía
============

* Provost, G. (2024). What Is Cache and How Does It Work? Retrieved from https://computer.howstuffworks.com/cache.htm
* Ruz, J. J. (2012). Estructura de Computadores, Facultad de Informática, UCM. Retrieved from https://www.fdi.ucm.es/profesor/jjruz/web2/temas/ec6.pdf#page=4.18
* GeeksforGeeks. (2025). Types of Cache. Retrieved from https://www-geeksforgeeks-org.translate.goog/system-design/types-of-cache/
* Ros, por I. (2024). Memoria caché: qué es y qué diferencias hay entre los tipos L1, L2, L3 y L4. Retrieved from https://www.muycomputer.com/2024/07/03/memoria-cache-que-es-y-que-diferencias-hay-entre-los-tipos-l1-l2-y-l3/