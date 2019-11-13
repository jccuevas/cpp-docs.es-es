---
title: ADVERTENCIA del compilador (nivel 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: b49696632fb567a943b42ac35b8fc244e6cc4fb4
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051695"
---
# <a name="compiler-warning-level-3-c4267"></a>ADVERTENCIA del compilador (nivel 3) C4267

'var': conversión de 'size_t' a 'type'; posible pérdida de datos

El compilador detectó una conversión de `size_t` a un tipo más pequeño.

Para corregir esta advertencia, use `size_t` en lugar de `type`. También puede usar un tipo entero que sea al menos tan grande como `size_t`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4267.

```cpp
// C4267.cpp
// compile by using: cl /W4 C4267.cpp
void Func1(short) {}
void Func2(int) {}
void Func3(long) {}
void Func4(size_t) {}

int main() {
   size_t bufferSize = 10;
   Func1(bufferSize);   // C4267 for all platforms
   Func2(bufferSize);   // C4267 only for 64-bit platforms
   Func3(bufferSize);   // C4267 only for 64-bit platforms
   Func4(bufferSize);   // OK for all platforms
}
```