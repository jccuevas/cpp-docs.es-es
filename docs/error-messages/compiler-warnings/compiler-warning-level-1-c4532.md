---
title: Compilador advertencia (nivel 1) C4532 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44aae61190b20bf1ef93b586c02e88837d487324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4532"></a>Advertencia del compilador (nivel 1) C4532
'continue': saltar desde el bloque __finally/finally tiene un comportamiento indefinido durante el control de terminación  
  
 El compilador encontró una de las siguientes palabras clave:  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 causando un salto fuera de un [__finally](../../cpp/try-finally-statement.md) o [finalmente](../../dotnet/finally.md) bloque durante la terminación anormal.  
  
 Si se produce una excepción, y mientras se está desenredando la pila durante la ejecución de los controladores de terminación (la `__finally` o bloques finally), y el código salta fuera de un `__finally` bloquear antes de la `__finally` bloque finaliza, el comportamiento es indefinido. Puede no devolver el control al código de desenredado, por lo que la excepción no puede controlar correctamente.  
  
 Si debe saltar fuera de un **__finally** bloquear, busque primero la terminación anómala.  
  
 El ejemplo siguiente genera la advertencia C4532; comenta simplemente las instrucciones de salto para resolver las advertencias.  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```