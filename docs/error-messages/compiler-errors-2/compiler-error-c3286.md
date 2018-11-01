---
title: Error del compilador C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 8c09ea34c7dabf2cadecad7c76d766c9496f5a5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461014"
---
# <a name="compiler-error-c3286"></a>Error del compilador C3286

> '*especificador*': una variable de iteración no puede tener especificadores de clase de almacenamiento

No se puede especificar una clase de almacenamiento en una variable de iteración. Para obtener más información, consulte [clases de almacenamiento (C++)](../../cpp/storage-classes-cpp.md) y [para cada uno, en](../../dotnet/for-each-in.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3286 y también muestra el uso correcto.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```