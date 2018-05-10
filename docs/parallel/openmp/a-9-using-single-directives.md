---
title: A.9 Using únicas directivas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e0e08b0b7bdea05bf4c627ae33cc42298c6dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a9---using-single-directives"></a>A.9 Usar directivas single
En el ejemplo siguiente se muestra la `single` directiva ([sección 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) en la página 15). En el ejemplo, un solo subproceso (normalmente el primer subproceso que se encuentra el `single` directiva) imprime el mensaje de progreso. El usuario no debe hacer ninguna suposición como a qué subproceso se ejecutará la `single` sección. Todos los demás subprocesos se omitirán el `single` sección y se detendrá en la barrera al final de la `single` construir. Si otros subprocesos pueden continuar sin tener que esperar el subproceso que ejecuta el `single` sección, un `nowait` cláusula puede especificarse en el `single` directiva.  
  
```  
#pragma omp parallel  
{  
    #pragma omp single  
        printf_s("Beginning work1.\n");  
    work1();  
    #pragma omp single  
        printf_s("Finishing work1.\n");  
    #pragma omp single nowait  
        printf_s("Finished work1 and beginning work2.\n");  
    work2();  
}  
```