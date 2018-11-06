---
title: A.24 Ejemplo de la cláusula private
ms.date: 11/04/2016
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
ms.openlocfilehash: facf5b953b26d284f6bfed4f35a9162f6d2bf212
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552963"
---
# <a name="a24---example-of-the-private-clause"></a>A.24 Ejemplo de la cláusula private

El `private` cláusula ([sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25) de una región paralela sólo tiene efecto en el ámbito léxico de la región, pero no para la extensión dinámica de la región.  Por lo tanto, en el ejemplo siguiente, todos los usos de la variable *un* dentro de la `for` bucle en la rutina *f* hace referencia a una copia privada de *un*, mientras que un uso en rutina *g* hace referencia a la plantilla global *un*.

```
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```