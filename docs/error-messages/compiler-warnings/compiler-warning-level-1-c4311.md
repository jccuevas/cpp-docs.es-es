---
title: Compilador (nivel 1) de la advertencia C4311 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba06488ed41e7e296f9f6c16f34af827274acfd4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4311"></a>Advertencia del compilador (nivel 1) C4311
'variable' : truncamiento de puntero de 'tipo' a 'tipo'  
  
 Esta advertencia detecta problemas de truncamiento de puntero de 64 bits. Por ejemplo, si el código se compila para una arquitectura de 64 bits, el valor de un puntero (64 bits) se truncará si se asigna a un `int` (32 bits). Para obtener más información, consulte [reglas para usar punteros](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 Para obtener información adicional acerca de las causas comunes de advertencia C4311, vea [errores comunes del compilador](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 En el ejemplo de código siguiente se genera la advertencia C4311 cuando se compila para un destino de 64 bits; a continuación, se muestra cómo corregirlo:  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```