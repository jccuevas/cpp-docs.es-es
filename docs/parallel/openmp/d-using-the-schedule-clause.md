---
title: "D. Using the schedule Clause | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# D. Using the schedule Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una región paralela tiene por lo menos una barrera, en su fin, y puede tener barreras adicionales dentro de ella.  En cada barrera, los otros miembros del equipo deben esperar el último subproceso para proteger.  Para minimizar este tiempo de espera, el trabajo compartido debe ser enrutado de modo que todos los subprocesos disminuyen la barrera casi al mismo tiempo.  Si algunos de que el trabajo compartido se contiene en las construcciones de **Para** , la cláusula de `schedule` se puede usar con este fin.  
  
 Cuando hay referencias repetidas a los mismos objetos, la opción de programación para una construcción de **Para** se puede determinar principalmente por las características del sistema de memoria, como la presencia y el tamaño de cachés y si los tiempos de acceso de memoria son uniformes o no uniforme.  Estas consideraciones pueden hacerlo preferible hacer que cada subproceso constantemente hace referencia al mismo conjunto de elementos de una matriz en una serie de bucles, aunque algunos subprocesos se asignan relativamente menos trabajo en algunos de los bucles.  Puede hacerlo con la programación de **Estática** con los mismos límites para todos los bucles.  En el ejemplo siguiente, observe que cero se utiliza como límite inferior en el segundo bucle, aunque **k** sería más natural si la programación no era importante.  
  
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
  
 En los ejemplos restantes, se supone que el acceso a la memoria no es la consideración clave, y, a menos que se indique lo contrario, que todos los subprocesos reciben los recursos de computación comparables.  En estos casos, la opción de programación para una construcción de **Para** depende de todo el trabajo compartido que debe realizarse entre la barrera anterior más próxima y la barrera cerrada implícitamente o la barrera subsiguiente más cercana, si hay una cláusula de `nowait` .  Para cada clase de programación, un ejemplo corto muestra cómo esa clase de programación es probable que sea la mejor opción.  Una descripción breve sigue cada ejemplo.  
  
 Programación de **Estática** también es adecuada para el caso más simple, una región paralela que contiene una única construcción de **Para** , con cada iteración y la misma cantidad de trabajo.  
  
```  
#pragma omp parallel for schedule(static)  
for(i=0; i<n; i++) {  
  invariant_amount_of_work(i);  
}  
```  
  
 Programación de **Estática** se caracteriza por las propiedades que cada subproceso obtiene aproximadamente el mismo número de iteraciones que otro subproceso, y cada subproceso puede determinar si las iteraciones asignada al.  Así no se requiere ninguna sincronización para distribuir el trabajo, y, suponiendo que cada iteración requiere la misma cantidad de trabajo, todos los subprocesos deben finalizar casi al mismo tiempo.  
  
 Para un equipo de subprocesos de `p` , deje *el múltiplo superior \(n\/p\)* sea *q*entera, que satisface *n \= el p\*q \- r* con *0 p de r \< de \<\=.* Una implementación de la programación de **Estática** para este ejemplo asignar iteraciones *de q* a los primeros subprocesos *p\-1* , e iteraciones *de q\-r* el último subproceso.  Otra implementación aceptable asignar iteraciones *de q* a los primeros subprocesos *de banda* , y las iteraciones *q\-1* a los subprocesos restantes *de r* .  Esto se muestra por qué un programa no debe depender de los detalles de una implementación concreta.  
  
 Programación de **dinámico** es adecuada para el caso de una construcción de **Para** con las iteraciones que requieren la variación, o incluso imprevisible, cantidades de trabajo.  
  
```  
#pragma omp parallel for schedule(dynamic)  
  for(i=0; i<n; i++) {  
    unpredictable_amount_of_work(i);  
}  
```  
  
 Programación de **dinámico** se caracteriza por la propiedad que ningún subproceso espera en la barrera más tiempo que tiene otro subproceso para ejecutar la iteración final.  Esto requiere que las iteraciones están asignadas de uno en uno a los subprocesos cuando están disponibles, con la sincronización para cada asignación.  La sobrecarga de sincronización puede reducirse especificando *una k* de tamaño del fragmento de mínimo mayor que 1, para asignar subprocesos *k* al mismo tiempo hasta que permanecen menos que *k* .  Esto garantiza que ningún subproceso espera en la barrera más tiempo que tiene otro subproceso para ejecutar la parte final \(como máximo\) de las iteraciones *de k* .  
  
 Programación de **dinámico** puede ser útil si los subprocesos reciben los recursos de computación diferentes, que tiene mucho el mismo efecto que cargas de trabajo diferentes para cada iteración.  De igual forma, la programación dinámica también puede resultar útil si los subprocesos son la construcción de **Para** las horas diferentes, aunque en algunos de estos casos en que la programación de **dirigido** puede ser preferible.  
  
 Programación de **dirigido** es adecuada para el caso en el que los subprocesos pueden proteger las horas diferentes una construcción de **Para** con cada iteración que requiere una cantidad de trabajo casi igual.  Esto puede suceder, por ejemplo, la construcción de **Para** va precedida por una o más secciones o construcciones de **Para** con cláusulas de `nowait` .  
  
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
  
 Como **dinámico**, la programación de **dirigido** garantiza que ningún subproceso espera en la barrera más tiempo que tiene otro subproceso para ejecutar la iteración final, o las iteraciones finales *de k* si un tamaño de fragmento *de k* se especifica.  Entre estas programaciones, la programación de **dirigido** se caracteriza por la propiedad que requiere la menor de las sincronizaciones.  Para *k*de tamaño de fragmentos, una implementación típica asignar *q \= el múltiplo superior \(n\/p\)* las iteraciones al primer subproceso disponible, establecen *n* el mayor *de n\-q* y *de p\*k*, y repetición hasta que se asignan todas las iteraciones.  
  
 Cuando la opción de programación óptima no está tan clara tal cual para estos ejemplos, la programación de **Motor en tiempo de ejecución** es adecuado para experimentar con distintos programaciones y tamaños de fragmento sin tener que modificar y volver a compilar el programa.  También puede resultar útil cuando la programación óptima depende \(de alguna manera confiable\) de los datos de entrada a los que se aplica el programa.  
  
 Para ver un ejemplo de las compensaciones entre distintas programaciones, considere compartir 1000 iteraciones entre 8 subprocesos.  Suponga que hay una cantidad de trabajo invariable en cada iteración, y el uso de como unidad de tiempo.  
  
 Si todos los subprocesos se inician al mismo tiempo, la programación de **Estática** realizará la construcción para ejecutarse en 125 unidades, sin la sincronización.  Pero suponga que un subproceso es 100 unidades tarde de llegada.  A continuación restantes los siete subprocesos esperan 100 unidades en la barrera, y el tiempo de ejecución para la construcción de conjunto aumenta en 225.  
  
 Dado que las programaciones de **dinámico** y de **dirigido** garantizan que ningún subproceso espere más de una unidad de la barrera, el subproceso retrasada hace que sus tiempos de ejecución que la construcción aumenta sólo a 138 unidades, más posiblemente retrasos de sincronización.  Si tales retrasos no son significativos, se vuelve importante que el número de sincronizaciones es 1000 para **dinámico** pero solo 41 para **dirigido**, suponiendo que el tamaño predeterminado del fragmento de uno.  Con un tamaño de sector de 25, **dinámico** y **dirigido** ambos final de 150 unidades, más los retrasos de las sincronizaciones necesarias, que ahora número sólo 40 y 20, respectivamente.