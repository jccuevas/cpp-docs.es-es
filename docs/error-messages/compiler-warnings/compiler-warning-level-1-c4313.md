---
title: Error de compilador advertencia (nivel 1) C4313 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4313
dev_langs:
- C++
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b90fe384ac3396e73eb2fc69aab3a6d48552adf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4313"></a>Advertencia del compilador (nivel 1) C4313
'function': 'format specifier' en cadena de formato entra en conflicto con el número de argumento de tipo 'type'  
  
 Hay un conflicto entre el formato especificado y el valor que está pasando. Por ejemplo, ha pasado un parámetro de 64 bits a un especificador de formato %d sin calificar, que espera un parámetro de entero de 32 bits. Esta advertencia solo tiene efecto cuando el código se compila para destinos de 64 bits.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente genera el error C4313 cuando se compila para un destino de 64 bits.  
  
```  
// C4313.cpp  
// Compile by using: cl /W1 C4313.cpp  
#include <stdio.h>  
int main() {  
   int * pI = 0;  
   printf("%d", pI);   // C4313 on 64-bit platform code  
   // Try one of the following lines instead:  
   // printf("%p\n", pI);  
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information  
}  
```