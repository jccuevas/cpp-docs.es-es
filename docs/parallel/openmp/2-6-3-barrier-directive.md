---
title: 2.6.3 barrier (directiva) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d9c64787d9c6cc2dd0809f75f8f9db9819174d0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="263-barrier-directive"></a>2.6.3 barrier (Directiva)
El **barrera** directiva sincroniza todos los subprocesos en un equipo. Cuando encuentra, cada subproceso en el equipo espera hasta que todos los demás han alcanzado este punto. La sintaxis de la **barrera** directiva es como sigue:  
  
```  
#pragma omp barrier new-line  
```  
  
 Después de que todos los subprocesos en el equipo han detectado la barrera, cada subproceso en el equipo empieza a ejecutar las instrucciones después de la directiva de barrera en paralelo. Tenga en cuenta que, dado el **barrera** directiva no tiene una instrucción del lenguaje C como parte de su sintaxis, hay algunas restricciones en su posición dentro de un programa. Vea [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) para la gramática formal. En el ejemplo siguiente se muestra estas restricciones.  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```