---
title: Advertencia del compilador C4972
ms.date: 11/04/2016
f1_keywords:
- C4972
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
ms.openlocfilehash: dcf08f26809c7c61e3e00c41c555416c95f4a0e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598840"
---
# <a name="compiler-warning-c4972"></a>Advertencia del compilador C4972

No se puede comprobar la modificación o el tratamiento directo del resultado de una operación de conversión unbox como valor L

Si se desreferencia un controlador en un tipo de valor, que también conoce como conversión unboxing y después se asigna a él, no es comprobable.

Para obtener más información, consulta [Boxing](../../windows/boxing-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4972.

```
// C4972.cpp
// compile with: /clr:safe
using namespace System;
ref struct R {
   int ^ p;   // a value type
};

int main() {
   R ^ r = gcnew R;
   *(r->p) = 10;   // C4972

   // OK
   r->p = 10;
   Console::WriteLine( r->p );
   Console::WriteLine( *(r->p) );
}
```