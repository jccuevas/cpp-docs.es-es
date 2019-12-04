---
title: Error del compilador C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 2adcee4cb20c39c39b06e0ac2087478cfe2d8937
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740902"
---
# <a name="compiler-error-c3622"></a>Error del compilador C3622

' Class ': no se puede crear una instancia de una clase declarada como ' keyword '

Se intentó crear una instancia de una clase marcada como [abstracta](../../extensions/abstract-cpp-component-extensions.md). Una clase marcada como `abstract` puede ser una clase base, pero no se pueden crear instancias de ella.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3622.

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
