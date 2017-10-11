---
title: Advertencia del compilador C4867 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 352b38744d83b3dc163125ff5ec8d80165f60c9a
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4867"></a>Advertencia del compilador C4867
'función': falta la lista de argumentos; la llamada a función Use 'llamar a' para crear un puntero a miembro  
  
 Un puntero a una función miembro se inicializó incorrectamente.  
  
 Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: conformidad de puntero a miembro mejorada.  Código que se compiló antes de Visual C++ 2005 ahora generará C4867.  
  
 Esta advertencia siempre se emite como error. Para deshabilitar esta advertencia, use la pragma [warning](../../preprocessor/warning.md) . Para obtener más información sobre C4867 y MFC/ATL, vea [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).  
  
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
