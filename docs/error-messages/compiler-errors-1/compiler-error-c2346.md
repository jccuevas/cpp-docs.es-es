---
title: Error del compilador C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: fc2aeac02ecc3f29406c2288051ca6cd9d3a4923
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760015"
---
# <a name="compiler-error-c2346"></a>Error del compilador C2346

' function ' no se puede compilar como Native: Reason

El compilador no pudo compilar una función en MSIL.

Para obtener más información, vea [Managed, Unmanaged](../../preprocessor/managed-unmanaged.md) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Quite el código de la función que no se puede compilar en MSIL.

1. No compile el módulo con **/CLR**o marque la función como no administrada con la Directiva Pragma no administrada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2346.

```cpp
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```
