---
title: Error del compilador C3498 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0429b9d21829f772596b6d0fd2c51d72b0924e26
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3498"></a>Error del compilador C3498
'var': no se puede capturar una variable que tiene un tipo administrado o WinRTtype  
  
 No se puede capturar una variable que tiene un tipo administrado o un tipo de Windows Runtime en una expresión lambda.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Pase la variable administrada o de Windows Runtime a la lista de parámetros de la expresión lambda.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3498 porque una variable que tiene un tipo administrado aparece en la lista de captura de una expresión lambda:  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente resuelve C3498 al pasar la variable administrada `s` a la lista de parámetros de la expresión lambda:  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
