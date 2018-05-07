---
title: Compilador advertencia (nivel 1) C4382 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c02f0cb2d22aebb9af31844aec3bf68b97c3442e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4382"></a>Advertencia del compilador (nivel 1) C4382
produciendo 'tipo': solamente se puede detectar un tipo con el destructor __clrcall o el constructor de copias en/CLR: pure módulo  
  
 El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015.  
  
 Cuando se compila con **/CLR** (no **/CLR: pure**), control de excepciones espera que las funciones miembro de un tipo nativo como [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro con `__clrcall` no se puede detectar la convención de llamada en un módulo compilado con **/CLR**.  
  
 Si la excepción se capturará en un módulo compilado con **/CLR: pure**, puede omitir esta advertencia.  
  
 Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4382.  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```