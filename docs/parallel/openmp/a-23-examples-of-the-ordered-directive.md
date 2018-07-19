---
title: Ejemplos A.23 de la directiva ordenada | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37cc4ea9db8cbd1a7bf095e2bde0ae482053a584
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692761"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23 Ejemplos de la directiva ordered
Es posible tener varias secciones ordenadas con una `for` especificado con el `ordered` cláusula. El primer ejemplo no es conforme, porque la API especifica lo siguiente:  
  
 "Una iteración de un bucle con una `for` construcción no debe ejecutar la misma `ordered` directiva más de una vez y no deben ejecutar más de un `ordered` directiva." (Consulte [sección 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) en página 22)  
  
 En este ejemplo no compatible, todas las iteraciones ejecutan 2 secciones ordenadas:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 Se muestra en el siguiente ejemplo compatible con un `for` con más de una sección ordenada:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```