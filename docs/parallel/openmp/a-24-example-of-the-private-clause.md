---
title: En el ejemplo de la cláusula privada se A.24 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f8d07f2d95b565077f5dfd78fdc4ff6edf30216
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a24---example-of-the-private-clause"></a>A.24 Ejemplo de la cláusula private
El `private` cláusula ([sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en página 25) de una región paralela solo tiene efecto en el ámbito léxico de la región, pero no para la extensión dinámica de la región.  Por lo tanto, en el ejemplo siguiente, todos los usos de la variable *una* dentro de la `for` bucle en la rutina *f* hace referencia a una copia privada de *un*, mientras que un uso en rutina *g* hace referencia a la plantilla global *un*.  
  
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