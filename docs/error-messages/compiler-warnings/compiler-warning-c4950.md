---
title: Advertencia del compilador C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 52c4de94dfe087b4dcf407295e556c9350b2cb8b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164994"
---
# <a name="compiler-warning-c4950"></a>Advertencia del compilador C4950

'tipo_o_miembro': marcado como obsoleto

Un miembro o tipo se marcó como obsoleto con el atributo <xref:System.ObsoleteAttribute>.

La advertencia C4950 siempre se emite como un error. Puede desactivar esta advertencia mediante la Directiva pragma [Warning](../../preprocessor/warning.md) o la opción del compilador [/WD](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4950:

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
