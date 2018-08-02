---
title: Reglas y limitaciones de las funciones Naked | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d49f915174383273f538c38a6ec002558601ca10
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466675"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Reglas y limitaciones de las funciones naked
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Las reglas y las limitaciones siguientes se aplican a las funciones naked:  
  
-   El **devolver** no permite la instrucción.  
  
-   Las construcciones de control estructurado de excepciones y control de excepciones de C++ no se permiten porque deben desenredarse a través del marco de la pila.  
  
-   Por la misma razón, se prohíbe cualquier forma de `setjmp`.  
  
-   Se prohíbe el uso de la función `_alloca`.  
  
-   Para asegurarse de que no aparezca ningún código de inicialización para las variables locales antes de la secuencia de prólogo, las variables locales inicializadas no se permiten en el ámbito de la función. En particular, la declaración de objetos de C++ no se permite en el ámbito de la función. Sin embargo, puede haber datos inicializados en un ámbito anidado.  
  
-   La optimización del puntero de marco (la opción del compilador /Oy) no se recomienda y se suprime automáticamente en una función naked.  
  
-   No se pueden declarar objetos de clase de C++ en el ámbito léxico de la función. Sin embargo, se pueden declarar objetos en un bloque anidado.  
  
-   El **naked** se omite la palabra clave cuando se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
-   Para [__fastcall](../cpp/fastcall.md) funciones naked, siempre que haya una referencia en el código de C o C++ en uno de los argumentos del registro, el código de prólogo debe almacenar los valores de ese registro en la ubicación de la pila para esa variable. Por ejemplo:  
  
```cpp 
// nkdfastcl.cpp  
// compile with: /c  
// processor: x86  
__declspec(naked) int __fastcall  power(int i, int j) {  
   // calculates i^j, assumes that j >= 0  
  
   // prolog  
   __asm {  
      push ebp  
      mov ebp, esp  
      sub esp, __LOCAL_SIZE  
     // store ECX and EDX into stack locations allocated for i and j  
     mov i, ecx  
     mov j, edx  
   }  
  
   {  
      int k = 1;   // return value  
      while (j-- > 0)   
         k *= i;  
      __asm {   
         mov eax, k   
      };  
   }  
  
   // epilog  
   __asm {  
      mov esp, ebp  
      pop ebp  
      ret  
   }  
}  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Llamadas de función naked](../cpp/naked-function-calls.md)