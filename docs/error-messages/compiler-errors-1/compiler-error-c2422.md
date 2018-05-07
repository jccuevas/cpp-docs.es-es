---
title: Error del compilador C2422 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a808e4b324b11c88be38ae7d8815bee4e232cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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