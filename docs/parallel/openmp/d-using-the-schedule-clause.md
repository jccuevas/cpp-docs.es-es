---
title: D. La cláusula schedule
ms.date: 01/22/2019
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: 89e011784c5cccedc4a75f38d553458ea2e5d7e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362886"
---
# <a name="d-the-schedule-clause"></a>D. La cláusula schedule

Una región paralela tiene al menos una barrera, en su extremo y puede tener otras barreras adicionales dentro de él. En cada barrera, los demás miembros del equipo deben esperar el último subproceso que llegue. Para reducir este tiempo de espera, se debe distribuir trabajo compartidas para que todos los subprocesos llegan a la barrera en aproximadamente al mismo tiempo. Si algunos de los que compartir el trabajo se encuentra en `for` construcciones, la `schedule` cláusula se puede usar para este propósito.

Cuando hay referencias repetidas en los mismos objetos, la opción de programación para un `for` construcción puede verse determinada principalmente por las características del sistema de memoria, como la presencia y el tamaño de las memorias caché y si los tiempos de acceso de memoria son uniformes o nonuniform. Estas consideraciones pueden hacer que sea preferible que cada subproceso sistemáticamente hacen referencia al mismo conjunto de elementos de una matriz en una serie de bucles, incluso si algunos subprocesos se asignan relativamente menos trabajo en algunos de los bucles. Esta configuración puede realizarse mediante el `static` programación con los mismos límites para todos los bucles. En el ejemplo siguiente, se usa cero como límite inferior en el segundo bucle, aunque `k` sería más natural si la programación no era importante.

```cpp
#pragma omp parallel
{
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    a[i] = work1(i);
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    if(i>=k) a[i] += work2(i);
}
```

En el resto de los ejemplos, se da por supuesto que la memoria acceso no es la principal consideración. A menos que se indique lo contrario, que todos los subprocesos reciben recursos de cálculo comparables. En estos casos, la opción de programación para un `for` construcción depende de todo el trabajo compartido que se realiza entre la anterior más cercana barrera y la barrera de cierre implícito o el más cercano de barrera próximas, si hay un `nowait` cláusula. Para cada tipo de programación, un breve ejemplo muestra cómo es probable que sea la mejor opción ese tipo de programación. Obtener una explicación breve sigue cada ejemplo.

El `static` también es adecuada para el caso más simple, una región paralela que contiene una sola programación `for` construir con cada iteración que requieren la misma cantidad de trabajo.

```cpp
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

El `static` programación se caracteriza por las propiedades que cada subproceso obtiene aproximadamente el mismo número de iteraciones que ningún otro subproceso, y cada subproceso puede determinar por separado las iteraciones asignadas a él. Por lo tanto no se requiere ninguna sincronización para distribuir el trabajo y, bajo el supuesto de que cada iteración requiere la misma cantidad de trabajo, deben finalizar todos los subprocesos en aproximadamente al mismo tiempo.

Para un equipo de *p* subprocesos, permiten *ceiling(n/p)* ser el entero *q*, que satisface *n = p\*p - r* con *0 < = r < p*. Una implementación de la `static` programar para este ejemplo se asignaría *q* iteraciones al primer *p-1* subprocesos, y *p-r* iteraciones para el último subproceso.  Asignaría otra implementación aceptable *q* iteraciones al primer *p-r* subprocesos, y *q-1* iteraciones para el resto *r*subprocesos. En este ejemplo se ilustra por qué un programa no debe confiar en los detalles de una implementación determinada.

El `dynamic` programación es adecuada para el caso de un `for` construir con las iteraciones que requieren distintos o incluso imprevisibles, volúmenes de trabajo.

```cpp
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

El `dynamic` programación se caracteriza por la propiedad que no hay ningún subproceso espera en la barrera de lleva más de otro subproceso para ejecutar su última iteración. Este requisito significa iteraciones deben asignarse una vez a subprocesos conforme estén disponibles con la sincronización para cada asignación. Se puede reducir la sobrecarga de sincronización especificando un tamaño mínimo del fragmento *k* mayor que 1, para que los subprocesos se asignan *k* a la vez hasta que menos de *k* permanecen. Esto garantiza que ningún subproceso espera en la barrera más larga que el otro subproceso para ejecutar su fragmento final de (a lo sumo) *k* iteraciones.

El `dynamic` programación puede ser útil si los subprocesos de recepción diferentes recursos de cálculo, que tiene el mismo efecto como diferentes cantidades de trabajo para cada iteración. De forma similar, la programación dinámica también puede ser útil si los subprocesos que llegan a la `for` construir en momentos diferentes, aunque en algunos casos el `guided` programación puede ser preferible.

El `guided` programación es adecuada para el caso en el que los subprocesos pueden llegar en momentos diferentes en un `for` construir con cada iteración que requieren la misma cantidad de trabajo. Esta situación puede ocurrir si, por ejemplo, el `for` construcción está precedida por una o más secciones o `for` construye con `nowait` cláusulas.

```cpp
#pragma omp parallel
{
  #pragma omp sections nowait
  {
    // ...
  }
  #pragma omp for schedule(guided)
  for(i=0; i<n; i++) {
    invariant_amount_of_work(i);
  }
}
```

Al igual que `dynamic`, el `guided` programar garantiza que ningún subproceso espera en la barrera más larga que el otro subproceso para ejecutar su última iteración o final *k* iteraciones si un tamaño de fragmento de *k* se especifica. Entre estas programaciones, la `guided` programación se caracteriza por la propiedad que requiere el menor número de sincronizaciones. Para el tamaño del fragmento *k*, asignará una implementación típica *q = ceiling(n/p)* establecer iteraciones para el primer subproceso disponible, *n* en el mayor de *n-q* y *p\*k*y repetir hasta que se asignan todas las iteraciones.

Cuando no es tan clara como para estos ejemplos, la elección de la programación óptima el `runtime` programación resulta práctica para experimentar con distintas programaciones y tamaños de fragmento sin tener que modificar y volver a compilar el programa. También puede ser útil cuando el plan óptimo depende (de alguna manera predecible) los datos de entrada al que se aplica el programa.

Para ver un ejemplo de las ventajas y desventajas entre distintas programaciones, considere la posibilidad de compartir las iteraciones de 1000 entre ocho subprocesos. Supongamos que hay una cantidad de trabajo en cada iteración, invariable y usarla como la unidad de tiempo.

Si todos los subprocesos se inician al mismo tiempo, el `static` programación hará que la construcción ejecutar en 125 unidades, sin sincronización. Pero supongamos que un subproceso es de 100 unidades a finales de que llegan. A continuación, esperan los subprocesos restantes siete por 100 unidades a la barrera y aumenta el tiempo de ejecución para la construcción de todo a 225.

Dado que tanto el `dynamic` y `guided` programaciones Asegúrese de que ningún subproceso espera más de una unidad en la barrera, hace que el subproceso diferido sus tiempos de ejecución para la construcción aumentar solo a 138 unidades, posiblemente incrementa retrasos de sincronización. Si estos retrasos no están insignificantes, resulta importante que el número de sincronizaciones es 1000 para `dynamic` pero 41 solo para `guided`, suponiendo que el tamaño del fragmento predeterminado de uno. Con un tamaño de fragmento de 25, `dynamic` y `guided` ambos finalizan en 150 unidades, además de los retrasos de las sincronizaciones necesarios, número que ahora solo 40 y 20, respectivamente.
