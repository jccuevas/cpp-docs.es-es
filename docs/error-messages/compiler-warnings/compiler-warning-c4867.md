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
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 86437fca7bfeef662bef9fe8311fb746a661264d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4867"></a>Advertencia del compilador C4867
'función': llamada de función falta la lista de argumentos; Utilice 'llamada' para crear un puntero a miembro  
  
 Un puntero a función miembro se inicializó incorrectamente.  
  
 Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual C++ 2005: compatibilidad mejorada de puntero a miembro.  Código que se compiló antes de Visual C++ 2005 ahora generará C4867.  
  
 Esta advertencia siempre se emite como error. Utilice la [advertencia](../../preprocessor/warning.md) pragma para deshabilitar esta advertencia. Para obtener más información sobre C4867 y MFC/ATL, vea [_ATL_ENABLE_PTM_WARNING](http://msdn.microsoft.com/Library/00b9ff5c-9834-4c40-911e-ee88d512c4af).  
  
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
