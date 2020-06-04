---
title: Advertencia del compilador C4958
ms.date: 11/04/2016
f1_keywords:
- C4958
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
ms.openlocfilehash: 63371d91367902c1eab539cb370e55440fcbf917
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164890"
---
# <a name="compiler-warning-c4958"></a>Advertencia del compilador C4958

> '*Operation*': la aritmética de puntero no se pudo comprobar

## <a name="remarks"></a>Observaciones

El uso de la aritmética de puntero producirá una imagen no comprobable.

Para obtener más información, consulte [código puro y comprobableC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

La opción del compilador **/clr: Safe** está en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Esta advertencia se emite como un error y se puede deshabilitar con la pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4958:

```cpp
// C4958.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )
using namespace System;

int main( ) {
   Int32 arr[] = new Int32[10];
   Int32* p = &arr[0];
   p++;   // C4958
}
```

El compilador implementa operaciones de matriz con aritmética de puntero. Por lo tanto, las matrices nativas no son comprobables; use una matriz de CLR en su lugar. Para obtener más información, vea [Matriz](../../extensions/arrays-cpp-component-extensions.md).

El ejemplo siguiente genera la advertencia C4958:

```cpp
// C4958b.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )

int main() {
   int array[5];
   array[4] = 0;   // C4958
}
```
