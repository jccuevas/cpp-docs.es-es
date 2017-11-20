---
title: Error del compilador C3487 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3487
dev_langs: C++
helpviewer_keywords: C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb659f2d7971d1dd2ff27c438839336d4744767e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3487"></a>Error del compilador C3487
'return type': todas las expresiones return deben deducirse como el mismo tipo: antes era 'return type'  
  
 Una expresión lambda debe especificar su tipo de valor devuelto a menos que contenga una sola instrucción return. Si una expresión lambda contiene varias instrucciones return, todas deben tener el mismo tipo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Especifique un tipo de valor devuelto final para la expresión lambda. Compruebe que todos los valores devueltos de la expresión lambda son del mismo tipo o pueden convertirse implícitamente al tipo de valor devuelto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3487 porque los tipos de valor devueltos de la expresión lambda no coinciden:  
  
```  
// C3487.cpp  
// Compile by using: cl /c /W4 C3487.cpp  
  
int* test(int* pi) {  
   // To fix the error, uncomment the trailing return type below  
   auto odd_pointer = [=]() /* -> int* */ {  
      if (*pi % 2)   
         return pi;  
      return nullptr; // C3487 - nullptr is not an int* type  
   };  
   return odd_pointer();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)