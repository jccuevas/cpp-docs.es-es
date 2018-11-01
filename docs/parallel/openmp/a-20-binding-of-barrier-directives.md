---
title: A.20 Enlace de directivas barrier
ms.date: 11/04/2016
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
ms.openlocfilehash: cf6f20a8539c47ca529af93e65f3a5fe244228d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652951"
---
# <a name="a20---binding-of-barrier-directives"></a>A.20 Enlace de directivas barrier

El enlace de la directiva de reglas de llamada para un **barrera** directiva para enlazar con la envolvente más cercana `parallel` directiva. Para obtener más información sobre el enlace de directivas, consulte [sección 2.8](../../parallel/openmp/2-8-directive-binding.md) en la página 32.

En el ejemplo siguiente, la llamada de *principal* a *sub2* es compatible porque la **barrera** (en *sub3*) se enlaza a la región paralela en *sub2*. La llamada de *principal* a *sub1* es compatible porque la **barrera** enlaza a la región paralela en la subrutina *sub2*.  La llamada de *principal* a *sub3* es compatible porque la **barrera** no enlazar a cualquier región paralela y se omite. Tenga en cuenta también que la **barrera** sólo sincroniza de subprocesos en la región paralela envolvente y no todos los subprocesos creados en el equipo de *sub1*.

```
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```