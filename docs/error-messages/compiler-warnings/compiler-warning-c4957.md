---
title: Advertencia del compilador C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 9afdd213baadd907afacde0ff7f14f3c78bc60a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528263"
---
# <a name="compiler-warning-c4957"></a>Advertencia del compilador C4957

> '*cast*': conversión explícita de '*cast_from*'para'*cast_to*' no es comprobable

## <a name="remarks"></a>Comentarios

Una conversión producirá una imagen no comprobable.

Algunas conversiones son seguras (por ejemplo, un elemento `static_cast` que desencadena conversiones definidas por el usuario y un elemento `const_cast`). Se garantiza que un elemento [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) genera código comprobable.

Para obtener más información, consulte [código puro y comprobable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

El **/CLR: safe** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

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