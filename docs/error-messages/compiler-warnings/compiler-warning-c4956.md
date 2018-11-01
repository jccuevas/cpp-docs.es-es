---
title: Advertencia del compilador C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: c15de8b22f56a2555cc763a45153139b1df01a31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449106"
---
# <a name="compiler-warning-c4956"></a>Advertencia del compilador C4956

> '*tipo*': este tipo no es comprobable

## <a name="remarks"></a>Comentarios

Esta advertencia se genera cuando se especifica [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) y el código contiene un tipo que no es comprobable. El **/CLR: safe** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Para obtener más información, consulte [código puro y comprobable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```