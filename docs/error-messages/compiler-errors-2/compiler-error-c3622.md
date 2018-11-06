---
title: Error del compilador C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518097"
---
# <a name="compiler-error-c3622"></a>Error del compilador C3622

'class': una clase declarada como 'palabra clave' no pueden crearse instancias

Se intentó crear una instancia de una clase marcada como [abstracta](../../windows/abstract-cpp-component-extensions.md). Una clase marcada como `abstract` puede ser una clase base, pero no pueden crearse instancias.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
