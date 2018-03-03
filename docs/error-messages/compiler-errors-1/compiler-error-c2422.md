---
title: Error del compilador C2422 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 852a495406a8baf147fc53262f8fe856fce726b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2422"></a>Error del compilador C2422
invalidación de segmento no válido en 'operando'  
  
 Código ensamblador en línea utiliza incorrectamente un operador de reemplazo de segmento (dos puntos) en un operando.  Entre las posibles causas se incluyen:  
  
-   El registro que precede al operador no es un registro de segmento.  
  
-   El registro que precede al operador no es el único registro de segmento del operando.  
  
-   El operador de reemplazo de segmento aparece dentro de un operador de direccionamiento indirecto (paréntesis).  
  
-   La expresión que sigue al operador de reemplazo de segmento no es un operando inmediato o un operando de memoria.  
  
 El ejemplo siguiente genera C2422:  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```