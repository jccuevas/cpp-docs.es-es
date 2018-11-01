---
title: A.19 Ejemplos donde se muestra un anidamiento incorrecto de directivas de uso compartido
ms.date: 11/04/2016
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
ms.openlocfilehash: 5be09dd3282260dabc2ef30dafc249539d6a6418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501951"
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 Ejemplos donde se muestra un anidamiento incorrecto de directivas de uso compartido

Los ejemplos en esta sección muestran las reglas de anidamiento de la directiva. Para obtener más información sobre el anidamiento de directivas, consulte [sección 2.9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33.

El ejemplo siguiente no es conforme porque interno y externo `for` directivas anidadas y enlazar a la misma `parallel` directiva:

```
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

La siguiente versión de forma dinámica anidada del ejemplo anterior también será no compatible:

```
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

El ejemplo siguiente no es compatible porque la `for` y `single` las directivas se pueden anidar y se enlazan a la misma región paralela:

```
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

El ejemplo siguiente no es conforme porque un `barrier` directiva dentro de un `for` puede producir un interbloqueo:

```
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

El ejemplo siguiente no es compatible porque la `barrier` da como resultado un interbloqueo debido al hecho de que sólo un subproceso a la vez puede entrar en la sección crítica:

```
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

El ejemplo siguiente no es compatible porque la `barrier` da como resultado un interbloqueo debido al hecho de que sólo un subproceso ejecuta el `single` sección:

```
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```