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
    :width: 50%
    :align: center   


Contenido
=========

¿Qué es la memoria caché?
-------------------------

Es una porción de memoria de alta velocidad que almacena temporalmente datos e instrucciones a los que el procesador (CPU) accede con frecuencia. Al tener estos datos cerca, la CPU puede acceder a ellos más rápidamente que si tuviera que recuperarlos de la memoria principal (RAM) o del almacenamiento secundario (disco duro o SSD).

.. centered:: ¿Cuál es el criterio para almacenar cerca un dato o una instrucción?

Principio de localidad
----------------------

Los programas tienden a acceder a los datos y las instrucciones en la memoria siguiendo una regla empírica `90% del tiempo de ejecución utiliza sólo el 10% de su código`. Por lo tanto, un programa accede a un elemento:

.. grid:: 2

    .. grid-item-card::  Localidad temporal 

        Es probable que vuelva a acceder a ese **mismo elemento**.
        +++
        Reutilización de datos en un corto período de tiempo.

    .. grid-item-card::  Localidad espacial

        Es probable que acceda a los **elementos cercanos**.
        +++
        Acceso a datos cercanos en la memoria.

Funcionamiento de la caché
--------------------------

.. raw:: html

    <a href="https://www.researchgate.net/figure/Flowchart-of-a-memory-request-showing-cache-hit-and-miss_fig2_373822770"><img src="https://www.researchgate.net/profile/Paul-Bilokon/publication/373822770/figure/fig2/AS:11431281187754656@1694402192962/Flowchart-of-a-memory-request-showing-cache-hit-and-miss.ppm" alt="Flowchart of a memory request showing cache hit and miss."/></a>
    Figure 2: Flowchart of a memory request showing cache hit and miss.

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
    :width: 50%
    :align: center      

Conclusiones
------------

- La memoria caché mejora significativamente el rendimiento del acceso a datos cuando hay alta localidad.
- Los accesos aleatorios resultan en más fallos de caché, lo que ralentiza la ejecución.
- La optimización del acceso a datos es crucial para el rendimiento de las aplicaciones.

Referencias
===========

* Provost, G. (2024). What Is Cache and How Does It Work? Retrieved from https://computer.howstuffworks.com/cache.htm
* Ruz, J. J. (2012). Estructura de Computadores, Facultad de Informática, UCM. Retrieved from https://www.fdi.ucm.es/profesor/jjruz/web2/temas/ec6.pdf#page=4.18
* GeeksforGeeks. (2025). Types of Cache. Retrieved from https://www-geeksforgeeks-org.translate.goog/system-design/types-of-cache/
* Ros, por I. (2024). Memoria caché: qué es y qué diferencias hay entre los tipos L1, L2, L3 y L4. Retrieved from https://www.muycomputer.com/2024/07/03/memoria-cache-que-es-y-que-diferencias-hay-entre-los-tipos-l1-l2-y-l3/
* Castillo, J. A. (2022). Qué es la memoria caché L1, L2 y L3 y cómo funciona. Retrieved from https://www.profesionalreview.com/2019/05/02/memoria-cache-l1-l2-y-l3/
* C++ Design Patterns for Low-latency Applications Including High-frequency Trading - Scientific Figure on ResearchGate. Available from: https://www.researchgate.net/figure/Flowchart-of-a-memory-request-showing-cache-hit-and-miss_fig2_373822770 [accessed 1 Dec 2025]