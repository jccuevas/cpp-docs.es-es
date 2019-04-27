---
title: Error del compilador C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: a6d75ca671e22203cb40ca18de21606834eeefa8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188096"
---
# <a name="compiler-error-c2346"></a>Error del compilador C2346

'function' no se puede compilar como nativa: razón

El compilador no pudo compilar una función en MSIL.

Para obtener más información, consulte [managed, unmanaged](../../preprocessor/managed-unmanaged.md) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Quite el código en la función que no se puede compilar en MSIL.

1. Cualquiera que no compile el módulo con **/CLR**, o marque la función como no administrados con el pragma no administrada.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2346.

```
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