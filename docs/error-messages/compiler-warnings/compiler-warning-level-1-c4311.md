---
title: Advertencia del compilador (nivel 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 52f8338423b5e3366b85207477b3b1ee5e9c399f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163107"
---
# <a name="compiler-warning-level-1-c4311"></a>Advertencia del compilador (nivel 1) C4311

'variable' : truncamiento de puntero de 'tipo' a 'tipo'

Esta advertencia detecta problemas de truncamiento de puntero de 64 bits. Por ejemplo, si el código se compila para una arquitectura de 64 bits, el valor de un puntero (64 bits) se truncará si se asigna a un `int` (32 bits). Para obtener más información, consulte [reglas para usar punteros](/windows/win32/WinProg64/rules-for-using-pointers).

Para obtener información adicional sobre las causas comunes de C4311 de advertencia, vea [errores comunes del compilador](/windows/win32/WinProg64/common-compiler-errors).

En el ejemplo de código siguiente se genera la advertencia C4311 cuando se compila para un destino de 64 bits; a continuación, se muestra cómo corregirlo:

```cpp
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```
