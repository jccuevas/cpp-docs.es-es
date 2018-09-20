---
title: A.20 enlace de directivas barrier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 628920caa6a122230f42394cc757e3abdb1874cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381314"
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