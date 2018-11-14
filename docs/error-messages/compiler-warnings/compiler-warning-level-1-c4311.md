---
title: Advertencia del compilador (nivel 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 5f9b8ce710879913fdad1be5c0f22f8e3f4ed9d7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518169"
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