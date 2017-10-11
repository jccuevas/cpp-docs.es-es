---
title: Error del compilador C3496 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 86c80c4b708bd4315b2ce2ceaf7b61e0629a8b2e
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3496"></a>Error del compilador C3496
'this' siempre se captura por valor: se ha omitido '&'  
  
 No se puede capturar el `this` puntero por referencia.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Capture el puntero `this` por valor.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3496 porque una referencia al puntero `this` aparece en la lista de captura de una expresión lambda:  
  
```  
// C3496.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      [&this] {}(); // C3496  
   }  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
