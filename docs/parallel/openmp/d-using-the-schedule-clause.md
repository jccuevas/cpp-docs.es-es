---
title: "D. Mediante la cláusula de programación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b51eeb36a4cffafde0e90586fec08d28b9672e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="d-using-the-schedule-clause"></a>D. Mediante la cláusula de programación
Una región paralela tiene al menos una barrera, en su extremo y puede incluir otras barreras adicionales dentro de él. En cada barrera, los demás miembros del equipo deben esperar el último subproceso a que llegue. Para minimizar este tiempo de espera, se debe distribuir trabajo compartidas para que todos los subprocesos llegan a la barrera en aproximadamente al mismo tiempo. Si algunos de los que comparten el trabajo se encuentra en **para** construye, la `schedule` cláusula se puede usar para este propósito.  
  
 Cuando hay referencias repetidas a los mismos objetos, la opción de programación para un **para** construcción puede verse determinada principalmente por las características del sistema de memoria, como la presencia y el tamaño de las cachés y si el acceso memoria horas son uniforme o no uniforme. Consideraciones acerca de este tipo puede hacer que sea preferible que cada subproceso constantemente hacen referencia al mismo conjunto de elementos de una matriz en una serie de bucles, incluso si algunos subprocesos se asignan relativamente menos trabajo de algunos de los bucles. Esto puede hacerse mediante el uso de la **estático** programación con los mismos límites para todos los bucles. En el ejemplo siguiente, tenga en cuenta que se usa cero como límite inferior en el segundo bucle, aunque **k** sería más natural si la programación no eran importante.  
  
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
  
 En el resto de los ejemplos, se supone que la memoria acceso no es la consideración dominante y, a menos que se indique lo contrario, que todos los subprocesos reciban recursos de cálculo comparables. En estos casos, la opción de programación para un **para** construcción depende de todo el trabajo compartido que se realiza entre la anterior más cercana barrera y la barrera de cierre implícito o el más cercano de barrera posterior, si no existe un `nowait` cláusula. Para cada tipo de programación, un pequeño ejemplo muestra cómo es probable que sea la mejor opción ese tipo de programación. Obtener una breve descripción sigue cada ejemplo.  
  
 El **estático** programación también es adecuada para el caso más simple, una región paralela que contiene un solo **para** construir, con cada repetición requiere que la misma cantidad de trabajo.  
  
```  
#pragma omp parallel for schedule(static)  
for(i=0; i<n; i++) {  
  invariant_amount_of_work(i);  
}  
```  
  
 El **estático** programación se caracteriza por las propiedades que cada subproceso obtiene aproximadamente el mismo número de iteraciones que ningún otro subproceso, y cada subproceso puede determinar por separado las iteraciones que se asignan a él. Por lo tanto no se requiere ninguna sincronización para distribuir el trabajo y, en la suposición de que cada iteración requiere la misma cantidad de trabajo, todos los subprocesos deben finalizar en aproximadamente al mismo tiempo.  
  
 Para un equipo de `p` subprocesos, permiten *ceiling(n/p)* ser el entero *preguntas*, que satisface *n = p\*q - r* con *0 < = r < p* . Una implementación de la **estático** programar para este ejemplo asignaría *preguntas* iteraciones al primer *p-1* subprocesos, y *q-r* iteraciones para el último subproceso.  Otra implementación aceptable asignaría *preguntas* iteraciones al primer *p-r* subprocesos, y *q-1* iteraciones hasta alcanzar el resto *r*subprocesos. Esto se ilustra por qué un programa no debe confiar en los detalles de una implementación determinada.  
  
 El **dinámica** programación es adecuada para el caso de un **para** construir con las iteraciones que requieren diferentes o incluso impredecibles, volúmenes de trabajo.  
  
```  
#pragma omp parallel for schedule(dynamic)  
  for(i=0; i<n; i++) {  
    unpredictable_amount_of_work(i);  
}  
```  
  
 El **dinámica** programación se caracteriza por la propiedad que no hay ningún subproceso espera en la barrera tarda más de otro subproceso para ejecutar su última iteración. Esto requiere que iteraciones asignarse uno a la vez a los subprocesos cuando estén disponibles, con la sincronización para cada asignación. Se puede reducir la sobrecarga de sincronización mediante la especificación de un tamaño de fragmento mínimo *k* mayor que 1, para que los subprocesos se asignan *k* en uno hasta que menos de *k* permanecen. Esto garantiza que ningún subproceso espera en la barrera más tiempo del necesario otro subproceso para ejecutar el último fragmento de (como máximo) *k* iteraciones.  
  
 El **dinámica** programación puede ser útil si los subprocesos de recepción diferentes recursos de cálculo, que tiene el mismo efecto como distintas cantidades de trabajo para cada iteración. De forma similar, la programación dinámica también puede ser útil si los subprocesos llegan a la **para** construir en momentos diferentes, aunque en algunos de estos casos la **interactiva** programación puede ser preferible.  
  
 El **interactiva** programación es adecuada para el caso en el que los subprocesos pueden llegar en momentos diferentes en un **para** construir con cada iteración que requieren aproximadamente la misma cantidad de trabajo. Esto puede ocurrir si, por ejemplo, el **para** construcción está precedida por una o varias secciones o **para** construye con `nowait` cláusulas.  
  
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
  
 Al igual que **dinámica**, **interactiva** programar garantiza que ningún subproceso espera en la barrera más tiempo del necesario otro subproceso para ejecutar su última iteración, o final *k* iteraciones si un tamaño de fragmento de *k* se especifica. Entre estas programaciones, el **interactiva** programación se caracteriza por la propiedad que requiere la menor cantidad sincronizaciones. Para el tamaño del fragmento *k*, asignará una implementación típica *q = ceiling(n/p)* establecer iteraciones para el primer subproceso disponible,  *n*  en el mayor de *n-q* y *p\*k*y repita hasta que se asignan todas las iteraciones.  
  
 Cuando la opción de la programación óptima no es tan sencilla como para estos ejemplos, el **en tiempo de ejecución** programación resulta útil para experimentar con distintas programaciones y tamaños de fragmento sin tener que modificar y volver a compilar el programa. También puede ser útil cuando el plan óptimo depende (de alguna manera predecible) los datos de entrada a la que se aplica el programa.  
  
 Para ver un ejemplo de las ventajas y desventajas entre distintas programaciones, considere la posibilidad de uso compartido de 1000 iteraciones entre 8 subprocesos. Suponga que hay una cantidad de trabajo en cada iteración, invariable y usarla como la unidad de tiempo.  
  
 Si todos los subprocesos que se inician al mismo tiempo, el **estático** programación hará que la construcción ejecutar en unidades de 125, sin sincronización. Sin embargo, supongamos que un subproceso es 100 unidades de tiempo de ejecución en que llegan. Esperan a que los subprocesos de siete restantes 100 unidades en la barrera y aumenta el tiempo de ejecución para la construcción de todo a 225.  
  
 Dado que tanto el **dinámica** y **interactiva** programaciones garantizar que ningún subproceso espera más de una unidad que aparece en la barrera, el subproceso diferido hace que el tiempo de ejecución para la construcción aumentar únicamente a 138 unidades, posiblemente aumentados por los retrasos de sincronización. Si estos retrasos no son insignificantes, resulta importante que el número de sincronizaciones es 1000 por **dinámica** pero 41 solo para **interactiva**, suponiendo que el tamaño del fragmento predeterminado de uno. Con un tamaño de fragmento de 25, **dinámica** y **interactiva** ambos finalización en 150 unidades, además de los retrasos de las sincronizaciones necesarios, qué número ahora solo 40 y 20, respectivamente.