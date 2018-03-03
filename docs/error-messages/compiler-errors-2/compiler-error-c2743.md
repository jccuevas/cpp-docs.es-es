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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29826dde6b9f92dd01e3a6420eed0d836660121f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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