---
title: Advertencia del compilador (nivel 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: 31e5b9a9b8e7b25a0d54648ce808ff6266a27321
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402182"
---
# <a name="compiler-warning-level-3-c4267"></a>Advertencia del compilador (nivel 3) C4267

'var': conversión de 'size_t' a 'type'; posible pérdida de datos

El compilador detectó una conversión de `size_t` a un tipo más pequeño.

Para corregir esta advertencia, use `size_t` en lugar de `type`. También puede usar un tipo entero que sea al menos tan grande como `size_t`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4267.

```
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