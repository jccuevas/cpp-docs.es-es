---
title: Error del compilador C3482 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3482
dev_langs: C++
helpviewer_keywords: C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ff7a17d663be7168c5743838d782043d7c0ee92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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