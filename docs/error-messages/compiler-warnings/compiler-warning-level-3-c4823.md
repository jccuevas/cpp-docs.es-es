---
title: Advertencia del compilador (nivel 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: a96877252b0b7699f5e4033f8e695f4d9016a6c9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541261"
---
# <a name="compiler-warning-level-3-c4823"></a>Advertencia del compilador (nivel 3) C4823

' función ': usa punteros anclados pero la semántica de desenredo no está habilitada. Considere la posibilidad de usar/EHa

Para desanclar un objeto en el montón administrado al que apunta un puntero anclado declarado en un ámbito de bloque, el compilador simula el comportamiento de los destructores de clases locales, "fingiendo" que el puntero anclado tiene un destructor que anula el puntero. Para habilitar una llamada a un destructor después de producir una excepción, debe habilitar el desenredo de objetos, que puede hacer mediante [/EHsc](../../build/reference/eh-exception-handling-model.md).

También puede desanclar el objeto manualmente y omitir la advertencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4823.

```cpp
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
