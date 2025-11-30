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

Escenarios de uso de la memoria caché
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. raw:: html

    <div style="width: 100%;"><div style="position: relative; padding-bottom: 56.25%; padding-top: 0; height: 0;"><iframe title="Memoria Caché" frameborder="0" width="1200" height="675" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://view.genially.com/692c85b7bea51fb65277fde8" type="text/html" allowscriptaccess="always" allowfullscreen="true" scrolling="yes" allownetworking="all"></iframe> </div> </div>

Tipos de caché de CPU
^^^^^^^^^^^^^^^^^^^^^

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
GeeksforGeeks. (2025). Types of Cache. Retrieved from https://www-geeksforgeeks-org.translate.goog/system-design/types-of-cache/
Ros, por I. (2024). Memoria caché: qué es y qué diferencias hay entre los tipos L1, L2, L3 y L4. Retrieved from https://www.muycomputer.com/2024/07/03/memoria-cache-que-es-y-que-diferencias-hay-entre-los-tipos-l1-l2-y-l3/