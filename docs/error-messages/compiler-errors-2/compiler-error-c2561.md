---
title: Error del compilador C2561 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8ece9a3d9347a5179844cbfca3425870c25e2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230909"
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