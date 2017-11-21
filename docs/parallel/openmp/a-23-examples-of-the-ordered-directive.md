---
title: Ejemplos A.23 de la directiva ordenada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b1d6f50eed2c4e89576dd4c17c5a87599bf59e4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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