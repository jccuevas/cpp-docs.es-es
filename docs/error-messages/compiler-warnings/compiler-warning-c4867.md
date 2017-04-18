---
title: Advertencia del compilador C4867 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: a052194893db90177b88eea8f80435777ae37773
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4867"></a>Advertencia del compilador C4867
'función': falta la lista de argumentos; la llamada a función Use 'llamar a' para crear un puntero a miembro  
  
 Un puntero a una función miembro se inicializó incorrectamente.  
  
 Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: conformidad de puntero a miembro mejorada.  Código que se compiló antes de Visual C++ 2005 ahora generará C4867.  
  
 Esta advertencia siempre se emite como error. Use la [advertencia](../../preprocessor/warning.md) pragma para deshabilitar esta advertencia. Para obtener más información sobre C4867 y MFC/ATL, vea [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4867.  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```
