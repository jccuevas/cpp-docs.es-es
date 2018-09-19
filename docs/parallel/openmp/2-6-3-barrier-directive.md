---
title: 2.6.3 barrier (directiva) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68df92207feb45a77055098cdb1227a68b04bcab
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689797"
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