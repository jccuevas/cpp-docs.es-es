---
title: Advertencia del compilador C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 340c26c97d0b5b686eee487cd3fd8b6b05bdf373
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164916"
---
# <a name="compiler-warning-c4957"></a>Advertencia del compilador C4957

> '*Cast*': la conversión explícita de '*cast_from*' a '*cast_to*' no es comprobable

## <a name="remarks"></a>Observaciones

Una conversión producirá una imagen no comprobable.

Algunas conversiones son seguras (por ejemplo, un elemento `static_cast` que desencadena conversiones definidas por el usuario y un elemento `const_cast`). Se garantiza que un elemento [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) genera código comprobable.

Para obtener más información, consulte [código puro y comprobableC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

La opción del compilador **/clr: Safe** está en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Esta advertencia se emite como un error y se puede deshabilitar con la pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4957:

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
