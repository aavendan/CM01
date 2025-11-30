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
.. image:: ./archivos/cache.png
    :alt: La caché es la mochila del estudiante
    :width: 100%
    :align: center   


Contenido
=========

¿Qué es la memoria caché?
-------------------------

La memoria caché es una pequeña porción de memoria de alta velocidad que almacena temporalmente datos e instrucciones a los que el procesador accede con frecuencia. Su propósito principal es reducir el tiempo de acceso a los datos y mejorar el rendimiento general del sistema. Al mantener una copia de los datos más utilizados cerca del procesador, la caché minimiza la necesidad de acceder a la memoria principal, que es más lenta.

Tipos de caché
--------------

1. **Caché de nivel 1 (L1)**: Es la caché más rápida y está integrada directamente en el procesador. Suele estar dividida en caché de instrucciones y caché de datos.
2. **Caché de nivel 2 (L2)**: Es más grande que la L1 y puede estar integrada en el procesador o ser una caché separada. Aunque es más lenta que la L1, sigue siendo mucho más rápida que la memoria principal.
3. **Caché de nivel 3 (L3)**: Es compartida entre varios núcleos de procesador y es más grande pero más lenta que la L2. Su función es mejorar la eficiencia del acceso a datos entre los núcleos.

Hit y Miss
----------

¿Cómo acelera la ejecución? 
^^^^^^^^^^^^^^^^^^^^^^^^^^^

¿Qué pasa cuando falla?
^^^^^^^^^^^^^^^^^^^^^^^

Aplicaciones actuales
---------------------

Demostración
============

Mini demostración: mostrar con un código simple (Python/C) cómo cambia el tiempo de acceso por localidad


Bibliografía
============

Provost, G. (2024). What Is Cache and How Does It Work? Retrieved from https://computer.howstuffworks.com/cache.htm
Ruz, J. J. (2012). Estructura de Computadores, Facultad de Informática, UCM. Retrieved from https://www.fdi.ucm.es/profesor/jjruz/web2/temas/ec6.pdf#page=4.18