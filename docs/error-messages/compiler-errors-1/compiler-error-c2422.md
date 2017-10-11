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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 65412576c3c1a5e6b8205652d826d0eca6d222e6
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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
