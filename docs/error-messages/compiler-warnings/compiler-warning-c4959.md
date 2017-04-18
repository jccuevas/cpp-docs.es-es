---
title: Advertencia del compilador C4959 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4959
dev_langs:
- C++
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: f7cde1151bd220415b950dcce089265be118de34
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4959"></a>Advertencia del compilador C4959
no se puede definir la estructura no administrada 'type' en /clr:safe porque el acceso a sus miembros proporciona código que no se puede comprobar  
  
 El acceso a un miembro de un tipo no administrado generará una imagen que no se puede comprobar (peverify.exe).  
  
 Para obtener más información, consulte [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Esta advertencia se emite como un error y puede deshabilitarse con la [advertencia](../../preprocessor/warning.md) pragma o [/wd](../../build/reference/compiler-option-warning-level.md) opción del compilador.  
  
 El ejemplo siguiente genera la advertencia C4959:  
  
```  
// C4959.cpp  
// compile with: /clr:safe  
  
// Uncomment the following line to resolve.  
// #pragma warning( disable : 4959 )  
struct X {  
   int data;  
};  
  
int main() {  
   X x;  
   x.data = 10;   // C4959  
}  
```
