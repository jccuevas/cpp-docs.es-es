---
title: C2743 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 7420231e64515b556cfe81fc695eda5f75231506
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2743"></a>C2743 de Error del compilador
'tipo': no se puede detectar un tipo nativo con el destructor __clrcall o el constructor de copias  
  
 Un módulo compilado con **/CLR** intentó detectar una excepción de tipo nativo y que usa el destructor del tipo o el constructor de copias `__clrcall` convención de llamada.  
  
 Cuando se compila con **/CLR**, control de excepciones espera que las funciones miembro de un tipo nativo sean [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro con `__clrcall` convención de llamada no pueden detectarse en un módulo compilado con **/CLR**.  
  
 Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2743.  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```
