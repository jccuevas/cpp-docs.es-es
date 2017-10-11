---
title: Error del compilador C2561 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ce30ffb454deb7bc847e736458295d037826a0ad
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2561"></a>Error del compilador C2561
'identificador': función debe devolver un valor  
  
 La función se declaró como devolver un valor, pero la definición de función no contiene una `return` instrucción.  
  
 Este error puede deberse a un prototipo de función incorrecto:  
  
1.  Si la función no devuelve un valor, declare la función con el tipo de valor devuelto [void](../../cpp/void-cpp.md).  
  
2.  Compruebe que todas las ramas posibles de la función devuelven un valor del tipo declarado en el prototipo.  
  
3.  Las funciones de C++ que contienen rutinas de ensamblado en línea que almacenan el valor devuelto en el `AX` register puede requerir una instrucción return. Copie el valor en `AX` a una variable temporal y devolver esa variable de la función.  
  
 El ejemplo siguiente genera C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```
