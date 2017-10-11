---
title: Error del compilador C3482 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b19769a8a326613401263fa7700b85c36a9dbbe1
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3482"></a>Error del compilador C3482
'this' solo se puede usar como captura lambda en una función miembro no estática  
  
 No se puede pasar `this` a la lista de captura de una expresión lambda declarada en un método estático o una función global.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Convierta la función de inclusión a un método no estático, o  
  
-   Quite el puntero `this` de la lista de captura de la expresión lambda.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo genera el error C3482:  
  
```  
// C3482.cpp  
// compile with: /c  
  
class C  
{  
public:  
   static void staticMethod()  
   {  
      [this] {}(); // C3482  
   }  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
