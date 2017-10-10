---
title: Error del compilador C2975 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2975
dev_langs:
- C++
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 07b2b96cd79364215c9a859a9fd0282768ff45e4
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2975"></a>Error del compilador C2975
'arg': argumento de plantilla no válido para 'type', se esperaba una expresión constante tiempo de compilación  
  
 El argumento de plantilla no coincide con la declaración de plantilla; una expresión constante debe aparecer dentro de los corchetes angulares. No se permiten variables como argumentos de plantilla. Compruebe la definición de plantilla para encontrar los tipos correctos.  
  
 El ejemplo siguiente genera el error C2975:  
  
```  
// C2975.cpp  
template<int I>  
class X {};  
  
int main() {  
   int i = 4, j = 2;  
   X<i + j> x1;   // C2975  
   X<6> x2;   // OK  
}  
```  
  
 También se producirá el error C2975 cuando usas __LINE\_ \_ como una constante de tiempo de compilación con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Una solución sería compilar con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en lugar de **/Zi**.  
  
```  
// C2975b.cpp  
// compile with: /ZI  
// processor: x86  
template<long line>   
void test(void) {}  
  
int main() {  
   test<__LINE__>();   // C2975  
}  
```
