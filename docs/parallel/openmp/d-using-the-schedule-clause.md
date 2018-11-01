---
title: D. Usar la cláusula schedule | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d40b22a5e724f8d8b587e2928d3d1305a7fa807a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446149"
---
# <a name="d-using-the-schedule-clause"></a>D. Usar la cláusula schedule

Una región paralela tiene al menos una barrera, en su extremo y puede tener otras barreras adicionales dentro de él. En cada barrera, los demás miembros del equipo deben esperar el último subproceso que llegue. Para reducir este tiempo de espera, se debe distribuir trabajo compartidas para que todos los subprocesos llegan a la barrera en aproximadamente al mismo tiempo. Si algunos de los que compartir el trabajo se encuentra en **para** construcciones, la `schedule` cláusula se puede usar para este propósito.

Cuando hay referencias repetidas en los mismos objetos, la opción de programación para un **para** construcción puede verse determinada principalmente por las características del sistema de memoria, como la presencia y el tamaño de las memorias caché y si el acceso memoria horas son uniformes o no uniforme. Estas consideraciones pueden hacer que sea preferible que cada subproceso sistemáticamente hacen referencia al mismo conjunto de elementos de una matriz en una serie de bucles, incluso si algunos subprocesos se asignan relativamente menos trabajo en algunos de los bucles. Esto puede hacerse mediante el uso de la **estático** programación con los mismos límites para todos los bucles. En el ejemplo siguiente, tenga en cuenta que, aunque se usa cero como límite inferior en el segundo bucle **k** sería más natural si la programación no era importante.

```
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

En el resto de los ejemplos, se supone que la memoria acceso no es la contrapartida dominante y, a menos que se indique lo contrario, que todos los subprocesos reciben recursos de cálculo comparables. En estos casos, la opción de programación para un **para** construcción depende de todo el trabajo compartido que se realiza entre la anterior más cercana barrera y la barrera de cierre implícito o el más cercano de barrera posterior, si no hay un `nowait` cláusula. Para cada tipo de programación, un breve ejemplo muestra cómo es probable que sea la mejor opción ese tipo de programación. Obtener una explicación breve sigue cada ejemplo.

El **estático** también es adecuada para el caso más simple, una región paralela que contiene una sola programación **para** construir con cada iteración que requieren la misma cantidad de trabajo.

```
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

El **estático** programación se caracteriza por las propiedades que cada subproceso obtiene aproximadamente el mismo número de iteraciones que ningún otro subproceso, y cada subproceso puede determinar por separado las iteraciones asignadas a él. Por lo tanto no se requiere ninguna sincronización para distribuir el trabajo y, bajo el supuesto de que cada iteración requiere la misma cantidad de trabajo, deben finalizar todos los subprocesos en aproximadamente al mismo tiempo.

Para un equipo de `p` subprocesos, permiten *ceiling(n/p)* ser el entero *q*, que satisface *n = p\*p - r* con *0 < = r < p* . Una implementación de la **estático** programar para este ejemplo se asignaría *q* iteraciones al primer *p-1* subprocesos, y *p-r* iteraciones para el último subproceso.  Asignaría otra implementación aceptable *q* iteraciones al primer *p-r* subprocesos, y *q-1* iteraciones para el resto *r*subprocesos. Esto ilustra por qué un programa no debe confiar en los detalles de una implementación determinada.

El **dinámica** programación es adecuada para el caso de un **para** construir con las iteraciones que requieren distintos o incluso imprevisibles, volúmenes de trabajo.

```
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

El **dinámica** programación se caracteriza por la propiedad que no hay ningún subproceso espera en la barrera de lleva más de otro subproceso para ejecutar su última iteración. Esto requiere que las iteraciones se asigne una vez a los subprocesos cuando estén disponibles con la sincronización para cada asignación. Se puede reducir la sobrecarga de sincronización especificando un tamaño mínimo del fragmento *k* mayor que 1, para que los subprocesos se asignan *k* a la vez hasta que menos de *k* permanecen. Esto garantiza que ningún subproceso espera en la barrera más larga que el otro subproceso para ejecutar su fragmento final de (a lo sumo) *k* iteraciones.

El **dinámica** programación puede ser útil si los subprocesos de recepción diferentes recursos de cálculo, que tiene el mismo efecto como diferentes cantidades de trabajo para cada iteración. De forma similar, la programación dinámica también puede ser útil si los subprocesos que llegan a la **para** construir en momentos diferentes, aunque en algunos casos el **guiado** programación puede ser preferible.

El **guiado** programación es adecuada para el caso en el que los subprocesos pueden llegar en momentos diferentes en un **para** construir con cada iteración que requieren la misma cantidad de trabajo. Esto puede ocurrir si, por ejemplo, el **para** construcción está precedida por una o más secciones o **para** construye con `nowait` cláusulas.

```
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

Al igual que **dinámica**, el **guiado** programar garantiza que ningún subproceso espera en la barrera más larga que el otro subproceso para ejecutar su última iteración o final *k* las iteraciones que si un tamaño de fragmento de *k* se especifica. Entre estas programaciones, el **guiado** programación se caracteriza por la propiedad que requiere el menor número de sincronizaciones. Para el tamaño del fragmento *k*, asignará una implementación típica *q = ceiling(n/p)* establecer iteraciones para el primer subproceso disponible, *n* en el mayor de *n-q* y *p\*k*y repetir hasta que se asignan todas las iteraciones.

Cuando la opción de la programación óptimo no es tan clara como para estos ejemplos, el **en tiempo de ejecución** programación resulta práctica para experimentar con distintas programaciones y tamaños de fragmento sin tener que modificar y volver a compilar el programa. También puede ser útil cuando el plan óptimo depende (de alguna manera predecible) los datos de entrada al que se aplica el programa.

Para ver un ejemplo de las ventajas y desventajas entre distintas programaciones, considere la posibilidad de compartir las iteraciones de 1000 entre 8 subprocesos. Supongamos que hay una cantidad de trabajo en cada iteración, invariable y usarla como la unidad de tiempo.

Si todos los subprocesos se inician al mismo tiempo, el **estático** programación hará que la construcción ejecutar en 125 unidades, sin sincronización. Pero supongamos que un subproceso es de 100 unidades a finales de que llegan. A continuación, esperan los subprocesos restantes siete por 100 unidades a la barrera y aumenta el tiempo de ejecución para la construcción de todo a 225.

Porque tanto el **dinámica** y **guiado** programaciones garantizar que ningún subproceso espera más de una unidad en la barrera, hace que el subproceso diferido sus tiempos de ejecución para la construcción aumentar sólo a 138 unidades, posiblemente incrementa retrasos de sincronización. Si estos retrasos no son insignificantes, resulta importante que el número de sincronizaciones es 1000 para **dinámica** pero 41 solo para **guiado**, suponiendo que el tamaño del fragmento predeterminado de uno. Con un tamaño de fragmento de 25, **dinámica** y **guiado** ambos finalizan en 150 unidades, además de los retrasos de las sincronizaciones necesarios, número que ahora solo 40 y 20, respectivamente.