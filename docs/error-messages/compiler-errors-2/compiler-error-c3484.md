---
title: Error del compilador C3484 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a8b8a5f9f51b2c3df57ab8a79e0f514a3c37a2f1
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3484"></a>Error del compilador C3484
se esperaba '->' antes del tipo de valor devuelto  
  
 Se debe proporcionar `->` antes del tipo de valor devuelto de una expresión lambda.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Proporcione `->` antes del tipo de valor devuelto.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3484:  
  
```  
// C3484a.cpp  
  
int main()  
{  
   return []() . int { return 42; }(); // C3484  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se resuelve el error C3484 al proporcionar `->` antes del tipo de valor devuelto de la expresión lambda:  
  
```  
// C3484b.cpp  
  
int main()  
{  
   return []() -> int { return 42; }();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
