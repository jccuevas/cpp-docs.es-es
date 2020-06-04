---
title: Advertencia del compilador (nivel 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 7b8dbf77defab2a711ad931057c740193908474b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186977"
---
# <a name="compiler-warning-level-1-c4382"></a>Advertencia del compilador (nivel 1) C4382

> produciendo '*Type*': un tipo con __clrcall destructor o un constructor de copias solo se puede detectar en el módulo/CLR: Pure

## <a name="remarks"></a>Observaciones

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Cuando se compila con **/CLR** (no **/clr: Pure**), el control de excepciones espera que las funciones miembro de un tipo nativo se [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro que utilicen `__clrcall` Convención de llamada no se pueden capturar en un módulo compilado con **/CLR**.

Si la excepción se detectará en un módulo compilado con **/clr: Pure**, puede omitir esta advertencia.

Para obtener más información, consulta [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```
