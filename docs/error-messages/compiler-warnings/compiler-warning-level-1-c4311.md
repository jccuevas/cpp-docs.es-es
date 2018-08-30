---
title: Del compilador (nivel 1) de la advertencia C4311 | Microsoft Docs
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
ms.openlocfilehash: adfd27a116ae5747a2dd899ce51c38f01055f356
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218545"
---
# <a name="compiler-warning-level-1-c4311"></a>Advertencia del compilador (nivel 1) C4311
'variable' : truncamiento de puntero de 'tipo' a 'tipo'  
  
 Esta advertencia detecta problemas de truncamiento de puntero de 64 bits. Por ejemplo, si el código se compila para una arquitectura de 64 bits, el valor de un puntero (64 bits) se truncará si se asigna a un `int` (32 bits). Para obtener más información, consulte [reglas para usar punteros](/windows/desktop/WinProg64/rules-for-using-pointers).  
  
 Para obtener más información acerca de las causas comunes de advertencia C4311, vea [errores comunes del compilador](/windows/desktop/WinProg64/common-compiler-errors).  
  
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