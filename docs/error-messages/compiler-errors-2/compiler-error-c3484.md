---
title: Error del compilador C3484 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de302987e4ea56e9ee6f29bed1b5842579a8f5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251961"
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