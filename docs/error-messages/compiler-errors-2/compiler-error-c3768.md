---
title: Error del compilador C3768 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3768
dev_langs:
- C++
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d334473e326f28a628ebda9dede7a83340a1cb34
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3768"></a>Error del compilador C3768
no se puede adquirir la dirección de una función vararg virtual en código administrado puro  
  
 El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015.  
  
 Cuando se compila con `/clr:pure`, no se puede adquirir la dirección de una memoria virtual `vararg` función.  
  
## <a name="example"></a>Ejemplo  

 El ejemplo siguiente genera C3768:  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```
