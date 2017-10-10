---
title: Error del compilador C3073 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3073
dev_langs:
- C++
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 860cc8fccb545a8c66a8a5724b9854e9547deb10
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3073"></a>Error del compilador C3073
'type': clase ref no tiene un constructor de copias definido por el usuario  
  
 En un [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) compilación, el compilador no generará un constructor de copias para un tipo de referencia. En cualquier **/CLR** compilación, debe definir su propio constructor de copias para un tipo de referencia si espera que una instancia del tipo que se va a copiar.  
  
 Para obtener más información, consulte [semántica de pila de C++ para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3073.  
  
```  
// C3073.cpp  
// compile with: /clr  
ref class R {  
public:  
   R(int) {}  
};  
  
ref class S {  
public:  
   S(int) {}  
   S(const S %rhs) {}   // copy constructor  
};  
  
void f(R) {}  
void f2(S) {}  
void f3(R%){}  
  
int main() {  
   R r(1);  
   f(r);   // C3073  
   f3(r);   // OK  
  
   S s(1);  
   f2(s);   // OK  
}  
```
