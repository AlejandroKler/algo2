---
layout: page
title: Pila
permalink: /tps/pila
---

Pila
=======

Para el viernes 8 de septiembre tienen que entregar una implementación de pila dinámica (es decir que pueda crecer o reducirse según la cantidad de elementos) que contenga punteros genéricos (`void*`).

En el archivo [pila.zip](https://sites.google.com/site/fiuba7541rw/tps/pila/pila.zip?attredirects=0&d=1) encontrarán el archivo `pila.h` que tienen que utilizar.  En este archivo están definidas las primitivas que tendrán que implementar, con su correspondiente documentación. Todas las primitivas tienen que funcionar en _tiempo constante_.

Hay que escribir el archivo `pila.c`, con la implementación de la estructura de la pila y de cada una de las primitivas incluidas en el encabezado.  Además de las primitivas, pueden tener funciones auxiliares, de uso interno, que no hace falta que estén declaradas dentro de pila.h. En pila.h se encuentran únicamente las primitivas que el usuario de la pila tiene que conocer.

En el archivo pila.c ya se les sugiere la siguiente estructura para la pila:

``` cpp
struct pila {
    void** datos;
    size_t cantidad;  // Cantidad de elementos almacenados.
    size_t capacidad;  // Capacidad del arreglo 'datos'.
};
```

Además de `pila.c`, tienen que entregar otro archivo `pruebas_alumno.c`, que contenga las pruebas unitarias para verificar que la pila funciona correctamente, y que al ejecutarlo puede verificarse que todo funciona bien y no se pierde memoria. El archivo `pruebas_alumno.c` debe contener una función llamada `pruebas_pila_alumno()` que ejecute todas las pruebas. Se permite (y recomienda) usar funciones auxiliares.

Las pruebas deberán verificar que:
1. Se pueda crear y destruir correctamente la estructura.
1. Se puedan apilar elementos, que al desapilarlos se mantenga el invariante de pila.
1. La redimensión funcione correctamente: hacer crecer la pila hasta un valor sabido mayor que el tamaño inicial, y desapilar elementos hasta que esté vacía, comprobando que siempre cumpla el invariante.
1. El apilamiento del elemento NULL es válido.
1. Condición de borde: comprobar que al desapilar hasta que está vacía hace que la pila se comporte como recién creada.
1. Condición de borde: las acciones de desapilar y ver_tope en una pila recién creada son inválidas.
1. Condición de borde: la acción de esta_vacía en una pila recién creada es verdadero.
1. Condición de borde: las acciones de desapilar y ver_tope en una pila a la que se le apiló y desapiló hasta estar vacía son inválidas.

Además de todos los casos no descriptos que ustedes crean necesarios.

Para compilar y verificar las pruebas:
1. Compilar todo el código:

        gcc -g -std=c99 -Wall -Wconversion -Wno-sign-conversion -Werror -o pruebas *.c

1. Verificar que no pierden memoria:

        valgrind --leak-check=full --track-origins=yes --show-reachable=yes ./pruebas
    
Al igual que en los casos anteriores, deberán entregar el código en papel, con el nombre y padrón, imprimiendo el archivo `pila.c` y el archivo `pruebas_alumno.c`.
Además, deben subir el código a la [página de entregas de la materia](https://algoritmos7541-rw.tk/entregas/), con el código completo.
