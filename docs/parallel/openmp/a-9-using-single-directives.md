---
title: "A.9 Using únicas directivas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11d41d62448d41d7a11ef747e65cc6ac47e4bd7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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