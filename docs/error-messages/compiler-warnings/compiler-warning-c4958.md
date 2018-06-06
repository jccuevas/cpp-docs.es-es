---
title: Advertencia del compilador C4958 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4958
dev_langs:
- C++
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e32acc4ec45275976e7fb56f993b10ba8a2a855
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704878"
---
# <a name="compiler-warning-c4958"></a>Advertencia del compilador C4958

> '*operación*': la aritmética con punteros no es comprobable

## <a name="remarks"></a>Comentarios

El uso de la aritmética de puntero producirá una imagen no comprobable.

Para obtener más información, consulte [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

El **/CLR: safe** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

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

El compilador implementa operaciones de matriz con aritmética de puntero. Por lo tanto, las matrices nativas no son comprobables; use una matriz de CLR en su lugar. Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).

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