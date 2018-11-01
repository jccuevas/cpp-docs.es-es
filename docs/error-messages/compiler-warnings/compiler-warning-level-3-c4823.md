---
title: Advertencia del compilador (nivel 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: 28d490c341c4d14c2e6c03e13007b5a8be423622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625924"
---
# <a name="compiler-warning-level-3-c4823"></a>Advertencia del compilador (nivel 3) C4823

'function': utiliza punteros anclados pero desenredo semántica no está habilitada. Considere el uso de /EHa

Para liberar un objeto en el montón administrado apuntado a un puntero anclado declarado en un ámbito de bloque, el compilador simula el comportamiento de los destructores de clases locales, "fingiendo" que el puntero anclado tenga un destructor que anula el puntero. Para habilitar una llamada a un destructor después de producir una excepción, debe habilitar desenredo de objetos, lo que puede hacer mediante el uso de [/EHsc](../../build/reference/eh-exception-handling-model.md).

Manualmente puede Desanclar el objeto y pasar por alto la advertencia.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4823.

```
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
