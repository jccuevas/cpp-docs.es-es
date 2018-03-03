---
title: Compilador (nivel 1) de la advertencia C4311 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2f4b7d7c9ac57f5bdc3fd219c7682e0ec639d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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