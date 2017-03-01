---
title: Compilador advertencia (nivel 1) C4382 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: 7
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 4571fe618b0ae89251d2748fbbcdfcb654201054
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4382"></a>Advertencia del compilador (nivel 1) C4382
produciendo 'tipo': un tipo con el destructor __clrcall o copiar el constructor solo puede capturarse en/CLR: pure módulo  
  
 El **/CLR: pure** opción del compilador está desusada en Visual Studio 2015.  
  
 Cuando se compila con **/CLR** (no **/CLR: pure**), control de excepciones espera que las funciones miembro de un tipo nativo sean [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro con `__clrcall` convención de llamada no pueden detectarse en un módulo compilado con **/CLR**.  
  
 Si la excepción será detectada en un módulo compilado con **/CLR: pure**, puede omitir esta advertencia.  
  
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
