---
title: C2743 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a762a7c816f713f9371ff50524ccb582753535b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2743"></a>C2743 de Error del compilador
'type': no se puede detectar un tipo nativo con el destructor __clrcall o el constructor de copias  
  
 Un módulo compilado con **/CLR** intentó detectar una excepción de tipo nativo y que usa el destructor del tipo o el constructor de copias `__clrcall` convención de llamada.  
  
 Cuando se compila con **/CLR**, control de excepciones espera que las funciones miembro de un tipo nativo como [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro con `__clrcall` no se puede detectar la convención de llamada en un módulo compilado con **/CLR**.  
  
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