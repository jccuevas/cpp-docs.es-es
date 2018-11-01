---
title: A.29 Uso de construcciones de uso compartido en una construcción critical
ms.date: 11/04/2016
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
ms.openlocfilehash: fac5576f859f63298d658b51c4307bb238e301c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643591"
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29 Uso de construcciones de uso compartido en una construcción critical

El ejemplo siguiente se muestra cómo utilizar una construcción de uso compartido dentro de un `critical` construir. En este ejemplo es compatible porque el uso compartido de construir y `critical` construcción no enlazar a la misma región paralela.

```
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```