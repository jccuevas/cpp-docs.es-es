---
title: Advertencia del compilador (nivel 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 84834ce0f980502e16a8398d35da85d1a005c9cb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990552"
---
# <a name="compiler-warning-level-4-c4668"></a>Advertencia del compilador (nivel 4) C4668

'símbolo' no está definido como macro de preprocesador y se reemplaza por '0' para 'directivas'

Se usó un símbolo que no se definió con una directiva de preprocesador. El símbolo se evaluará como false. Para definir un símbolo, puede usar la [directiva #define](../../preprocessor/hash-define-directive-c-cpp.md) o la opción del compilador [/d](../../build/reference/d-preprocessor-definitions.md) .

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4668:

```cpp
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```
